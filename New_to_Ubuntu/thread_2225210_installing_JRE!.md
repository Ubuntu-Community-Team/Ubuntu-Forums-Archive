---
title: "installing JRE?!"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by Danny_R on 2014-05-20
yallo all so im following a guide to install JRE

which says 

> [h=4]Installing Java[/h]  
[LIST]
[*]Download Java JRE: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
[*] Unpack it and move it where you retain suitable.
  tar xfvz jre-7u40-linux-i586.tar.gz 
mv jre1.7.0_40 /opt/jre1.7.0_40

[*] Complete the set-up
  update-alternatives --install /usr/bin/java java /opt/jre1.7.0_40/bin/java
[/LIST]


i downloaded the JRE (jre1.8.0_15), untarred it, an put it in usr/src

then trying to complete the setup with the command 

```
update-alternatives --install /usr/bin/java java /usr/src/jre1.8.0_15/bin/java
```

but all that happens when i run the command is > update-alternatives: --install needs <link> <name> <path> <priority>

have i missed something stupid!?

thanks

---

### Post by slickymaster on 2014-05-20
Why don't you install Java the easy way, via a PPA repository. The PPA supports JDK8 for both 32bit and 64bit and it's just a script that automatically downloads and install Oracle Java 8.
Everything is done automatically so you'll get updates through the update manager for JDK8 which includes JRE8 and the Java browser plugin.
All you have to do is to run, in a terminal window, the following commands:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

### Post by squakie on 2014-05-20
I'm not on Ubuntu at the moment, but wasn't the jre in the normal repositories?  If you don't have a package manager installed:

sudo apt-get install synaptic

When that finishes, look for and select Synaptic Package Manager from the menus.

In the search box, try java and see what all packages come up.

If it's there, click it and mark for installation, then click apply and wait for it to finish.

Since I'm not on Ubuntu right now I can't promise it's there.  One thing to keep in mind:  always use the package manager or the software center when ever possible to install software.  Software from other sources, even as reputable as Oracle is (hey, I met the guy to discuss porting to our systems years ago), sometimes things become more complicated for updating, etc..

---

### Post by Danny_R on 2014-05-20
top banana! 

its running through now

thanks!

---

### Post by Danny_R on 2014-05-20
delete

---

### Post by squakie on 2014-05-20
You're welcome!  Glad it's working for you!

---

