---
title: "[SOLVED] Netbeans 6.1 + Tomcat6 + Web application development"
date: 2008-11-13
forum: Programming Talk
---

### Post by dynamethod on 2008-11-13
hey there, i have installed netbeans 6.1 via apt-get same as tomcat6, im trying to follow this guide here:

[http://www.netbeans.org/kb/60/web/quickstart-webapps.html](http://www.netbeans.org/kb/60/web/quickstart-webapps.html)

however, i get to "Select the server to which you want to deploy your application. Only servers that are registered with the IDE are listed."

Heres a SS to help explain my problem:

[http://img224.imageshack.us/my.php?image=wtftd3.png](http://img224.imageshack.us/my.php?image=wtftd3.png)

---

### Post by CptPicard on 2008-11-13
It is much, much easier just to use the built-in tomcat when developing. I use appservers I configure myself only on my deployment servers.

---

### Post by cl333r on 2008-11-13
> **dynamethod said:**
> hey there, i have installed netbeans 6.1 via apt-get same as tomcat6, im trying to follow this guide here:

[http://www.netbeans.org/kb/60/web/quickstart-webapps.html](http://www.netbeans.org/kb/60/web/quickstart-webapps.html)

however, i get to "Select the server to which you want to deploy your application. Only servers that are registered with the IDE are listed."

Heres a SS to help explain my problem:

[http://img224.imageshack.us/my.php?image=wtftd3.png](http://img224.imageshack.us/my.php?image=wtftd3.png)

I usually download the NetBeans version which comes bundled with GlassFish and Tomcat so Netbeans knows where your server(s) are located.

---

### Post by dynamethod on 2008-11-13
> **cl333r said:**
> I usually download the NetBeans version which comes bundled with GlassFish and Tomcat so Netbeans knows where your server(s) are located.


Sorry but do you have a link, im having trouble finding the package myself(I actually downloaded netbeans via apt-get)

On a windows machine i had downloaded netbeans from the netbeans site, it did have the tomcat6 plugin and web services plugins installed, however im having the same problem on the windows machine too, it keeps telling me "the specified catalina home folder is not valid", i havet to ask, what IS the catalina home folder supposed to be??

---

### Post by tinny on 2008-11-13
> **CptPicard said:**
> It is much, much easier just to use the built-in tomcat when developing. I use appservers I configure myself only on my deployment servers.

The problem is that Netbeans 6.1 doesnt bundle with tomcat by default. (it use to in version 5.x)

I personally just use Glassfish when developing within Netbeans (because its already configured)

Ive never tried configuring tomcat in Netbeans 6.1. Maybe you need to point to the "bin" folder?

---

### Post by cl333r on 2008-11-13
> **dynamethod said:**
> Sorry but do you have a link, im having trouble finding the package myself(I actually downloaded netbeans via apt-get)

On a windows machine i had downloaded netbeans from the netbeans site, it did have the tomcat6 plugin and web services plugins installed, however im having the same problem on the windows machine too, it keeps telling me "the specified catalina home folder is not valid", i havet to ask, what IS the catalina home folder supposed to be??

Go to:
[http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)
and choose to download the NetBeans version called "Web & Java EE" its size is 139MB (as you can notice below). It contains the Tomcat server and as you install that version of NetBeans it (I mean the NetBeans installer) will ask you which servers you wanna install together with NetBeans, choose Tomcat only, since you probably don't wanna have 2 servers installed.
I also wanna note that in a week (on the 20th November) Sun will release NetBeans 6.5 which will have many cool improvements.

---

### Post by cl333r on 2008-11-13
The catalina home folder is the folder where the Tomcat server is installed. Yes, the name should be like "Tomcat home folder", not "Catalina home folder".
But, if you install NetBeans as I suggested you won't have to specify the catalina home folder since NetBeans keeps track of that while installing itself and the Tomcat server.

---

### Post by dynamethod on 2008-11-13
Sigh...


[http://img219.imageshack.us/my.php?image=screenshotyr9.png](http://img219.imageshack.us/my.php?image=screenshotyr9.png)

I cant make sense of what the problem is,

---

### Post by cl333r on 2008-11-13
If you are installing NetBeans from the web as I suggested please make sure first that you uninstalled the previous version of NetBeans and the Tomcat server.

---

### Post by cl333r on 2008-11-13
Here's a short video where I install tomcat from the NetBeans installer. Normally it would also install NetBeans and GlassFish, but since those were already installed on my computer, the installer only allowed me to install Tomcat.
After I started NetBeans it already knew where tomcat is located, so no other steps were required from me. So I created a little web demo project on Tomcat. Here's the video (9MB):
[http://xlinuks.googlepages.com/tomcat.ogv](http://xlinuks.googlepages.com/tomcat.ogv)

---

### Post by aszxcv on 2008-11-13
what player players ogv format

---

### Post by cl333r on 2008-11-14
Pretty much every Linux supports the ogg video, if you're using windows you should install the "k lite codec" video codecs package.

---

### Post by dynamethod on 2008-11-15
thanks guys its working fine now, i uninstalled the version installed via apt-get, and downloaded the netbeans package from the site with the tomcat addon, working fine, thanks again

---

### Post by slowtrain on 2009-03-31
Hi folks:  I got the same "the specified catalina home folder is not valid" error message trying to set up my Tomcat6 server with Netbeans 6.1.  The thing is, I know exactly what the catalina home path is and fed it to Netbeans 6.1.  The first time I put it in, Netbeans took it but I got hung up on user / password issues and closed the window.  The next 5 times I tried it, I got the 'not valid' error.  I'm going to try the suggestion here of installing the 'all components' version of Netbeans without Synaptic.  Just wish the Ubuntu repositories would work!

---

