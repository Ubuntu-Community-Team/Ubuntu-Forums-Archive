---
title: "flash problems, maybe?"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by saintj0n on 2012-01-01
I am trying to play games on [www.free80sarcade.com](www.free80sarcade.com) and am getting a blank screen when I bring up pretty much any of the games.  I have linux restricted drivers in synaptic but could be missing something.  I don't know how to install flash and java and all of the other good plug ins.  Can anyone direct my path here?:confused:

---

### Post by LinuxCharms on 2012-01-01
To install Java/Flash and all of those good things, just go into the Software Center and search for them. Then install. Lemme know if that helps. (:

---

### Post by wildmanne39 on 2012-01-01
Hi, for flash it would be best to open firefox and click on tools, addons then type flashaid in the addon window and install flashaid and follow the directions it will install the best flash for your system and fix any flash problems it detects and best of all it is written by a staff member.
Thanks

---

### Post by corrytonapple on 2012-01-01
Even if you don't use Firefox, get it.  Then go to **Tools > Addons > 'FlashAid'**.  Meaning search for "flashaid".  Forum member lovinglinux made it.  It installs the correct version of flash, and it always makes this stuff work well.

---

### Post by Rodney9 on 2012-01-02
Lubuntu uses Chromium, [www.free80sarcade.com](www.free80sarcade.com) , works .

```
sudo apt-get install lubuntu-restricted-extras
```

[http://ubuntuforums.org/showthread.php?t=1880394&highlight=lubuntu](http://ubuntuforums.org/showthread.php?t=1880394&highlight=lubuntu)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by I2k4 on 2012-01-03
FWIW, while I like and run Lubuntu on my netbook, I had nothing but trouble with Chromium both in Flash installation and accessing a number of sites I use regularly.  Best to just use Chrome (which comes with Flash preinstalled) or the recent, improved FireFox.

---

### Post by QIII on 2012-01-03
Don't try to install Java from the repos.

Oracle has decided that they are not going to play nice and have withdrawn licenses for Ubuntu.

Even if there is a Java in the repos, it is old and has security problems.

While one hopes that OpenJDK will eventually be recognized by the world, it is not right now.

If you have problems with Java, I would suggest installing it per this excellent tutorial:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

