---
title: "Tomcat/JSP/MySQL Project Trouble"
date: 2007-06-02
forum: Programming Talk
---

### Post by gh228 on 2007-06-02
Greetings,

I have to do a small project using these elements and am encountering difficulty.

I installed Ubuntu Server and the Kubuntu desktop on top.

Created a small, single table database in MySQL.

Installed JRE 1.6 with the apt-get (which shows when I do java -version)

I've extracted Tomcat 5.5 into usr/local but cannot get it to run.

I had no luck understanding the JAVA_HOME environment variable issue (I'm a newbie) - could not figure out where these statements need to go.  Seems everyone has a different answer.

Essentially I need to get Tomcat running, install a JDBC driver and then create a JSP that displays a simple SQL query from the table.

I'd LOVE if there's someone out there I can communicate with to help me over the bumps as I encounter them.  I need to have this done within the next few days and most of this is new to me.

Thanks!

---

### Post by pmasiar on 2007-06-02
Is Tomcat/java strict requirement? 

Your life could be much simpler and coding more productive using different environments. Both Ruby and Python are *much* better suited for web apps than java.

---

### Post by gh228 on 2007-06-03
Thanks for responding, Pmasiar.

The preference was a JSP page output showing an SQL query on the sample database.  I don't know anything about Ruby or Python, but I don't know much about Java/JSP either!  I also figured with the LAMP stack I installed with Ubuntu server that producing that output with PHP would be fairly easy, but it is the Tomcat install that is both essential and the biggest problem right now.

When I try to run catalina on the command line it doesn't recognize it.  I'm not sure what I did wrong.  I installed Java with apt-get java-package and get a JRE 1.6 message when I type java -version.

I extracted a Tomcat 5.5 tar to a folder under usr/local.

Thanks!

---

### Post by stx69uk on 2007-06-04
A useful recent post, which includes fixing your JAVA_HOME is at:

[http://ubuntuforums.org/showthread.php?t=436295](http://ubuntuforums.org/showthread.php?t=436295)

and a general guide at:

[https://help.ubuntu.com/community/ApacheTomcat5](https://help.ubuntu.com/community/ApacheTomcat5)

Good luck with Servlets/JSPs!

---

