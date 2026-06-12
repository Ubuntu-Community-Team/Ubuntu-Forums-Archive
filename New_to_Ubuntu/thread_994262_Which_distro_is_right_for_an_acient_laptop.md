---
title: "Which distro is right for an acient laptop?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by rhcm123 on 2008-11-26
I have a 1998 IBM laptop. Thats right. 1998. And it still runs, that old pentium II. Now, I've been using debian/ubuntu/xubuntu/gentoo (it depends on which computer) distros, and I've loved them all. I prefer ubuntu or debian based os's, but this machine can't even boot minimal gentoo, ubuntu server, etc. I was working on arch, but it dosen't have a direct internet connection, so getting files to and from the internet just wasn't working out.

I would like to put some form of linux on it, but I can't even get one to boot. The only two that have worked are arch and an old distro called deli linux (which is still in beta and unstable).

I think the problem is that i'm using too new distros. I have 2008.0 gentoo, ubuntu 8.10 server, etc. I was thinking somthing like 5.04 ubuntu, etc. 
Can anybody reccomend me a very light distro with  or a old distro that supports this hardware? I don't care about GUI's (my filing server never even had one), but my only request is that it support APT, yum, etc. I hate the puppy linux package system with a passion. :)

---

### Post by NewJack on 2008-11-26
I guess if Xubuntu doesn't work for you, try Damn Small Linux (DSL)?  I believe it is Debian based.

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by Amorget on 2008-11-26
I have Xbuntu running on a Pentium II 450 w/ 768 (or something like that) megs of RAM.  It actually runs well enough that I could browse the web and do normal stuff with a modern OS.

---

### Post by binbash on 2008-11-26
Linux Mint fluxbox edition

---

### Post by ibuclaw on 2008-11-26
I have two possible options.

Firstly, a deriative of Ubuntu. Still in beta. Their aim is to deliver lightweight "power saving" desktops. Called WattOS, I know that their alpha releases used openbox... though I'm not too sure what they use now in their beta release.
[http://www.planetwatt.com/](http://www.planetwatt.com/)

Secondly, this is not Debian based (uses it's own bespoke package manager), but a very light/powerful and up-to-date distro called Slitaz that is so small... DSL looks bloated!
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)


Well worth checking out, you never know what you might like. ;)
Regards
Iain

---

### Post by kerry_s on 2008-11-26
what's the full specs of the machine?
if we don't know the specs we can only guess what distro's might work and send you running around in circles trying to load os's that would never work, because your not even close to the requirements. 

i use a old vaio from 99, 450mhz 256mb ram, running debian lenny custom install.

---

### Post by rhcm123 on 2008-11-26
> **kerry_s said:**
> what's the full specs of the machine?
if we don't know the specs we can only guess what distro's might work and send you running around in circles trying to load os's that would never work, because your not even close to the requirements. 

i use a old vaio from 99, 450mhz 256mb ram, running debian lenny custom install.

It's fun downloading these. I have an old computer i might partition and 10 boot now :). Now, my specs are 233 mhz, about 95 mb of ram and a 10 gb IDE hard drive. It has a cd drive and an external floppy (3 and 1/2 inch, not the awesome 5 inch kind). No known graphics card.

---

### Post by rhcm123 on 2008-11-26
> **kerry_s said:**
> what's the full specs of the machine?
if we don't know the specs we can only guess what distro's might work and send you running around in circles trying to load os's that would never work, because your not even close to the requirements. 

i use a old vaio from 99, 450mhz 256mb ram, running debian lenny custom install.

I think the main problem is that the cd drive is too old for ISOLINUX (the kernel that boots when you load an install cd). I get the ISOLINUX text (ISOLINUX 3.61 (date)) then then nothing. Sometimes error, sometimes not. I think I need a floppy based distro. Any ideas?

---

### Post by brokenreality on 2008-11-26
Puppy Linux would work great on that laptop!

---

### Post by DirtDawg on 2008-11-26
[Puppy Linux]("http://www.puppylinux.org/") is said to be pretty slick and it's designed to be easy on the resources.

