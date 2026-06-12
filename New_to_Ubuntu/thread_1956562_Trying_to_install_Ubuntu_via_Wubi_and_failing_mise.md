---
title: "Trying to install Ubuntu via Wubi and failing miserably"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by AbsolutelyClueless on 2012-04-11
Dear all,

First of all, apologies if I post this in the wrong forum. Also, I'd like to say that I had a look at the bugfixes/wubi threads, but I seem to lack the basics to even understand what they are saying.

Over the last couple of days, I have been trying to install Ubuntu using wubi on my ASUS Eee PC 1101 HA. I was looking at trying it out and running it in parallel to Windows XP (already installed). 

The installation runs smoothly, the pc reboots, I get to choose which OS, I see the Ubuntu screen... but then some kind of command line shell comes up. Eventually, it stops progressing.

The last entries are:

* stopping cold plug devices
* stopping log initial device creation
* starting configure network device security
* starting ubuntu live cd installer
* starting CUPS printing spooler/server
* checking battery state...
* stopping system V runlevel compatibility

And then, nothing happens anymore. I don't know whether it matters, but the font is white, while some lines above it is brownish.

I would greatly appreciate any help. If I can't make it work, I will have to stay a Windows user for the rest of my entire live - please help me to avoid that cruel fate....

---

### Post by Tony Flury on 2012-04-11
i have never used Wubi, but one thought - why did you choose the WUBI istall ? I would go for a dual boot option - you might have a lot more luck

---

### Post by AbsolutelyClueless on 2012-04-11
To be honest, out of convenience - it appeared to be a "one click" solution that doesn't require intimate linux expertise to get started.

---

### Post by Curtis6767 on 2012-04-11
__Did you see this: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


[]("https://www.youtube.com/watch?v=7VxvmaZOB8A")

---

### Post by bcbc on 2012-04-11
The problem isn't to do with Wubi. Check this out: [http://ubuntuforums.org/showthread.php?t=1837473](http://ubuntuforums.org/showthread.php?t=1837473). This lists some kernel boot option overrides you need.

To override boot options review this thread: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (wubi specific is in post #8 and depends on how you installed wubi). If you go with a normal dual boot, follow instructions in the first post on how to override the boot options on the live CD (since you are not dealing with a 'one-click' solution anymore).

---

