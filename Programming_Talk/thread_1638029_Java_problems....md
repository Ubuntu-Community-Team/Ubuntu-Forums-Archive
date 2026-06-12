---
title: "Java problems..."
date: 2010-12-05
forum: Programming Talk
---

### Post by stamatiou on 2010-12-05
Hey guys I have the Ubuntu Maverick Meerckat installed and I would like to  ask you a few things about Java...
1. Is Java preinstalled, if not how can I install it?
2. Where can I find easy tutorials on Java? (It doesn't matter what type of tutorial is, video, text anything.....)

---

### Post by howefield on 2010-12-05
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)


> Sun Java moved to the Partner repository

For Ubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the Ubuntu archive. It is recommended that you use openjdk-6 instead.

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line:

     sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
     sudo apt-get update   # update to know about new repository

Change the above to maverick.

---

### Post by Quikee on 2010-12-05
> **howefield said:**
> [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

Change the above to maverick.

There is no need for proprietary Sun/Oracle JDK/JRE. OpenJDK is almost identical and is available in the default repository. 

Just install default-jdk package:
```
apt-get install default-jdk
```
or search and install this package in synaptic.

---

### Post by stamatiou on 2010-12-05
Hey guys, because aI am a newbie can you speak more clearly?
Is there a shell comaand so I can install and program on Java? And If you can suggest me any tutorials please do....
Thanks.....:p

---

### Post by Zugzwang on 2010-12-05
> **stamatiou said:**
> Hey guys, because aI am a newbie can you speak more clearly?
Is there a shell comaand so I can install and program on Java? And If you can suggest me any tutorials please do....
Thanks.....:p

The "code" that Quikee posted is actually a shell command to install the so-called Java development kit that you definitely need for programming in Java. With respect to tutorials and the like, look at the following forum posts:

[http://ubuntuforums.org/showthread.php?t=713622](http://ubuntuforums.org/showthread.php?t=713622) (first steps in Java & Linux. Skip step 0 (outdated) and instead use Quikee's command).

[http://ubuntuforums.org/showpost.php?p=1997993](http://ubuntuforums.org/showpost.php?p=1997993)

---

### Post by howefield on 2010-12-05
As indicated in my earlier post, you want to decide whether to use the open source solution or Suns (Oracle) proprietary solution.

The open source version should already be available to you via Applications > Ubuntu Software Centre. You are looking for openjdk-6-jre and icedtea6-plugin

If you want to use the proprietary solution, you will first need to enable the partner repository, do that by going to System > Administration > Synaptic Package Manager > Settings > Repositories > Other Software tab and check the Canonical Partners option and close.

Reload your software packages by clicking the Reload button on the Synaptic Package Manager window, then search for sun-java6-jre sun-java6-fonts and sun-java6-plugin, mark for installation, and install.

---

### Post by scorp123 on 2010-12-05
> **Quikee said:**
> There is no need for proprietary Sun/Oracle JDK/JRE.  Not true. There's a lot of things out there that simply won't work with OpenJDK yet.

---