---

### Post by Billybob97060 on 2008-11-26
check out this site, you should be able to fit this on 1 or 2 floppy disks if you have the capability :)

---

### Post by halitech on 2008-11-26
if you like Debian based distros, go for Debian itself with XFCE. I have it running on an old Toshiba Tecra (see sig) and it runs fine.

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by rhcm123 on 2008-11-26
> **brokenreality said:**
> Puppy Linux would work great on that laptop!

> **DirtDawg said:**
> [Puppy Linux]("http://www.puppylinux.org/") is said to be pretty slick and it's designed to be easy on the resources.


I hate the puppy linux package manager. With a passion. No, thanks. :) :)

---

### Post by rhcm123 on 2008-11-26
> **halitech said:**
> if you like Debian based distros, go for Debian itself with XFCE. I have it running on an old Toshiba Tecra (see sig) and it runs fine.

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

The problem with that is that this machine has no interwho connection. I mean none. It has a phone jack. And i have a 5 mb down/up fiber conecction.
I need somthing that i can burn to an ISO here then run the installer on teh ibms

---

### Post by halitech on 2008-11-26
+1 on disliking puppy. Its almost like running a stable version of windows with its lack of security. Only good thing is you can take it with you easily on a cd and run it on almost any system

---

### Post by halitech on 2008-11-26
> **rhcm123 said:**
> The problem with that is that this machine has no interwho connection. I mean none. It has a phone jack. And i have a 5 mb down/up fiber conecction.
I need somthing that i can burn to an ISO here then run the installer on teh ibms

there is a cd version you can download that has XFCE preinstalled, might be better suited for you then as long as you have a cd rom

[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso)

---

### Post by ibuclaw on 2008-11-26
> **Billybob97060 said:**
> check out this site, you should be able to fit this on 1 or 2 floppy disks if you have the capability :)

Which site?

Regards
Iain

---

### Post by brokenreality on 2008-11-26
If you don't like the Puppy, Have you try AntiX from the Mepis community.

---

### Post by Billybob97060 on 2008-11-26
wow.. just realized how retarded my earlier post was. here is the website [http://en.wikipedia.org/wiki/BasicLinux](http://en.wikipedia.org/wiki/BasicLinux) sorry about that :)

---

### Post by ibuclaw on 2008-11-26
> **Billybob97060 said:**
> wow.. just realized how retarded my earlier post was. here is the website [http://en.wikipedia.org/wiki/BasicLinux](http://en.wikipedia.org/wiki/BasicLinux) sorry about that :)
Hey, we all are fallible.

This kinda looks like the bare bones to what Slitaz is made of (a distro I mentioned earlier in the thread).

In any case, Thanks mate, I'm gonna try this one out/play around with it.

Regards
Iain

---

### Post by Billybob97060 on 2008-11-26
no problem, silatz would probably do great and be a little more useful than this, i was just recommending something that he could install by floppy, because of the cd drive issue mentioned earlier :)

---

### Post by rhcm123 on 2008-11-26
> **Billybob97060 said:**
> wow.. just realized how retarded my earlier post was. here is the website [http://en.wikipedia.org/wiki/BasicLinux](http://en.wikipedia.org/wiki/BasicLinux) sorry about that :)

i was wondering about that :)
i will look into that tonight, i will be booting windows later tonighty :)

---

### Post by rhcm123 on 2008-11-26
> **halitech said:**
> there is a cd version you can download that has XFCE preinstalled, might be better suited for you then as long as you have a cd rom

[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso)

I really don't need a gui, or if i do i'll apt-get it later (you can do that, i was astounded to learn!), so is their a command line based v of it?

---

### Post by halitech on 2008-11-26
should be able to do a command line server install from the same cd, not that I've tried. I usually go with the net installs and grab everything from online

---

### Post by io5150 on 2008-11-26
I have installed puppy on an old Dell Latitude CPIa (PII-366MHz, 128 RAM) and it seems to run quite well... but I haven't had time to play with it much.

