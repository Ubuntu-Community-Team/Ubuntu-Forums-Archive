---
title: "Adding runlevels?"
date: 2006-07-23
forum: Programming Talk
---

### Post by LadyDoor on 2006-07-23
Hey,

So I was considering installing Gentoo for a while, and it gave me this idea:  is it possible to create new runlevels and choose which to boot at startup in GRUB, like you can in Gentoo? Specifically, I would like to be able to choose to have NDISWrapper/Wireless come up when my laptop's unplugged and in a wireless area OR have eth0/ethernet come up when it's plugged in, OR neither if completely 'netless (if plugged in AND in a wireless area, at present, neither one comes up because they conflict or something).

Here's the Gentoo stuff. Does anybody have any ideas on this?

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=4)

Thanks in advance,
Door

---

### Post by simonn on 2006-07-24
Read up to, but not including 4.b in the doco you linked to so you understand how /etc/inittab works.

You then just need to change the symlinks in /etc/rc?.d where ? is the runlevel.

---

