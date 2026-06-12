---
title: "Hardy 64bit FF3B5 Sun Java Plugin"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by tactx on 2008-05-28
I installed  the Sun Java Runtime, but when I went to install the FF plugin it says its not available for my 64bit AMD Processor (Mines Intel 64). Im having trouble with various net apps like shopping cart on various sites and was wondering what my best options were.

---

### Post by sayakb on 2008-05-28
```
sudo apt-get install ubuntu-restricted-extras
```
Will install java plugin. Do restart your computer once after installing this package.

---

### Post by drs305 on 2008-05-28
> **tactx said:**
> I installed  the Sun Java Runtime, but when I went to install the FF plugin it says its not available for my 64bit AMD Processor (Mines Intel 64). Im having trouble with various net apps like shopping cart on various sites and was wondering what my best options were.

Java plugins are a problem in 64-bit. The recommended, and I believe for now, better option for trouble-free Firefox java plugins on a 64-bit machine is to run a 32-bit browser. There is a 64-bit forum for these matters, and here is the 'sticky' post at the top:
[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by tactx on 2008-05-28
> **LinuxIsInnovation said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```
Will install java plugin. Do restart your computer once after installing this package.

I ran this line of code and now see the "GCJ Web Browser Plugin (using IcedTea) 1.0" plugin loaded and enabled. Testing at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) doesn't work while testing at [http://javatester.org/version.html](http://javatester.org/version.html) did appear to work.?

> Java plugins are a problem in 64-bit. The recommended, and I believe for now, only option for trouble-free Firefox java plugins on a 64-bit machine is to run a 32-bit browser. There is a 64-bit forum for these matters, and here is the 'sticky' post at the top:
[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956) 

The sticky has no replies and is a closed topic. I am confused is this telling me I need to use 32-bit Ubuntu or 32-bit Firefox, and if its FireFox, can I/ how do I install 32-bit firefox on 64-bit Ubuntu? Can it co-exist with my 64-bit Firefox that is already installed?

Thanks for helping...:)

---

### Post by drs305 on 2008-05-28
> **tactx said:**
> 
The sticky has no replies and is a closed topic. I am confused is this telling me I need to use 32-bit Ubuntu or 32-bit Firefox, and if its FireFox, can I/ how do I install 32-bit firefox on 64-bit Ubuntu? Can it co-exist with my 64-bit Firefox that is already installed?

Thanks for helping...:)

I run 64-bit swiftweasel, a variant of firefox, and 32-bit firefox, so they can coexist. The names of the programs (even if both are firefox) are different so there isn't a conflict. I suppose I could just run the 32-bit version only to make my life simpler, but this combination allows me to run just about every web page I've looked at. 

There are many good developments when it comes to 64-bit java (open-jdk, icedtea, etc) and there are even rumors that a true 64-bit sun java is on the near horizon but it's not quite there yet. Most people that have tried alternatives to sun-java plugins on firefox can't yet get all sites to work.

The best site for wading through this is and installing 32-bit apps on 64-bit machines is Kilz's thread:
[http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)

It may seem a bit overwhelming but if you just follow the instructions exactly it works fine.

---

### Post by philinux on 2008-05-28
> **tactx said:**
> I ran this line of code and now see the "GCJ Web Browser Plugin (using IcedTea) 1.0" plugin loaded and enabled. Testing at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) doesn't work while testing at [http://javatester.org/version.html](http://javatester.org/version.html) did appear to work.?


Sounds like it's working then. The first link does not work for many.

If the other one works I'd say you're good to go.

---

### Post by jspiers on 2008-11-08
Sun still doesn't have a 64-bit Java plugin, even though this has been a known issue for over 6 years:

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695)

I am shocked.  I never realized Sun was so negligent.

---

### Post by jamesstansell on 2008-11-08
> **jspiers said:**
> Sun still doesn't have a 64-bit Java plugin, even though this has been a known issue for over 6 years:

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695)


To clarify, Sun does have it, but is still testing it and plans to release it in the next several months.

In the meantime the icedtea project has produced a credible 64-bit plugin; see the icedtea6-plugin package in ubuntu 8.10 (Intrepid).

IIUC the 64-bit Konqueror browser also can run java applets even though it doesn't use a plugin.

---

### Post by TFrog on 2009-02-04
> **jamesstansell said:**
> To clarify, Sun does have it, but is still testing it and plans to release it in the next several months.

In the meantime the icedtea project has produced a credible 64-bit plugin; see the icedtea6-plugin package in ubuntu 8.10 (Intrepid).

IIUC the 64-bit Konqueror browser also can run java applets even though it doesn't use a plugin.

Sun has released a 64 bit Java update (JRE 6 Update 12) as of yesterday (February 3, 2009).  How soon we'll see packages in the various supported Ubuntu (and variants) distros there's no telling.  You can download the bin files from Sun but they are not posted at [www.java.com](www.java.com) as of yet.  The new 64 bit Java JRE includes a 64 bit plugin for 64 bit users.  Suggest you read the Sun site for more info on it.

---

### Post by funky_uncle on 2009-02-05
Just subscribing to this thread in case anybody ever comes up with a solution.

---

### Post by drs305 on 2009-02-05
> **funky_uncle said:**
> Just subscribing to this thread in case anybody ever comes up with a solution.

Sun just released update 12 with a 64-bit java plugin. Here's a thread about it and ethoxyethaan has instructions on how to install it.
[http://ubuntuforums.org/showthread.php?t=1058539]("http://ubuntuforums.org/showthread.php?t=1058539")

It's been working fine for me so far, but so did the alpha/beta.

---

### Post by funky_uncle on 2009-02-05
> **drs305 said:**
> Sun just released update 12 with a 64-bit java plugin. Here's a thread about it and ethoxyethaan has instructions on how to install it.
[http://ubuntuforums.org/showthread.php?t=1058539]("http://ubuntuforums.org/showthread.php?t=1058539")

It's been working fine for me so far, but so did the alpha/beta.Ah yes, it finally works! If I wasn't already fed up from spending the whole day trying to get flash and java to work, I'd take the time to try and understand *how* it works...

I still can't get Opera to work with java though, I tried changing the path to /opt/jre1.6.0_12/lib/amd64/libnpjp2.so but that didn't work.

---

