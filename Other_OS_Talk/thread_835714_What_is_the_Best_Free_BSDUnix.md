---
title: "What is the Best Free BSD/Unix?"
date: 2008-06-20
forum: Other OS Talk
---

### Post by acelin on 2008-06-20
I already have Open Solaris, but wanted to try some others. Any suggestions? Please explain why as well!

---

### Post by x1a4 on 2008-06-20
[FreeBSD]("http://www.freebsd.org/") because it integrates well with Xfce, it's stable, secure, fairly easy to use and very well documented.

* FreeBSD 7 can create a large virtual disk image by simply adding physical disks.
* The kernel can be scaled to eight processors.
* Huge software repository.
* 10Gbps network optimization for high performance workloads
* Merged virtual memory and filesystem buffer cache
* TrustedBSD Audit - a security event logging service, providing fine-grained, secure, reliable logging of system events via the audit service.
* GEOM-Based Disk Encryption

---

### Post by acelin on 2008-06-20
It looks like it has the largest user base as well... can you get most open source programs working with it?

---

### Post by jrusso2 on 2008-06-20
Depends on what your using it for.  For a desktop I would think something like PC BSD would be best.

For a server Freebsd or Solaris.

For a Firewall Open BSD.

and for an embedded device NetBSD.

---

### Post by cardinals_fan on 2008-06-20
I LOVE NetBSD.  It's fast, clean, stable, and powerful.  The only dings are that NVIDIA doesn't release NetBSD drivers and that Opera doesn't have a NetBSD version.

FreeBSD is pretty good and supports the above software.

---

### Post by goexplode on 2008-06-20
My experiences with FreeBSD have been nothing but good. I'll have to agree with others that it is fast, clean, and stable. Furthermore, its ports system is extremely easy to use, and allows for a high degree of customization.

---

### Post by Sami_Sdata on 2008-06-20
I used FreeBSD for my desktop machine at home for years.  I recently loaded Ubuntu on that machine but FreeBSD is still running on the firewall machine.  I started running it to learn more about the low level workings of Juniper routers.  They run FreeBSD under their routing software.  Only problem that kept bothering me was how slowly new hardware drivers would appear.

---

### Post by sujoy on 2008-06-21
free bsd seems to be the most popular amongst desktop users

---

### Post by init1 on 2008-06-21
As obscure as it is, I like Debian kFreeBSD. It's Debian but with the FreeBSD kernel instead of Linux. 
[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

---

### Post by cardinals_fan on 2008-06-21
> **init1 said:**
> As obscure as it is, I like Debian kFreeBSD. It's Debian but with the FreeBSD kernel instead of Linux. 
[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)
Does that support all Debian packages that don't specifically require the Linux kernel?

---

### Post by init1 on 2008-06-22
> **cardinals_fan said:**
> Does that support all Debian packages that don't specifically require the Linux kernel?
Most of them I think. I couldn't get X running though. The server started and I could move my mouse but the window manager I installed didn't start, even after some changes to /etc/X11/Xsession. It probably would have worked if I had a better understanding of X. 
All the apps come from "unstable" and "unreleased" repos so they should be relatively new. Last I checked, the newest packages are from February.

---

