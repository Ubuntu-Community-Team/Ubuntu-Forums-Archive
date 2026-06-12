---
title: "Updated to 8.04, how do I update grub?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Dan_472 on 2008-04-30
Hello

I just updated to 8.04, and I'm not sure if grub is loading the new kernel.
I have both Ubuntu and Puppy on multiple drives and partitions, here's the boot part of menu.lst:


```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Puppy
root		(hd1,1)
kernel		(hd1,1)/vmlinuz root=/dev/ram0 pmedia=idehd
initrd		(hd1,1)/initrd.gz

title		Puppy in ram only
root		(hd1,2)
kernel		(hd1,2)/vmlinuz root=/dev/ram0 pmedia=idehd pfix=ram
initrd		(hd1,2)/initrd.gz

title		Ubuntu 7.10, kernel 2.6.23.14
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.23.14 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.23.14

title		Ubuntu 7.10, kernel 2.6.23.14 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.23.14 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.23.14

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.17-11-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 7.10, kernel 2.6.17-11-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 7.10, kernel 2.6.15-28-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-k7 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-k7

title		Ubuntu 7.10, kernel 2.6.15-28-k7 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-k7 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.15-28-k7

title		Ubuntu 7.10, kernel 2.6.15-28-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu 7.10, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu 7.10, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 7.10, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=5e128b4a-a008-44e6-88c5-4637d954deb3 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

I haven't changed any HDD partitions.  What should I do?

Thank You

---

### Post by mikewhatever on 2008-04-30
You can check which kernel is used with <uname -r>. It looks like you have 2.6.22 and 2.6.23, but Hardy should have 2.6.24. You can try <sudo update-grub>, but backup the existing menu with <sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup>.

---

### Post by Dan_472 on 2008-04-30
Problem solved!
Thank you.

A few things I had to do which may only apply to my system, but I'll post anyway for anyone else who is in the same situation:

I had to move menu.lst to another directory before <sudo update-grub> would make a fresh copy in /boot/grub/

I had to copy-and-paste the lines about PuppyLinux, probably because they are in another partition.

Thanks again.

---

