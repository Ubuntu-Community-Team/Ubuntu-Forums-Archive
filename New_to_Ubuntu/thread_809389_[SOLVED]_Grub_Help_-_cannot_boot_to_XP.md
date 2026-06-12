---
title: "[SOLVED] Grub Help - cannot boot to XP"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by spamzilla on 2008-05-27
My brain has turned to mush and I cannot think clearly atm. I have just installed XP and Ubuntu was previously installed. I setup XP, booted into the livecd and ran:

```

sudo grub

find /boot/grub/stage1

root (hd0,0)

setup (0,0)

quit

```

Restarted now I cannot boot into XP, but I can boot into Ubuntu. What did I do wrong?

```

** sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002c56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2437    19575171   83  Linux
/dev/sda2            2438       13320    87417697+  83  Linux
/dev/sda3           13321       13575     2048287+  82  Linux swap / Solaris
/dev/sda4           13576       19457    47247165    7  HPFS/NTFS

```

Can anyone help me out?

Cheers

---

### Post by sayakb on 2008-05-27
Try adding this to /boot/grub/menu.lst
```
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
```

---

### Post by kansasnoob on 2008-05-27
If I understand correctly you installed XP after Ubuntu, if so look at this tutorial:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Just follow the sections "Reinstall GRUB to the MBR" and "Modify the Boot Menu".

Hopefully this helps.

---

### Post by alienexplorers on 2008-05-27
What does your /boot/grub/menu.lst file look like.  Can you post it here?

---

### Post by spamzilla on 2008-05-27
> **LinuxIsInnovation said:**
> Try adding this to /boot/grub/menu.lst
```
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
```

I did that and got the following:

> 
error:13 invalid or unsupported executable format

press any key to continue

Here's my /boot/grub/menu.lst file:

```

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=c90fb310-02ea-4bb7-ab2a-d3f56160af2f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=c90fb310-02ea-4bb7-ab2a-d3f56160af2f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd0,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#Windows XP Professional
title Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

```

Thanks

---

### Post by spamzilla on 2008-05-27
> **kansasnoob said:**
> If I understand correctly you installed XP after Ubuntu, if so look at this tutorial:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Just follow the sections "Reinstall GRUB to the MBR" and "Modify the Boot Menu".

Hopefully this helps.

That is what I did andI get the following:

```

error:13 invalid or unsupported executable format

press any key to continue 

```

However, in Gparted, there is an orange ! next to my XP partition. What does this mean?

---

### Post by bumanie on 2008-05-27
> cat /boot/grub/menu.lst The first reply won't help because you need ubuntu to recognise windows is there (although adding noverify is worthwhile, but won't work on its own). You will probably have to add drive map commands to your grub list which are inputed between makeactive and chainloader +1. Not sure whether the boot flag on ubuntu partition is going to allow windows to boot or not - mmm can't remember that. Someone else may know. Usually windows is the boot partition on a dual boot system. I think you will have to set grub root to (hd0,3).
Map commands as follows
map (hd0,0) (hd0,3)
map (hd0,3) (hd0,0)
It is much simpler to install windows first. Can't guarantee the above will work. You should look here for more information on grub
[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Duck2006 on 2008-05-27
Change this

#Windows XP Professional
title Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

to this

#Windows XP Professional
title Windows XP Professional
rootnoverify (hd0,3)
makeactive
chainloader +1

---

### Post by spamzilla on 2008-05-27
> **Duck2006 said:**
> Change this

#Windows XP Professional
title Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

to this

#Windows XP Professional
title Windows XP Professional
rootnoverify (hd0,3)
makeactive
chainloader +1

That worked, thanks :KS

---

