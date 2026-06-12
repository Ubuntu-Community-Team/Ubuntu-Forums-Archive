---
title: "Grub Error 13: &quot;Invalid or unsupported executable format&quot;"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Gallus on 2008-09-18
I know there are severeal threads and suggested solutions about this problem. But nothing worked...

When I try to boot with my windows partition (sda2) (Ubunutu is on the same partition but sda1) i'll get this error message:

[B]set aux_hd="hd0"
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0 0 300 
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0x1fe 0x1fe 2
rootnoverify (hd0,0)
make active
chainloader +1

Error 13: Invalid or unsupported executable format[/B]

---

### Post by bobnutfield on 2008-09-18
Hello,

Can you post the output of

> fdisk -l

and the Windows boot entry in your /boot/grub/menu.lst file?  There is something wrong with the boot order it appears.  Did you install Windows AFTER Ubuntu?

---

### Post by Crafty Kisses on 2008-09-18
You need to change the entry for Windows. Open a Terminal and enter:
```

sudo gedit /boot/grub/menu.lst
```

---

### Post by Gallus on 2008-09-18
Output of fdisk -l


Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00073ee6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       26182   210306883+  83  Linux
/dev/sda2           26183       30025    30868897+   7  HPFS/NTFS
/dev/sda3           30026       30401     3020220    5  Erweiterte
/dev/sda5           30026       30401     3020188+  82  Linux Swap / Solaris

Yes, I installed Windows AFTER Ubunutu...

And what should I write into menu.lst?

At the moment there is no entry about my Windows partition...I tried to insert the following lines:
title		Windows
rootnoverify	(hd0,0)
makeactive
chainloader +1

But it doesn't work and I didn't know what to write- it was just copy and paste from antother post in the internet...

---

### Post by unutbu on 2008-09-18
Edit your menu.lst:```


gksu gedit /boot/grub/menu.lst
```

Change the stanza you posted to
```

title		Windows
root		(hd0,1)
makeactive
chainloader	+1

```

---

### Post by bobnutfield on 2008-09-18
Change this:

> title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

to this:

> title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1

And as long as you Windows boot sector is intact, it should boot.  Windows sometimes complains about being on the second partition, but it can work.

---

