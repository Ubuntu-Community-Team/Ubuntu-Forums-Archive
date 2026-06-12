---
title: "Which Distro to try if I really want to get my hand dirty and learn how Linux works?"
date: 2007-01-01
forum: Other OS Talk
---

### Post by happy-and-lost on 2007-01-01
Don't get me wrong. I love the effortlessness and stability of Ubuntu, and the fact that anyone can install and use it, but I've got a real itch to learn Linux properly. I really want to know how it fits together and *really* understand what I'm doing. Which distro would you guys recommend? One with a relatively simple to understand partitioner would be ideal, I don't want to damage my dual boot setup.

Another quick question - can I make my swap an extended partition? I've already got 4 primary and I'll need another for my "dirty" Linux.

Cheers :D

---

### Post by bonzodog on 2007-01-01
why do you have 4 primary partitions?

Even in a dual boot, you should only need one - for windows.

Linux is entirely happy in a logical partition, as the grub boot loader in the MBR tells it where to look to boot.

You should really have only one primary with the entire win setup on it, then an extended, with as many logicals as you need for linux. 

As for learning how linux works - well, once you have the HDD partitions set up properly, and windows installed the in the first primary, then ubuntu in the first 3 logicalof the first extended (root, home, swap), leave some room for the next linux distro. 
I would suggest Slackware, Zenwalk, or if you fancy building from source, try Gentoo. 

Slackware is a very good way of learning linux. - it throws you to a console on the first boot after install, where you have to configure X yourself first.  Then you would need to edit the /etc/inittab file to change the default runlevel to 4 so it boots into X next time.
There are all sorts of things you can learn by using Slackware- but be patient, the curve is um...steep.

---

### Post by arvster on 2007-01-01
I would also give my vote to Slackware. That was what I used for quite some time. At first I was reading a lot of manuals and trying things on my own (compiling the kernel, playing with config files). By countless broken things because of my experiments and attempts to fix them I learned quite a lot. Gentoo was also nice, but I found Slackware better personally, as waiting for countless things to compile can be quite annoying. Probably the ultimate way to learn Linux system internals would be Linux From Scratch [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/) ,but I never tried it myself- basically you build everything yourself- no distro or anything is there at the beginning.

---

### Post by happy-and-lost on 2007-01-01
Wow, Slackware does sound.. tough. I think I'll start with what I sort of know (Debian), and work my way up from there, eventually to Slack. I'd feel very geeky if I got Gentoo going. :mrgreen:

---

### Post by RAV TUX on 2007-01-01
> **happy-and-lost said:**
> Don't get me wrong. I love the effortlessness and stability of Ubuntu, and the fact that anyone can install and use it, but I've got a real itch to learn Linux properly. I really want to know how it fits together and *really* understand what I'm doing. Which distro would you guys recommend? One with a relatively simple to understand partitioner would be ideal, I don't want to damage my dual boot setup.

Another quick question - can I make my swap an extended partition? I've already got 4 primary and I'll need another for my "dirty" Linux.

Cheers :D


I suggest [Sorcerer.]("http://sorcerer.aakin.net/")

---

### Post by PilotJLR on 2007-01-01
You can absolutely learn Linux with Ubuntu... although Ubuntu includes a lot of easy to use GUI apps  for configuration, you don't have to use them. Stay on the command line, and you'll learn a lot!

I'd also recommend learning Fedora too, because Red Hat Enterprise Linux has a large install base on enterprise servers. It's very similar, but the RPM package management system is worth learning.

---

### Post by Wight_Rhino on 2007-01-01
How about Arch? It has a decent package manager with few dependency problems, but you get to configure everything via the config files.

---

### Post by rejser on 2007-01-01
My vote is on slackware, you get to  learn where it is important to optimize your system and how to do it. You will get to know the different deamons in the background better.

---

### Post by manmower on 2007-01-01
If you *_really_* want to get your hands dirty I, like others in this thread, would recommend Linux From Scratch (LFS). Haven't tried it myself, but it should help you understand Linux about as much as is humanly possible, since you literally start from scratch. Will be time-consuming though.

Gentoo isn't as hard as it may look, they have the best documentation of any distro and the manual will walk you through it. You just have to be prepared for the compile times (very discouraging for me on older hardware).

Arch is what I currently use. Being the distro that finally got me into configuring my system via simple text files rather than relying on GUIs, it seems pretty 'vanilla' so I suppose it wouldn't be a bad introduction to the inner workings of Linux, and aims to be as simple as possible (config files are kept straightforward and mostly self-explanatory and stored in the same place as much as possible, etc.). Hands down the fastest distro I have tried (faster than Gentoo in my case) and binary packages + easy package management (pacman) means no more waiting for hours for Firefox to compile. Excellent system for compiling your own packages when the need arises, too.

Debian, never tried it myself, I think the experience would not be entirely dissimilar to Arch, except it would probably be noticeably slower (Arch is i686 optimized and rather lightweight), and it's structure is bound to be more complicated.

---

### Post by M_the_C on 2007-01-01
I would also recommend Linux From Scratch.

I've already learnt so much and I haven't managed to install it yet.

---

### Post by arox on 2007-01-01
LFS
Arch
Slackware
Crux

---

### Post by RAV TUX on 2007-01-01
> **RAV TUX said:**
> I suggest [Sorcerer.]("http://sorcerer.aakin.net/")

Also refer to the [Sorcerer Thread]("http://www.ubuntuforums.org/showthread.php?t=329219") here.
[http://www.ubuntuforums.org/showthread.php?t=329219](http://www.ubuntuforums.org/showthread.php?t=329219)

---

