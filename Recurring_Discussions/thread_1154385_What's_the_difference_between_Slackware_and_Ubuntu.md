---
title: "What's the difference between Slackware and Ubuntu?"
date: 2009-05-09
forum: Recurring Discussions
---

### Post by Gucko on 2009-05-09
Hi guys, I heard a lot about Slackware, so what's the difference between Slackware and Ubuntu?

Is it hard? Do you really need to be a pro to use? Is it great and strong? And what kind of people do use it? Programmers? I heard that it's intended for people who works with hardware.

Thank :)

---

### Post by Gucko on 2009-05-09
...and for hackers.

---

### Post by t0p on 2009-05-09
Earlier on you posted the question "What's the difference between Fedora and Ubuntu.  Now you're asking about Slackware.

I certainly wouldn't tell you that Google Is Your Friend.  Instead I'll refer you to my reply in that other thread.

---

### Post by RiceMonster on 2009-05-09
It's pretty much as far away from Ubuntu as you can get.

[http://www.slackware.com/info/](http://www.slackware.com/info/)

It's got a very primitive package management system (no repos, no dependancy handling), but some people consider that a good thing. Also, the install process is drastically different. You have to partition your hard drive manually, a walk through numerous configuration options.

---

### Post by kk0sse54 on 2009-05-09
[http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Slackware](http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Slackware)

---

### Post by monsterstack on 2009-05-09
There are three main flavours of Linux, from which all of the other Linuxes are derived. Debian, Red Hat and Slackware. Debian has debs for package managedment. Red Hat uses RPM. Slackware uses the hope and pray method.

See for [yourself]("http://www.kde-files.org/CONTENT/content-pre1/57722-1.png"). [kde-files.org] [[COLOR="Red"]png file[/COLOR]]

You'll be surprised from where some of the distros come from.

---

### Post by Daveski on 2009-05-09
An old saying in the Linux community says, "If you learn Red Hat, you learn Red Hat. If you learn SuSE, you learn SuSE. But if you learn Slackware, you learn Linux"

---

### Post by chris200x9 on 2009-05-09
> **monsterstack said:**
> There are three main flavours of Linux, from which all of the other Linuxes are derived. Debian, Red Hat and Slackware. Debian has debs for package managedment. Red Hat uses RPM. Slackware uses the hope and pray method.

See for [yourself]("http://www.kde-files.org/CONTENT/content-pre1/57722-1.png"). [kde-files.org] [[COLOR="Red"]png file[/COLOR]]

You'll be surprised from where some of the distros come from.

lol @ this chart: arch...I guess being built up from scratch means crux derived...:confused:

---

### Post by will1911a1 on 2009-05-09
> **chris200x9 said:**
> lol @ this chart: arch...I guess being built up from scratch means crux derived...:confused:

Arch being based on Crux is a pretty common misconception.

---

### Post by sertse on 2009-05-09
Not derived, but still inspired by the concepts originally in found in CRUX. The ideological cornerstone "The Arch Way" could be said to be first found in CRUX, with Arch being a much better implementation of that concept.  

So you can go along being proud that Arch is independent etc, but still some respect should be paid...

---

### Post by eilu on 2009-05-09
Slackware isn't THAT bad! Although I use a derivative, [SLAX]("http://www.slax.org") (think slackware 101 or slackware kindergarden) which I converted to a full slackware install to HD.
Package management can be a dog sometimes speciall when it turns into a cascade of hunt-the-dependency (and the dependencies' dependencies), but it's very snappy on my ancient P3 and works for me.
I'd have to agree that learning slackware is like learning linux- I didn't dive into the command line in my years with Ubuntu as much as I did in my days (so far) of Slackware. It's fun though, and I'm keeping it.

---

### Post by andrew.46 on 2009-05-12
Hi Gucko,

> **Gucko said:**
> Hi guys, I heard a lot about Slackware, so what's the difference between Slackware and Ubuntu?

Best way to really find out is to download it and give it a run :-). On the root of the DVD there are [very detailed instructions for installation]("http://slackware.osuosl.org/slackware-12.2/Slackware-HOWTO").

> Is it hard? Do you really need to be a pro to use? Is it great and strong? And what kind of people do use it? Programmers? I heard that it's intended for people who works with hardware.

Well, I use it as my primary distro and I am just a very ordinary user :-). I attach a screenshot, the desktop is xfce.

All the best,

Andrew

---

### Post by petrus4 on 2009-05-14
> **Gucko said:**
> Hi guys, I heard a lot about Slackware, so what's the difference between Slackware and Ubuntu?

Slackware and Ubuntu are almost completely different.

Slackware is basically a native or natural Linux system.  Ubuntu on the other hand is something Debian based, the primary goal of which is to be a clone of Microsoft Windows.

I've seen a number of threads in the General Help forum here recently about people with Jaunty having totally broken, dysfunctional systems that simply will not boot.  Slackware takes some more effort to configure initially, but if you're willing to do that, once it is set up, Slackware generally does not break down in that way.

Slackware and Ubuntu are both simple, but in different ways.  Ubuntu is designed to be simple for end users, but it buys this simplicity by being extremely complex technically and on the "under the hood," side of things.

Slackware, to some extent, is the opposite.  It can take a little more effort to set up and use, but it is much simpler on the technical side, and it is that simplicity which also makes it more reliable and less likely to break.  The other thing is that once a user becomes knowledgeable about Slackware's internals, then not only does the system become easier for end use, but the level of high reliability and robustness stays, as well.

Slackware's technical simplicity has the other advantage, that it is flexible.  Ubuntu is not flexible or versatile at all.  You can perform a certain number of relatively pre-planned tasks with it, but if you try and do anything even slightly unusual, things break almost immediately.

I removed the symlinks to gdm from /etc/rc*.d in Ubuntu, and the entire system immediately began falling apart, including elements like bash and ALSA which should not be affected by changing the window environment at all.

Slackware on the other hand, because of said simplicity and relatively clean modularity, can be used robustly in just about any manner you can imagine, including ways that the original designers didn't foresee.

---

### Post by javyn999 on 2009-05-17
I installed Slackware in Virtualbox last night.  It definitely doesn't hold your hand the way Ubuntu does during install, but I wasn't expecting it to.  

Following a walkthrough so I knew what to type to execute the partition manager made it quite easy.  If you can install any pre-XP Microsoft Operating system, I think you can install Slackware w/o issue.  

Setting it up on the other hand...different story heheh.

The bootup speed of Slackware is amazing.  I am new to Linux in general, and was going to buy several books on learning to use Ubuntu, command line, etc...but now think I am going to focus my learning on my Slackware VM, that way it will make me more proficient with all distributions rather than just Ubuntu.

---

