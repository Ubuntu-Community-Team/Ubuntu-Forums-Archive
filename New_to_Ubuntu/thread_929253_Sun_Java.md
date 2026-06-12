---
title: "Sun Java"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by manners2345 on 2008-09-24
I am using ubuntu desktop 8.04 fully updated as far as I know, and  Firefox 3.02

A few days ago Sun released update 7 to java6. A couple of days later my yahoo mail and chat stopped working, have to go to classic mail, cannot get into my bigstring.com mail, google adwords disappeared from my webpage, several other things apparently also use java as they stopped working and disappeared. 

Went to Sun java website to upgrade to update 7 as it has not appeared in a ubuntu as of yet.

Managed to download to desktop, came in as a dot Bin. After much trial and error, using terminal. got it to run and said it was done. sun jave 6 update 6  is usr/lib/jvm/, so is update 7. nothing works!!! 

If I go to root terminal an enter java version, the following is what get:


root@OlerThanDirt-laptop:/home/fred# java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
root@OlerThanDirt-laptop:/home/fred# 

So what should I do??  I did not put in smiley face!!! maybe it means something???

My thought is do and un-install for update 6 and 7,then re-install 7

Anybody got any ideas???

As per usual advance thank you cannot find star with blue ribbon!!! to use

manners2345

---

### Post by hubie on 2008-09-24
You can try and see if you get the same behavior with different flavors of Java.  To see how to change the default java in use, see the bottom of [this page]("https://help.ubuntu.com/community/Java").

---

### Post by manners2345 on 2008-09-25
I have SOLVED this one. In the SUN JRE for which ever update you are trying to get to run. Look in the BIN file, There is one called Control Panel, double click on it comes with a dialog box asking if you want to run in terminal, display, or run, picking the run option as root If you have done a launch pad for nautilus. allows you to set it up using a GUI

At least that is the way I remember it!!! Kicking 70 yrs CRS is pretty prevalent 

A PIECE OF CAKE WITH FROSTING, this way

manners2345

CRS= Cannot remember stuff is the clean way. Sub Stuff with another S word   :roll: this is an LOL

---

### Post by kpkeerthi on 2008-09-25
It should be **java -version** and not **java version**

---

### Post by The Cog on 2008-09-25
It should be > java -version - you are missing the minus sign.

---

