---
title: "Looking for contributor or guidelines for jMonkeyEngine package"
date: 2010-10-27
forum: Packaging and Compiling Programs
---

### Post by erlend_sh on 2010-10-27
Greetings. I'm a manager with the [jMonkeyEngine]("http://jmonkeyengine.com") project. For the past two weeks we've been casually discussing [how to go about getting our product into a Ubuntu repository]("http://jmonkeyengine.org/groups/features/forum/topic/jm3-ppa-for-ubuntu") in order to be easily installed directly from the Software Center. Specifically we would distribute jMonkeyPlatform, which is a complete game development environment built around jMonkeyEngine 3.

It's a long shot, but I was hoping maybe we would stumble upon a fellow Java game development enthusiast around here, who's got some experience with Ubuntu package distribution and is willing to help.

Otherwise though, we would also greatly appreciate being pointed in the direction of a more concisely put packaging tutorial, as opposed to one that is [100 pages long]("http://www.debian.org/doc/debian-policy/").

---

### Post by lykeion on 2010-10-28
Wow, this project looks great. I'll definately keep my eye on this. 
Unfortunately I've no experience with packaging myself, and all I can do is to point to some links. 
Hopefully someone with more experience can assist you further.

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)
[http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)
[http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html](http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html)
[http://ptspts.blogspot.com/2010/02/how-to-create-debianubuntu-package-deb.html](http://ptspts.blogspot.com/2010/02/how-to-create-debianubuntu-package-deb.html)
[http://ubuntuforums.org/showthread.php?t=980032](http://ubuntuforums.org/showthread.php?t=980032)
[http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/](http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/)

---

### Post by SevenMachines on 2010-10-28
Hi, the ubuntu packaging guide is always the best place to start to get an idea of how packaging is done and everything fits together.
For java packaging you should use javahelper i'd suggest, which adds java related stuff to debhelper, it should detect an ant build system if thats what you're using.

Debian recommended packages to look at are 
>  $ apt-get source libcsv-java weirdx
the debian directory of these packages should show how java packaging should be done.

Theres an explanation of specific javahelper packaging things here
along with some examples of java packaging including some ant ones

[EDIT] For some reason links arent appearing so...
Packaging Guide: [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
Javahelper: [http://pkg-java.alioth.debian.org/docs/tutorial.html](http://pkg-java.alioth.debian.org/docs/tutorial.html)
Examples: [http://pkg-java.alioth.debian.org/examples/](http://pkg-java.alioth.debian.org/examples/)

---

### Post by erlend_sh on 2010-10-28
Thanks for kind words and pointers. Using a[nt-deb-task]("http://code.google.com/p/ant-deb-task/") we've come as far a .deb package:
[http://normen.bitwaves.de/download/jme3-sdk_0.6.1_all.deb](http://normen.bitwaves.de/download/jme3-sdk_0.6.1_all.deb)

I suppose now we should get in touch with some MOTUs. I suppose this is all I need then?
[https://wiki.ubuntu.com/MOTU/GettingStarted](https://wiki.ubuntu.com/MOTU/GettingStarted)

---

### Post by ludovicc on 2010-11-27
Hello,

Consider joining the Debian Java team and ask for sponsorship there. 
[http://wiki.debian.org/java](http://wiki.debian.org/java), and the pkg-java team ([http://pkg-java.alioth.debian.org/](http://pkg-java.alioth.debian.org/))
Can you make available the sources that you used to package your project?

I'm not sure that using ant-deb-task will be accepted as a way to package jMonkeyEngine. Debian (and Ubuntu) require some well defined information in your package: a description, the list of dependencies, the copyright.

What is the build system used for this project normally? Ant or Maven?
I can help you anyway, contact me (my Launchpad ID: ludovicc, mail [email]ludovic.claude@laposte.net[/email])

---

