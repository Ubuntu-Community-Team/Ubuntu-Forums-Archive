---
title: "Installing Java"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by casterwil on 2013-05-22
hello my name is musharraf i'm 10 years old.
I am trying to install Java. I dont get why my install keeps failing.
It keeps saying 'item can not be read'.

Can anyone help me?

---

### Post by monkeybrain2012 on 2013-05-22
You can install OpenJDK from the repo. If you must use Oracle's Java the easiest way is explained here [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by newb85 on 2013-05-22
Welcome to the forums!

More information is needed in order to help you.  First, what release of Ubuntu are you using?  You can identify it by its name (something like "Raring Ringtail" or "Precise Pangolin") or its number (like 12.04 or 13.04).

Secondly, where did you obtain the package and how are you trying to install it?  (If you downloaded it from a website, please specify the address.)

---

### Post by hendrel on 2013-05-22
Here are step by step instruction that shows how to install Oracle Java 7 update 21 on Ubuntu 13.04: [http://hendrelouw73.wordpress.com/2013/05/07/how-to-install-oracle-java-7-update-21-on-ubuntu-13-04-linux/](http://hendrelouw73.wordpress.com/2013/05/07/how-to-install-oracle-java-7-update-21-on-ubuntu-13-04-linux/)

---

### Post by craig10x on 2013-05-22
Yeah, he could do it that rather complicated way...but if he would like to do it easily....here's the place to go:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

He simply pastes in 3 terminal commands, agrees to the java license on the third command, and not only does he have the latest Oracle Java but a ppa updater is placed in the ubuntu updater that will bring in the latest versions as they are released ;)

Actually, monkeybrain2012 posted this link before this post...we both can tell you that it works great!

---

### Post by hendrel on 2013-05-22
I do not agree with craig10x. Although the PPA method provided by [www.webupd8.org](www.webupd8.org) is quicker it is problamatic in the following areas:

1. You do not have insight into the scripts that get's executed when installing from a PPA. Hence viruses can easily be installed via the PPA.
2. Second in the case of Java you do not want the PPA to automatically update to the latest version. You might have software that rely on the currently installed version.
3. Following the blog post provided by hendrel is great for a newby since it provides step by step instructions on the installation process. Something you will need to know as a programmer anyhow.

---

### Post by ronnyroll on 2013-05-22
looks like your installation key number is not correct

---

### Post by QIII on 2013-05-22
> **hendrel said:**
> 1. You do not have insight into the scripts that get's executed when installing from a PPA. Hence viruses can easily be installed via the PPA.
webupd8.org is highly trusted. Do you have any better insight into what happens when you install something from the official repos? All the webupd8 installer does is download the official Oracle Java 7 installation and follow the installation instructions.

> 2. Second in the case of Java you do not want the PPA to automatically update to the latest version. You might have software that rely on the currently installed version.
Yes, actually, you do want updates immediately.  Updates contain security fixes.  If you have software that specifies a particular version, the software is poorly written. I have never encountered this issue unless software looks for Java 6, in which case I won't use it.

> 3. Following the blog post provided by hendrel is great for a newby since it provides step by step instructions on the installation process. Something you will need to know as a programmer anyhow.
Why would a programmer necessarily need to know how the JVM and JDK are installed?

I help maintain the wiki in my signature.  I specifically made sure that the webupd8 method is at the top of the list of command line methods because it is simply the easiest method ***and ***it does update Oracle Java 7 automatically.

I have been working with Java for many years and, as a software developer, I can say that this is simply the best way to go about it.

---

