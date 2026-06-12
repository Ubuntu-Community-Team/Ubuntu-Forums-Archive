---
title: "Ubuntu 13.10 vs 11.10"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by apprime on 2014-01-06
hello,

I have an old laptop with 11.10 ubuntu on, is it worth me upgrading to 13.10? Is there a whole bunch of newer software packages for it etc?

am I at a security risk with 11.10 still?

I just wanted to know if there was a major difference in the versions before I re-install everthing

thanks,
Jon

---

### Post by Frogs Hair on 2014-01-06
11.10 is no longer supported and a security risk . An upgrade or clean installation of 12.04 would be a good Idea.(long term support) See the link for support dates of other releases and keep in mind hardware is a consideration depending on the age of the computer.  Don't forget about the Ubuntu flavors either. :)  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by whitesmith on 2014-01-06
As for newer software packages, Linux isn't like Windows in that upgrades are necessary to run them. I've seen plenty of dusty machines in computer rooms that shocked me when I ran```
uptime
```on them, but the mere fact that something works elsewhere doesn't mean that it's a good idea to emulate it with your own equipment. Heed the earlier post by #Frogs Hair. Cheers.

---

### Post by kurt18947 on 2014-01-07
> **Frogs Hair said:**
> 11.10 is no longer supported and a security risk . An upgrade or clean installation of 12.04 would be a good Idea.(long term support) See the link for support dates of other releases and keep in mind hardware is a consideration depending on the age of the computer.  Don't forget about the Ubuntu flavors either. :)  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

+1 on other flavors, particularly on older machines.  Lubuntu & Xubuntu seem to be less demanding than Ubuntu, particularly on machines with older/weaker graphics systems.

Edit: Here is an example of a possible security issue that will not be automatically fixed in non-supported distros AFAIK:

[http://lists.x.org/archives/xorg-announce/2014-January/002389.html](http://lists.x.org/archives/xorg-announce/2014-January/002389.html)
> Description:
============

Scanning of the libXfont sources with the cppcheck static analyzer
included a report of:

  [lib/libXfont/src/bitmap/bdfread.c:341]: (warning)
      scanf without field width limits can crash with huge input data.

Evaluation of this report by X.Org developers concluded that a BDF font
file containing a longer than expected string could overflow the buffer
on the stack.  Testing in X servers built with Stack Protector resulted
in an immediate crash when reading a user-provided specially crafted font.

As libXfont is used to read user-specified font files in all X servers
distributed by X.Org, including the Xorg server which is often run with
root privileges or as setuid-root in order to access hardware, this bug
may lead to an unprivileged user acquiring root privileges in some systems.

How much of a risk is this?  I have no idea but AFAIK if an exploit is created as a result of this disclosure, it won't be fixed by the distro maintainers.

---

