---
title: "Tux Guitar isn't working"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Papenco on 2008-06-29
Okey, I've intalled TuxGuitar but can't launch it. I've tried reinstalling and all that stuff. BUt when I go to the apps menu and select it it just doesn't launch. What can I do?

---

### Post by ad_267 on 2008-06-29
It doesn't like the java that comes with ubuntu for some reason. You have to install sun-java6-jre

For future reference, if something won't run from a menu go to Applications - Accessories - Terminal and type the name of the application that you want to run. You can type the beginning, eg. tux and press tab to autocomplete. When you run it in the terminal it will show errors there if there are problems so you can sort out what's wrong.

---

### Post by Papenco on 2008-06-29
Thanks, it was that.

---

### Post by CarlWalters on 2008-06-30
> **ad_267 said:**
> It doesn't like the java that comes with ubuntu for some reason. You have to install sun-java6-jre

For future reference, if something won't run from a menu go to Applications - Accessories - Terminal and type the name of the application that you want to run. You can type the beginning, eg. tux and press tab to autocomplete. When you run it in the terminal it will show errors there if there are problems so you can sort out what's wrong.

thanks from me too - it sorted me out :)

---

### Post by jwalters on 2009-03-21
tried to get tuxguitar running and this is what I got . . .I'm stuck! helppp

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Bölvaður on 2009-03-21
Look in the upper left corner of your screen and then continue reading here below to follow these instructions:

Applications &#8594; Accessories &#8594; Terminal

type:
```
sudo dpkg --configure -a
```
enter password (blindly)

you can also download a package (tuxguitar) from their webpage and just extract it and move it to a location like ~/programs/tuxguitar  (~ stands for /home/jwalters/)


there are many posts about this problem because the E which probably stands for Error gives people the image that this is a cryptic text :P

but really the dpkg program was just interrupted or some thing, so you must manually run 'dpkg --configure -a' to correct the problem as root (sudo in front of or log in as root).

---

### Post by jwalters on 2009-03-21
thank you very much . . . I think that was it.

---

### Post by utfan2012 on 2010-06-29
I put in sudo apt-get install javajre and it said i had the package already installed then i tried the terminal method of opening and this is what i got...


paul@paul-desktop:~$ tuxguitar
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Control
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Control
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
	... 1 more

---

### Post by GavinWiggins on 2010-09-18
I'm having the same problem.  TuxGuitar simply will not open when I click it.  When I run it in a terminal, I get the same thing as the other guy:

Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Control
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Control
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 1 more

Installing sun-java6-jre from the synaptic package manager did not solve the problem.  However, when I tried sudo apt-get install javajre, I got this message: Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package javajre

---

### Post by GavinWiggins on 2010-09-18
I just found this link, and it worked for me!

[http://ubuntuforums.org/showthread.php?p=9096204&nojs=1#goto_threadsearch](http://ubuntuforums.org/showthread.php?p=9096204&nojs=1#goto_threadsearch)

---

