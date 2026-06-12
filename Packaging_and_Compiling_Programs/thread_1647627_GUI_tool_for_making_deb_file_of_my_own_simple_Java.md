---
title: "GUI tool for making deb file of my own simple Java application?"
date: 2010-12-17
forum: Packaging and Compiling Programs
---

### Post by knahrvorn on 2010-12-17
I've made a simple Java application which I'd like to package into a deb file for ease of installation on other machines. The installation is basically copying a few (<10) .class files (and perhaps a shell script for starting the program) and adding to CLASSPATH.

I've had some looks at various deb file packaging guides, including [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete), but it all seems quite confusing and overwhelming, as I'm new to Makefiles and pretty much everything else mentioned in these guides. Also, it seems like it is necessary to do a lot of work in order to package a simple program.

Therefore, I'm looking for an easy-to-go-to (GUI?) tool that can do this for me without too much hazzle. If possible, it would be nice with something that works directly from within Eclipse, which is my preferred environment, but a stand-alone tool is also fine.

Thanks in advance for any advise.

---

### Post by MadCow108 on 2010-12-17
I don't think there are gui's for packaging and it probably would not make very much sense. The command line tools are quite easy to use nowadays

I have never packaged a java program (nor ever written one) but it possibly can be as easy as running dh_make (from devscripts package) in your source tree and adapting the rules to
dh $@ --with javahelper
and modify or remove the generated templates

this site might help you:
[http://wiki.debian.org/Java#Developers-JavapackagingworkinDebian](http://wiki.debian.org/Java#Developers-JavapackagingworkinDebian)

---

### Post by SevenMachines on 2010-12-18
Theres been a few attempts, i'm not sure how far advanced they all got, none of them seem very active these days, maybe someones used them and knows more.
Have to agree with [MadCow108]("http://ubuntuforums.org/member.php?u=804725") though, the command line tools are the best way, and can actually be remarkably simple once you get an overview of how it works and what files are important/optional.

Anyway, here are some i vaguely remember, there may be more, i wouldnt rely on any of them though
[https://launchpad.net/debianpackagemaker](https://launchpad.net/debianpackagemaker)
[https://launchpad.net/giftwrap](https://launchpad.net/giftwrap)
[https://launchpad.net/debomatic](https://launchpad.net/debomatic)
[https://launchpad.net/debcreator](https://launchpad.net/debcreator)

---

### Post by hakermania on 2010-12-19
And a little tutorial over here (it might help)
[Full Guide -> How to package your Qt application and include it in ubuntu! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1642956")

---

### Post by SevenMachines on 2010-12-19
[hakermania]("http://ubuntuforums.org/member.php?u=895189"), it might also be a good idea to add your guide to the packaging guides on the wiki too, so your good work doesnt get lost in amongst all the threads and more people might find it. i dont know if theres a java specific one yet or not, i'll do a quick one sometime if no-one else, specifically someone who knows more about java packaging :) , gets round to it

---

### Post by nikhilbhardwaj on 2010-12-24
if its a java application, then wouldn't a jar file do just fine??

---

### Post by knahrvorn on 2013-03-01
With this one you need no makefile:
[http://blog.pryds.eu/2013/02/package-java-apps-for-ubuntu-and-debian.html](http://blog.pryds.eu/2013/02/package-java-apps-for-ubuntu-and-debian.html)

Not a GUI tool, though, but it is specifically aimed at installing your app as class files, and based on Eclipse Java project.

---

### Post by Malsasa on 2013-03-02
> **knahrvorn said:**
> I've made a simple Java application which I'd like to package into a deb file for ease of installation on other machines. The installation is basically copying a few (<10) .class files (and perhaps a shell script for starting the program) and adding to CLASSPATH.

I've had some looks at various deb file packaging guides, including [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete), but it all seems quite confusing and overwhelming, as I'm new to Makefiles and pretty much everything else mentioned in these guides. Also, it seems like it is necessary to do a lot of work in order to package a simple program.

Therefore, I'm looking for an easy-to-go-to (GUI?) tool that can do this for me without too much hazzle. If possible, it would be nice with something that works directly from within Eclipse, which is my preferred environment, but a stand-alone tool is also fine.

Thanks in advance for any advise.

Hello, you and me have same problem. I have launched my app (JAR) in DEB package by intensely following this most simple and easiest tutorial: 

[COLOR=#236E25][FONT=monospace][http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/](http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/)

[/FONT][/COLOR]That is the clearest I think compared with original Debian/Ubuntu packaging guide. It is easy and I recommend it for you. Sure, you will need more tutorials but if you wanna easiest guide, read it :)

I am sorry for my English.

---

### Post by QIII on 2013-03-02
Thank you for sharing.  Everyone’s questions and answers are valuable.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own. Not only will you be more likely to get a response, but things change so quickly in the software world that an old thread may cause you more trouble than it will help due to outdated information.

Please feel free to add a link to the original thread in your new one if you think it might be helpful.

Best wishes!

This thread should not have been woken from its slumber 12 hours ago.

*Thread **closed.***

---

