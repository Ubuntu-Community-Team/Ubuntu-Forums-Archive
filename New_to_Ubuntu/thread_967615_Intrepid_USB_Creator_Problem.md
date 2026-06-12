---
title: "Intrepid USB Creator Problem"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-11-02
I created a USB Boot disk on my flash drive. However being more familiar with Grub than syslinux I installed grub onto instead. When it boots it gives the message

```
no init found. Try passing init=
busybox V1.10.2

(initramfs)
```
My initrd is /casper/initrd.gz and my kernel is /casper/vmlinuz
are these not correct?

---

### Post by caljohnsmith on 2008-11-02
If you at least allowed the Intrepid installer to install syslinux to the boot sector of the Ubuntu partition, and all you did was replace the MBR on that drive with Grub, you should be able to boot the Ubuntu partition with simply:
```
title   Ubuntu Intrepid on USB
root    (hd0,X)
chainloader +1
```
Where X is your Ubuntu partition minus one, e.g. sdb3 = (hd0,2). I just helped someone a few days ago do exactly what you are trying to do, i.e. use Grub to boot the partition instead of syslinux, and that's exactly how we did it. But that assumes you at least allowed the Intrepid installer to install syslinux to the boot sector of the Ubuntu partition.

---

### Post by C.S.Cameron on 2008-11-02
I understand that 8.10 is no longer using root(hd0,X) in menu.lst it is using uuid.
(initramfs) is still a bug with flash drives over 2G.

---

### Post by caljohnsmith on 2008-11-02
> **C.S.Cameron said:**
> I understand that 8.10 is no longer using root(hd0,X) in menu.lst it is using uuid.

That's true Intrepid uses "uuid" by default, but you can still use the "root (hdX,Y)" notation if you want to; either is OK. :)

---

### Post by C.S.Cameron on 2008-11-02
I tried rewriting menu.lst the old way with "root (hdX,Y)" on a Full flash drive install but may have made an error, will try again.
Using switchconf to select different xorg.conf's still works.

---

