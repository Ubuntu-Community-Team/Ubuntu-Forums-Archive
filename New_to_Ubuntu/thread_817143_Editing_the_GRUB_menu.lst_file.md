---
title: "Editing the GRUB menu.lst file"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rockerphil on 2008-06-03
ok, need a quick hand here. i just installed DSL as a secondary OS on my absolutely ancient Dell Dimension desktop and can't figure out how to add it to the grub menu. here's some basic info on where i've got it installed to


phil@phil:~$ sudo fdisk -l

Disk /dev/sda: 7510 MB, 7510164480 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000269b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         868     6972178+  83  Linux
/dev/sda2             869         913      361462+   5  Extended
/dev/sda5             869         913      361431   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe26ae26a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            3846        4865     8193150   83  Linux
/dev/sdb2               1        3845    30884931    7  HPFS/NTFS

Partition table entries are not in disk order
phil@phil:~$ 


DSL is currently installed to /dev/sdb1, but i don't know where to go from here, any ideas? and thanx in advance guys



Phil


ps. if any other information is needed just ask

---

### Post by spiderbatdad on 2008-06-03
[http://ubuntuforums.org/showthread.php?t=441553](http://ubuntuforums.org/showthread.php?t=441553)

---

### Post by ibuclaw on 2008-06-03
First, get the UUID of your partition, as found in the command
```
blkid /dev/sdb1
```

Then putting a block like this in your menu.lst file should work:
```

title           Damn Small Linux
root            (hd1,0)
kernel          /boot/vmlinuz**<kernel-version>** root=UUID=**<UUID Number>** ro
initrd          /boot/initrd.img**<kernel-version>**

```
Replace <UUID Number> with the UUID number of the drive.

You will have to mount the partition and search the /boot directory to find out the kernel version numbers of the vmlinuz and initrd.img files.

Regards
Iain

---

### Post by rockerphil on 2008-06-03
hey tinivole, thanx for the help man, i did exactly like you said, i found that the version of DSL i'm using is using kernel version 2.4.26, so here's what i've got as the final entry in my /boot/grub/menu.lst file


title           Damn Small Linux
root            (hd1,0)
kernel          /boot/vmlinuz-2.4.26 generic root=UUID=6cc5faf5-6908-4697-bf6a-$
initrd          /boot/initrd.img-2.4.26 generic


but when i try to boot in to the OS it says "file not found". any suggestions?


also, here's the output of the code you gave me

root@phil:~# blkid /dev/sdb1
/dev/sdb1: UUID="6cc5faf5-6908-4697-bf6a-d17230bcc73b" TYPE="ext2" 
root@phil:~#

---

### Post by Duck2006 on 2008-06-03
Try

title Damn Small Linux
root (hd1,0)
chainloader +1

---

### Post by rockerphil on 2008-06-03
thanx duck2006, just tried it and i get "invalid or unsupported executable format"

---

### Post by Duck2006 on 2008-06-03
Where did you tell DSL to load it,s grub?

---

### Post by rockerphil on 2008-06-03
yea, i told DSL to install it's own GRUB. here's the contents of DSL's /boot/grub/menu.lst file

# This sets the default entry to boot. 
# Remember that GRUB counts from 0, so 1 is the second entry.

default 0
	
# This sets the length of time in seconds that grub will wait for the user to select an OS
# before it boots the default on. I reccommend at least 15 seconds.

timeout 15

# Enter the entry for DSL here. Something like this.

title DSL
kernel /boot/linux24 root=/dev/hdd1 quiet vga=normal noacpi noapm nodma noscsi frugal 

title DSL fb800x600
kernel /boot/linux24 root=/dev/hdd1 quiet vga=788 noacpi noapm nodma noscsi frugal 

title DSL fb1024x768
kernel /boot/linux24 root=/dev/hdd1 quiet vga=791 noacpi noapm nodma noscsi frugal 

title DSL fb1280x1024
kernel /boot/linux24 root=/dev/hdd1 quiet vga=794 noacpi noapm nodma noscsi frugal 

#title DSL with toram, mydsl, restore, hostname, and passwords
#kernel /boot/linux24 root=/dev/hdd1 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda5 restore=hda5 host=DSL1 secure

#title DSL with XFree86
#kernel /boot/linux24 root=/dev/hdd1 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda5/xfree restore=hda6 host=DSL1 secure

#title DSL with mydsl, restore, persistentancy, hostname, and passwords
#kernel /boot/linux24 root=/dev/hdd1 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda3 restore=hda3 home=hda3 opt=hda3 host=DSL1 secure

#title DSL Runlevel 2
#kernel /boot/linux24 root=/dev/hdd1 quiet vga=normal noacpi noapm noscsi nodma frugal 2 base norestore

#title DSL Check filesystem(s)
#kernel /boot/linux24 root=/dev/hdd1 quiet vga=normal noacpi noapm noscsi nodma frugal 2 base norestore legacy checkfs

#title Windows
#root (hd0,0)
#chainloader +1
#makeactive
#boot

---

### Post by bumanie on 2008-06-03
title     Damn Small Linux
root      (hd1,0)
kernel    /boot/vmlinuz-2.4.26-generic root=UUID=6cc5faf5-6908-4697-bf6a-d17230bcc73b ro quiet splash
initrd     /boot/initrd.img-2.4.26-generic
quiet
savedefault

Give that a try. I think you missed the hyphen betweem kernel number and -generic and also left the UUID short. Can't guarantee this will work, but it should - even tiny errors like that will cause boot issues.

PS: Add to ubuntu /boot/grub/menu.lst

---

### Post by rockerphil on 2008-06-03
nope, i get the message "file not found"

---

### Post by bumanie on 2008-06-03
I changed quiet to makeactive and added chainloader +1 command. 

title Damn Small Linux
root (hd1,0)
kernel /boot/vmlinuz-2.4.26-generic root=UUID=6cc5faf5-6908-4697-bf6a-d17230bcc73b ro quiet splash
initrd /boot/initrd.img-2.4.26-generic
savedefault
makeactive
chainloader +1

If that doesn't work we can look at fstab. > cat /etc/fstab and try making a mount point for /dev/sdb1

---

