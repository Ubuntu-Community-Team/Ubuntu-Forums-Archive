---
title: "Weak wifi signal strength"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by VonMatterhorn on 2012-10-31
Dear fellow Ubuntu users,

First of all, I'm sorry to be the one millionth person to post about the same issue but all posts concerning these issues did NOT resolve mine (and I've been through literally hundreds of threads). I have extremely poor wifi reception on my Lenovo machine, while everything works fine on Windows, I have to sit near one meter of my router to have a decent internet connection.

I have little to no knowledge about hardware and technical computer stuff but I do know how to work the Linux command line. Please help me, these wireless issues are the only thing keeping me from removing the dark side of my computer (being the dual booted windows 7).

I've tried installing versions 11.4, 11.10, 12.04 and 12.10, up until now 12.04 gives me the best wireless reception (still barely two meters).

Any help would be much appreciated!!

BTW: How can ubuntu be such a superior OS and yet perform so weak on wireless drivers? I mean, 90% of all ubuntu issues seem to be about wifi connection...

---

### Post by newb85 on 2012-10-31
90% is highly exaggerative.  Any machine you buy with Windows or OSX pre-loaded will also come with drivers designed for all the on-board hardware installed.  In Ubuntu, the drivers might be made available by the HW manufacturer (otherwise they have to be reverse-engineered), but they still have to be installed.  Ubuntu has come a long way in this area, and in most cases, driver installation is fully automated or very easy.

First thing we need to know is your specific hardware.

```
sudo lshw -C network
```

---

