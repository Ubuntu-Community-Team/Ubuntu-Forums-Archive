---
title: "MySQL Database Design Callenge"
date: 2011-03-09
forum: Programming Talk
---

### Post by vargadanis on 2011-03-09
Hello everyone!

I am facing with challenges concerning an application. Here they are:

_Challenges:_
 - plugin supported application design
 - plugins data should be separated from the data of other plugins/users
 - when a plugin is enabled, it has the option to initialize it's data structure
 - plugins must be prevented to read other plugin's data

Think of an application like wordpress.. It's got plugins, plugins can store data in database. The difference is that this website will be massively multiuser and each plugin will be specific to the user and will store unique data for each user.

_Questions:_
 - what approach is good to solve the challenges above?

My approach:> 
 - database connection for user authentication -> store user data/settings/access rights in memory (sessions?) -> close connection
 - create 1 connection to the user DB
 - create 1 connection/plugin for each plugin the user has got with appropriate access rights
 - store the plugin data in a DB specific to user, only user credentials can access it which is read from the authentication connection then stored in memory

Example DBs:

GLOBAL_AUTH_TABLE:
 - userID
 - username
 - password
 - ...

DB_{USERID}:
 - listOfUserPlugins
 - ...
 - plugin1Table
 - plugin2Table

In this case the login process would look like:
1) Auth: connect to auth DB -> authenticate() -> close connection
2) Create connection to DB_{USERID}
3) Create connection for plugin1 which has access only to plugin1 table in DB_{USERID}
4) Create connection for plugin2 which has access only to plugin2 table in DB_{USERID}

Problems with this approach:
 - whenever the user logs in each plugin must initiate a database connection with proper access rights.. If the connections are opened and closed whenever the plugin performs DB transactions, the disk IO/CPU usage will be high, the code will be slower. If I use persistent DB connections which are closed only when the user logs out/closes browser window, the DB might error out after a while that too many connections and memory usage will be high.

What I would like:
 - a design that scales well to many users with many plugins
 - gracious to CPU/Memory

Any tips?

---

