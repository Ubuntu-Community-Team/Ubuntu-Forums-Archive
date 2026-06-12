---
title: "My Slowest, Crappiest Computer Running Linux"
date: 2008-07-27
forum: Other OS Talk
---

### Post by Bungo Pony on 2008-07-27
Here's what I have Damn Small Linux running on:

A 486 DX/2 Compaq Laptop
16M RAM
128M Hard Drive
No CD-ROM drive

It takes nearly five minutes to boot (4:51 from power-on) and it's barely useable. Dillo doesn't even bother to load at boot (which might actually be a good thing :) )

If you wanna know how I did it:

1) I installed DSL onto the hard drive using a BETTER laptop with a CD-ROM drive. Swapping it into another computer is fine since DSL looks for devices everytime it boots.

2) DSL requires 200M of hard drive space to install. I initially tried installing Slitaz on this thing (which requires 120M of space), but it didn't even boot. During the install of DSL after it prompted me to choose the boot loader, I mounted the HD and deleted some 'bloat' (Firefox, games, etc) and there was enough drive space for it to install Lilo.

3) I installed the hard drive into the 486 and let it boot. 

I now have a completely useless computer with an OS that barely functions!

---

### Post by steveneddy on 2008-07-27
Sweet! My old 486 answers my phone and takes faxes. Still runs windows 95.

---

### Post by K.Mandla on 2008-07-27
> **Bungo Pony said:**
> I now have a completely useless computer with an OS that barely functions!
I am so totally jealous right now. :mrgreen: No really: I would love to get my hands on something like that. :twisted:

---

### Post by kerry_s on 2008-07-27
i would try a text based system, maybe debian base with links2 for web browsing.

---

### Post by Sef on 2008-07-27
16 mb ram is too little for DSL.  Check out [DeliLinux]("http://www.delilinux.org/").  It would be have to be installed with no GUI.

---

### Post by molom on 2008-07-27
Can I buy it? How much? ;)

And I think Windows Vista can run on that thing quite smoothly, (60% of the time it works all the time). :lolflag:

---

### Post by Bungo Pony on 2008-07-27
Maybe I could sell it as a prototype to Microsoft for their Open Source line :D

---

### Post by K.Mandla on 2008-07-27
What's the model number of that laptop, anyway?

---

### Post by Bungo Pony on 2008-07-27
> **K.Mandla said:**
> What's the model number of that laptop, anyway?

It's a LTE Elite 4/50CX

---

### Post by Midwest-Linux on 2008-07-27
Good post, enjoy reading stuff like this. I have a Gateway Nomad 425/DX 25 that originally ran Windows 3.11. Which might be a good candidate for this, right now it boots up to bios and thats it.

---

### Post by insane_alien on 2008-07-27
you could try some of the floppy based distributions. i believe there is even one with X on it.

---

### Post by tdrusk on 2008-07-27
DeLi is the answer.

---

### Post by MONODA on 2008-07-28
you should try CRUX :D it takes a bit of knowledge and time to set up but then you will actually have a functioning system.

---

### Post by darrelljon on 2008-07-28
Try the Linux distros under 50Mb [here]("http://ubuntuforums.org/showthread.php?t=575456").

---

### Post by K.Mandla on 2008-07-28
> **MONODA said:**
> you should try CRUX :D it takes a bit of knowledge and time to set up but then you will actually have a functioning system.
It would be interesting to see if Crux helped that at all. Getting it on there would be a trick, and keeping the system within that hard drive space while compiling would be a small feat too. What fun!

---

### Post by chris4585 on 2008-07-29
just amazing... I'd love to have that just to play with,

---

### Post by Midwest-Linux on 2008-07-29
Ok tried the server method, installing Ubuntu as a server and then adding components. It hung up on the language pack. (One site suggested installing it as a server and then add the desktop from there).

 Back to DSL, last time I tried installing it through the Boot options, DSL could not find the hard drive. So thats why I tried the minimal install Ubuntu iso and followed the methods suggested in the links.

 So I'm back to DSL, I didn't use the F2 or F3 boot options. I let it run completely through and now I have DSL on my desktop. Looks nice, except there is one problem...the PS2 mouse doesn't work, so I tried the USB mouse...it doesn't work either. 

OK... I'll be back with a update....


BTW ... I saw several Omnibook 5700 up for bid on E-bay...one of them was a LOT of five.

---

### Post by mikjp on 2008-07-29
> **MONODA said:**
> you should try CRUX :D it takes a bit of knowledge and time to set up but then you will actually have a functioning system.

Crux does not run on a 486. 

> Packages on the official CRUX ISO image are compiled with optimization for i686 (Pentium-Pro/Celeron/Pentium-II or better) processors. Do not try to install it on an i586 (Pentium, AMD K6/K6-II/K6-III) or lower processor, since it simply will not work. ([http://crux.nu/Main/Handbook2-4#ntoc10](http://crux.nu/Main/Handbook2-4#ntoc10))

I would try NetBSD, Minix or FreeDOS on that hardware.

---

### Post by regomodo on 2008-07-29
try the [net install]("http://www.debian.org/CD/netinst/") of debian. when you get the option, deselect all environment setups ( file-server/workstation, etc)

---

### Post by K.Mandla on 2008-07-30
> **mikjp said:**
> Crux does not run on a 486. 
True, but there are ways around that. Figuring them out would be part of the fun in owning a machine like that.

---

### Post by mikjp on 2008-07-30
Well, I have enough fun in using Slackware on P100 with 40 MB and Debian on iBook 600 MHz & 384 MB. Minix and especially NetBSD would also be at least as fun to use as Crux is ;-)

---

### Post by sstusick on 2008-07-30
Wow, that thing is ancient! 

Hope you're having fun with it, :lolflag:

---

### Post by wannadumpwindows on 2008-07-30
I have an AMD K-62 @ 266 Mhz  with 96Mb and I somehow managed to get Ubuntu on it. IT runs slow as heck and takes forever to boot. But once I pulled the monitor ans stopped X from starting, it makes for a pretty good little server for media files and the like, stuffed in the corner.

I guess I can't even call it a server, I use it more like a network hard drive.

But the install was a serious pain. Took me 5 or 6 tries. But it works pretty well for what I need it for now. It's still running Gutsy. =D

---

### Post by init1 on 2008-07-30
I'd run FreeDOS on it. It'll boot very quickly (faster than 5 minutes anyway :D) and you might be able to do things with it. I doubt that thing has a NIC, but if it does, you might be able to get Arachne working on it. 
[www.freedos.org](www.freedos.org)

---

