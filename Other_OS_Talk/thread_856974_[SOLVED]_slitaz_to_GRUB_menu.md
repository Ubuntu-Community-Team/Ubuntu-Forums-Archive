---
title: "[SOLVED] slitaz to GRUB menu"
date: 2008-07-12
forum: Other OS Talk
---

### Post by AnLGP on 2008-07-12
Hello,

I'd like to add slitaz cooking [http://www.slitaz.org/en/get/#cooking](http://www.slitaz.org/en/get/#cooking)

to the GRUB menu that way I can boot.  I know it involves editing the /boot/grub/menu.lst file, but I'm not sure what to add to get it to work.  IE. the slitaz specifics.  Can anyone help please?  Thanks!

---

### Post by cardinals_fan on 2008-07-12
title  SliTaz GNU/Linux 1.0 (Kernel 2.6.24.2-slitaz)
       root(hd0,0)
       kernel /boot/vmlinuz-2.6.24.2-slitaz root=/dev/hda1 vga=normal

[http://www.slitaz.org/en/doc/handbook/install.html](http://www.slitaz.org/en/doc/handbook/install.html)

---

### Post by AnLGP on 2008-07-12
ah cool I read that I figured the cooking would be different.  Thanks!

---

### Post by AnLGP on 2008-07-12
Hello again,

I posted this same question on the slitaz forum as well and between here and there I got these two responses and none of them work


title    SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.25.5-slitaz)
root    (hd1,2)
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/sdb3

title SliTaz GNU/Linux 1.0 (Kernel 2.6.24.2-slitaz)
root(hd0,0)
kernel /boot/vmlinuz-2.6.24.2-slitaz root=/dev/hda1 vga=normal


---------------

partitions table:

Slitaz is on /dev/sdb3


Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1200

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7476    60050938+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19157   153878571   83  Linux
/dev/sdb2           30028       30401     3004155    5  Extended
/dev/sdb3           19158       30027    87313275   83  Linux
/dev/sdb5           30028       30401     3004123+  82  Linux swap /

cardinals fan when I try yours it says something about kernel panic.  I can put it in again and reboot to see exactly what if you'd like.

---

### Post by cardinals_fan on 2008-07-12
This should have worked:
```
title SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.25.5-slitaz)
root (hd1,2)
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/sdb3
```

My response was not meant to be cut & pasted; it needed editing.  But the section above should work... :confused:

---

### Post by AnLGP on 2008-07-12
ah ok.  I plugged this back in

title SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.25.5-slitaz)
root (hd1,2)
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/sdb3

and this

[http://i297.photobucket.com/albums/mm213/musicauniversalis/0712081635.jpg](http://i297.photobucket.com/albums/mm213/musicauniversalis/0712081635.jpg)

is what comes at the end.  "unable to mount root fs on unknown-block (0,0)

here's the menu.lst


title		Ubuntu
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=653ab398-5d27-4452-a8ca-8549e3438d32 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=653ab398-5d27-4452-a8ca-8549e3438d32 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.25.5-slitaz)
root (hd1,2)
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/sdb3

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by cardinals_fan on 2008-07-12
That's weird... let me think about it.

---

### Post by init1 on 2008-07-13
In SliTaz, my hard drive is recognized as /dev/hda when it is usually recognized as /dev/sda. I think that my be the problem for you. Try this:

title SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.25.5-slitaz)
root (hd1,2)
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/sda3

Good luck! :D

---

### Post by AnLGP on 2008-07-13
This worked:

title SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.25.5-slitaz)
root (hd1,2)
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/sda3

---

### Post by cardinals_fan on 2008-07-13
> **AnLGP said:**
> This worked:

title SliTaz GNU/Linux (cooking) (Kernel vmlinuz-2.6.25.5-slitaz)
root (hd1,2)
kernel /boot/vmlinuz-2.6.25.5-slitaz root=/dev/sda3
Aha!  So it was sda, not sdb.

---

### Post by AnLGP on 2008-07-13
What's all that mean, exactly?  It's the type of HDD I suppose?

---

### Post by cardinals_fan on 2008-07-13
> **AnLGP said:**
> What's all that mean, exactly?  It's the type of HDD I suppose?
To SliTaz, it's on the first hard drive (a) rather than the second (b).

---

### Post by edfish on 2008-07-13
thanks!!!
[email]edfish@live.co.uk[/email] 


:lolflag:

---

### Post by init1 on 2008-07-14
> **AnLGP said:**
> What's all that mean, exactly?  It's the type of HDD I suppose?
It means that the kernel is recognizing the hard drive differently than most distros. This happens to me in SliTaz too. Unfortunately, in addition to the unusual recognition, hard drive access is really slow. It's still a great live distro though :D

---

### Post by cardinals_fan on 2008-07-14
> **init1 said:**
> It means that the kernel is recognizing the hard drive differently than most distros. This happens to me in SliTaz too. Unfortunately, in addition to the unusual recognition, hard drive access is really slow. It's still a great live distro though :D
Actually, many distros recognize IDE disks as "sd*" rather than "hd*".

---

### Post by AnLGP on 2008-07-15
> Unfortunately, in addition to the unusual recognition, hard drive access is really slow. It's still a great live distro though 

I haven't had any problems besides the grub menu.  HD access is fine and music worked for me right out of the box, internet did, etc etc. all.  Install stuff took some work to get used to but I found out I have to reload the list and then I just do it in the terminal using tazpkg get-install ...

---

### Post by init1 on 2008-07-15
> **AnLGP said:**
> I haven't had any problems besides the grub menu.  HD access is fine and music worked for me right out of the box, internet did, etc etc. all.  Install stuff took some work to get used to but I found out I have to reload the list and then I just do it in the terminal using tazpkg get-install ...
Glad to hear it :D

---

