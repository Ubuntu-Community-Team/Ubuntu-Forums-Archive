---
title: "Netbeans slow on linux"
date: 2009-01-29
forum: Programming Talk
---

### Post by mnml on 2009-01-29
Hi, my netbeans IDE is running slowly on linux.
I'm using SUN JRE 6, I would like to know if there is anything I can do to improve its performances.
Thanks

---

### Post by cl333r on 2009-01-29
Compared to windows, the graphical interface is slower at least because Java 6 update 10 and above on Linux doesn't use hardware acceleration, unlike windows. There seems to be a guy or 2 at Sun working on this:

[http://78.31.67.79:8080/jxrender/](http://78.31.67.79:8080/jxrender/)

but no one has a clue not even remotely when this gets done.

---

### Post by HotCupOfJava on 2009-01-29
Actually, the version of Netbeans I got from the repositories did not use strictly Sun packages. Some portions seem to be from the GNU Project. The version I run on the Windows partition is all Sun. I have also noticed the performance issue, but the previous reply might be the issue.

---

### Post by CptPicard on 2009-01-29
> **HotCupOfJava said:**
> Actually, the version of Netbeans I got from the repositories did not use strictly Sun packages. Some portions seem to be from the GNU Project.

The one from repos may be bad enough to actually use GNU Classpath as dependency... don't do that. Get the sun-jdk from repos and then just get the Netbeans package from their site, and install it under /opt or /usr/local or something like that.

---

### Post by HotCupOfJava on 2009-01-30
> **CptPicard said:**
> The one from repos may be bad enough to actually use GNU Classpath as dependency... don't do that. Get the sun-jdk from repos and then just get the Netbeans package from their site, and install it under /opt or /usr/local or something like that.

Now THAT is a great idea....

---

### Post by edwardtilbury on 2009-09-01
Here's what I did to fix it from being slow on Ubuntu 64 bit 9.04

I tried 6.5, and thought it didn't do php so I installed 6.7 and got slowness and 6.8.1M and got slowness.. 

I didn't realize but 6.5 HAS PHP, I just had to go the plugin menu and put a check mark next to it... DUH!  


Go to synaptic and right click on all the 'java6' stuff , full delete

Full delete / or uninstall of any netbeans installs

Go to your user folder and look for .nbi .netbeans netbeans .. anything like that I deleted..

reboot (window habit, might not be necessary)

install java6 jdk's from add/remove , I didn't install the 32 bit one.. 
install java6 se from add/remove,  I don't know if I need it, but what the hell, SE sounds cool.
install netbeans 6.5 from add/remove

I left net beans 6.5 open all night... no problems, running smooth and fast!

:D

---

