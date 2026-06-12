---
title: "How do I set up JBoss and Struts to work with Eclipse?"
date: 2006-11-18
forum: Programming Talk
---

### Post by Zunino on 2006-11-18
Hello.

I have Eclipse installed and would like to be able to use that IDE to develop web applications using Struts and EJBs (later) without having to rely on a non-free plug-in such as MyEclipse.

I have downloaded JBoss (4.0.5.GA) and Struts (1.3.5) and unzipped them to /opt/jboss and /opt/struts, respectivelly. What should I do next?

Thank you,

-- 
Ney André de Mello Zunino

---

### Post by invalid on 2006-12-13
I'd like to see a nice walkthrough of this as well.

---

### Post by lloyd mcclendon on 2006-12-14
you can google to get jboss running, there should be some sort of script in the /bin directory.  you could write an init script to start it automatically.  you'll probably have to do a bunch of configuration first, best of luck, you may have to pay for the docs.  jboss is like microsoft with a public cvs tree.  after that you can integrate eclipse & jbosst, you may want to download a version with some plugins, [www.yoxos.com/ondemand](www.yoxos.com/ondemand) .. if you do actually do this let me know, i haven't had the time to mess with the run on server thing.


and why are you using struts?  if you're going to run jboss you really should look at seam.  struts is a steaming pile of crap.

also you didn't even have to download struts, instead download maven and learn how to use it for your builds.  it's pretty cool

---

### Post by invalid on 2006-12-15
> **lloyd mcclendon said:**
> and why are you using struts?  if you're going to run jboss you really should look at seam.  struts is a steaming pile of crap.

I'm assigned to maintain an existing struts project, so I have no choice :)

Thanks for your suggestions, I'll look into them.

---

### Post by pipster on 2007-01-23
First I would download the latest java JDK.  The version of java that comes with ubuntu slows down ALOT when you run eclipse and and app server.  I would go with the jar file version of the jdk.  I have it extracted to /usr/lib/jvm.  Then you should replace the java-gcj sym-link in the /usr/lib/jvm directory.  
```
 sudo rm java-gcj 
```
```
 sudo ln -s /usr/lib/jvm/jdk1.5.0_09/ ./java-gcj
```
make sure that the sym link worked
```
 java --version 
```
It should now have the latest version that you installed there.

Jboss has an Eclipse based IDE available for free.  It comes with all the plug-ins for jboss and works great.  Download the jar file version and run it with ```
sudo java -jar {{jboss-ide.jar}}
```.  You can put it where ever you want, but I like it in /usr/local because this is where jboss server is installed by default.  

Next get the jboss as from jboss.com.  Get the jems-installer version.  Run it with ```
 sudo java -jar jems-installer-1.2.0.GA.jar
```  If you are going to have this clustered then you need to install the ejb3-clustered version, if not then do the ejb3 version.

Once you have the IDE installed you need to make a new project of the server type.  Set this up with the server that you installed (should be at /usr/local).

Next start a new project of the jboss-ide type sub-category of j2ee1.4.  Then import the struts-blank.war file into your project.  That should bring in all the jars and xml files you need.  If you need more help with struts then copy the ear files from the struts installation that you have into the {JBOSS_HOME}/server/default/deploy directory.  This will deploy them to your app-server.  You can at this point start the jboss server through the ide or from {jboss_home}/bin directory by using ```
sudo ./run.sh
``` or ```
sudo java -jar run.jar
```.  If you are having problems with the permissions with jboss when starting it you can do several things.  One is to change the permissions like this from /usr/local ```
 sudo chmod 777 {jboss_home} -R
``` THIS IS NOT A GOOD IDEA.  You can also make yourself the owner of the directory from /usr/local ```
 sudo chown {ur_name} {jboss_home} -R 
```

Have fun.

---

