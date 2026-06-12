---
title: "Opensolaris is really exciting me!"
date: 2009-01-02
forum: Other OS Talk
---

### Post by Luke has no name on 2009-01-02
Disclosure: I have had very little hands-on experience with it, and I promptly put Ubuntu back on my laptop due to no touchpad driver. 

Opensolaris is looking like the go-to operating system for server environments. Reading some ZFS usage docs, it's the best filesystem available for many reasons: Snapshots, transactions, and the combination of disk manager and filesystem are very appealing.

Of course, Xen is fully supported on Osol, so virtualization is as much of a breeze on Osol as on any other *nix system. 

Crossbow, coming out in SXCE build 105, sounds completely AWESOME. Read about it here: [http://www.cuddletech.com/blog/](http://www.cuddletech.com/blog/) (scroll down a bit). It's basically full network virtualization, which is very very cool. You can literally create a virtual network infrastructure on one machine.

Sun's websites and clarifications on some things could use work, but their user manuals are incredibly useful. The package naming scheme in IPS will be cleaned up in time. I have some exploring to do w.r.t. Sun Studio, Netbeans, and other development related topics, but I'm really liking the prospects of Opensolaris. It will likely be the host of my server, which I just massively upgraded (1.3 TB HD space, 6GB RAM, Antec Nine Hundred case). I'll probably still run Ubuntu Server as a VM and play. Along with IPCop, CentOS, and Windows Server 2008.

---

### Post by LowSky on 2009-01-02
If you want try Nexenta, its a Ubuntu port that uses ZFS and Solaris kernel

---

### Post by Grant A. on 2009-01-02
I loaded it into virtualbox on Windows Vista, I didn't really find anything that was more appealing or different for me than what I can already get on Xubuntu. I think I'll give it some more time to fully mature before I pick it up.

---

### Post by fistfullofroses on 2009-01-02
Besides ZFS, and the network virtualization system, I think that Solaris kernel is far better than the Linux kernel. The only thing I think makes Linux seem better to so many people is that it has been open source far longer than most other kernels. This means it had the opportunity to gain a wider audience and more support. Hence, it has more hardware support (more so than even Windoze).

---

### Post by Sorivenul on 2009-01-02
ZFS is an interesting and important feature of OpenSolaris, however it is not the only one. The latest release is really quite an improvement on 2008.05, and things will only get better. Indeed, OpenSolaris is definitely a system to watch.

However ZFS and OpenSolaris are not the only systems making innovations. DragonFlyBSD (a fork from the FreeBSD 4.x series) has the HAMMER filesystem, which is an interesting departure from ZFS.

Read more about HAMMER here:
[LIST]
[*][http://www.ntecs.de/blog/articles/2008/01/17/zfs-vs-hammerfs/]("http://www.ntecs.de/blog/articles/2008/01/17/zfs-vs-hammerfs/")
[*][http://leaf.dragonflybsd.org/mailarchive/users/2008-01/msg00068.html]("http://leaf.dragonflybsd.org/mailarchive/users/2008-01/msg00068.html")
[/LIST]

---

### Post by creek23 on 2009-01-02
> **LowSky said:**
> If you want try Nexenta, its a Ubuntu port that uses ZFS and Solaris kernel

Will that make Nexenta as the first GNU/Solaris? or is OpenSolaris it the first one? If I'm right, Opensolaris uses GNOME right?

---

### Post by cmay on 2009-01-03
> **creek23 said:**
> Will that make Nexenta as the first GNU/Solaris? or is OpenSolaris it the first one? If I'm right, Opensolaris uses GNOME right?

open-solaris has some ofsprings where as there is belenix and nexenta that is using many of the gnu tools. open-solaris uses gnome but belenix uses both kde and xfce on a livecd that can be installed on usb stick by running the commmand pfexec usbdump it can also be installed to harddisk of course.  it has compiz enabled per default and it has many programs  installed  but i do not know nexenta since the cd i  tried to install worked fine but once the system was installed it started up and at boot i saw a boot screen sayin nexenta and then just a black screen. belenix i use on a usb stick and i been using open-solaris for around 4 or 5 month on my new  computer that serves  as my  office computer.

---

### Post by cardinals_fan on 2009-01-03
> **Luke has no name said:**
> 
Opensolaris is looking like the go-to operating system for server environments. Reading some ZFS usage docs, it's the best filesystem available for many reasons: Snapshots, transactions, and the combination of disk manager and filesystem are very appealing.

I'll second the tip on HAMMER above.

---

### Post by Nxion on 2009-01-05
> **cardinals_fan said:**
> I'll second the tip on HAMMER above.

Agreed. I am defiantly going to check out Nexenta. This look like an amazing project.

---

### Post by cardinals_fan on 2009-01-05
> **Nxion said:**
> Agreed. I am defiantly going to check out Nexenta. This look like an amazing project.
I tried Nexenta.  It didn't amaze me much.  DragonFlyBSD (with the aforementioned HAMMER) is a bit more interesting [to me].

---

### Post by kk0sse54 on 2009-01-05
> **cardinals_fan said:**
> I tried Nexenta.  It didn't amaze me much.  DragonFlyBSD (with the aforementioned HAMMER) is a bit more interesting [to me].

HAMMER is still interesting to me but I've lost any scrap of interest in DragonflyBSD after it just totally refused to boot no matter what cd I used (hardware compatibility problems, understandable) but then after trying the install cd it froze on the boot up and screwed up all my USB devices for my other operating systems installed on my computer (and several kernel compilations later here I am :) finally recovered).

---

### Post by cardinals_fan on 2009-01-05
> **C!oud said:**
> HAMMER is still interesting to me but I've lost any scrap of interest in DragonflyBSD after it just totally refused to boot no matter what cd I used (hardware compatibility problems, understandable) but then after trying the install cd it froze on the boot up and screwed up all my USB devices for my other operating systems installed on my computer (and several kernel compilations later here I am :) finally recovered).
Bizzare.

Fortunately, I never had that problem.  DragonFly's Pkgsrc implementation was kind of screwy, but that was a year ago and they may have improved it by now.

---

