---
title: "NexentaOS - GNU/Ubuntu based Solaris"
date: 2007-05-16
forum: Other OS Talk
---

### Post by WalmartSniperLX on 2007-05-16
[http://www.gnusolaris.org/gswiki/ScreenShots](http://www.gnusolaris.org/gswiki/ScreenShots)

 Rather nifty eh? Don't know if this has been posted in the forums yet :lolflag: I'm a little intersted in it. I dl the vmware image and am soon to install it and run it in my linux system. :D


OK this was a dumb post. Moderators, please remove this thread :D please lol

---

### Post by Kalixa on 2007-05-16
> **WalmartSniperLX said:**
> [http://www.gnusolaris.org/gswiki/ScreenShots](http://www.gnusolaris.org/gswiki/ScreenShots)

 Rather nifty eh? Don't know if this has been posted in the forums yet :lolflag: I'm a little intersted in it. I dl the vmware image and am soon to install it and run it in my linux system. :D


OK this was a dumb post. Moderators, please remove this thread :D please lol

I for one do not consider it a stupid post. I am actually really interessted in Nexetna. I like Sun and everything they do in general, and if this could be combined with the rest of the gnu world this could end up being a really niftly OS. Debian+DTrace+ZFS. Sounds pretty neat!

---

### Post by matthew on 2007-05-16
It's not a dumb thread.

I've been watching Nexenta for a while. Let us know how the install goes. It's still alpha, I believe, so it's probably got some good bugs. Oh, if only I had time for one more project to play with...

---

### Post by hartz on 2007-05-16
> **matthew said:**
> Oh, if only I had time for one more project to play with...

My feeling exactly.  I actually have Nexenta installed, but my sound wasn't working and currently the project is falling behind in solving the logged bugs.  Beta 1 is now 5 months late.

[http://www.gnusolaris.org/gswiki/Bugs](http://www.gnusolaris.org/gswiki/Bugs)

I actually just wish I had the time to see if I could help solve some of the bugs!

---

### Post by dca on 2007-05-16
I would think now that Ian is working for Sun that much more work will be done on the Solaris OS.  At least making it more palateable like Debian so laptop and desktop installs can be done w/o driver issues and other glitches...

---

### Post by reidms on 2007-05-22
This is very interesting-

I have just installed Solaris x86 and it is pretty bad compared to the Sparc version-

I am gonna check this out- I think it has potential; its 12 month ranking at distrowatch is 30 and Alpha 7 has recently been released

---

### Post by billdotson on 2007-05-22
I didn't see anything all that great.  I installed it as a virtual machine in vbox and I looked.. didn't see anything that much different.  Looked like Ubuntu, but did less.  What is the reason to use it really?

---

### Post by hartz on 2007-05-23
Solaris Zones
ZFS
SRM
Running 32 and 64-bit apps simultaneously on a 64-bit kernel with no performance degradation.
dtrace

---

### Post by billdotson on 2007-05-25
um I dunno what ZFS really does, I don't even know what Solaris Zones is and those other things.. 64 bit apps.. what is the point?  Almost all apps are 32 bit anyway.  What is dtrace and what is SRM?

---

### Post by hartz on 2007-05-26
[DISCLAIMER]I am, after all, a Solaris bigot and a Sun Engineer[/DISCLAIMER]

Solaris is a 64-bit OS, so you get access to very large files, memory spaces, etc at no cost eg trickery with memory segmentation.

The ability to run 32-bit apps means you don't lose out on Flash and other such niceties.

Solaris Zones is a Server virtualization technology.  As long as you just want multiple "virtual" instances of your main kernel, it is brilliant.  You cannot however run Windows or BSD or whatever in a Solaris Zone.  It just runs Solars.  And it is an enterprise class tool, meaning it is stable.

Dtrace is tracing on steroids.  Anything from bus traps to library calls, from network-tracing to CPU-traps.  It's all there, and once you got your head arround its scripting language it is the greatest tool ever to find performance bottlenecks.  And it is an enterprise class tool, meaning it is stable.

ZFS - makes magic of managing disks/storage.  Creating a new file system is as easy as making a directory.  Very easy to manage anything from adding mirrors to growing file systems to splitting off more file systems.  Allows billions of small file systems or a single large file system to be created all with very little overhead.  Oh yeas, there is self-healing and automatic data CRC checking and encryption and compression, etc.  Just flick on the settings you want.  And it is an enterprise class tool, meaning it is stable.

SRM: Guarantee response times op applications.  Allocate minimum shares of CPU time.  Free CPU still available to all other processes.  Much more complicated than can be explained in one paragraph, but I'm planning on doing a talk on it in a few weeks time at the Cape Town Linux User's Group meeting.  P.S.  This too is an enterprise class tool, meaning it is stable.

All of this is free in OpenSolaris.  Actually, even Solaris is free, has been for about 8 years if truth be known, though only up to 4 CPUs in some cases.  Now it's just free as in beer.  OpenSolaris is free as in Speech.

<GRIN>

---

### Post by hanzomon4 on 2007-05-26
I'm pretty excited about opensolaris so I'll play the skeptic.. *What does all of that mean for desktop users mister solaris dude?* I'm really asking about Solaris in the next few years after more time has been put into projects focusing on consumer desktops, like Nexenta and BeleniX. Isn't that debian guy working for sun now? That should help in bringing the fruits of Solaris to the non-techie linux user(that has to seem like an oxymoron to some). I can't wait to see user friendly technology built on top of the latest Sun innovations...

---

### Post by Hendrixski on 2007-06-12
> **hartz said:**
> [DISCLAIMER]
All of this is free in OpenSolaris.  Actually, even Solaris is free, has been for about 8 years if truth be known, though only up to 4 CPUs in some cases.  Now it's just free as in beer.  OpenSolaris is free as in Speech.
<GRIN>

Fhat's the only kind of free that matters.  Free of cost means nothing because viruses are free of cost too... but they're not free as in freedom.

I'm looking forward to the day where someone can swap out a Linux Kernel for an OpenSolaris Kernel, or a BSD kernel.  Though, OpenSolaris is not quite there yet in terms of driver support.  Hopefully CDDS will allow companies who insist on making proprietary drivers to make them for the Solaris Kernel as well, but that may yet be a few years away.

It's exciting!  Let's keep watching and hopefully nexenta will hold its own against Windows, rather than stealing them from Linux and BSD.

---

### Post by Dragonbite on 2007-06-13
Has anybody read Ian Murdock's blog and what are your thoughts on it?

[[COLOR="Blue"][COLOR="Blue"]http://ianmurdock.com/2007/06/08/where-do-i-download-opensolaris/[/COLOR][/COLOR]]("http://ianmurdock.com/2007/06/08/where-do-i-download-opensolaris/")

At first was all "sounds good" but now I'm beginning to wonder why? With [[COLOR="Blue"][COLOR="Blue"]Belenix[/COLOR][/COLOR]]("http://www.genunix.org/distributions/belenix_site/"), [[COLOR="Blue"][COLOR="Blue"]Shillix[/COLOR][/COLOR]]("http://schillix.berlios.de/"), [[COLOR="Blue"][COLOR="Blue"]Nexenta[/COLOR][/COLOR]]("http://www.gnusolaris.org/") and [[COLOR="Blue"][COLOR="Blue"]Solaris Express[/COLOR][/COLOR]]("http://developers.sun.com/sxde/") (Developer Ed. or Community Ed.).

---

### Post by cantormath on 2007-06-13
> **WalmartSniperLX said:**
> [http://www.gnusolaris.org/gswiki/ScreenShots](http://www.gnusolaris.org/gswiki/ScreenShots)

 Rather nifty eh? Don't know if this has been posted in the forums yet :lolflag: I'm a little intersted in it. I dl the vmware image and am soon to install it and run it in my linux system. :D


OK this was a dumb post. Moderators, please remove this thread :D please lol

Pretty cool.

---

### Post by Hendrixski on 2007-06-13
[quote=Ian Murdoch]
But how many of you have actually experienced this great stuff first hand? How many hands go down if you’re under 30 and don’t remember the Sun workstation—i.e., you’re one of the many for whom Linux = Unix for as long as you’ve been in the computer business?
[/quote]

hah hah.  I'm under 30 and I used to work on Solaris 8 ... hence my user icon.  It is one hell of a solid system.

Ian forgets to mention how woefully behind Linux they are in driver support.  While in theory they can bridge the gap quicker because of the CDDS license, they still have a long long long long long way to go. Very few people will be able to get an OpenSolaris distribution running in the near future.

Also, he points out how they're trying to convert Linux users to OpenSolaris rather than targeting proprietary platforms like Mac or Windows.  Maybe it's because we'll put up with more crap when it comes to drivers not working.

---

