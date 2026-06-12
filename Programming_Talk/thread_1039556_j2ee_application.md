---
title: "j2ee application"
date: 2009-01-14
forum: Programming Talk
---

### Post by manojpotla on 2009-01-14
Hi All,

I have been trying to develop a web application in j2ee on ubuntu. I have so far installed the jdk and ant. Still need to install eclipse and Jboss. Could anyone point me out to some useful resources which would hel me develop a basic web application even a "Hello World" Example. using ant and deploying it in JBOSS. I have developed web app in Windows, trying to start the same in Ubuntu.

Thanks & Regards,
Manoj Potla

---

### Post by thomasaaron on 2009-01-14
I don't know if you are married to Eclipse or not, but newest Netbeans IDE has templates for just about every kind of application you could imagine.

It also can be downloaded with an number of bundles, including java ee and web. 

Check it out at...

[http://www.netbeans.org/downloads/](http://www.netbeans.org/downloads/)

---

### Post by manojpotla on 2009-01-15
Hi Thomas

I am not inclined towards Eclipse or netbeans, what I am trying to do is to set up a web application with ant and JBOSS not trying to depend on the IDE so that I can understand what it takes to make a webproject. So far i could set my ant, jdk and mysqlserver working. It would be of great help if anone could help me in this.

Thanks & Regards,
Manoj

---

### Post by Ruhe on 2009-01-15
Hey, what's the problem installing jboss?
Just [download]("http://www.jboss.org/jbossas/downloads/") it and unpack where you want.
But it's not so easy to create "hello world" app, because j2ee is too complicated. 
JBoss is well [documented]("http://www.redhat.com/docs/en-US/JBoss_Enterprise_Application_Platform/"). And you can try to run [sample applications]("http://www.redhat.com/docs/en-US/JBoss_Enterprise_Application_Platform/4.3.0.cp03/gettingstarted.zip").

Else, and I think better way, is to read some pages from [j2ee tutorial]("http://java.sun.com/javaee/5/docs/tutorial/doc/"). You'll find a lot of sample applications there. But this apps are supposed to be deployed on glassfish servers, so you'll need to write your own ant files for them.

---

### Post by manojpotla on 2009-01-15
HiRuhe

Thanks for the info. I know it is difficult to do so. As of now i do have my JBOSS up and running and mysqlserver setup. I hope to have a test webapp up and running. I have a small project that i have set up in windows using ant however that doesnt work. Throwing small errors. Will list the errors once i try it in ubuntu. 

Thanks
Manoj

---

### Post by manojpotla on 2009-01-19
Hi All,

I have finally set up a j2ee project with ANT,and JBOSS. Thanks for your inputs.

Manoj

---

