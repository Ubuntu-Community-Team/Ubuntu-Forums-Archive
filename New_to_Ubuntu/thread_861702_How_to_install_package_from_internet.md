---
title: "How to install package from internet?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by rfreed23 on 2008-07-16
Help please....

I want to install a package off the internet, something called myeclipse. I download the tarball, no problem. I double click the tarball and it expands out to a folder. So far so good. I go into the newly created folder and there's a bunch of stuff in there, mostly folders. The most promising thing I see is something called 'myeclipse-installer' so I double click it, and it gives the following error:

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Myeclipse-installer. No Java virtual machine
was found after searching the following locations:
/home/freed/downloads/myeclipse-6.5-pulse-2.2.1.200807081915-linux-gtk-x86/jre/bin/java
java in your current PATH

.... but I do have java installed! (When I enter 'javac -version' it returns 'javac 1.6.0_06'). I even tried copying the java executable into the directory path in the error message (although I really don't think I should have to do that). When I do that, and then double click myeclipse-installer, nothing happens. 

I would use apt or synaptic but neither seems to recognize what I have downloaded. How do I install this thing??

---

### Post by SunnyRabbiera on 2008-07-16
try to stick to the repositories, what kind of application is this?

---

### Post by rfreed23 on 2008-07-16
> **SunnyRabbiera said:**
> try to stick to the repositories, what kind of application is this?

myeclipse is a java IDE, similar to eclipse which is in fact in the repositories. I needed a few more bells & whistles though, and I use myeclipse at work on windows ([http://www.myeclipseide.com/](http://www.myeclipseide.com/)).

---

### Post by RomeReactor on 2008-07-16
Hi. NetBeans is also available in the repositories. Regarding MyEclipse, is there a **readme** or **install** file in the folder?

---

### Post by rfreed23 on 2008-07-16
> **RomeReactor said:**
> Hi. NetBeans is also available in the repositories. Regarding MyEclipse, is there a **readme** or **install** file in the folder?

I've heard of netbeans, but have never used it. Guess I could if I have to. Does it support development of enterprise java beans? That's why I'm trying to get myeclipse installed.

No readme or similar file from the myelipse download. Here's what's in the folder:
freed@Ubuntu:~/downloads/myeclipse-6.5-pulse-2.2.1.200807081915-linux-gtk-x86$ ls -la
total 348
drwxr-xr-x 4 freed freed   4096 2008-07-16 20:33 .
drwxr-xr-x 5 freed freed   4096 2008-07-15 18:57 ..
drwxr-xr-x 2 freed freed   4096 2008-07-16 17:54 configuration
-rw-r--r-- 1 freed freed    164 2008-07-08 19:22 .eclipseproduct
-rw-r--r-- 1 freed freed   7748 2008-07-08 19:22 icon.xpm
-rw-r--r-- 1 freed freed 266168 2008-07-08 19:22 libcairo-swt.so
-rwxr-xr-x 1 freed freed  52580 2008-07-08 19:22 myeclipse-installer
drwxr-xr-x 7 freed freed   4096 2008-07-16 17:54 plugins
freed@Ubuntu:~/downloads/myeclipse-6.5-pulse-2.2.1.200807081915-linux-gtk-x86$

---

### Post by RomeReactor on 2008-07-16
> **rfreed23 said:**
> I've heard of netbeans, but have never used it. Guess I could if I have to. Does it support development of enterprise java beans? That's why I'm trying to get myeclipse installed.

It's available as a plugin.

> No readme or similar file from the myelipse download. Here's what's in the folder:
freed@Ubuntu:~/downloads/myeclipse-6.5-pulse-2.2.1.200807081915-linux-gtk-x86$ ls -la
total 348
drwxr-xr-x 4 freed freed   4096 2008-07-16 20:33 .
drwxr-xr-x 5 freed freed   4096 2008-07-15 18:57 ..
drwxr-xr-x 2 freed freed   4096 2008-07-16 17:54 configuration
-rw-r--r-- 1 freed freed    164 2008-07-08 19:22 .eclipseproduct
-rw-r--r-- 1 freed freed   7748 2008-07-08 19:22 icon.xpm
-rw-r--r-- 1 freed freed 266168 2008-07-08 19:22 libcairo-swt.so
-rwxr-xr-x 1 freed freed  52580 2008-07-08 19:22 myeclipse-installer
drwxr-xr-x 7 freed freed   4096 2008-07-16 17:54 plugins
freed@Ubuntu:~/downloads/myeclipse-6.5-pulse-2.2.1.200807081915-linux-gtk-x86$

Try this:
```
gksudo gedit /etc/eclipse/java_home
```
and add this as the first line, right after the three commented lines:
```
/usr/lib/jvm/java-6-sun-1.6.0.06
```
then run the installer again. More details [here]("http://forums.debian.net/viewtopic.php?p=60783&sid=26aebb081b019fcf6df15a1648b2cb40#60783").

---

### Post by arpanaut on 2008-07-16
Do you have eclipse itself installed...
from what I see MyEclipse is built upon or a add on/plugin to it?
I know nothing about either program, but that's the impression I got from their FAQ.

????????

---

### Post by rfreed23 on 2008-07-17
> **RomeReactor said:**
> It's available as a plugin.



Try this:
```
gksudo gedit /etc/eclipse/java_home
```
and add this as the first line, right after the three commented lines:
```
/usr/lib/jvm/java-6-sun-1.6.0.06
```
then run the installer again. More details [here]("http://forums.debian.net/viewtopic.php?p=60783&sid=26aebb081b019fcf6df15a1648b2cb40#60783").

Tried it, same error :(

---

### Post by rfreed23 on 2008-07-17
> **arpanaut said:**
> Do you have eclipse itself installed...
from what I see MyEclipse is built upon or a add on/plugin to it?
I know nothing about either program, but that's the impression I got from their FAQ.

????????

Yes, I do have eclipse installed, but you bring up an interesting thought. Maybe myeclipse itself should be treated as an eclipse plugin (which has it's own way of installing). Still, if that's the case then I'm puzzled as to why there's a 'myeclipse-installer' that doesn't work. At any rate, I'm on my way to work and will work on this tonight - I'll try then to install it as an eclipse plugin.

---

### Post by rfreed23 on 2008-07-17
Aha - I found the answer! For any inquiring minds out there, [here ya go]("https://help.ubuntu.com/community/EclipseIDE")

---

### Post by odalton on 2008-08-02
Interesting setup 
[http://www.tanguay.info/web/tutorial.php?idCode=phpDevelopmentQuick&sectionIdCode=installEclipse](http://www.tanguay.info/web/tutorial.php?idCode=phpDevelopmentQuick&sectionIdCode=installEclipse)

This is the best method following the wiki - with the nightly update http://
[http://dev.phpeclipse.com/wiki](http://dev.phpeclipse.com/wiki)


gd luck

---

