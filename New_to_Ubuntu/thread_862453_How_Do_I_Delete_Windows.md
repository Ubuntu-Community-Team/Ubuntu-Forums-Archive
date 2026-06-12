---
title: "How Do I Delete Windows?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by hopkinsjeni on 2008-07-17
I am trying to delete windows and am having problems. 
Firstly, I can't unmount the ntfs as it brings up an error that it is being used by another program but for the life of me I can't think what.
Also when I went to change the info in fstab I couldn't find what I was looking for, one of my friends is very ubuntu savvy and says this looks a tad odd:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



I installed ubuntu through wubi and I really want to get rid of windows, any help would be great, this is driving me nuts!
Thank you

---

### Post by NightwishFan on 2008-07-17
You need to do a full install of Ubuntu, as wubi is installed in windows.

Put an ubuntu cd in and reboot and hit "install ubuntu" then when it comes time to partition, backup all your personal files to a dvd or flash drive, then hit use all disk. That will remove everything: windows, ubuntu with wubi etc then it will install a normal session of ubuntu on your entire hard disk. Use with care as if you do not back up all data will be deleted!

---

### Post by aktiwers on 2008-07-17
I dont think you can get rid of Windows when you used a Wubi install.
Then you have to make a clean install without Wubi, and choose to wipe windows.

Wubi installs a virtual harddrive on your into Windows. Then unstalls Ubuntu on that hardrive. Then let you boot to that harddrive and use ubuntu.

So I would go for a clean install, and if you want to save most of you configurations, backup your current /home folder and use it om the net install.

---

### Post by eriqjaffe on 2008-07-17
You can also use [lvpm](http://lubi.sourceforge.net/lvpm.html) to migrate your WUBI-image-based install to a disk-based install.

---

### Post by space.duck on 2008-07-17
i would use the gparted live cd and delete the windows partition and reinstall ubuntu on the whole disk. happy days. ubuntu all round.
:)

---

### Post by oldos2er on 2008-07-17
"I installed ubuntu through wubi and I really want to get rid of windows"

 Boot the Ubuntu live cd, choose install; when the partitioner comes up, choose 'Guided--Use Entire Disk".

---

### Post by zalmoxes on 2008-07-26
> **oldos2er said:**
> 
 Boot the Ubuntu live cd, choose install; when the partitioner comes up, choose 'Guided--Use Entire Disk".

dont you lose all your data if you do this?

i've installed my ubuntu using wubi, and i really want to get rid of windows now... without losing my data...

---

### Post by RiceMonster on 2008-07-26
Back up your data from your wubi install then do a full install, that's probably the easiest way to do it.

---

### Post by jamesrfla on 2008-07-26
If you get rid of Windows it will get rid of Ubuntu as well since you used Wubi. If you are ready to get rid of Windows forever then back up all your files, documents, and internet favorites to a flash drive or to another storage drive. The insert the Ubuntu CD and install it using the entire disk which means Ubuntu will be on the entire hard drive. Then restore your files.

---

### Post by Paqman on 2008-07-26
> **eriqjaffe said:**
> You can also use [lvpm](http://lubi.sourceforge.net/lvpm.html) to migrate your WUBI-image-based install to a disk-based install.

+1 to this.

This option will preserve all your data and settings. A clean install is an option, but you'd be starting from scratch. I'd definitely use LVPM, myself.

---

