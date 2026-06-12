---
title: "'subprocess installed post-installation script returned error exit status 2'"
date: 2014-11-24
forum: New to Ubuntu
---

### Post by flaymond on 2014-11-24
Hey, I got an error on terminal after I installed robocode. Actually, I'm accidentally open robocode while the program is in process to install. Suddenly, I got an error messages like this..

Edit- It happened when I open the robocode while the program is still in process to install.....when i try sudo-apt get install -f, it won't fix it....I try remove the program...and worked..but the the terminal  still in same condition...and I put sudo apt-get autoremove to remove uneeded packages.....but won't work....i try using synaptic to completely remove them..but still not working...how can I fix this....even it's a not a big problem..its really annoying when Terminal is my main power and workspace in Ubuntu....:(
Edit- When I try command ***sudo apt-get upgrade***, it keep saying that 1 is not fully installed. How to fully install it or remove it???


```
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up icedtea-netx:i386 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-i386/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-netx:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@Inter76%:~$ sudo apt-get autoremove robocod
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package robocod
user@Inter76%:~$ sudo apt-get autoremove robocode
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'robocode' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up icedtea-netx:i386 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-i386/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-netx:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


(it happen I try sudo apt-get upgrade to fix the error, I try to reinstalling back..but it still in same condition..please help :()

---

### Post by slickymaster on 2014-11-24
Apparently you run into an already reported bug: [Bug #1363785]("https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/1363785")

Even though that bug isn't fixed yet, there's a workaround provided in the bug report that seems to work. See [post #39]("https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/1363785/comments/39") and give it a try.

---

### Post by flaymond on 2014-11-24
I had to reinstalling the OS, I don't know how to do more advance than that.

---

