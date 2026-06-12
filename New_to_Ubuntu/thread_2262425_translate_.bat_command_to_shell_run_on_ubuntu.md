---
title: "translate .bat command to shell run on ubuntu"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by NGUYEN_QUANG_PHUC on 2015-01-24
hi all,
i've a .bat scripts running on windows but i want tranlaste it to shell to run it on Ubuntu server. however must keep it in background processing before server shutdown.
Anyone known please translate it for me. i'm very thank.
The first start.bat file running will call one.bat and two.bat
start.bat file contents :> [INDENT]@echo off
echo start server
path=%path%;%~dp0\jdk7\bin
echo.
ping -n 2 127.0.0.1 >nul
start /MIN one.bat start
echo one.bat    One started
echo.
ping -n 2 127.0.0.1 >nul
start /MIN two.bat start
echo two.bat     Two started

[/INDENT]
The one.bat contents 
> title RunEmail
@echo off
java -cp Gameserver.jar;lib/antAll.jar;lib/antlr-2.7.6.jar;lib/bsh-2.0b4.jar;lib/c3p0-0.9.1.2.jar;lib/commons-beanutils-1.8.3.jar;lib/commons-codec-1.4.jar;lib/commons-collections-3.2.1.jar;lib/commons-dbcp.jar;lib/commons-dbcp-1.2.2.jar;lib/commons-httpclient-3.0.jar;lib/commons-lang-2.4.jar;lib/commons-logging-1.1.1.jar;lib/commons-pool-1.3.jar;lib/dom4j-1.6.1.jar;lib/easymock-2.2.jar;lib/easymockclassextension-2.2.1.jar;lib/ezmorph-1.0.6.jar;lib/h2-1.3.169.jar;lib/hibernate3.jar;lib/hibernate-jpa-2.0-api-1.0.0.Final.jar;lib/hibernate-tools-2.1.3.jar;lib/javassist.jar;lib/javax.servlet.jar;lib/jdom.jar;lib/jetty-6.1.3.jar;lib/jetty-util-6.1.3.jar;lib/json-lib-2.3-jdk15.jar;lib/jta.jar;lib/jxl.jar;lib/log4j-1.2.12.jar;lib/mysql-connector-java-5.0.3-bin.jar;lib/netty-3.5.7.Final.jar;lib/org.springframework.beans-3.0.2.RELEASE.jar;lib/org.springframework.core-3.0.2.RELEASE.jar;lib/protobuf-java-2.4.1.jar;lib/slf4j-api-1.5.6.jar;lib/slf4j-log4j12-1.5.6.jar;lib/slf4j-simple-1.5.6.jar start.RunEmail


cmd



The two.bat contents t> title Run843@echo off
java -cp Gameserver.jar;lib/antAll.jar;lib/antlr-2.7.6.jar;lib/bsh-2.0b4.jar;lib/c3p0-0.9.1.2.jar;lib/commons-beanutils-1.8.3.jar;lib/commons-codec-1.4.jar;lib/commons-collections-3.2.1.jar;lib/commons-dbcp.jar;lib/commons-dbcp-1.2.2.jar;lib/commons-httpclient-3.0.jar;lib/commons-lang-2.4.jar;lib/commons-logging-1.1.1.jar;lib/commons-pool-1.3.jar;lib/dom4j-1.6.1.jar;lib/easymock-2.2.jar;lib/easymockclassextension-2.2.1.jar;lib/ezmorph-1.0.6.jar;lib/h2-1.3.169.jar;lib/hibernate3.jar;lib/hibernate-jpa-2.0-api-1.0.0.Final.jar;lib/hibernate-tools-2.1.3.jar;lib/javassist.jar;lib/javax.servlet.jar;lib/jdom.jar;lib/jetty-6.1.3.jar;lib/jetty-util-6.1.3.jar;lib/json-lib-2.3-jdk15.jar;lib/jta.jar;lib/jxl.jar;lib/log4j-1.2.12.jar;lib/mysql-connector-java-5.0.3-bin.jar;lib/netty-3.5.7.Final.jar;lib/org.springframework.beans-3.0.2.RELEASE.jar;lib/org.springframework.core-3.0.2.RELEASE.jar;lib/protobuf-java-2.4.1.jar;lib/slf4j-api-1.5.6.jar;lib/slf4j-log4j12-1.5.6.jar;lib/slf4j-simple-1.5.6.jar start.Run843
cmd

[HR][/HR]My server is running Ubuntu 14.

---

### Post by Jordan_Cameron on 2015-01-24
A little more info would be nice:- What are these scripts actually for?  What is it you are trying to setup on the server?

---

### Post by ian-weisser on 2015-01-24
The .bat files seem to run a gameserver in the background as your user. Don't do that. That's kludgy and potentially unsafe.

Use a system user (user without a login nor shell) to run internet-facing services - not your user, not root. The system user owns only the service's data files. This protects your system if your gameserver gets compromised.

See the  'man adduser' comand for how to add a system user.
See 'man mv' and 'man chown' for how to move the gameserver files to a new dir in /var, and how to change their ownership to the new system user.  

Use an Upstart or systemd job to start/stop the service when the network comes up or down...just like all the other services on your system. Don't use autostart commands or terminal multiplexors or other kludges. Using upstart/systemd is *easier* than the other ways.

See [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/) for how to add an upstart job to /etc/init so you can start and stop the server using simple commands like 'service gameserver start' and 'service gameserver stop', and have the server autostart when the network comes up. Pretty much all of the commands in your .bat files, once edited for proper location, will go into the Upstart script stanza.

Running a service properly will make it easier to maintain, more reliable, safer, simpler to backup and restore...and easier for us to help you when you have questions.

---

### Post by NGUYEN_QUANG_PHUC on 2015-01-25
hi, 
it's is realtime game online, these scripts will only running on my server to communicate front-end and database server, receive and process request from clients throught java or json.

The main structure of server side scripts here :

[IMG]http://i.imgur.com/6xcuneX.jpg[/IMG]
On the **start **directory
[IMG]http://i.imgur.com/UDMhrfH.jpg[/IMG]
When server starting successfullyl willl be follow photo and them still open until i close the window or running **Stop.bat** 
[IMG]http://i.imgur.com/swsT31R.jpg[/IMG]

So i want "translate" start.bat, one, two.. to shell run on my ubuntu server but it running on backgroud proccessing as systems or intergate serivces.

im a newcomer at ubuntu and this is new job, i dont known what's  mean of command  and how to get same running on ubuntu by shell
[B]
java -cp Gameserver.jar;lib/antAll.jar;lib/antlr-2.7.6.jar;lib/bsh-2.0b4.jar;lib/c3p0-0.9.1.2.jar;lib/commons-beanutils-1.8.3.jar;lib/commons-codec-1.4.jar;lib/commons-collections-3.2.1.jar; start.Run843" on file one,two... seven.bat[/B].

Anyone teaching me how to do that or translate a little example with abow command, please

---

### Post by NGUYEN_QUANG_PHUC on 2015-01-25
anyone helo me

---

### Post by ian-weisser on 2015-01-25
Basically, you copy the .bat file, and then fix all the paths.

Change the .bat suffix to .sh, and make the new shell script executable.
All those 'lib/' paths won't work since 'lib/' may not be a valid path in Ubuntu. Change each path to where that .jar actually is now.
Plan on some time debugging to fix whatever breaks, because those are really ugly batch files.

---

