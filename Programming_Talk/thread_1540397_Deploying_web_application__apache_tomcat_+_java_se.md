---
title: "Deploying web application  apache tomcat + java servlet + apache derby"
date: 2010-07-27
forum: Programming Talk
---

### Post by OnlineBuddy on 2010-07-27
**THIS DOCUMENT SHOULD HELP ANYONE WANTING TO MAKE JAVA WEB APP**
.
i have some experience with web based development using TOMCAT + SERVLET + DERBY/ms SQLserver2005..
i recently made a hospital management system application(SERVER SIDE SOLUTIONS.)..
.
The following steps indicate how to set-up your databases and tomcat,please forgive me but i am a new ubuntu user and some of my command line syntax might be wrong..:oops:!!
.
**you basically have to maintain 2 tiers..**
[SIZE=3]*_**1st tier**_*[/SIZE]--->DATABASE SIDE(i used apache derby 10.4.1.3 CLIENT/SERVER driver)
.
you first need to setup [B]derby
.
set PATH->[/B] $DERBY_HOME/bin
then start the **ij** tool
ij>CONNECT 'jdbc:derby:*<database-name>*;create=true;
>  [I]'PUT YOUR SQL COMMANDS HERE TO CREATE YOUR TABLES'
.
you will observe a folder with your database-name created in your present directory...
this folder has your DATABASE..**.this is the directory where you have to start your server**
.
[/I]**set CLASSPATH**->      /../../derby.jar  and  /../../derbyclient.jar
**START SERVER**-> java -jar"$DERBY_HOME/lib/derbyrun.jar" server start
this should start your server
.
.
[SIZE=3]*_**2nd tier**_*[/SIZE]--->tomcat side
.
first go your $CATALINA_HOME/webapps...and create a folder for your web application
.
DIRECTORY STR>
.
<$CATALINA_HOME>
                 <webapps>
                                <'app. name'>
                                                   <WEB-INF>
                                                                       <classes>   _*here your servlet classes go*_
                                                                       <lib>     _*here you have to put your derby.jar and derbyrun.jar*_
                                                                        web.xml  _*here you will identify/map your servlet names*_
                                                  <here you will put your rest of the 'html' or 'jsp' files>
.
**STARTING SERVER-> **automatically stared usiing 'jsvc'in most installations, or you could start DEAMON using $CATALINA_HOME/bin/startup.sh
.
.[U][I][B]
running application
put in url [http://localhost:8080/](http://localhost:8080/)[/B][/I][/U]
and check if the tomcat server has been started or not....
you could also use ANT technology to manage your web applications...
[U][B].
[/B][/U]you should edit the tomcat-users.xml file and place a name/password over there, _**NEVER**_ share it if you are going to use your application in production evironment!! 
.
allow your firewall to accept incoming requests at the port you specified tomcat to run on(_**DEFAULT 8080**_)
.
.
[U][B]FOR ANY MORE QUERIES SEND ME A 'pm'
[/B][/U]

---

