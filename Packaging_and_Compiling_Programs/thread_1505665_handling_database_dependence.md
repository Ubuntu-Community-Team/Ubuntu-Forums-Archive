---
title: "handling database dependence"
date: 2010-06-09
forum: Packaging and Compiling Programs
---

### Post by tanderson on 2010-06-09
I have wrote a program using qt and has a database back end. I am looking into creating a .deb package, and have browsed some tutorials. I feel fairly confident I will be able to muddle through it this first time. My question is how to deal with the database dependence options in the .deb. I am using the qt sql module so I have options on which database can be used. 

Can the installation look for running servers and then use a database that is already installed and running? this would avoid having multiple database servers running.

Maybe there should be multiple packages that will allow user to select a back end database?

Maybe just use sqlite as default and let user switch to a server if wants. I think that is what amarok does, but I don't like it. I have used a program that corrupts the sqlite database when it crashes(program bug, power outages). might not be sqlite fault, but makes me nervous.

akonadi uses mysql so isn't mysql running by default on all new installations? Maybe I should go with that?

If no database is installed how to setup the database after it is installed? Maybe a script run after database installation that will have root priveledges? I need to create a database and user.

What about configuration files. I have made some changes to my postgres config file, which causes me to modify sysctl.conf file for shared memory. I am wondering what I can do in a .deb for these files? If server is getting installed then I could modify the config file, but if server is already installed and running I might not want to change the file. Having to administrate this database server is going to be a pain for end user.

I am starting to see why amarok just uses sqlite by default. I would like to make the installation and setup as painless for the user as possible. I have compiled and run on linux and mac, and I would like to eventually make a windows port also. Any suggestions? thanks.

---

### Post by diesch on 2010-06-09
It sounds like your program can use a remote database so don't expect users to have a local database installed. Maybe add a "Suggests" dependency for a popular database like MySQL or SQLite.

To create a database and a database user you don't need root privileges as most database servers have their own user management.

I'd ask the user up for what database to use if no database is configured at program start up, display what's needed  and offer to create the necessary database stuff.

Try to avoid the need for a special configuration of the database server.

---

