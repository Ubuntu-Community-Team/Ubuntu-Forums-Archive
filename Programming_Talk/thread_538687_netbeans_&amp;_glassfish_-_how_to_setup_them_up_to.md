---
title: "netbeans &amp; glassfish - how to setup them up together"
date: 2007-08-30
forum: Programming Talk
---

### Post by nicolasdiogo on 2007-08-30
hi,

i have installed Netbeans 5.5 and glassfish and java 1.5  from Ubuntu repo.
but i don't seem able to configure Netbeans to recognise glassfish.
i followed information available on Netbeans website so i believe it is a Ubuntu issue.
has anyone managed to make these two application to work together?

many thanks

---

### Post by glok_twen on 2007-09-02
i have had the same difficulty - did you get any info about this?

---

### Post by xlinuks on 2007-09-02
Have a look at "Java EE 5 SDK Update 3 Preview 2" from [http://java.sun.com/javaee/downloads/ea/](http://java.sun.com/javaee/downloads/ea/)
As you can see Sun is currently working on bundling GlassFish with NetBeans so it installs automatically when you install NetBeans, perhaps this early access version meets your needs..

---

### Post by glok_twen on 2007-09-02
thanks i made some progress too.

here are my notes if anyone needs pointers. so far i've confirmed the the web server part gets up and running. i have been able to deploy an .ear file into  the server but haven't really confirmed it runs correctly yet.

i installed it all via ubuntu packages and this item included into /etc/apt/sources.list
[http://download.java.net/ubuntu/](http://download.java.net/ubuntu/) feisty/

listens for user apps on
[http://localhost:8080/](http://localhost:8080/)

listens for admin console on
[http://localhost:4848/](http://localhost:4848/)
the default username is admin and the password is adminadmin
(don't forget to change it right away)

installed domain1 automatically

install directory
/usr/share/sunappserver/

domain directory
/var/lib/sunappserver/domains/domain1

to stop and start the server itself:
sudo /usr/share/sunappserver/bin/asadmin stop-domain domain1
sudo /usr/share/sunappserver/bin/asadmin start-domain domain1

to test whether it's up, point to localhost:8080 and you should get a message that the server is up and running

to register it in netbeans, use the directories above for the install and domain dirs. then, use register a remote server but point it to localhost

this might work, i haven't yet tested an EE app with it yet.

---

