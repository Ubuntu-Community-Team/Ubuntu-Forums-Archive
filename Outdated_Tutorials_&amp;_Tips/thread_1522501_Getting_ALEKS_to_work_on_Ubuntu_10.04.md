---
title: "Getting ALEKS to work on Ubuntu 10.04"
date: 2010-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Oolongtea on 2010-07-02
ALEKS is a pain but you need it if you are to pass that math class eh? Well here's a tutorial on how to get ALEKS up and running on Ubuntu.

First off open software sources and enter this:
```
deb http://archive.canonical.com/ lucid partner
```

Then enter this command in a terminal to update:
```
sudo apt-get update
```

After the update enter this command. You will be asked to accept the terms and conditions Java demands:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts[/CODE

After all that follow this link to the ALEKS website to download the latest plugin. After the download is complete put it in your home folder. 
[http://www.aleks.com/downloads/linux_jvm]("http://www.aleks.com/downloads/linux_jvm")

This is the last step. Just enter this last command into a terminal and your hard work will pay off next time you open up **_Firefox_** and login to ALEKS.
[CODE]sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/ext/
```

---

### Post by visionsuser on 2010-08-26
I've done all of the above, and still can't get ALEKS to load in Firefox. I can go to the Java test page at java.com, and it works fine. I also get "applet started" and the "loading..." at ALEKS.com, but then it craps out and I get an error message that  starts with:

> Please check the URL "/alekscgi/x/Isl.exe..."

Since I had several different jvm's in the /usr/lib/jvm directory, I cp's the aleksPack10.jar file into the jre/lib/ext directory of each entry in the jvm directory (java-1.6.0-openjdk, java-6-openjdk, java-6-sun, and java-6-sun-1.6.0.20).

No luck.

Any ideas?

---

### Post by visionsuser on 2010-08-26
I should also add that I'm, for some reason, forced to use the icetea plugin in order to get Java to work on the test site, but if I disable icetea, Firefox won't find the "regular" Java plugin. I've put the symlinks in the mozilla plugin directory, but nothing shows up.

---

### Post by visionsuser on 2010-08-27
Update: I completely uninstalled openJDK (including icetea) and installed the Sun jre fresh. Everything is now working. Looks to me like ALEKS doesn't like either the openJDK version of java, the icetea browser plugin, or both.

---

### Post by Oolongtea on 2010-08-27
what version of Java do you have?

---

### Post by jackechanprime on 2010-09-11
I'm just going to repost what i said on another thread, since my question remains basically the same...

********
K, now i've got a new problem for you...

Aleks fully installed and "functional."
Program is loading and initializing smoothly, program comes online and is (apparently) completely operational... HOWEVER...

The actual problem interfaces (as it's a math homework program, it has interfaces where you input your final answer as well as "buttons," which are some form of script link, for getting explanations as well as other basic GUI functions within the program (back, next, done, etc.). THESE SCRIPTS ARE NOT RUNNING. The result is that when i attempt to actually perform the point of the program and solve a homework problem, I CANNOT ACTUALLY ANSWER IT. not only that, but even if i could answer it, without the "done" button rendering, i cannot actually submit my answer!

Ask anything you need to know, and i'll tell you.

ubuntu 10.04, firefox 3.--something (latest), jre6 (reinstalled literally yesterday, so should be the latest version, most importantly, jre IS working.)

Any help GREATLY appreciated. like everyone else who seems to be having this problem, if i cant get ALEKS running right, i automatically fail this math course.
********

thanks for any responses, help needed badly.

---

### Post by jackechanprime on 2010-09-13
O_o erm... it seems to have fixed itself. No idea how, but it works fine now, minus a few input glitches where the box doesn't realize I'm actually "talking to it" But that's easily fixed. Didn't even to a system update, and now it works. total mystery to me.

I used your directions above to get it working in the first place though, so whatever you had me do worked eventually. O_o

thanks!
~Q

---

