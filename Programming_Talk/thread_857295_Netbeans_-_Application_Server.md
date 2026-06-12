---
title: "Netbeans - Application Server"
date: 2008-07-12
forum: Programming Talk
---

### Post by PaulM1985 on 2008-07-12
Hi

I am trying to follow a tutorial from a book on how to create Java Servlets.  I opened an example in Netbeans and I got the following error:

"One or more projects do not have the target server set properly"

I opened up the "Resolve Missing Server Problems" window, and I don't have a server installed.

I have tried to install Tomcat, Glassfish and others and I always get an invalid installation folder message.  

I'm not too sure what I am doing and any help would be much appreciated.

Paul

---

### Post by xlinuks on 2008-07-12
I hope you don't have the NetBeans version from the repos.
Here's how I do when GlassFish doesn't come bundled with NetBeans.
I download and install the latest version of GlassFish (not from the repos, but from the web).
Then I install the GlassFish plugin in NetBeans (Tools->Plugins)
Then I go to Tools-Servers and register the GlassFish server I just installed with NetBeans.
Then I open the NetBeans project that requires GlassFish.
If you decide the install the current version from the web, make sure you also install the updates, NetBeans will notify you there are 11 updates available, after you perform them and open NetBeans again, there will be 1 more update. Thus the update will take place in 2 steps.

---

### Post by tinny on 2008-07-13
> **xlinuks said:**
> I hope you don't have the NetBeans version from the repos.
Here's how I do when GlassFish doesn't come bundled with NetBeans.
I download and install the latest version of GlassFish (not from the repos, but from the web).
Then I install the GlassFish plugin in NetBeans (Tools->Plugins)
Then I go to Tools-Servers and register the GlassFish server I just installed with NetBeans.
Then I open the NetBeans project that requires GlassFish.
If you decide the install the current version from the web, make sure you also install the updates, NetBeans will notify you there are 11 updates available, after you perform them and open NetBeans again, there will be 1 more update. Thus the update will take place in 2 steps.

These instructions are what you want.

Just to add one more thing, if you do download [NetBeans]("http://download.netbeans.org/netbeans/6.1/final/") from the web make sure you at least get the "Web & J2EE" bundle. If not get "All". Then everything you need for J2EE development is ready to go straight out of the box! :)

---

### Post by PaulM1985 on 2008-07-13
Hi

Thanks for the advice.  I have tried to install Glassfish from the net, following the instructions from the Glassfish page, and I get this error after typing:

 % java -Xmx256m -jar glassfish-installer-v2ur2-b04-linux.jar 


Exception in thread "main" java.io.FileNotFoundException: glassfish/jbi/components/sun-http-binding/httpbc.jar (No such file or directory)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:160)
	at org.jvnet.poormans_installer.Main.install(Main.java:120)
	at org.jvnet.poormans_installer.Main.main(Main.java:69)

Is this a problem with the file that they have on the site?

Paul

---

### Post by PaulM1985 on 2008-07-13
I have installed Tomcat and after overcoming all the problems with tomcat-users.xml, making all .sh files executable and changing the read only permissions on the files to read and write... I am there.

Paul

---

### Post by xlinuks on 2008-07-13
There seems to be something wrong with your system since GlassFish can't install itself... On Ubuntu on amd and intel it installs itself fine, dunno why _you_ get errors. I do have a httpbc.jar file 845.2 KB.

---

