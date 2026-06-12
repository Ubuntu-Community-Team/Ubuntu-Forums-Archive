---
title: "Enabling Java in Firefox - libnpjp2.so file missing"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by ancaleth on 2012-09-27
Noticing that the command to create a symbolic link (necessary to enable the Java plugin in Firefox) was meant for 32-bit instead of 64-bit, I tried to remove the symbolic link and ended up deleting the file libnpjp2.so from usr/lib/mozilla/plugins.

Now I am quite lost. How do I recreate the libnpjp2.so file? And how should I proceed from there on to avoid the former mistake and have Java running smoothly?

I run ubuntu 11.04 64-bit, Firefox 15.0.1. The Icedtea-plugin is installed.

My Java version is:
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

Any help would be greatly appreciated. I need to install Java urgently for a work project.

---

### Post by 73ckn797 on 2012-09-27
See if this link will help: [https://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU](https://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU)

32 & 64 bit Java installation info.

---

### Post by ancaleth on 2012-09-27
Thanks, this saved me. Everything works fine now!

---

### Post by geronl on 2012-09-27
> **ancaleth said:**
> Thanks, this saved me. Everything works fine now!

You can use "Thread Tools" to list this as SOLVED

---

### Post by 73ckn797 on 2012-09-28
> **ancaleth said:**
> Thanks, this saved me. Everything works fine now!
Glad to hear you got things worked out. It has worked every time for me. I just do not like that Java is not updated regularly as in the recent past. I have been able to run the openjdk and icedtea java versions on a 32 bit system. They are available in the repositories.

---

