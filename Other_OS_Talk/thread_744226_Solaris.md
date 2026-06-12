---
title: "Solaris?"
date: 2008-04-03
forum: Other OS Talk
---

### Post by whitefang5412 on 2008-04-03
Ok, I may know a lot about linux, computers, and the such but I don't know everything, so why not ask a question? :)

Can anyone give me some insight as of to what solaris is? Is it a Linux operating sytem? If so is it debian based, redhat based or other, or is it unix like BSD. Thanks.

---

### Post by linuxtoindia on 2008-04-03
i think solaris is not pure linux

---

### Post by munkyeetr on 2008-04-03
It is UNIX-based, and released by Sun Microsystems

[http://www.sun.com/software/solaris/index.jsp](http://www.sun.com/software/solaris/index.jsp)
[http://en.wikipedia.org/wiki/Solaris_Operating_System](http://en.wikipedia.org/wiki/Solaris_Operating_System)

---

### Post by whitefang5412 on 2008-04-03
Thanks for clearing things up guys.

---

### Post by igknighted on 2008-04-03
> **munkyeetr said:**
> It is UNIX-based, and released by Sun Microsystems

[http://www.sun.com/software/solaris/index.jsp](http://www.sun.com/software/solaris/index.jsp)
[http://en.wikipedia.org/wiki/Solaris_Operating_System](http://en.wikipedia.org/wiki/Solaris_Operating_System)

More like solaris IS unix, while linux is unix-LIKE (caps for emphasis, not shouting).  They are two separate, independant operating systems (read: kernels), that use many of the same programs to deliver the end user experience.  Solaris is a powerhouse in the corporate server room, but is just branching out into the desktop.  Sun's Project Indiana (headed by Ian Murdock, founder of Debian) is the most promising Desktop Solaris version, but it is still a few years off from being a viable desktop solution.  But with a major corporate backer that really seems to be pushing to make Solaris a desktop choice, don't be surprised to see it catch up to linux in terms of usability in the not too distant future.

---

### Post by dca on 2008-04-03
Even the "power" button requires a driver...  :D

---

### Post by bwhite82 on 2008-04-03
> Solaris?

Walk the other way, trust me.

---

### Post by D-EJ915 on 2008-04-03
> **dca said:**
> Even the "power" button requires a driver...  :D
it requires ACPI to be enabled for it to work in Linux too

---

### Post by 3rdalbum on 2008-04-04
The userspace utilities for Solaris are different to those on GNU/Linux, so your favourite commands might not work the same way, and probably don't accept the same options.

Also, the /dev on Solaris is freaking scary :-D

---

### Post by LinuxGuy1234 on 2008-04-05
Even scarier... the console font is ugly. /dev on Solaris is even ugly than in *BSD and Linux. If I were to try something it would not be:
* Windows (OLD)
* Solaris (NEW)

---

### Post by laxmanb on 2008-04-05
Naah... I'm using SXDE 01/08 right now. And it's pretty good. Hardware support is good as well. And /dev is different from Linux, but you have to get used to it.

And seriously, console font is ugly is a flaw?

---

### Post by tubasoldier on 2008-04-05
I'm suprised to see so many scared of Solaris. I've used it in the past but never stuck with it because of the lack of hardware support. I haven't tried it out in a few years, maybe its time to check it out again...

---

### Post by ch_123 on 2008-04-05
Its also bloody slow... Unless they make some massive improvements to it, I think Linux is a better Desktop OS by far. Now, for Server and special applications, it may or may not be better. Depends on what you use your PC for.

---

### Post by mr.farenheit on 2008-04-05
basic unix. don't bother though, too over complicated for nothing.

---

### Post by mmichalik on 2008-04-05
Solaris is pretty much the leading Corporate America UNIX O/S right now.  It' way easier to use then HP and IUX.  

It's extremely powerful but, is designed really to run on RISC processors.  I know they have an Intel based version but, it's nothing compared to the RISC based stuff.

At my last corporate job, I had a production domain on a SUN E15K for my production Oracle instance.  We had 24 CPU's, 48 Cores, 75 gigabytes of RAM (just in my domain, that's not the total for the box) and 15 Terrabytes of space attached via a EMC SAN.  That box was screaming fast!  But, what else would you expect for a computer that cost 1.2 million dollars (minus the storage)

That box, by the way, could support 18 separate domains on it at one time.  It was pretty amazing.

---

### Post by jinx099 on 2008-04-05
Wow,  a lot of Solaris haters around here.  I guess that's not surprising.

Solaris is a great OS for servers.  I am using Solaris on my personal server.  Gotta love ZFS!

---

### Post by D-EJ915 on 2008-04-06
> **mr.farenheit said:**
> basic unix. don't bother though, too over complicated for nothing.
it's no more complicated than any other Unix os

> **ch_123 said:**
> Its also bloody slow... Unless they make some massive improvements to it, I think Linux is a better Desktop OS by far. Now, for Server and special applications, it may or may not be better. Depends on what you use your PC for.some nice FUD here, lol, Solaris is quite fast, especially SXCE

Biggest issue I have with Solaris is no virtual consoles.

---

### Post by laxmanb on 2008-04-06
Yeah... speed is pretty good. It feels slow if your disk controller is not fully supported (on some older systems)

---

### Post by angry_johnnie on 2008-04-17
You know, if you just want to see what it's like, you could try [Belenix]("http://www.genunix.org/distributions/belenix_site/"), which is a Solaris live CD.  It comes with both KDE and XFCE and is actually pretty good.

Edit:  if you eventually feel bold enough to install it, just make sure you don't put it in a logical partition.  Ask a lot of questions, and backup your data.

---

