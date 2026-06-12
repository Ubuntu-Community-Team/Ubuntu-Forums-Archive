---
title: "i dont know what OS to use?"
date: 2007-03-29
forum: Other OS Talk
---

### Post by da1nonlymikeo on 2007-03-29
i want to try another linux distro other than ubuntu. i looked at gentoo and suse, but they take like 4 cd's to install?

 whats a distro thats somewhat easy to install? and requires maybe just one or two disks

---

### Post by justin whitaker on 2007-03-29
> **da1nonlymikeo said:**
> i want to try another linux distro other than ubuntu. i looked at gentoo and suse, but they take like 4 cd's to install?

 whats a distro thats somewhat easy to install? and requires maybe just one or two disks

Well, have a look at the best/worst distros to install threads....lots of good info in there.

Then just figure out what interests you.

Actually, Gentoo is 1 CD, just for different architectures. SUSE is available as 1 DVD, if the CDs seem too much. Fedora and Mandriva also come in DVD editions.

Personally, I would check out:
PCLinuxOS
Vector
Gobolinux
Sabayon

All have an interesting take on Linux worth looking at.

---

### Post by steven8 on 2007-03-30
LiveCD's are the way to find out.  Here is a link to a great list:

[http://www.livecdlist.com/]("http://www.livecdlist.com/")

---

### Post by igknighted on 2007-03-30
> **steven8 said:**
> LiveCD's are the way to find out.  Here is a link to a great list:

[http://www.livecdlist.com/]("http://www.livecdlist.com/")

The above list is not complete by any means.  Fedora offers a liveCD as well, for example (in fact they offer a KDE liveCD as well as a gnome liveCD with their latest test3 of Fedora 7).

You should really be more specific with what you are looking for this new OS to do.  Do you want bleeding edge?  Do you want blazing speed?  Features?  Stability?  There are so many linux OSs out there we can't really recommend one until we know more about what you want.

---

### Post by jdhore on 2007-03-30
I would also like to throw Debian into the ring...you can do a netinstall with Debian plus you learn A LOT more than you do with Ubuntu, but you still have a lot of nice features like apt-get, nano, etc

---

### Post by Nils Olav on 2007-03-30
> **jdhore said:**
> I would also like to throw Debian into the ring...you can do a netinstall with Debian plus you learn A LOT more than you do with Ubuntu, but you still have a lot of nice features like apt-get, nano, etc

... or you could put your time to better use and just read stuff.

---

### Post by aysiu on 2007-03-30
This might help you pick things:
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

### Post by tommcd on 2007-03-31
Try zenwalk. [http://zenwalk.org/](http://zenwalk.org/) It's only a 400mb download, and comes with all multimedia codecs installed. It is light, fast and up to date (2.6.20 kernel, xorg 7.2, all apps up to date as well). The only downside is that their repositories have a limited amount of software. Their philosophy is "one tool per task". But the tools they have all work well and are up to date.
If you install it and want to dual boot with ubuntu, don't install lilo (yes, zen uses lilo, because it is based on slackware and slackware uses lilo). Just update or reinstall grub to detect zenwalk. Grub makes life easier than lilo imo.

---

### Post by danddi on 2007-03-31
Hey tommcd,  You said to update or reinstall grub.  Could you say how to reinstall grub please. I am a relatively new linux user. I just bought vista on a gateway laptop. I installed Ubuntu after resizing with the windows resizer.  Everything worked fine.  I used the remainder of my unallocated space to install SAM Linux. I now cannot boot Ubuntu. Vista and SAM work fine.  Ubuntu is still there I just can't access it. I don't know how to put Ubuntu back in the boot loader or is it the MBR?  I hope reinstalling grub will work and it seems like it should be easy. Thanks in advance.

---

### Post by hanzomon4 on 2007-03-31
Why use a linux? I've been trying pc-bsd and it's amazing. It has a kde desktop and uses .pbi(binaries) and the ports tree(source install) to find, install, uninstall software. It's more obscured then linux and doesn't use the linux kernel(obviously). It's based off of Freebsd.

For a linux I've heard that foresight was good but I've never tried it(wouldn't install to my usb drive). You could also try Nexenta, an opensolaris with a ubuntu/gnu userland(?). I'd wait for Nexenta alpha 7 because it should then allow you to use zfs as your root filesystem.

---

### Post by SOULRiDER on 2007-03-31
Ive tried installing gentoo from source several times and failed miserably....

I think im gonna stick to kubuntu for a while :D

---

### Post by handy on 2007-03-31
[PC-BSD is fun.]("http://www.pcbsd.org/")

[http://people.freebsd.org/~murray/bsd_flier.html](http://people.freebsd.org/~murray/bsd_flier.html)

[http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

Some good info' in those links too...

---

### Post by tommcd on 2007-03-31
> **hanzomon4 said:**
> Why use a linux? I've been trying pc-bsd and it's amazing. It has a kde desktop and uses .pbi(binaries) and the ports tree(source install) to find, install, uninstall software. It's more obscured then linux and doesn't use the linux kernel(obviously). It's based off of Freebsd.

For a linux I've heard that foresight was good but I've never tried it(wouldn't install to my usb drive). You could also try Nexenta, an opensolaris with a ubuntu/gnu userland(?). I'd wait for Nexenta alpha 7 because it should then allow you to use zfs as your root filesystem.

I was just looking at PC-BSD last night. Is it easy to install and use? How about hardware detection? The documentation on their wiki looks pretty good.

---

### Post by tommcd on 2007-03-31
> **danddi said:**
> Hey tommcd,  You said to update or reinstall grub.  Could you say how to reinstall grub please. I am a relatively new linux user. I just bought vista on a gateway laptop. I installed Ubuntu after resizing with the windows resizer.  Everything worked fine.  I used the remainder of my unallocated space to install SAM Linux. I now cannot boot Ubuntu. Vista and SAM work fine.  Ubuntu is still there I just can't access it. I don't know how to put Ubuntu back in the boot loader or is it the MBR?  I hope reinstalling grub will work and it seems like it should be easy. Thanks in advance.

What bootloader does SAM use? Did you install grub or lilo when you installed SAM? And if so did you install them to the MBR or the root directory of SAM?
Anyway, to reinstall grub from the ubuntu live CD follow this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
or from the ubuntu alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
Hope this helps.

---

### Post by RAV TUX on 2007-04-01
> **da1nonlymikeo said:**
> i want to try another linux distro other than ubuntu. i looked at gentoo and suse, but they take like 4 cd's to install?

 whats a distro thats somewhat easy to install? and requires maybe just one or two disks

**[[B]Foresight** Linux]("http://www.foresightlinux.com/")[/B]



(it is my primary OS)

---

### Post by karellen on 2007-04-01
try these:
pclinux os
mepis
vector linux

---

### Post by handy on 2007-04-01
> **tommcd said:**
> I was just looking at PC-BSD last night. Is it easy to install and use? How about hardware detection? The documentation on their wiki looks pretty good.

There are known issues with the Asus A7N266-VM motherboard.  As a general rule because of the BSD license, firmware is more likely supported, nVidia support BSD also.

My install was quicker & easier than any Ubuntu install, but that doesn't mean a huge amount because of the number of possible hardware combinations.

The [***_PC-BSD Forum_***]("http://forums.pcbsd.org/") is helpful too.

Also, the [***_FreeBSD Handbook_***]("http://www.pl.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html") is excellent.

---

### Post by darksong on 2007-04-01
PCBSD does look nice. The way the guy/gal in the flash demo installed a programme was rather impressive - whats it like finding those type of files though?

---

### Post by stokedfish on 2007-04-01
PCLinuxOS, Mandriva, OpenSUSE, Arch, Gentoo, Sabayon and like 500+ others:

[http://distrowatch.com/](http://distrowatch.com/)

Nobody can tell you what to use, make up your own mind man.

---

### Post by darksong on 2007-04-01
I am currrently using PCLinuxOS 2007 version and i am very impressed - it has very good config tools, snaptic package manager and all of that stuff. Some of the little details aswell such as when you scroll over your music in your file browser you get a nice little preview of the song - all adds up to make it seem that much more speacial.

---

### Post by RAV TUX on 2007-04-01
> **da1nonlymikeo said:**
> i want to try another linux distro other than ubuntu. i looked at gentoo and suse, but they take like 4 cd's to install?

 whats a distro thats somewhat easy to install? and requires maybe just one or two disksAfter testing and user over 300 distros, I found that none where quite right, So I built my own....I highly reccommend it to you, I call it [COLOR=Purple]**Oz**[/COLOR]:

[see some **Oz** screenshots here]("http://www.ubuntuforums.org/showthread.php?t=398478")

[download **Oz** here]("http://www.rpath.org/rbuilder/project/oz/")

Post [COLOR=Purple]**Oz**[/COLOR] questions [here.]("http://cafelinux.org/forum/index.php/board,35.0.html")

---

### Post by danddi on 2007-04-01
> **tommcd said:**
> What bootloader does SAM use? Did you install grub or lilo when you installed SAM? And if so did you install them to the MBR or the root directory of SAM?
Anyway, to reinstall grub from the ubuntu live CD follow this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
or from the ubuntu alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
Hope this helps.

Thanks for the info.  I reinstalled SAM first and then Ubuntu, it only took a couple of hours.  Ubuntu saw the windows and SAM partitions with no problem and I am now able to access all OS's.  I plan on bookmarking these pages and getting back to them later when I have time.  Thank you again for the info!

---

### Post by handy on 2007-04-01
> **darksong said:**
> PCBSD does look nice. The way the guy/gal in the flash demo installed a programme was rather impressive - whats it like finding those type of files though?

[Here is where the .pbi's are found]("http://www.pbidir.com/"), there are more being made all the time.

---

### Post by tommcd on 2007-04-01
Thanks for the info Handy.
Quick question:  I have a multiboot system with a /data directory that I use to store my personal files, music, pictures, etc. It is formatted in ext3. Will PC-BSD recognize this and be able to mount it, as well as read and write to it the same as a linux distro would?

---

### Post by handy on 2007-04-02
> **tommcd said:**
> Thanks for the info Handy.
Quick question:  I have a multiboot system with a /data directory that I use to store my personal files, music, pictures, etc. It is formatted in ext3. Will PC-BSD recognize this and be able to mount it, as well as read and write to it the same as a linux distro would?

Yes PC-BSD can read / write to ext file systems, it calls ext3, ext2, but it matters not a jot!

---

### Post by tommcd on 2007-04-03
Cool, thanks again Handy.

---

### Post by darksong on 2007-04-03
What is PCBSD Like on config tools? I am running PCLinuxOS 2007 atm and it is brilliant, very good config tools, snaptic ect.

---

