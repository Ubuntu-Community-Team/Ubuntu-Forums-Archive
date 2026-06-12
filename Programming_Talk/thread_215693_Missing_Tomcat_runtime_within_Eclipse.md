---
title: "Missing Tomcat runtime within Eclipse"
date: 2006-07-14
forum: Programming Talk
---

### Post by jaredvolkl on 2006-07-14
I apologize if I am posting this in the wrong forum, I'm new.

Here's my situation. I am trying to set up a JSP development environment. I installed Tomcat and Mysql through synaptic, but I have installed Eclipse myself as 3.2 (Callisto) was not in the repositories yet.

The problem I'm having is getting Eclipse to recognize Tomcat. I've also installed the WTP through Eclipse updates, and everything seems to be there.

Next I go into Window->Preferences->Server->Installed Runtimes and I see nothing. OK, so I go to add, and I get no servers listed at all. 

Fine. So I try searching instead. Now I am a new to Ubuntu, but not Linux. From what I could tell, Tomcat seems to be in /usr/share/tomcat5. I've tried pointing the search to that directory, also tried the bin directory within that and also the common/lib directory and none of them add the Tomcat runtimes to Eclipse.

Help!

---

### Post by jaredvolkl on 2006-07-14
Scratch that. I solved this by installing the JST package through Eclipse's update system. After that all my servers show up.

---

### Post by ilcavero on 2007-07-02
I'm suffering the exact same problem, the worse thing is that the embedded tomcat that comes with Netbeans package is correctly detected, but the standalone one that I got from apt-get is not. This is probably an eclipse bug, but one that I can't reproduce on windows. It's annoying the hell out of me.

---

### Post by ilcavero on 2007-07-05
I found a workaround, the thing is that eclipse wants to see the webapps directory on tomcat, but it seems that they moved it to /var/lib/tomcat5.5/webapps, I had a /usr/share/tomcat5.5-webapps directory, so I just copied it to  /usr/share/tomcat5.5/ and renamed it to webapps.

here are some useful links about tomcat5.5 and feisty:

[http://ubuntuforums.org/showthread.php?t=436295&highlight=tomcat+5.5+feisty](http://ubuntuforums.org/showthread.php?t=436295&highlight=tomcat+5.5+feisty)
[http://blogs.sun.com/superpat/entry/tomcat_on_ubuntu_feisty](http://blogs.sun.com/superpat/entry/tomcat_on_ubuntu_feisty)
[https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/103145](https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/103145)

---

