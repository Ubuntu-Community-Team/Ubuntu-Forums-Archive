---
title: "Project Indiana"
date: 2007-11-04
forum: Other OS Talk
---

### Post by jinx099 on 2007-11-04
I'm surprised this hasn't been mentioned yet.

The first preview of Sun's Project Indiana is available to download and try out.  Has anyone else tried it out yet?

I installed it and played with it for a very short time.  It is based on OpenSolaris build 75 and has gnome 2.20, ZFS for root filesystem, and a package management system.  The CD is a liveCD that you can install to the HD as well, like Ubuntu's desktop CDs.

[http://www.opensolaris.org/os/project/indiana/](http://www.opensolaris.org/os/project/indiana/)

What are your thoughts on it?

---

### Post by Antman on 2007-11-04
> **jinx099 said:**
> I'm surprised this hasn't been mentioned yet.

The first preview of Sun's Project Indiana is available to download and try out.  Has anyone else tried it out yet?

I installed it and played with it for a very short time.  It is based on OpenSolaris build 75 and has gnome 2.20, ZFS for root filesystem, and a package management system.  The CD is a liveCD that you can install to the HD as well, like Ubuntu's desktop CDs.

[http://www.opensolaris.org/os/project/indiana/](http://www.opensolaris.org/os/project/indiana/)

What are your thoughts on it?

I saw it on the site but was hesitant to play with it. I'm wondering how they have come along as a desktop OS?!?

---

### Post by jinx099 on 2007-11-06
Wow, I really thought more people would care about this release!

---

### Post by scorp123 on 2007-11-06
> **jinx099 said:**
>  What are your thoughts on it? Well, finally a good step in the right direction. Having to mess around with the current Solaris packet system is such a pain ... It's about time they added some "apt" like features to their "pkg*" programs.

---

### Post by scorp123 on 2007-11-06
> **jinx099 said:**
> Wow, I really thought more people would care about this release! Well .... this here isn't exactly a forum where the typical Solaris user (= system admins!) would hang around. And those of us who do probably don't think it's so exciting that they would start a lengthy discussion about Solaris on a Linux forum. In the end it's just another UNIX release ... :)

---

### Post by igknighted on 2007-11-06
> **jinx099 said:**
> Wow, I really thought more people would care about this release!

I'm excited, I just haven't had time to try it yet with school and work.  Unfortunately it may be a few weeks yet.  But Solaris has always been my secret OS crush, so I will try it as soon as possible.

---

### Post by VCSkier on 2007-11-06
What advantages/disadvantages/differences does Solaris have when compared to Linux?  It's a completely different unix based kernel, right?

---

### Post by jinx099 on 2007-11-06
> **VCSkier said:**
> What advantages/disadvantages/differences does Solaris have when compared to Linux?  It's a completely different unix based kernel, right?
Yep, totally different kernels.  Solaris is UNIX derived where Linux is a UNIX clone.

Solaris advantages are ZFS, Zones, Dtrace, and other technical things.
Linux's main advantage is hardware support.

---

### Post by VCSkier on 2007-11-06
Do Solaris' advantages equate to a significant difference for the end user?  Being a rather typical end user, technical differences generally prove irrelevant to me unless they result in a performance difference, or something like that.  Basically, why would a GNU/Linux user want to switch?

---

### Post by scorp123 on 2007-11-06
> **VCSkier said:**
>  Do Solaris' advantages equate to a significant difference for the end user?  Solaris up and until now was never really intended for the "end user". Solaris if anything is a server OS and a very stable one at that. It's only recently that Sun Microsystems has discovered that if they made Solaris a little bit more "Linux-like" that their OS might appeal to the same people who use Linux too. It's all about market share :)

> **VCSkier said:**
>  Basically, why would a GNU/Linux user want to switch?  Excellent question :lolflag:

Seriously: If you have that shiny expensive SUN hardware in your server room and you really need those Solaris features (e.g. because your apps such as Oracle demand that) then by all means use Solaris..... Solaris 10 for example is an excellent server OS. A bit tricky though, but otherwise a real nice UNIX. I like it far better than e.g. HP-UX which I had to use in the past seven years while working for HP. :lolflag:

But if you don't need those Solaris-specific features ... well, Ubuntu Server (for AMD64) just happens to run very very well on the AMD64 based machines; and it works tip top on SUN hardware too. And I really really like the possibilities I have with "apt" and "aptitude"; that's a feature that is completely missing with commercial UNIXes ... so if those Solaris-specific features are not really that important, then by all means use Ubuntu Server. It really does it's job very very well.

And as end-user ... trust me, you don't want Solaris. Not yet. Just to mention that e.g. the Solaris installer by default doesn't take any prisoners and will automagically completely wipe the first harddisk it finds in your system. And it's really fast at that :)  ... Your harddisk is gone before you can utter "What the .... ?" :)

I wouldn't want that on my desktop system. And hardware support is rather limited at the moment. So for an end-user Solaris doesn't really offer much at the moment. I am not saying it's a "bad" OS .... but end-users simply aren't the typical target audience for Solaris. Not yet at least .... Linux is sooooo much nicer and easier to use. :)

