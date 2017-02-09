
####What is Node.js?
Node.js is a server-side platform built on Google Chrome's JavaScript Engine (V8 Engine).

####Where to use Node.js
* I/O Bound Applications
* JSON API Based Applications
* Single Page Applications

### Installing Node.js

> **From Binaries:** Download the Node.js Binaries from Official Download Page
> [<i class="icon-download"></i> Go To Downloads page](https://nodejs.org/en/download/)


> **On Ubuntu:** 

> ```curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
> sudo apt-get install -y nodejs```



Creating a Simple Node.js Application
-------------
___
#### <i class="icon-file"></i> Initializing a Node.js Application


Make a New Folder for your Node.js Application and cd into that new folder using Terminal (CMD)

```
mkdir SampleNodeJSApp
cd SampleNodeJSApp/
```

Initialize a Node.js Application using NPM package manager

```
npm init
```
Now you will be asked a series of questions. You need to answer according to your project.
> * name : Name of your project in lowercase
> * version : Version of your project.
> * description : Description about your Project
> * entry point : Defines entry point for App. Usually index.js or server.js
> * test command : Command to execute test suite
> * git repository : Link of Git repo
> * keywords : Keywords which describes your application best.
> * author : Your Name
> * license : License

Now you will be presented a generated package.json file to review.
![](http://prabod.rathnayaka.me/content/images/2017/02/Selection_001.png)
![](http://prabod.rathnayaka.me/content/images/2017/02/Selection_002.png)
---
#### Sample Directory Structure for Node.js App

![](http://prabod.rathnayaka.me/content/images/2017/02/Selection_004.png)

> * assets :  Contains all client-side assets that require compilation
>    * css : Contains all your LESS/Stylus style-sheets
>    * js : Contains your client-side CoffeeScript/ES6 files
> * dist : Contains all compiled server-side scripts
> * LICENSE : License file
> * package.json : file contains meta data about your app or module
> * public : Contains your static files that are not handled by any compilers 
> * README.md : Read Me file
> * routes.js : Contains all routes
> * server.js : Entry Point
> * src : Contains all server-side scripts
>    * controller : Contains all Controllers
>    * middleware : Contains all middleware scripts
>    * model : Contains Models if 
> * test : Contains all unit testing scripts ( implemented using a testing-framework of your choice )
> * views : Contains all your express views ( pug,handlebars, ejs or any other templating engine )

---

#### Some Frameworks Available for Node.js

1. [Express.js](http://expressjs.com/) : a minimalist framework for building a host of web and mobile applications as well as application programming interfaces (APIs).
2. [Hapi.js](https://hapijs.com/) : a powerful Node.js web framework for building application program interfaces (APIs) and other software applications. 
3. [Socket.io](http://socket.io/) : a Node.js server framework for building real-time web applications
4. [Meteor](https://www.meteor.com/) : an open-source, model-view controller (MVC) framework for building websites and web/mobile applications. 
5. [Sails.js](http://sailsjs.org/) : Sails.js is one of the most popular real-time frameworks around for building Node.js applications. Sails.js offers a model-view controller (MVC) pattern for implementing data-driven application programming interfaces (APIs). 


---

#### Some of the Databases that can be used as our app's backend

1. [MongoDB](https://www.mongodb.com/) : a free and open-source cross-platform document-oriented database program
2. [MYSQL](https://www.mysql.com/) : an open-source relational database management system (RDBMS).
3. [PostgreSQL](https://www.postgresql.org/) : an object-relational database (ORDBMS)

There are hundreds of NoSQL Databases available that can be integrated with Node.js. Finding one for your application type is your responsibility :p.

---

To Proceed with the sample app I'll choose Express.js and MongoDB

Installing Express.js
```
npm install express --save
```
**--save option will add express to package.json**

Assuming MongoDB installed on your system
If not follow this [link](https://www.mongodb.com/download-center?jmp=nav#community)

Installing MongoDB driver
```
npm install mongodb --save
```
We will be creating a simple user authentication system using passport.js

Add passport and passport-local dependencies to package.json
```
"passport": "~0.2.0",
"passport-local": "~1.0.0"
```

We need some other dependencies too.Finally your dependencies should look like this
```
"dependencies": {
        "bcrypt-nodejs": "latest",
        "body-parser": "^1.12.4",
        "connect-flash": "^0.1.1",
        "cookie-parser": "^1.3.5",
        "cookie-session": "^1.1.0",
        "crypto": "^0.0.3",
        "express": "^4.12.4",
        "express-handlebars": "^3.0.0",
        "express-validator": "^2.10.0",
        "mongodb": "^2.2.22",
        "mongoose": "^4.8.1",
        "morgan": "^1.7.0",
        "passport": "^0.2.2",
        "passport-local": "^1.0.0",
        "serve-static": "^1.9.3"
    }
```

Now we need to choose a templating engine for our Node.js app

**Few Popular Choices will be**
> * [Handlebars](http://handlebarsjs.com)
> * [EJS](http://embeddedjs.com/)
> * [Pug](https://pugjs.org/)
> * [dust.js](http://github.com/linkedin/dustjs/)
> * [Mustache.js](https://github.com/janl/mustache.js/)

Personally I would go for Handlebars. Because it is similar to HTML. It is upto you to choose a Templating engine. I recommend you to go through each of these templating engines and choose one that suits you.

**Or you can use [AngularJS](https://angularjs.org/) , [ReactJS](https://facebook.github.io/react/) or Something like [VueJS](https://vuejs.org/) for the frontend**

**Some Additional Modules used in Sample Application**

* [Mongoose](http://mongoosejs.com/) : Mongoose provides a straight-forward, schema-based solution to model your application data.
* [Morgan](https://github.com/expressjs/morgan) : HTTP request logger middleware for node.js

**Let's get down to Business**

First we need to define a User model for our application using Mongoose. ( or not use Mongoose at all. [Read more about this issue](http://stackoverflow.com/a/18531821/2926901) )

 <script src="https://gist.github.com/prabod/7e8e52624c3d6fecac89d8b6cdd6dd14.js"></script>

I have implemented only local registration part. you can refer passport.js website to know more about social media logins.

Now we can implement passport.js login and signup strategies

<script src="https://gist.github.com/prabod/ea6561b6837b44b21b8b11ae87035283.js"></script>

Routes will look like this

<script src="https://gist.github.com/prabod/0d20b644ad65fa92022b611b04dbaf2a.js"></script>

Our Application's Entry Point Server.js will look like this

<script src="https://gist.github.com/prabod/70fa629ee9d9fce4de517ed8872e720b.js"></script>


**Final Output**
![](http://prabod.rathnayaka.me/content/images/2017/02/Sample-Node-js-Application---Google-Chrome_005.png)

**Final Folder Structure**
![](http://prabod.rathnayaka.me/content/images/2017/02/prabod-prabod-GP62-6QE---SampleNodeJSApp_006.png)

You can find the source to this Sample Application Here 
###[GITHUB REPOSITORY](https://github.com/prabod/Sample-Node.js-Application)
___
**Guide to setup**

1. Fork this Repo <a class="github-button" href="https://github.com/prabod/Sample-Node.js-Application/fork" data-icon="octicon-repo-forked" data-style="mega" data-count-href="/prabod/Sample-Node.js-Application/network" data-count-api="/repos/prabod/Sample-Node.js-Application#forks_count" data-count-aria-label="# forks on GitHub" aria-label="Fork prabod/Sample-Node.js-Application on GitHub">Fork</a>
2. Clone Forked Repo to your local machine ```
git clone https://github.com/YOURUSERNAME/Sample-Node.js-Application.git```
3. Install dependencies```
npm install```
4. Start Application```
npm start```


#### Now you can build your app on top of this sample application

