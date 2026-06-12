---
title: "HOWTO Get frostwire to work - updated for Hardy"
date: 2008-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Frak on 2008-06-28
This post is used to install the version of frostwire from frostwire's server, instead of using the Ubuntu version.

This tutorial installs java6 in your system. You must use Java to have this work. IcedTea can be used, but I have had bugs with it, and in the latest version it doesn't seem to work with me at all.

Java5 does work. Just replace "/usr/lib/jvm/java-6-sun/jre/bin/java" with "/usr/lib/jvm/java-5-sun/jre/bin/java"

Ubuntu x86 users
```
sudo apt-get install sun-java6-jre
wget http://iacchus.frostwire.com/frostwire/4.13.5/frostwire-4.13.5.i586.deb
sudo dpkg -i frostwire-4.13.5.i586.deb
sudo update-alternatives --config java # select the one that says "/usr/lib/jvm/java-6-sun/jre/bin/java"

```

Ubuntu x86_64 users
```
sudo apt-get install ia32-sun-java6-bin
wget http://iacchus.frostwire.com/frostwire/4.13.5/frostwire-4.13.5.i586.deb
sudo dpkg -i frostwire-4.13.5.i586.deb
sudo update-alternatives --config java # select the one that says "/usr/lib/jvm/ia32-java-6-sun/jre/bin/java"

```

That should fix your issues.

---

### Post by OsakaWilson on 2008-06-29
Be sure to read that last line carefully. What is written after the # is telling you how to proceed after putting in the code.
And by the way, Frak, if you feel yourself getting hit by a power wave of love, it could be coming from me for solving this problem for me.

---

### Post by genexxa27 on 2008-06-29
Just a quick question will that work if a person is using sun java 5 instead of 6.

---

### Post by Frak on 2008-06-29
> **genexxa27 said:**
> Just a quick question will that work if a person is using sun java 5 instead of 6.
Just replace 6 with 5, such as /usr/lib/jvm/java-5-sun/jre/bin/java instead.

If it works, tell me and I'll reflect it in the OP.

---

### Post by genexxa27 on 2008-06-30
I got Frostwire to work and i have a turbo charged connection. And its working good with java 5. Thanks for the How to.:D

---

### Post by backupdevice on 2008-06-30
Thx man, solved my problems

---

### Post by TonkaToy on 2008-08-24
yea thanks man this worked great :)

---