---

### Post by tubasoldier on 2007-11-06
i've been watching Solaris since they open sourced it a few years ago. As far as desktop use is concerned they have a long way to go. As far as server use is concerned, a great option. Of course that is my opinion. 

The Solaris kernel still does not have the hardware compatibility that Linux does. Which makes it much harder to get your ethernet/video/wireless card working. Wireless is very far behind.

I am exited about what Sun is doing with it. Hopefully it gains momentum. I think competition is good. Especially something like Solaris and Linux. It is a different kind of competition. Unlike windows we are closer to comparing apples to apples.

So good luck Solairs. I'll give you a look in five years.

---

### Post by D-EJ915 on 2007-11-06
I booted the liveCD on my laptop, surprisingly it detected the 1280x768 resolution right off the bat.  Wireless worked fine.  2 things that didn't work: scrolling on the touchpad and the brightness control for the LCD.  But considering that it's a developer release and not oriented at laptops that's pretty good imo.

I ran solaris express community edition on my desktop in the first half of this year and it was more compatable with my hardware than windows was, windows would refuse to use my wireless card but opensolaris worked great with it.  Weird how that works out.

For me, personally, I can make any OS do kinda what I want it to (at least any *Nix, for sure) so it doesn't matter what OS I use, as long as I have a C compiler I'm good to go.

---

### Post by jinx099 on 2007-11-07
Yeah, I'm mostly interested in Solaris and Indiana for my server with ZFS, Zones, and BrandZ.  BrandZ is a virtualization app and you can run certain Linux kernels too (last time I checked you were limited to an old 2.4 kernel and CentOS 3).

Good stuff.  I hope Indiana makes for a more user friendly and more desktop oriented OS while keeping its server reliability.

---

### Post by rliegh on 2007-11-08
I'm putting my toes back in the Linux waters after having been consistently scalded by most of the 2.6 kernels. For the most part I stick to either (net)BSD or OpenSolaris for my *nix fix (and to Windows XP when I just flat-out *don't wanna think about it*. :twisted: )

Solaris provides stability, and if you have a device driver that compiles now, it will compile in the future. That's *guarenteed*. 

I tried installing vmware workstation on the 2.6 kernel that ships with Slackware 12. No dice -won't compile because it's *too new* of a 2.6 version and too much has changed. Ditto for the blob I require to run my Intel software modem. It compiles just fine on older 2.6 kernels, not on newer ones. 

With Solaris, you wouldn't have that situation. *_Period_*. It would work, or it wouldn't. As an end-user, that makes life *much more pleasent*.

