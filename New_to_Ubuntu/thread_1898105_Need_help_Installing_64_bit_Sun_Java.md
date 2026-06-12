---
title: "Need help Installing 64 bit Sun Java"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by vincej on 2011-12-20
Hi - I have installed 64 bit Ubuntu, now , I also want my application to run on the Sun Java 64 bit version, not 32 bit and not OpenJDK. 

It would appear that I have successfully downloaded and installed 64 bit Sun Java, in so far that when I installed it, "Done" appeared on the terminal. 

However, when I go to open a jar file ( my application) Sun Java does not appear under the "Open with other applications" panel.  OpenJDK does appear. 

similarly when I check the versions through the terminal with "java -versions" I get : 

xyz@linux-Dell-9150:~$ java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

I was expecting there to be something like java AMD64 . 

Is it possible that even though I have "installed" it, it is not active ? 

I put it in the same directory as the other versions ie usr/lib/jvm

What have I done wrong ?? 

Many Many thanks for all you help and ideas !

---

### Post by QIII on 2011-12-20
Here is the best tutorial I have run across.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Just follow the directions.  (Run the uninstall script that should be in your jvm directory first.)

I don't remember if he says to uninstall OpenJDK anymore, but if he does don't.  That can bork other stuff.  You can remove the IcedTea browser plugin, though.

What you have done is installed Java, but you haven't told your machine to use it.  The tutorial is a great way to go because as soon as a new version comes out, you basically delete a directory and start fresh.

This might be quicker and you wouldn't have to uninstall what you have, but I don't think you would capture the browser plugin:

```
sudo update-alternatives --config java
```

---

