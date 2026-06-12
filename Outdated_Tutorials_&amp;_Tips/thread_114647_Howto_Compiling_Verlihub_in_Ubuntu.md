---
title: "Howto: Compiling Verlihub in Ubuntu"
date: 2006-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by stoffepojken on 2006-01-09
This is my first howto and I am new to Linux myself so dont be afraid to complain if I have made any mistakes in this howto. My English isn't that good either but I hope you understand what I am writing. :)

Verlihub is a software to run a hub on the direct connect network (DC++). I run my hub on it and it works great for me. The Verlihub homepage is located at:[http://verlihub.sourceforge.net/]("http://verlihub.sourceforge.net/")

Let's get this hub up and running :)

Velihub requires a mysql-database.


To install mysql:

```
sudo apt-get install mysql-server
```


Now you must set your mysql-root password:

```
mysqladmin -u root password **********
```

Here you replace the stars with a password of your choice. This is not the same as your root password in ubuntu. You can choose whatever you want. But remember this password because we need it later on.


Thanks to this great swedish howto I found out about the depenencies:[http://forum.directconnect.se/showthread.php?t=4550]("http://forum.directconnect.se/showthread.php?t=4550")


To install the dependencies type in a terminal:

```
sudo apt-get install build-essential mysql-server libmysqlclient10-dev libpcre3-dev geoip-bin libgeoip-dev g++-3.3
```

Now download the verlihub source to your /home folder:[http://prdownloads.sourceforge.net/verlihub/verlihub-0.9.8c-RC2.tar.gz?use_mirror=mesh]("http://prdownloads.sourceforge.net/verlihub/verlihub-0.9.8c-RC2.tar.gz?use_mirror=mesh")



untar it type in a terminal:

```
tar xzvf verlihub-0.9.8c-RC2.tar.gz
```

cd to to the folder:

```
cd /home/your_user_name/verlihub-0.9.8c
```


By googling to this thread on the great verlihub forums I found the solution to my configure proplems: [http://forum.verlihub.net/viewtopic.php?t=638]("http://forum.verlihub.net/viewtopic.php?t=638")

Type in a terminal:

```
CXX=g++-3.3 ./configure
```

Now it should configure without errors

Then to compile type in a terminal:

```
make
```


If no errors type in a terminal:

```
sudo make install
```


Now Verlihub is installed but we have a few steps to go before we have our hub up and running.



Verlihub has a great install-script that creates a database and sets up your hub by answering some questions. To run that script type in a terminal:

```
vh_install
```


Now in the terminal the script starts and the questions comes up.

Your name ? (root)     <---- click enter

Hello root,
let's start with configuration of database access..

--------------------------------
mysql database for verlihub will be called? (******)    <---- name of your choice

mysql user to access verlihub gonna be?(******)      <----- choose a user name. Whatever you want. The script is going to create a new database

password to access verlihub be?(******)    <---- Choose a password of your choice.

mysql server will run where? (localhost)    <------ klick enter here

Is this info correct ? (Y/N)  <---- type y


I think that you will be prompted for your root password here I cannot check because verlihub is allready on my computer but type the password that you choosed when you installed mysql server not your ubuntu root password.

what is will be the configuration folder ? (/etc/verlihub) <--- click enter


Now the database is created. We are going to set up our new hub:

Give me your DC hub master nickname.. ([SU]root)   <---- Choose your name on the hub here

Choose your password.. (1136781435)   <---- Choose your password that you are going to use when you are connecting to the hub

Which will be default ONE hub  port number? (4111)  <---- choose what portnumber that the hub will run on

What will be your hub hostname? (*****)  <----- type your hub adress here except the port number

Give me the name of your hub (hub of root)  <---- Type the name that you want for your hub

Is this info correct ? (Y/N)  <---- type yes if everything is right

Now to start the hub. Type verlihub in a terminal or to make the hub run in the background type vh_runhub



Now you are ready to connect to your hub. Connect with a dc client with your        name and password.

If you are connecting from the same computer as the bub is running on just connect to localhost:**** <--- replace the stars with the portnumber that you choosed earlier

If you are connecting from another computer connect to the hub computers ip number+the port that you choosed.


I hope that this howto works for you. If not tell me so I can change in the howto.

I will not answer any questions about running a hub. Type !help in main chat :)



Happy sharing :)

---

### Post by NelD on 2006-02-25
How do I autostart Verlihub?
How do I start Verlihub as root? ( want to use port:411 )

---

### Post by SteffJay on 2006-06-18
The verlihub forum is closed....  please can you give the workaround to the install problem......  :wink:

---

### Post by stoffepojken on 2006-07-19
I got some mails so maybe I should refresh this old howto :). Let the piracy move on. Sorry mods... :)

---

### Post by Fabbritzio on 2006-08-30
After !restart appears this message and I can't restart verlihub:

> Config dir ./.verlihub
(1) Tue Aug 29 18:29:50 2006 # cMySQL - Connecting to mysql server: root@localhost/verliNEW
(0) Tue Aug 29 18:29:50 2006 # cVHPluginMgr - using plugins in: ./.verlihub/plugins
------------------------
(0) Tue Aug 29 18:29:50 2006 # tCache - 5 items preloaded.
(0) Tue Aug 29 18:29:50 2006 # tCache - 0 items preloaded.
(0) Tue Aug 29 18:29:50 2006 # cVHPluginMgr - Open dir: ./.verlihub/plugins/
(0) Tue Aug 29 18:29:50 2006 # cVHPluginMgr - OnPluginLoad: plugman
(1) Tue Aug 29 18:29:50 2006 # cVHPluginMgr - Succes loading plugin: ./.verlihub/plugins/libplug_pi.so
(0) Tue Aug 29 18:29:50 2006 # cServerDC - Listening for connections on 0.0.0.0:2500 TCP
(0) Tue Aug 29 18:29:50 2006 # cServerDC - Can't listen on 0.0.0.0:411 TCP
(1) Tue Aug 29 18:29:50 2006 # cServerDC - Destructor cServerDC
Allocated objects: 19
Caught error:Can't listen


I type  > netstat -tnlp and this is what appears:

> netstat -tnlp
(Not all processes could be identified, non-owned process info
will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN -
tcp 0 0 127.0.0.1:37650 0.0.0.0:* LISTEN -
tcp 0 0 0.0.0.0:11124 0.0.0.0:* LISTEN 2 5052/ldcpp
tcp 0 0 0.0.0.0:11125 0.0.0.0:* LISTEN 2 5052/ldcpp
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN -
tcp 0 0 127.0.0.1:59387 0.0.0.0:* LISTEN -
tcp6 0 0 :::80 :::* LISTEN - 

what is the problem because I can't restart verlihub. I don't have any errors when I make compile files. My English isn't that good either but I hope you understand what I am writing.

---

### Post by irishdunn on 2009-01-21
I wrote this blog post a couple days ago, it also covers automatic start up:

[http://blog.agdunn.net/?p=3](http://blog.agdunn.net/?p=3)

---

