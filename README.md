# Setup-Nodejs-Shared-Hosting

Setup Nodejs specific version in Shared Hosting via ssh 


# First we need to find what version we need to download it and loaded in our shared hosting 

Here you will find all NodeJs version you want to installed on your hosting 

```
https://nodejs.org/dist/
```

# i will choose this version for this tutuorial 

v18.9.1

once i click on the page for example : https://nodejs.org/dist/v18.9.1/

you will find list of gz files i will choose >> node-v18.9.1-linux-x64.tar.gz

then i will download the version to my machine 

```
cd ~

wget https://nodejs.org/dist/v18.9.1/node-v18.9.1-linux-x64.tar.gz

```

# It’s now time to unpack the downloaded archive. Use the command:

```
tar xvf node-v18.9.1-linux-x64.tar.gz
```

Replace node-v18.9.1-linux-x64.tar.gz with the name of the archive you have downloaded in
your case.

Executing this command launches a long prompt with the names of the files that are getting extracted.
No worries; this is absolutely normal. It means that the unpacking process was successful.


# Rename the extracted folder to nodeext with the following command:

```
mv node-v18.9.1-linux-x64 nodejs
```

# Install the node and npm binaries using the following commands

```
mkdir ~/bin
cp nodejs/bin/node ~/bin
cd ~/bin
ln -s ../nodejs/lib/node_modules/npm/bin/npm-cli.js npm
```

# Node.js and NPM should now appear on the server. You can double-check they installed with the following commands:

```
node --version 
npm --version
```

or

```
node -v
npm -v
```

Run Node.js Apps


This guide describes the installation of Node.js and NPM on the server.
Naturally, you would like to use them with an actual application. There are different possible configurations for Node.js apps; as such, there are multiple ways to run them.

To run a Node.js application that is production-ready and has a package.json file included, you can use the following command:

nohup npm start --production &

In the case you are running a Node.js app that does not have a package.json file included, you can use the following prompt:

nohup node my_app.js &

In this case, you won’t be able to manage this application with npm.


How to stop an application


To stop a running Node.js application, you can execute the following command via SSH:

```
pkill node
```

This command kills any Node processes on the server.

# Connect your Website with a Running Node.js App

Apache is standard for cPanel installations. If you run Apache, you can use a specific
.htaccess file code to make your site work with the Node.js app. Follow these steps:

4. Enter the following code:

```
DirectoryIndex disabled
RewriteEngine On
RewriteRule ^$ http://127.0.0.1:XXXXX/ [P,L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ http://127.0.0.1:XXXXX/$1 [P,L]
```

## Now, replace XXXXX with the port your Node.js application is working on.

## Happy developing ## 
## Mahmoud Elkalamawy ## 
