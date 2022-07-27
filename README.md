# Intro-To-React
 
This is a brief intro of REACT and details file structure alongside the basics of REACT.


## Introduction to REACT

Built by Facebook/META, REACT is a javascript based framework for developing modern front-end applications. It's a client side framework meaning that you're primarily editing what the user sees. It's similar to other modern frameworks such as Vue or Angular. It's a tool used for building different UI components which can then be pieced together to make a full client front-end.

REACT requires good knowledge of JavaScript, HTML, and even CSS to some extent. It primarily relies on JavaScript so if your JavaScript background is weak, it might be a good idea to review up a bit.

REACT works by creating a virtual DOM in memory and before it actually makes change to the browser DOM, it does all the necessary manipulations. This leads to REACT being able to change only what needs to be changed once it finds out which changes are new and have been made.

## Node

Node JS is a JavaScript runtime. It's what we use to manage the backend and is used for building scalable network applications. 

For many REACT applications, Node is critical. Before continuining further, make sure you have Node installed by going to: https://nodejs.org/en/. Note that NPM should be included in your node installation. 

## NPM and NPX

NPM is the world's largest software registry. It holds pacakges which users can use in their applications and they can interact with it using the command line. It is bundled with Node and it will by highly useful for anything related to managing packages.

NPX lets you run a command from a local or remote npm package. For REACT, the main command we'll be doing is `npx create-react-app` which will create a template for us to use.To start, you'll just run the command `npx create-react-app name` where name is the name of the folder. You can also create it in the current folder using `npx create-react-app .`. If you're downloading the react application from online, you can use `npm install` which downloads all the required modules that are needed.

## Github
Since we'll be deploying this REACT application to Github, make sure you have GIT installed on your computer and a github account to use. Setting up github desktop may also be helpful.

## Github Pages
For deploymnent, we'll be making use of Github pages. Github pages will only deploy the front-end side of the REACT application. Github pages is use for static sites and will take all the HTML, CSS, and JavaScript then build it into a public website. Later on, we discuss how to deploy a site to github pages using the `gh-pages` npm package.

## REACT BOilerplate Structure
- node_modules: contains all the modules we use for the application
- Public
    - index.html: the only html file, the one the gets rendered
    - favicon.ico: icon symbol
    - manifest.json: makes the application into a progressive web app
    - robots.txt: information, if the website allows for web scraping
- src
    - App.css: css file 
    - Index.css: css file
    - App.js: file that typically combines components by importing them
    - serviceWorker.js: used to progressively add app features
    - setupTests.js: writes test cases
- package.json: list of all of the packages the application utilizes
- .gitignore: stores what we want github to ignore
- README.md: contains information on how to run the REACT application
- package-lock.json: locks the versions of all the packages used


## Deployment on Github Pages

Deploying to github will require you to use the `gh-pages` npm package. We'll first need to start off by creating an empty repository on GitHub with the following format:
- {username}.github.io (for example, priyanshumahey.github.io)

From there, open up that repo in a local computer and we'll create a react app in it. We can use 
``` shell
$ npx create-react-app website
```
Then we need to cd into the new folder and install `gh-pages` using npm:
``` shell
$ npm install gh-pages --save-dev
```

Then from there, we need to edit and add a homepage property to the package.json file.

Open the project.json file and add a homepage property in the form of:
https://{username}.github.io/{repo-name}. For example, this could look like:
``` JSON
{
  "name": "website",
  "version": "0.1.0",
  "homepage": "https://priyanshumahey.github.io/",
  "private": true,
```
Inside package.json, we will also add a predeploy property and a deploy property to the scripts object. So it should end up looking something like:
``` JSON
"scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
```

We will then need to add a remote that points to the Git repository. This can be done using:
``` shell
$ git remote add origin https://github.com/{username}/{repo-name}.git
```
After this, deploying the app to GitHub Pages can be done through:
``` shell
$ npm run deploy
```
Now running the deploy command should run and deploy the website onto github!

You can also choose to upload all the backend code to github if desired as well!