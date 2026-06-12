---
title: "Looking for a suitable distro..."
date: 2009-01-22
forum: Other OS Talk
---

### Post by SoftVision on 2009-01-22
I've tried some distros for more than a year now and I've decided what stuff I'd like in the distro I'd like to try next:
[LIST][*]Speed & Source-based - Zero bloat, no unncessary services on startup, possibly vanilla packages or compilation. [*]Stable barebones base install - Just a quick/simple base I can build on. The base doesn't have to be bleeding edge, it needs to be stable so I can forget about it as long as it works on my hardware. [*]KDE 4.2 - I know it hasn't released but the distro should support it by the time it does or even a few months ahead. If not then I can just grab the packages from kde.org and compile. There should be someway then to upgrade those KDE packages when there are point releases. [*] Release cycle - rolling or 6-month releases, anything will do really.[/LIST]

I've already used Arch for a long time and I'd like to look at a few others. I'm very open to BSD because I've seen distros with BSD-style initscripts and its made me curious. I don't need such extensive customisations and time consumption with USE flags so I'd prefer not to go with Gentoo.

I've got a few in mind: Slackware, FreeBSD, CRUX. Can't think of more. 

Any suggestions?

---

### Post by kk0sse54 on 2009-01-22
I'd highly recommend all three of those you've already mentioned although if you're going to try out some of the *BSD I'd also recommend trying out NetBSD. I'm running KDE 4.2 Beta on it without any problems although be forwarned about some of the quirks with *BSD (flash & proprietary video drivers :evil:).

---

### Post by Sorivenul on 2009-01-22
You have listed the distributions I would suggest. 

FreeBSD is awesome, and you can currently install the KDE 4.2 Beta on it, I believe. It gets my official vote. Slackware is next on my list for you, simply because maintaining a CRUX system takes more effort, IMO. I find myself working to make CRUX work for me more than I ever have with FreeBSD or Slackware.

Good luck!

---

### Post by cardinals_fan on 2009-01-22
CRUX or NetBSD.  Clean, simple elegance.

Slackware is great but binary.  FreeBSD is also okay.

---

### Post by SoftVision on 2009-01-22
> **C!oud said:**
> I'd highly recommend all three of those you've already mentioned although if you're going to try out some of the *BSD I'd also recommend trying out NetBSD. I'm running KDE 4.2 Beta on it without any problems although be forwarned about some of the quirks with *BSD (flash & proprietary video drivers :evil:).

I don't have any proprietary video drivers, I just have an Intel card. Yes, I've heard about flash being unavailable. I'll still give it a shot sometime. 

How did you go about installing KDE 4.2 beta on NetBSD?

---

### Post by rliegh on 2009-01-22
I don't think you're going to get KDE 4.2 on NetBSD yet; OpenBSD has a rolling release cycle (every May and every November since 1996) and otherwise meets your requirements -but the software in their ports tends to be old versions.

FreeBSD meets your requirements, but I don't think you could really call them  "rolling release" oriented -they seem to come out with a version about once a year or so. 

Of course, none of those may fit your requirements.

What do you mean by "source based"? You *could* install Open Solaris and get the Nevada source package which would give you the same kernel+userland source set that you'd get with the BSDs (minus X -which you could also grab from their xorg project). I have no idea about how KDE 4.2 works with them, but they tend to release pretty often (OpenSolaris comes out twice a year, and you have twice-monthly "community express" releases that come with the kitchen sink). No one would ever call Solaris "minimalist", however.

Then there's slackware -minimalistic; no idea about whether you could consider them "source based" (I don't).

Lastly, there's Gentoo -it's never worked for me, so I couldn't tell you about it.

HTH.

---

### Post by kk0sse54 on 2009-01-22
> **rliegh said:**
> I don't think you're going to get KDE 4.2 on NetBSD yet; OpenBSD has a rolling release cycle (every May and every November since 1996) and otherwise meets your requirements -but the software in their ports tends to be old versions.
I'm using my NetBSD machine right now using the latest beta 4.1.96 since KDE 4.2 isn't released for another 5 days, and the maintainer for it has definitely been keeping up. Pretty sure FreeBSD also has the 4.2 release candidate but I don't know about OpenBSD, I'd have to check their ports page.

---

### Post by SoftVision on 2009-01-22
Ok I'm downloading the NetBSD i386 4.0.1 CD. Will it be possible to dual boot with Windows XP? After installing, how do I get KDE 4.2?

---

### Post by DM was on fire! on 2009-01-22
> **SoftVision said:**
> Ok I'm downloading the NetBSD i386 4.0.1 CD. Will it be possible to dual boot with Windows XP? After installing, how do I get KDE 4.2?

Most OSes can be dualbooted with XP (but don't quote me on this).
As for installing KDE 4.2...

[http://kde.org/info/4.1.96.php#binary](http://kde.org/info/4.1.96.php#binary)

---

### Post by SoftVision on 2009-01-22
> **DM was on fire! said:**
> Most OSes can be dualbooted with XP (but don't quote me on this).
As for installing KDE 4.2...

[http://kde.org/info/4.1.96.php#binary](http://kde.org/info/4.1.96.php#binary)

When 4.2 final is released, how do I upgrade these binaries?

---

### Post by jay576 on 2009-01-22
Ever think about trying Gentoo?

---

### Post by SoftVision on 2009-01-22
> **jay576 said:**
> Ever think about trying Gentoo?

I did. Maybe I will one day. But not right now, thanks anyway. :)

---

### Post by jay576 on 2009-01-22
> **SoftVision said:**
> I did. Maybe I will one day. But not right now, thanks anyway. :)
I thought that description made you perfect for gentoo.
You know you could always install kde4.2 on your own on top of any distros base

---

### Post by SoftVision on 2009-01-22
> **jay576 said:**
> I thought that description made you perfect for gentoo.
You know you could always install kde4.2 on your own on top of any distros base

It does sort of yes. Gentoo will be on my radar though. :)

---

### Post by kk0sse54 on 2009-01-22
> **SoftVision said:**
> Ok I'm downloading the NetBSD i386 4.0.1 CD. Will it be possible to dual boot with Windows XP? After installing, how do I get KDE 4.2?

Yes NetBSD can be dual booted with XP however I do not suggest using the NetBSD bootloader, it's much easier to install and use grub. If NetBSD 4.0.1 provides everything you need then you should be fine otherwise I think NetBSD-5.0_BETA is coming to a stage where it's pretty stable ( I haven't had any problems running it).

And do *not* install KDE from kde.org. Instead say hello to pkgsrc (package management system for NetBSD). You might want to take a look at this.

**[The pkgsrc guide]("http://netbsd.org/docs/pkgsrc/index.html")**

I'd recommend using the current branch of pkgsrc (if you want more up to date software), but once you've got that set up you also need to download the**[ pkgsrc-wip]("http://pkgsrc-wip.sourceforge.net/")** branch in order to compile and install KDE4. While there is a meta-pkg to pull in all the components of KDE4 I suggest you only do a base install (wip/kdebase4) and then pick and choose the sets that you want.

Another great site to get familiar with is [**pkgsrc.se**]("http://pkgsrc.se/") which basically allows you to browse through the different branches of pkgsrc so that you may decide on pkgsrc-2008Q3, pkgsrc-2008Q4, or current etc etc. It's also a great place to look up packages and see what version they are and the dependencies that will be installed.

---

### Post by fistfullofroses on 2009-01-22
> **SoftVision said:**
> It does sort of yes. Gentoo will be on my radar though. :)

GoboLinux

---

