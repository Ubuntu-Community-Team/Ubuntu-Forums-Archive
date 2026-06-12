---
title: "Windows + Pardus + El&#305;ve =&gt; Elive won't boot"
date: 2007-10-06
forum: Other OS Talk
---

### Post by nganon on 2007-10-06
Hello Guys,
I have just installed Elive Gem 1.0 but it wont boot. 
I installed GRUB to the root partition because I had Windows bootloader on MBR which boots Pardus 2007.2 as well as WindowsXP. Pardus GRUB is installed in Pardus root partition and boots both Windows and Pardus. I reconfigured the grub.conf of Pardus (see below) to boot Elive but when I select Elive from GRUB menu I end up with a black screen     , cursor blinking. 
Earlier,I tried to intall Elive GRUB on the MBR but boot failed at "Loading Stage1.5.." screen. So I had to reinstall GRUB (with LSRCD) to the MBR to get back on the work. The HDD  geometry and recent GRUB confs  are as below:


```

grub> geometry (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82
   Partition num: 4,  Filesystem type is reiserfs, partition type 0x83
   Partition num: 5,  Filesystem type is fat, partition type 0xb
```

```

# fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       18725     9437368+   c  W95 FAT32 (LBA)
/dev/hda2           18726       70738    26214552   83  Pardus
/dev/hda3           70739       73859     1572984   82  Linux swap / Solaris
/dev/hda4           73860      116280    21380184    f  W95 Ext'd (LBA)
/dev/hda5   *       73871       92581     9430155   83  Elive
/dev/hda6           92582      116280    11944296    b  W95 FAT32

```

```

# cat /mnt/hda5/boot/grub/menu.lst
# See www.gnu.org/software/grub for details
# By default, boot the first entry
default 0
# Boot automatically after 5 seconds
timeout 25
gfxmenu /boot/grub/message.elive

title Elive Gem
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /boot/vmlinuz-2.6.18-elive root=/dev/hda5 vga=normal
initrd /boot/initrd.img-2.6.18-elive

# This is a divider, added to separate the menu items below from the Debian
# ones.

# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
chainloader     +1

title           Pardus 2007.2 [2.6.18.8-86] - hda2 (on /dev/hda2)
root            (hd0,1)
kernel          /boot/kernel-2.6.18.8-86 root=/dev/hda2 video=vesafb:nomtrr,pmipal,ywrap,1024x768-32@60 splash=silent,fadein,theme:pardus console=tty2 mudur=language:en quiet resume=/dev/hda3
initrd          (hd0,1)/boot/initramfs-2.6.18.8-86
savedefault
boot

title           Memory RAM diagnostic
root            (hd0,4)
kernel          /boot/memtest
savedefault
boot

```


```

# cat /boot/grub/menu.lst
default 0
background 10333C
timeout 7
splashimage (hd0,1)/boot/grub/splash.xpm.gz

title Pardus 2007.2 [2.6.18.8-86] - hda2
root (hd0,1)
kernel (hd0,1)/boot/kernel-2.6.18.8-86 root=/dev/hda2 video=vesafb:nomtrr,pmipal,ywrap,1024x768-32@60 splash=silent,fadein,theme:pardus console=tty2 mudur=language:en quiet resume=/dev/hda3
initrd (hd0,1)/boot/initramfs-2.6.18.8-86

title Windows XP (fat32) - hda1
rootnoverify (hd0,0)
makeactive
chainloader +1

title Elive Gem 1.0 - hda5
root (hd0,4)
kernel (hd0,4)/boot/vmlinuz-2.6.18-elive vga=normal
initrd (hd0,4)/boot/initramfs-2.6.18.8-86

```


Something is wrong but what?
Any ideas how to fix that up ?

Thanks in advance

---

### Post by RAV TUX on 2007-10-06
> **nganon said:**
> Hello Guys,
I have just installed Elive Gem 1.0 but it wont boot. 
I installed GRUB to the root partition because I had Windows bootloader on MBR which boots Pardus 2007.2 as well as WindowsXP. Pardus GRUB is installed in Pardus root partition and boots both Windows and Pardus. I reconfigured the grub.conf of Pardus (see below) to boot Elive but when I select Elive from GRUB menu I end up with a black screen     , cursor blinking. 
Earlier,I tried to intall Elive GRUB on the MBR but boot failed at "Loading Stage1.5.." screen. So I had to reinstall GRUB (with LSRCD) to the MBR to get back on the work. The HDD  geometry and recent GRUB confs  are as below:


