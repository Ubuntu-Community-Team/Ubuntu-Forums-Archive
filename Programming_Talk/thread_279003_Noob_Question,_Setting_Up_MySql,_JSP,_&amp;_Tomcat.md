---
title: "Noob Question, Setting Up MySql, JSP, &amp; Tomcat"
date: 2006-10-17
forum: Programming Talk
---

### Post by soapytheclown on 2006-10-17
Hey all!! wondered if i could get some help here, at uni we're doing databases for our internet software development module, and suprise all the work we're doing is on windows, we've been asked to try setting similar setups to the lab at home if we get time:

a web server Tomcat 
a database server mySQL

now ive got windows and thats great exceot i hate it and would rather use Ubuntu since i have no doubt it can do the same job probably better!

so so far ive gone into synaptic and installed:-

tomcat5
tomcat5-webapps
tomcat5-admin
mysql-client
mysql-client-5.0
mysql-server
mysql-server-5.0
mysql-common

now i guessed that typing "sudo mysql" in terminal would give me something and it did so im guessing thats all fine, frmo that command prompt i typed in:- 
CREATE DATABASE XXXXXXXXXXXXdb;

GRANT ALL PRIVILEGES ON XXXXXXXXXXXXXdb.* TO YYYYYYYYYY@localhost IDENTIFIED BY 'ZZZZZZ';

GRANT SELECT, INSERT, UPDATE, DELETE ON XXXXXXXXXXXdb.* TO VVVVVVVV_web@localhost IDENTIFIRED BY 'UUUUUU';

USE XXXXXXXXXdb;

but im stumped as to what to do with tomcat and the jsp side of things, remmember im very new to all this its the first sort of database work ive ever done so im im being stupid i apologies!!! but any help ppl?!!

Thankyou all in advance!!!

---

### Post by Paul41 on 2006-10-17
If you get phpmyadmin (or the mysql admin and query tools) from synaptic it will make working with mysql easier.  I haven't worked with Tomcat or JSP so I don't know how to help you with that.

---

