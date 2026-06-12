---
title: "Problems with HDD. It grew from 1TB to more than 1 TB"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by jeroen8 on 2015-01-31
Dear people,

I just bought a new HDD for my computer. I plugged it in the computer and started to the computer. 
Everything went okay. I could find the HDD, but the problem was that my girlfriend could not access the HDD. So I changed the couple point in the "disks" program, that I found by searching for "disks" on my computer.
It used to be /media/jeroen (<== my profile) and I changed it to /media/Files, I also created an extra folder in the media folder where I could couple to HDD to, so my girlfriend could access as well.

Before I discovered this I found something on the internet that I had to edit the /etc/fstab file. I had to add something like this:
/dev/sda2 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0

And do sudo mount -a in a terminal.

So I did that. Still she couldnt access the disk, so I went further and found that I could change the couple point in the disks program. 

Now, all kinds of things are written inside my fstab file and as soon as I start my computer it asks to wait or to ignore the mounting of 2 disks. which I found the exact same name in the fstab. 
Apparently by commenting them out in the fstab file, the error dissapeared.
This is my fstab file:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=95d2f338-14da-4391-9539-5f0a83952275 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=574A-D94C  /boot/efi       vfat    defaults        0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
# /dev/disk/by-uuid/5eb4dc0c-5c60-46e2-989c-5d744dbabcd2 /mnt/5eb4dc0c-5c60-46e2-989c-5d744dbabcd2 auto nosuid,nodev,nofail,x-gvfs-show 0 0


# /dev/disk/by-uuid/1F055C1724A594D8 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0
# /dev/sda2 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/07F53B2A675B5762 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0

But what also happened is that my disk now has 3 partitions! The HDD itself is 1TB, but the combination of the 3 partitions is more than 1 TB!! As I want to delete a partition I get this error:
Error deleting partition /dev/sda1: Command-line `parted --script "/dev/sda" "rm 1"' exited with non-zero exit status 1: Error: /dev/sda: unrecognised disk label
 (udisks-error-quark, 0)

I have no idea what is going on at the moment. Could somebody please help me?
I want to go back to 1 HDD with 1 TB.

Regards,
Jeroen

P.s. before this happened I had some files on the HDD (for testing). These files also dissapeared as soon as I did a restart.

---

### Post by sandyd on 2015-01-31
> **jeroen8 said:**
> Dear people,

I just bought a new HDD for my computer. I plugged it in the computer and started to the computer. 
Everything went okay. I could find the HDD, but the problem was that my girlfriend could not access the HDD. So I changed the couple point in the "disks" program, that I found by searching for "disks" on my computer.
It used to be /media/jeroen (<== my profile) and I changed it to /media/Files, I also created an extra folder in the media folder where I could couple to HDD to, so my girlfriend could access as well.

Before I discovered this I found something on the internet that I had to edit the /etc/fstab file. I had to add something like this:
/dev/sda2 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0

And do sudo mount -a in a terminal.

So I did that. Still she couldnt access the disk, so I went further and found that I could change the couple point in the disks program. 

Now, all kinds of things are written inside my fstab file and as soon as I start my computer it asks to wait or to ignore the mounting of 2 disks. which I found the exact same name in the fstab. 
Apparently by commenting them out in the fstab file, the error dissapeared.
This is my fstab file:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=95d2f338-14da-4391-9539-5f0a83952275 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=574A-D94C  /boot/efi       vfat    defaults        0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
# /dev/disk/by-uuid/5eb4dc0c-5c60-46e2-989c-5d744dbabcd2 /mnt/5eb4dc0c-5c60-46e2-989c-5d744dbabcd2 auto nosuid,nodev,nofail,x-gvfs-show 0 0


# /dev/disk/by-uuid/1F055C1724A594D8 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0
# /dev/sda2 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/07F53B2A675B5762 /media/Files auto nosuid,nodev,nofail,x-gvfs-show 0 0

But what also happened is that my disk now has 3 partitions! The HDD itself is 1TB, but the combination of the 3 partitions is more than 1 TB!! As I want to delete a partition I get this error:
Error deleting partition /dev/sda1: Command-line `parted --script "/dev/sda" "rm 1"' exited with non-zero exit status 1: Error: /dev/sda: unrecognised disk label
 (udisks-error-quark, 0)

I have no idea what is going on at the moment. Could somebody please help me?
I want to go back to 1 HDD with 1 TB.

Regards,
Jeroen

P.s. before this happened I had some files on the HDD (for testing). These files also dissapeared as soon as I did a restart.

Can you post the output of
```

sudo parted -l
```

Thanks!

---

### Post by nerdtron on 2015-02-01
gparted is better at handling/formatting partition. You can install it from the software center.

And while you're at it, a screenshot from Disks utility can be helpful.

---

### Post by jeroen8 on 2015-02-01
Hi All,

Here is the outcome of sudo parted -l:
I see the two partitions. They are given in red below. 
It give it all in Dutch, but I translated some parts. 

Error: /dev/sda: unkown lable                                     


Model: ATA Crucial_CT240M50 (scsi)
Disk /dev/sdb: 240GB
Sectorgrootte (logisch/fysiek): 512B/4096B
Partitietabel: gpt


Number Beginning   End  Size  Bestandssysteem  Naam  Vlaggen
 1      1049kB  538MB  537MB    fat32                  opstart
 2      538MB   794MB  256MB    ext2
 3      794MB   240GB  239GB                           lvm




[COLOR=#ff0000]Model: Linux device-mapper (linear) (dm)[/COLOR]
[COLOR=#ff0000]Disk /dev/mapper/ubuntu--vg-swap_1: 8527MB[/COLOR]
[COLOR=#ff0000]Sectorgrootte (logisch/fysiek): 512B/4096B[/COLOR]
[COLOR=#ff0000]Partitietabel: loop[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Number Beginning  End  Size  Bestandssysteem  Vlaggen[/COLOR]
[COLOR=#ff0000] 1      0,00B  8527MB  8527MB   linux-swap(v1)[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Model: Linux device-mapper (linear) (dm)[/COLOR]
[COLOR=#ff0000]Disk /dev/mapper/ubuntu--vg-root: 231GB[/COLOR]
[COLOR=#ff0000]Sectorgrootte (logisch/fysiek): 512B/4096B[/COLOR]
[COLOR=#ff0000]Partitietabel: loop[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Number Beginning  End  Size  Bestandssysteem  Vlaggen[/COLOR]
[COLOR=#ff0000] 1      0,00B  231GB  231GB    ext4[/COLOR]

See here the linke to the screenshot: [http://i62.tinypic.com/28j9jxh.png](http://i62.tinypic.com/28j9jxh.png). 
I'm sorry, but this is as well in Dutch. I hope you understand, otherwise you can ask me.

Thank you very much for the help.

Regards,
Jeroen

---

### Post by oldfred on 2015-02-01
I do not know LVM.

But LVM can span more than one drive using more than one physical partition. So did you add new drive to LVM, not as a separate partition? The risk of spanning like that is that if either drive fails, you lose all data on both drives. But you have the convenience of one very large drive. So really good backups to another drive are required.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
    
Gparted will only show the physical partitions, not the logical partitions inside the lvm.

---