```

grub> geometry (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82
   Partition num: 4,  Filesystem type is reiserfs, partition type 0x83
   Partition num: 5,  Filesystem type is fat, partition type 0xb
``````

# fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       18725     9437368+   c  W95 FAT32 (LBA)
/dev/hda2           18726       70738    26214552   83  Pardus
/dev/hda3           70739       73859     1572984   82  Linux swap / Solaris
/dev/hda4           73860      116280    21380184    f  W95 Ext'd (LBA)
/dev/hda5   *       73871       92581     9430155   83  Elive
/dev/hda6           92582      116280    11944296    b  W95 FAT32

``````

# cat /mnt/hda5/boot/grub/menu.lst
# See www.gnu.org/software/grub for details
# By default, boot the first entry
default 0
# Boot automatically after 5 seconds
timeout 25
gfxmenu /boot/grub/message.elive

title Elive Gem
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /boot/vmlinuz-2.6.18-elive root=/dev/hda5 vga=normal
initrd /boot/initrd.img-2.6.18-elive

# This is a divider, added to separate the menu items below from the Debian
# ones.

# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
chainloader     +1

title           Pardus 2007.2 [2.6.18.8-86] - hda2 (on /dev/hda2)
root            (hd0,1)
kernel          /boot/kernel-2.6.18.8-86 root=/dev/hda2 video=vesafb:nomtrr,pmipal,ywrap,1024x768-32@60 splash=silent,fadein,theme:pardus console=tty2 mudur=language:en quiet resume=/dev/hda3
initrd          (hd0,1)/boot/initramfs-2.6.18.8-86
savedefault
boot

title           Memory RAM diagnostic
root            (hd0,4)
kernel          /boot/memtest
savedefault
boot

```
```

# cat /boot/grub/menu.lst
default 0
background 10333C
timeout 7
splashimage (hd0,1)/boot/grub/splash.xpm.gz

title Pardus 2007.2 [2.6.18.8-86] - hda2
root (hd0,1)
kernel (hd0,1)/boot/kernel-2.6.18.8-86 root=/dev/hda2 video=vesafb:nomtrr,pmipal,ywrap,1024x768-32@60 splash=silent,fadein,theme:pardus console=tty2 mudur=language:en quiet resume=/dev/hda3
initrd (hd0,1)/boot/initramfs-2.6.18.8-86

title Windows XP (fat32) - hda1
rootnoverify (hd0,0)
makeactive
chainloader +1

title Elive Gem 1.0 - hda5
root (hd0,4)
kernel (hd0,4)/boot/vmlinuz-2.6.18-elive vga=normal
initrd (hd0,4)/boot/initramfs-2.6.18.8-86

```
Something is wrong but what?
Any ideas how to fix that up ?

Thanks in advance

First install windows, then Pardus and then install Elive last, then Elive will automatically detect your other OS's and the boot loader should work.

My advice is instead of using Elive Gem 1.0 is to use Xubuntu 7.10 and install e17 CVS testing on Xubuntu following [Rui Pais]("http://ubuntuforums.org/member.php?u=862")'s  guide here:
[http://ubuntuforums.org/showthread.php?t=546746&highlight=e17&page=7](http://ubuntuforums.org/showthread.php?t=546746&highlight=e17&page=7)

---

### Post by nganon on 2007-10-06
> **RAV TUX said:**
> First install windows, then Pardus and then install Elive last, then Elive will automatically detect your other OS's and the boot loader should work.

My advice is instead of using Elive Gem 1.0 is to use Xubuntu 7.10 and install e17 CVS testing on Xubuntu following [Rui Pais]("http://ubuntuforums.org/member.php?u=862")'s  guide here:
[http://ubuntuforums.org/showthread.php?t=546746&highlight=e17&page=7](http://ubuntuforums.org/showthread.php?t=546746&highlight=e17&page=7)

Thanks for your advice. 
Thats exactly how I installed all three of them. 1st Windows then Pardus (GRUB to its own partition), then Elive  (GRUB to MBR). 
But I ended up with "Loading Stage1.5 Please wait.." screen. 
As you see in my Elive grub.conf , both Windows and Pardus are detected. Failed to show the grub menu. where GRUB  is installed in the MBR and give black screen with blinking cursor when Elive is selected. 
There must be a way else than giving up or reinstalling all OS's.

---

