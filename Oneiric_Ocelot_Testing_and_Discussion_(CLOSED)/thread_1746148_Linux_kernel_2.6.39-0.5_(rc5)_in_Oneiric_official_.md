---
title: "Linux kernel 2.6.39-0.5 (rc5) in Oneiric official repos"
date: 2011-05-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-01
New linux kernel 2.6.39-0.5 (rc5) is in Oneiric official repos now.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/2.6.39-0.5](https://launchpad.net/ubuntu/oneiric/+source/linux/2.6.39-0.5)

It works well.
Though during installation it throws an error of possible missing Realtek firmware (package linux-firmware).

---

### Post by DougieFresh4U on 2011-05-01
Had rc4 on my Natty install and seemed ok. No problems with rc5 and my Oneiric install.:D

---

### Post by Harry33 on 2011-05-02
The linux 2.6.39 meta packages are now in Launchpad.
For those who use them.
I personally don't use meta packages.
That is because it narrows possibilities for a custom setup.

Anyway, here:
[https://launchpad.net/ubuntu/oneiric/+source/linux-meta/2.6.39.0.1](https://launchpad.net/ubuntu/oneiric/+source/linux-meta/2.6.39.0.1)

---

### Post by jppr on 2011-05-02
> **Harry33 said:**
> The linux 2.6.39 meta packages are now in Launchpad.
For those who use them.
I personally don't use meta packages.
That is because it narrows possibilities for a custom setup.

Anyway, here:
[https://launchpad.net/ubuntu/oneiric/+source/linux-meta/2.6.39.0.1](https://launchpad.net/ubuntu/oneiric/+source/linux-meta/2.6.39.0.1)

Works fine :popcorn:

---

### Post by rtalcott on 2011-05-03
the desktop (to me) seems really fast now...anyone else seeing this?

rt

---

### Post by xm.carlos on 2011-05-07
I feel the same. My computer is now faster.
Sysinfo was reporting 800Mhz for my CPU and now reports correctly 1600Mhz.
Maybe has to do with some ACPI stuff.

---

### Post by cecilpierce on 2011-05-07
This is the fastest I've seen in awhile, usually its up at 1min30sec-1min45sec.

---

### Post by Harry33 on 2011-05-07
There is already 2.6.39-1 rc6 in Ocelot repos and another thread about it:

[http://ubuntuforums.org/showthread.php?t=1749439](http://ubuntuforums.org/showthread.php?t=1749439)

---

### Post by beew on 2011-05-07
> **cecilpierce said:**
> This is the fastest I've seen in awhile, usually its up at 1min30sec-1min45sec.

Maybe I am missing something, are you talking about boot time? 10.04 and 10.10 take about 25 -30 seconds to boot (from power on to up and running) on all machines I have tested and 11.04 takes about 35-40s (to load Unity). Never have I experienced anything more than a minute.

---

### Post by VinDSL on 2011-05-07
> **beew said:**
> 10.04 and 10.10 take about 25 -30 seconds to boot (from power on to up and running) on all machines I have tested and 11.04 takes about 35-40s (to load Unity).[...]
Same here... sorta.

My fastest boot time, ever, was with 10.10 -- 19 seconds.

Normally, 10.10 (GNOME2) boots this machine in 22-27 seconds.

11.04 & 11.10 (UNITY) takes 30-38 seconds.

Here's my current setup...

```

vindsl@Zuul:~$ uname -s -r && unity --version && cat /etc/lsb-release && /usr/lib/nux/unity_support_test -p
**[COLOR="Red"]Linux 2.6.39-020639rc6-generic[/COLOR]**
**[COLOR="red"]unity 3.8.12[/COLOR]**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="**[COLOR="red"]Ubuntu oneiric (development branch)[/COLOR]**"
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 **[COLOR="red"]NVIDIA 270.41.06[/COLOR]**

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
vindsl@Zuul:~$ 

```


That said, I haven't noticed any reduction in boot time with any of the 2.6.39 rc's -- and I've run them all.  

If anything, they're a tad-bit slower on this machine, than 2.6.38 (see sig for specs).

2.6.36 & 2.6.37 boot Unity in the 30-ish second range too.  Dittos for the Liquorix kernels.

Not complaining -- just saying...  ;)

---

### Post by ranch hand on 2011-05-09
My fastest boot time since 10.04 is 3.5 minutes.  Don't know what happened there, is not usually near that fast.

---

### Post by Harry33 on 2011-05-10
> **ranch hand said:**
> My fastest boot time since 10.04 is 3.5 minutes.  Don't know what happened there, is not usually near that fast.

Well well!
You should do something about that.

I haven't seen any boot (from grub to desktop) last longer that 30 seconds after Karmic (9.10). My Natty setups and one Oneiric pre-alfa vary from 15 to 25 secs now. However, that 15 secs is possible only with a minimal gnome2 setup (total of 720 packages) and a very fast WD HDD (10.000 rpm).

---

### Post by ranch hand on 2011-05-11
I did do something about it.   I use Debian.

---

### Post by Harry33 on 2011-05-12
> **ranch hand said:**
> I did do something about it.   I use Debian.

Ok. What kind of boot times you have with Debian?

---

### Post by nutznboltz on 2011-05-13
> **rtalcott said:**
> the desktop (to me) seems really fast now...anyone else seeing this?

> [Linux 2.6.38 eliminates last main global lock, improving performance]("http://blog.internetnews.com/skerner/2011/01/linux-2638-eliminates-last-mai.html")
By Sean Michael Kerner on January 19, 2011 9:20 AM 

... With 2.6.37, the Big Kernel Lock (BKL) was removed, but apparently there is at least one more big global lock that needed to come out. In 2.6.38 there is a new RCU (Read/Copy/Update)-based path name lookup.

    "It's some seriously good stuff, and gets rid of the last main global lock that really tends to hurt some kernel loads," Linus Torvalds commented about the RCU lookup.

Torvalds added that the new lookup improves kernel performance by as much as 30 to 50 percent in some cases.

Except that Sean was wrong about the last global lock being removed on 2.6.38 as a subsequent patch to 2.6.39 did that:

> [BKL: That's all, folks]("https://lkml.org/lkml/2011/1/25/520")
Arnd Bergmann / Tue, 25 Jan 2011 23:17:34 +0100

This removes the implementation of the big kernel lock, at last. A lot of people have worked on this in the past, I so the credit for this patch should be with everyone who participated in the hunt.

In simple terms when computers with multiple CPUs (or multi-core CPUs) tried to run code on each core simultaneously on older Linux versions like Lucid's Linux version 2.6.32 they were prevented from doing so if the code was trying to access certain kernel features.  For example if one process was doing network I/O it would have to wait when a totally different process was doing disk I/O.  Now with Linux version 2.6.37 through 2.6.39 the number of conditions when such waiting would occur has been reduced allowing multi-core operations to run simultaneously in many cases that wasn't happening with older Linux versions.

---

### Post by VinDSL on 2011-05-13
> **rtalcott said:**
> the desktop (to me) seems really fast now...anyone else seeing this?

> **nutznboltz said:**
> Now with Linux version 2.6.37 through 2.6.39 the number of conditions when such waiting would occur has been reduced allowing multi-core operations to run simultaneously in many cases that wasn't happening with older Linux versions.
There is no disputing that the newer kernels make this 7 year-old machine faster.

Is it a day n' night difference?  No.

Fast as Puppy Linux, for instance?  No.

Boot is 10-15 seconds slower, but this is probably due to Baby Unity, not the kernel.  And, it will grow faster, with maturity.

The Desktop (admittedly a broad term) is very fast & responsive.

GtkPerf scroll times are down a bit, but this is the combined result of running the latest nVidia drivers on an older game card.

Networking is MUCH faster, now that I switched to the "DSL connection".  It bypasses all the nonsense taking place on my LAN hardware.

Overall, this machine (see sig) is performing admirably on UbuOO with 2.6.39rc7, so I'm a happy camper!  ;)

---

### Post by ranch hand on 2011-05-14
> **Harry33 said:**
> Ok. What kind of boot times you have with Debian?
You know, I have never measured it exactly but it is the fastest thing I have on the box.  I have had little success with bootchart in Ubuntu and none at all in Debian.  I usually use a stop watch.  Have to dig it out and get back to you on that.

---

### Post by ranch hand on 2011-05-14
55 seconds.

Using bootchart2 with pybootchartgui.

I think that adds about 2 seconds to the boot time but folks do like a standardized method of measurement for very good reason.

After my last post I checked the boot chart packages and had never seen bootchart2 before, haven't looked at it for months and bootchart just did not work.  This does, I am glad of that.

Have to try it on my other installs Sqeeze, Wheezy (like this install but I don't use it except to try my "improvements" on to see if they break something) and Sid.

Thanks for the nudge.

---