This probably isn't true of Indiana, but as far as desktop-ness goes, Solaris Express ships with real player, a tweaked version of gnome, native support for playing mp3 files, realplayer 10 and macromedia flash are included out of the box as are native NVidia drivers which are *automatically installed* (cavaet -still d/l'ing Ubuntu so I don't know if you guys do that now -you didn't back in 2005), also included is a gratis copy of Star Office (which includes a few bits and pieces that aren't included in OpenOffice.org).

Downside? *Slooooowwwwww*, IMHO as a desktop it's second only to Vista in how 'draggy' it feels, even on a current Athlon 64 FX. Sound *can* be wonky to set up, sometimes you do have to hunt down drivers (that may be changing with OSS becoming Open Source and supported on Solaris) and there's a more limited amount of software for Solaris, much of which is community-ported from the good folks over at Blastwave. Some things work weird, such as Wine and Qemu drags much more so than it does on Linux.

So, those are the pros and cons IMHO of running Solaris as an end-user. If you're just web surfing and mucking about with videos, mp3s and youtube and whatnot what Solaris would have to offer you is an esthetically pleasing version of Gnome running on top of a kernel which is probably twenty times more stable than Linux is.

It's free: [http://get.opensolaris.org](http://get.opensolaris.org) -I think you can even get vmware images to load into vmware player if you don't want to take the plunge (but I don't know the URL offhand), and it's definately worth checking out! :guitar:

---

### Post by kazuya on 2007-11-08
I shall be trying this out today. I got the livecd this morning. It is very tempting. And i am curious to learn some new things on it. Ishall test it as a desktop OS not server...

Wish me luck. I would report when done.

---

### Post by igknighted on 2007-11-08
> **rliegh said:**
> I'm putting my toes back in the Linux waters after having been consistently scalded by most of the 2.6 kernels. For the most part I stick to either (net)BSD or OpenSolaris for my *nix fix (and to Windows XP when I just flat-out *don't wanna think about it*. :twisted: )

Solaris provides stability, and if you have a device driver that compiles now, it will compile in the future. That's *guarenteed*. 

I tried installing vmware workstation on the 2.6 kernel that ships with Slackware 12. No dice -won't compile because it's *too new* of a 2.6 version and too much has changed. Ditto for the blob I require to run my Intel software modem. It compiles just fine on older 2.6 kernels, not on newer ones. 

With Solaris, you wouldn't have that situation. *_Period_*. It would work, or it wouldn't. As an end-user, that makes life *much more pleasent*.

This probably isn't true of Indiana, but as far as desktop-ness goes, Solaris Express ships with real player, a tweaked version of gnome, native support for playing mp3 files, realplayer 10 and macromedia flash are included out of the box as are native NVidia drivers which are *automatically installed* (cavaet -still d/l'ing Ubuntu so I don't know if you guys do that now -you didn't back in 2005), also included is a gratis copy of Star Office (which includes a few bits and pieces that aren't included in OpenOffice.org).

Downside? *Slooooowwwwww*, IMHO as a desktop it's second only to Vista in how 'draggy' it feels, even on a current Athlon 64 FX. Sound *can* be wonky to set up, sometimes you do have to hunt down drivers (that may be changing with OSS becoming Open Source and supported on Solaris) and there's a more limited amount of software for Solaris, much of which is community-ported from the good folks over at Blastwave. Some things work weird, such as Wine and Qemu drags much more so than it does on Linux.

So, those are the pros and cons IMHO of running Solaris as an end-user. If you're just web surfing and mucking about with videos, mp3s and youtube and whatnot what Solaris would have to offer you is an esthetically pleasing version of Gnome running on top of a kernel which is probably twenty times more stable than Linux is.

It's free: [http://get.opensolaris.org](http://get.opensolaris.org) -I think you can even get vmware images to load into vmware player if you don't want to take the plunge (but I don't know the URL offhand), and it's definately worth checking out! :guitar:

Good post.  Linux has long been about new features, sometimes at the expense of stability.  Just ask any BSD user, and one would guess solaris as well.

I think for those who like to tinker and play with the latest and greatest, Linux is the way to go.  But long term, if any *nix will become exceedingly popular, it will be a BSD or Solaris distro, because of the stability in the kernel over the long haul.

---

### Post by kazuya on 2007-11-08
> **igknighted said:**
> Good post.  Linux has long been about new features, sometimes at the expense of stability.  Just ask any BSD user, and one would guess solaris as well.

I think for those who like to tinker and play with the latest and greatest, Linux is the way to go.  But long term, if any *nix will become exceedingly popular, it will be a BSD or Solaris distro, because of the stability in the kernel over the long haul.

I'm sorry, but I beg to differ. Look at companies like novell with Suse,., More especially, look at Ubuntu. The BSDs and Solaris are catching up in terms of ease of use for desktop OSes; But most of the linux distros blow by these guys in volumes in terms of acceptance and prevailance.

Take a look at the distro Indiana for example. It is based on Solaris. It runs fine, uses gnome as default DE.. On the surface, it looks and behaves like another distro; Stability-wise, I do not see any difference. Infact, the developers there coment about there being a need for better network package equivalent {like in Debian apt-get}. I referenced this from the release page.

[http://distrowatch.com/table.php?distribution=indiana](http://distrowatch.com/table.php?distribution=indiana)
Indiana is a binary distribution of an operating system built out of the OpenSolaris source code. The distribution is a point of integration for several current projects on OpenSolaris.org, including those to make the installation experience easier, to modernise the look and feel of OpenSolaris on the desktop, [COLOR="Red"]and to introduce a network-based package management system into Solaris[/COLOR]. The resulting distribution is a live CD install image, and is fully permissible to be redistributed by anyone.

---

### Post by igknighted on 2007-11-08
> **kazuya said:**
> I'm sorry, but I beg to differ. Look at companies like novell with Suse,., More especially, look at Ubuntu. The BSDs and Solaris are catching up in terms of ease of use for desktop OSes; But most of the linux distros blow by these guys in volumes in terms of acceptance and prevailance.

Take a look at the distro Indiana for example. It is based on Solaris. It runs fine, uses gnome as default DE.. On the surface, it looks and behaves like another distro; Stability-wise, I do not see any difference. Infact, the developers there coment about there being a need for better network package equivalent {like in Debian apt-get}. I referenced this from the release page.

[http://distrowatch.com/table.php?distribution=indiana](http://distrowatch.com/table.php?distribution=indiana)
Indiana is a binary distribution of an operating system built out of the OpenSolaris source code. The distribution is a point of integration for several current projects on OpenSolaris.org, including those to make the installation experience easier, to modernise the look and feel of OpenSolaris on the desktop, [COLOR="Red"]and to introduce a network-based package management system into Solaris[/COLOR]. The resulting distribution is a live CD install image, and is fully permissible to be redistributed by anyone.

Linux is on top right now because in the past the licensing was more favorable for developers.  Sun's Solaris wasn't that popular because it was closed source and you had to pay for it.  BSD isn't as popular because its license isn't as favorable to the developers, as anyone can steal/improve their code without contributing back (this is still the case).

Both BSD and Solaris, therefor, are behind right now in terms of drivers for hardware, userbase, desktop applications, etc.  But with Solaris becoming open-source, you have an opportunity to see that shift.  My argument is that Solaris is a better platform for a _mainstream_ distribution to build on, because of long-term stability in the kernel.

The linux kernel developers are amazing, but they push out new technology all the time that causes breakages with old hardware.  Look at the struggles with the ATI drivers and new kernels.  With a kernel model like BSD or Solaris, there wouldn't be issues like this.  This allows for companies to release proprietary software that interact with the kernel and know that it will work.  I know this is not necessarily popular, but Adobe will never open-source photoshop or other popular apps that people want.  AMD and Nvidia can never truly open-source their drivers due to issues with not owning all the code themselves.  These are serious issues for widespread adoption.  And they are able to be addressed with a kernel like Solaris or BSD that focuses on stable APIs rather than the latest and greatest.

This is not an indictment of linux.  Personally, I prefer the latest and greatest.  But for those who don't, which I feel is a large percentage of users, these other kernels may be a better choice from which to build an OS.  I don't mind being a new software lab rat running the cutting edge kernel, and then having the things that work best be ported back when a stable kernel does an upgrade.

Of course, it is possible to freeze the kernel version in linux.  Look at RHEL, SLED and Ubuntu's LTS.  But is that the answer?  I don't think so.  In linux, running the old kernel means old drivers and often old applications.  With Solaris and BSD (now I am no expert here, but this is my understanding) you could upgrade the kernel without these breakages.  This is why I believe it would a better solution.

sidenote: I am not an expert in kernel design and am talking based on how I understand things as an observer.  I don't consider myself completely ignorant on the subject, but if I am wrong in places (very possible) please do correct me.

---

### Post by scorp123 on 2007-11-08
> **igknighted said:**
>  With Solaris and BSD (now I am no expert here, but this is my understanding) you could upgrade the kernel without these breakages.  True. If a driver worked for Solaris 7 it will still work for Solaris 9, most likely even Solaris 10. You can't do that with Linux where changing the kernel means breaking all your drivers.

---

### Post by kazuya on 2007-11-09
great points guys. I stand corrected then. I never thought about that. For me though, right now, Linux is way ahead, but I can see your reasoning now in regards to the kernel and driver compatibilities.

I cannot mount or see my other drive partitions with Indiana like I could with Mint or ubuntu..
Maybe, I just do not know where to look?

---

### Post by igknighted on 2007-11-09
> **kazuya said:**
> great points guys. I stand corrected then. I never thought about that. For me though, right now, Linux is way ahead, but I can see your reasoning now in regards to the kernel and driver compatibilities.

I cannot mount or see my other drive partitions with Indiana like I could with Mint or ubuntu..
Maybe, I just do not know where to look?

Hmm, does solaris even read/write to ext3?  It's been a while since I've used it, but I seem to recall not being able to mount ext3 drives.

Your best bet would be to try and mount it by its block address (this, being solaris, is not /dev/sda# or /dev/hda#... but I sadly forget how they name drives) using the mount command (mkdir ~/folder && mount /block/device ~/folder)

---

### Post by Genican1 on 2007-11-09
well, i was thinking about installing it.  I tried it live and it was quite nice.  my FAT USB drive mounts nicely, gnome is nice, etc...

one big deal:  my network card isn't supported.  I found a driver for it, but I can't find a C compiler. no gcc, no cc, no suncc...  any help?  I thought this was a DEVELOPER release.  Who's going to develop on something with no compiler?  Or did they mean the OpenSolaris developers want to show off what they've done?

---

### Post by rliegh on 2007-11-09
> **Genican1 said:**
> ... I can't find a C compiler. no gcc, no cc, no suncc...  any help? 

Check for /usr/sfw/bin and /usr/ccs/bin, then add both to your PATH. suncc would live in /opt/SUNWspro/bin if it existed on your system (I'm doubting it does, since sunstudio 12 creates symlinks in /usr/bin -if it were installed you would know it).

---

### Post by scorp123 on 2007-11-09
> **igknighted said:**
>  Your best bet would be to try and mount it by its block address (this, being solaris, is not /dev/sda# or /dev/hda#... but I sadly forget how they name drives)  On Solaris disks are named like **/dev/dsk/c0t1d2s3** .... Where "c" stands for "controller", so "c0" is the first disk controller (e.g. your first IDE or SCSI or SATA adapter). The "t" stands for "target" ... that would be the "LUN" in SCSI-terminology as there could be multiple devices connected to the same controller (especially when SCSI is used). The "d" stands for "disk" ... that's a pretty much obvious one. And "s" stands for "slice" ... that's how Solaris calls disk partitions. So in my example that would be:
- the 4th partition (count starts at 0)
- on the 3rd disk
- on SCSI device target with the LUN=1
- on the first disk controller

Piece of advice .... Never ever do any manipulations on [COLOR="Red"]**slice 2**[/COLOR] (e.g. [COLOR="Red"]/dev/dsk/c0t0d0s2[/COLOR] .... **Don't touch this!!**) .... On Solaris the "s2" partition *always* goes from the very first disk sector to the very last disk sector. And yes, it does overlap with anything else that lives on the disk. The "s2" slice encompasses all the other slices on the disk. So you never ever touch "s2" on a Solaris installation.

Some detailed info on Solaris slices can be found here:
[http://multiboot.solaris-x86.org/iv/3.html](http://multiboot.solaris-x86.org/iv/3.html)

---

