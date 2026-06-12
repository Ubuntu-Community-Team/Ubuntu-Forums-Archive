---
title: "making a smaller partition"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Himie on 2008-05-04
hi im using live session and i want to install from my cd (ubuntu 7.10) but my hd is small and i want the partition for linux to be 10gb only but the smallest partition the guided mode can make is 40gb, can someone explain to me how to make a 10gb partition using manual setup or another way? thx

---

### Post by TeoBigusGeekus on 2008-05-04
[http://ubuntuforums.org/showthread.php?t=779503]("http://ubuntuforums.org/showthread.php?t=779503")

---

### Post by drsox1899 on 2008-05-04
Hi there.

What else is on your disc ?  Do you want to dual boot ?

If there is nothing else and you don't want to dual boot with any Win installation, then in the Partition part of the Install process you can do this :

You need to setup at least 3 partitions :

1. For Ubuntu as /.  Size min4GB suggest 5GB as ext3 format
2. For your personal data as /home. Size - as much as you can spare (4GB?) as ext3 format
3. Swap partition. Size = 2x amount of RAM that you have.

All these choices can be made in the Manual part of the Partitioner.  Select Edit Partition and you can chose how big, what format and Mount point ( chose between /, /home, etc, etc)

If you want to do this before you install then I have used PartedMagic : [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

It's a clone of Partition Magic (Symantec Windows App) and runs as a live CD. I have found it to be very good.  All the partitions can be setup from that.

Otherwise GParted is a good alternative.

Luck

---

### Post by Himie on 2008-05-04
> **drsox1899 said:**
> Hi there.

What else is on your disc ?  Do you want to dual boot ?

If there is nothing else and you don't want to dual boot with any Win installation, then in the Partition part of the Install process you can do this :

You need to setup at least 3 partitions :

1. For Ubuntu as /.  Size min4GB suggest 5GB as ext3 format
2. For your personal data as /home. Size - as much as you can spare (4GB?) as ext3 format
3. Swap partition. Size = 2x amount of RAM that you have.

All these choices can be made in the Manual part of the Partitioner.  Select Edit Partition and you can chose how big, what format and Mount point ( chose between /, /home, etc, etc)

If you want to do this before you install then I have used PartedMagic : [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

It's a clone of Partition Magic (Symantec Windows App) and runs as a live CD. I have found it to be very good.  All the partitions can be setup from that.

Otherwise GParted is a good alternative.

Luck

thx i also have windows on another partition that i want to keep

so i make 3 partitions named    /.    /home.  and swap?

---

### Post by TeoBigusGeekus on 2008-05-04
They are not named /, /home and swap. These should be their mount points.

---

### Post by kansasnoob on 2008-05-04
I started with these guides and had hardly any trouble:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

But since then I've evolved to using either a GParted Live CD or using GParted from any Ubuntu Live CD (just >System>Administartion>Partition Editor while booted into the live CD) and shrinking the old Windows partition (I strongly recommend a back up, clean up, creating a system restore point, and defrag) to free up at least 10 GB.

Once I have 10 GB free, I just reboot the Ubuntu Live CD and choose install in the use "the largest continous free space". Then GRUB is installed properly, the installer decides the needed size of Swap, and I can use any live version of GParted to edit the size of my partitions later on.

By default the GRUB menu will show up during "start-up", then there's a 10 second delay to choose if I'd rather boot into Windows. If so I need only press "esc" and "arrow up or down to select my choice, then hit "enter".

NOTES:  
(1)I've never tried this in Ubuntu 7.10 or lower!
(2)I've never tried less than 10GB to install Ubuntu 8.04!
(3)I'm still a nOOb myself!
(4)If you use this method and decide later to remove Ubuntu altogether you will have to restore the MBR (master boot record) to Windows!

Most importantly ------------- I'm still only a few months into Ubuntu, so run my suggestions by a few longer term users!

---

### Post by drsox1899 on 2008-05-04
Himie :

The APC link referred to by kansasnoob is fine.  Use Page 3 in your case.  As you already have an Xp installation then you should follow this HowTo.

If you ONLY have a partition with Xp, then first defrag it (so that you don't lose any data), then let the Ubuntu installer deal with the partitioning.  

In the screen marked : Dualboot - Partition Disks, slide the slider until you see that the new partition size is 10GB.

The partitioner will create the partitions needed.

After you have a bit more experience with this, then you can go back and redo any installation with a separate /home partition (back it up and then restore so that you don't lose any data - easy to do)

Maybe then you may have a bigger or second disc and can setup to use more space for your own files.

The terminology of Ubuntu is different to Win Xp - Mount points are places where section of the install are placed, they aren't drives as WinXp uses.

If you create a separate /home on a DIFFERENT partition, then future installs won't touch it, just as long as you don't select it to be formatted each time.

It's like installing WinXp to the C drive, but all the My Documents, Shared Files, Desktop etc are being installed to another drive.

Here's a link that explains Files & Directories : [http://lowfatlinux.com/linux-directories.html](http://lowfatlinux.com/linux-directories.html)

---

### Post by Himie on 2008-05-05
i forgot to defrag the windows installation and i tried resizing now after the boot of xp nothing appears just a black screen can someone help.... i used the gparted live cd

---

### Post by drsox1899 on 2008-05-05
> **Himie said:**
> i forgot to defrag the windows installation and i tried resizing now after the boot of xp nothing appears just a black screen can someone help.... i used the gparted live cd

Oh dear.  From other posts on this forum, it seems that if you have the XP disk, you can run the recovery mode from the disk.  I'm no expert in this but I would suggest you try this first.

Here's another possibility. Have a look at the options shown in this forum thread 

[http://ubuntuforums.org/showthread.php?t=648650&highlight=restoring+windows](http://ubuntuforums.org/showthread.php?t=648650&highlight=restoring+windows)

You might be better off running the Ubuntu LiveCD to find your XP partition and copy your XP data files to another drive/USB for later restore.

---

### Post by Himie on 2008-05-05
anyway to get the xp "secret" administrator password? system recovery console wont let me use it with my admin account i need the "secret" admin password...

EDIT: nvm i could get xp to work again repairing it with the cd

---

### Post by drsox1899 on 2008-05-06
> **Himie said:**
> anyway to get the xp "secret" administrator password? system recovery console wont let me use it with my admin account i need the "secret" admin password...

EDIT: nvm i could get xp to work again repairing it with the cd

Glad to hear that it worked.

---

### Post by Himie on 2008-05-07
yea now i must get a step by step guide to help me from scratch xD

thx everyone who helped me with this problem

---