---

### Post by DirtDawg on 2008-11-26
> **rhcm123 said:**
> I hate the puppy linux package manager. With a passion. No, thanks. :) :)

Hmm, that's good to know. Never actually tried it myself.

---

### Post by ibuclaw on 2008-11-26
Almost forget, you could try out the Ubuntu Minimal CDs too and install the packages you wish to have - essentially, build your own Ubuntu/Debian OS environment.

Just enter either of the following directories:
installer-i386/current/images/netboot/
installer-amd64/current/images/netboot/

And grab the 8mb mini.iso image.


Here are the links:

Gutsy: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/)

Hardy: [http://archive.ubuntu.com/ubuntu/dists/hardy/main/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/)

Intrepid: [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/)

There's jaunty there too, if you feel a bit on the wild side ;)

Regards
Iain

---

### Post by rhcm123 on 2008-11-26
> **DirtDawg said:**
> Hmm, that's good to know. Never actually tried it myself.

that's because you have to make your own packages. It dosent even support tarballs (!)

---

### Post by gigaferz on 2008-11-26
puppy!!!!!!!

or windows 2000???

---

### Post by rhcm123 on 2008-11-26
yay! I got a very modified (and i mean very!) version of arch to run on it!
The best part? I got to keep windows, because Windows 98 is one of my favoirite os's. Period. (Sorry, i was born into windows and on windows I shall stay.)

However, this was fun and it works now!!!!!!

---

### Post by sportscrazed2 on 2008-11-26
why not donate it to that laptop for every child charity

---

### Post by rhcm123 on 2008-11-26
> **sportscrazed2 said:**
> why not donate it to that laptop for every child charity

cause it's still useful
don't throw it away if you can still use it
and i can still use it
And plus, i doubt kids in aruba will want to play minsweeper all day. :)

I ALSO GOT UBUNTU 8.04 SERVER ON IT!!! GO ME! GO ME!! I put it on through the modded arch install and it works!!!

---

### Post by mikjp on 2008-11-27
> **rhcm123 said:**
> Can anybody reccomend me a very light distro with  or a old distro that supports this hardware?

What about Slackware?

It is possible that the laptop does not support booting from CD. In that case you need a boot floppy. See my signature for more info.

mikko

---

### Post by EV500B on 2008-11-27
For Debian and xfce, it will be preferable to install it minimally using the Debian+xfce cd.
Then, on the first boot, you should be able to launch aptitude and install all the applications you need; it will be faster compared to the default installation.
If you have time, you can try out NetBSD; it "could be" faster than the first choice.

---

### Post by sbsaxman on 2008-11-27
Puppy Linux is a very easy one to try, and easy to abandon if it doesn't work.  I run it nicely on a Gateway laptop, 300 MHz P-II, 192 MB RAM.  One trick I had to do was start with Puppy 2.17, save the pup_save file, upgrate to 3.01, save the file, then upgrade again to 4.11.  Very snappy, and all the goodies you expect, with no fuss.  Plays wmv's, flash, mp3's, right out of the gate.  

If you want to try Xubuntu: 
1. Use the "Alternate install" (text-based installer)
2. You'll probably want to quickly install ICEWM, FVWM, Fluxbox, or some other lightweight WM.  Xfce just doesn't fit that description if you have a P-II... sorry.  
Might work, but I'm not sure if your RAM will be enough to get you thru.

good luck!

---

### Post by Jesan Fafon on 2008-11-27
I agree to Puppy. I love that distro and it is the Live CD I lend out most often.

I recommend as highly as I possibly can for an older laptop like yours.

---

### Post by rhcm123 on 2008-11-29
> **Jesan Fafon said:**
> I agree to Puppy. I love that distro and it is the Live CD I lend out most often.

I recommend as highly as I possibly can for an older laptop like yours.

I've tried and hated puppy. I have had support issues with it, etc.
Now, i thought i posted this, but because i got arch on it, the system magically started supporting booting from cd's, and i got xubuntu on it. Slow as **** but it works!

---

