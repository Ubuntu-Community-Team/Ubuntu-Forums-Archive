---
title: "[SOLVED] Grub Issues"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by LVCNSOL on 2008-10-01
I have 2 hard drives a 320GB SATA and a 250GB IDE
Recently I installed Ubuntu on about 100GB partition on the IDE (I unpluged the SATA during the install as it has my XP on it).
Now I have connected them both up again, booting from the IDE, i have tried to configure grub to find my XP install as well, but no luck. I can boot into Ubuntu through grub, but to boot into XP I need to change hard drive boot order in the BIOS.
How can i configure grub to find my XP? 

fdisk output
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x146e146d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17165   137877831    7  HPFS/NTFS
/dev/sda2           17166       30401   106318170    5  Extended
/dev/sda5           17166       30024   103289886   83  Linux
/dev/sda6           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb48fb48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS


device.map
> 
(hd0)	/dev/sda
(hd1)	/dev/sdb




Another thing is in the menu.lst there are double entries for ubuntu, why i have no idea, anyone able to shed some light?
> 
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4cd6f33e-c5cd-4763-81b7-5ec58a54f1d2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4cd6f33e-c5cd-4763-81b7-5ec58a54f1d2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4cd6f33e-c5cd-4763-81b7-5ec58a54f1d2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4cd6f33e-c5cd-4763-81b7-5ec58a54f1d2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Any help appreciated
Thanks Very Much

---

### Post by Orange_and_Green on 2008-10-01
If you want to boot XP leaving the boot order as it is (having the drive with ubuntu start first), please add this entry to your menu.lst:

```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
savedefault
chainloader +1

```

(spaces are important so be sure to copy them correctly or the commands will not be recognised). If you're curious, what this means is that, since Windows' boot loader is programmed in a way that it fails to start if it doesn't reside on the first partition of the first hard drive (I will be polite and refrain from commenting on that :)), you have to throw in those two "map" instructions to use advanced BIOS functionalities that trick Windows into believing it sits on the first boot drive even if that's not the case.

This should fix it. Good luck:KS

PS As to your second question, you will see that the entries differ by the number after the word "kernel". That means that you can currently choose to start Ubuntu with the 2.6.24-16 kernel (the one that came with your installation CD) or with the 2.6.24-19 kernel (the latest one). You will get a new entry every time the update manager installs a new kernel version. You should normally use the latest kernel (essentially for security reasons, and also for better driver support). But you still get to keep the possibility to boot with the older kernels so you can fall back on them if the new kernel breaks something (I had that happen once with my graphics card). Neat feature huh :)?

---

### Post by Bucky Ball on 2008-10-01
You have:

Ubuntu latest kernel
Ubuntu latest recovery kernel
Last version of the kernel
Last recovery version of the kernel

... in your menu.lst - notice the 19 at the end of the first two and 16 at the end of the second two. This is normal. :)

[QUOTE=Orange and Green](spaces are important so be sure to copy them correctly or the commands will not be recognised).[/QUOTE]

Most definitely, which is why I suggest you copy and paste the whole thing over to your menu.lst to avoid this.

---

### Post by LVCNSOL on 2008-10-01
Thank you to you both :D

Orange_and_Green that worked perfectly :D

Thanks

---

### Post by Bucky Ball on 2008-10-01
Nice one O&G. 

PseudZ, don't forget to mark your thread as solved from the 'Thread Tools' so others might find this solution. 

Enjoy! :)

---

