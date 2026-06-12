---
title: "Deploying a servlet"
date: 2006-12-09
forum: Programming Talk
---

### Post by welshboy on 2006-12-09
I've followed an example that I found on the forums for deploying a servlet,

link is :
[http://www.ubuntuforums.org/showthread.php?t=172897&highlight=CATALINA_HOME](http://www.ubuntuforums.org/showthread.php?t=172897&highlight=CATALINA_HOME)

And i've followed each instruction to the letter, yet I still don't have anything coming up.  The URL I use to try and get it running is

[http://localhost:8180/servlet/HelloWorld](http://localhost:8180/servlet/HelloWorld)

The servlet has it a hello folder within the webapps dir, and it has the WEB-INF and classes folder etc as well, and yet I still get a 404 error - Resource Not found.

I'm at a dead loss as to why it ain't working.

I am running Tomcat 5.5 on Edgy, and I've installed it from the repositories.  And I currently have Java 1.5.08 which is also installed from the repos.

Any help will result in profuse thanks.

---

### Post by firebadger on 2006-12-09
Servlet should be in a folder WEB-INF/classes/test
The folder(s) below the classes dir should represent the package structure.

If that doesn't work, post your web.xml and the locations of your files.

---

### Post by welshboy on 2006-12-09
Hi badger,

I've not had much success with this either, and I must confess that I don't have a web.xml file for it, as the book I'm using to work on servlets didn't say that I needed one.

My files are in the following location:

emyr@Wookie:/var/lib/tomcat5.5/webapps/hello/WEB-INF$ 

And the hello has a WEB-INF folders
and in that there is a class folder.  

and in the class folder there is: 

helloWorld [directory] HelloWorld.class  HelloWorld.java
emyr@Wookie:/var/lib/tomcat5.5/webapps/hello/WEB-INF/classes$ 

and the HelloWorld.class and java files are in there too.

I'm not sure what I'm meant to put in the web.xml file if I'm honest, as the book I'm using didn't mention that I needed to write one.  However I am more than willing to learn.

Many thanks

---

### Post by lloyd mcclendon on 2006-12-09
post web.xml in code [] tags and we'll figure out what's wrong. 

the first thing to do is stop working in /var/lib

what you'll want to do is start using ant to deploy the web app as a war file.  google for tomcat ant tasks for more info.  you'll have to write a little build.xml file to handle this, if you need help let me know and i can post portions of mine.

alternatively, you can create a context element in tomcat/conf/server.xml

something like <Context path="/webAppName" docBase="/home/you/src/webAppName" ... />  see the docs for more info

i actually do option 2 on localhost while i'm developing stuff, then when it's ready to go i use option 1 to deploy it on our testing/production servers.  works pretty well actually.

i hope you are just writing this servlet for learning purposes, you won't want use a hand crafted servlet on an actual webapp considering there's tons of great (and no so great) sevlet frameworks available.

one definately worth looking at is stripes: [http://stripes.mc4j.org](http://stripes.mc4j.org) .. stripes with spring, hibernate, and freemarker is a great stack.

and jboss seam looks great and very powerful but i've been too busy to look at it.

---

