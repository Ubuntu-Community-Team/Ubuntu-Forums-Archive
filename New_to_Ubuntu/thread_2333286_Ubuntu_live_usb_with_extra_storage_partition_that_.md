---
title: "Ubuntu live usb with extra storage partition that I can access from the live-system"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by martinesue on 2016-08-08
I'm booting off a live usb and would I also want to use the same usb stick for storing data from the live-session. I'm not at all interested in full system persistence, but rather to have the stick function as a normal storage device where I can put and read the files of my choice.


I have tried to simply add a partition to the drive (note: not while running the live system) but the problem is I'm not able to later mount this when I've started the live system again. When trying to mount */dev/sdb3* it says it is already mounted or busy, and I'm guessing the problem is that */dev/sdb* is mounted at */cdrom*.


[B]To clarify, this is what I'm doing

[/B]
 1. Starting my normal ubuntu system (not live) 
 2. Writing the ubuntu iso to the usb stick using dd
 3. Using *fdisk* to add a fat partition, and then formatting the partition 
 4. I can use the new partition and add files without any trouble in my normal system. 
 5. I live-boot using the stick, and I'm unable to mount the partition. 
 6. I can see the partition using *fdisk -l* and also in *thunar*, but when I try to mount it, it says "already mounted". 
 7. Running *mount | grep sdb *gives me [I]/dev/sdb on /cdrom type iso9660 (ro,noatime)

[/I]I previously had a debian live stick with an extra partition and had no problem whatsoever mounting and using that.

---

### Post by yancek on 2016-08-08
Your output from the mount command you ran doesn't look right.  When I run the same command you did on sdc, a flash drive with an ntfs and ext4 partition, I get the output below:

> mount | grep sdc
/dev/sdc1 on /media/MULTIBOOT type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc3 on /media/22b4a3c2-4b1d-4b95-8586-0964341007e1 type ext3 (rw,nodev,nosuid,uhelper=udisks2) 

Your output shows just sdb which would be correct if you used dd to copy to that drive.  Does the second partition show when you run fdisk?
Did you check under the /media directory on the usb drive to see if your partition is available there.

---

### Post by martinesue on 2016-08-09
Is that the very same flash stick you have booted the live system from? That's where my problem is. Using a normal separate usb-stick is no trouble.

fdisk shows three partitions. One small efi, one large ubuntu partition, and my intented data partition as sdb3. Only sdb shows up in "mount", without any number.
Only "cdrom" is available under /media.

---

### Post by CatKiller on 2016-08-09
Where are you identifying that partition as sdb3? The sd*x* assignments are done at boot time, and there is no reason to think that they would be the same in different environments, or even on subsequent boots.

---

### Post by martinesue on 2016-08-09
> **CatKiller said:**
> Where are you identifying that partition as sdb3? The sd*x* assignments are done at boot time, and there is no reason to think that they would be the same in different environments, or even on subsequent boots.
*sudo fdisk -l*&#8203;

---

### Post by CatKiller on 2016-08-09
I was more asking whether that was from your live environment, or wherever you created the partition from.

---

### Post by martinesue on 2016-08-09
I've ran the command on both. They seem to end up on the same letter, but of course that could differ.

On my normal system I have no problem mounting the drive (manually on in thunar).

Is my question really that unusual? I've google like a maniac and all I can find is full persistence. 
I don't want that for multiple reasons

1) No interest in storing nothing but a few small files
2) Performance
3) Security (leave no trace of the session)

I'm building a custom live-cd so any hack you can think of to solve the problem is interesting.

---

### Post by CatKiller on 2016-08-09
OK, so if /dev/sdb really is your thumb drive, you need to find out why your computer thinks that it is also your cd-rom drive, and what is mounting that to /media. Do you have a cd-rom drive in that computer? Is there a cd in the drive? What are the contents of your /etc/fstab? Also, what happens if you try to mount that partition by its UUID rather than by its /dev designation?

---

### Post by martinesue on 2016-08-09
No cd-drive. 
I thought that mounting to /cdrom was the standard behavior of the live-usb. I simply boot from the official live-iso, and the same on multiple computers.

/etc/fstab contains:
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

Same problem when mounting by UUID.

---

### Post by CatKiller on 2016-08-09
My experience has always been that only cd-roms get mounted to /media/cdrom. Other drives get mounted other places.

I've just noticed that you're saying that the mount point is **/cdrom**, straight under the / directory. That is **definitely** non-standard.

I'm afraid I'm out of ideas of what might cause the symptoms you describe.

Edit: Since your / is mounted as an overlay, that system means that the usual fstab methods probably don't apply. I have no idea how that is configured, but that's probably the next place to look.

---

### Post by martinesue on 2016-08-09
I started digging a bit in the init scripts and in for instance the beginning of /usr/share/initramfs-tools/scripts/casper it says "mountpoint = /cdrom", so I think it is standard.

Editing these scripts are however probably above my ability.


Any other ideas? What confuses me is how simple this was in Debian. I had no problem the boot-usb being locked there. I could mount as normal.

---

### Post by yancek on 2016-08-09
An Ubuntu Live CD whether on a CD/DVD or flash drive does have a cdrom directory in the / (root) of the filesystem.  There is a cdrom directory under /media also but it is a link to the other directory.

I have a usb with Ubuntu Live on it and repeated your process.  Booted another Linux system and used GParted to create a second partition on the usb drive.  Booting this usb drive and checking the /media directory shows the other partitions on the main hard drive as well as the first partition mounted at cdrom but not the second partition on the usb drive.  Checked fstab and mtab and there was no listing for the second partition in either location.

I ran the mount command you posted earlier and got the same result you did.  Then created a mount point and mounted the second partition and got the same message, /dev alreadymounted or busy.  Tried to unmount the partition from the mount point and the message said it was not mounted.  The second partition does show a UUID with sudo blkid but of course that does not show a mount point.   Creating a directory with the UUID from blkid in the /media directory doesn't work either.  Generally, a partition UUID will be in /media but it is not.  The second partition does also show with fdisk and lsblk but that doesn't help either.

If this is possible, I'm not sure what would be needed?

---

### Post by C.S.Cameron on 2016-08-09
If you just want to store stuff on the boot USB drive just stick it in a folder on the root of the drive.
When booting Ubuntu from the drive look in filesystem/cdrom for the storage folder.

If you plan on occasionally exchanging data with windows machines note that they only can see the first partition on a flash drive.

But I am not sure with 16.04.

---

### Post by yancek on 2016-08-09
> If you just want to store stuff on the boot USB drive just stick it in a folder on the root of the drive.
When booting Ubuntu from the drive look in filesystem/cdrom for the storage folder.

That won't work as it is a read-only filesystem.  You can copy/create all the folders/files you want and they will not be there on reboot whether it is in the root of the filesystem the /home directory or cdrom.

---

### Post by Geoffrey_Arndt on 2016-08-10
Well, one way to do what OP wants is to insert a standard **_SD photo card_** into an MMC slot, and save your data there on a fat32 (great for many small files.)     

IF, repeat, IF you also have a modern wireless printer (HP, Epson, Brother) . . most of those have MMC slots (ports) built in, and can save/access that data from the same PC via usb printer cable connection or wireless connection via Samba. 

But the safest and most EFFECTIVE way to do what OP wants is to do a FULL install to a USBv3 Flashstick, or even better, a portable SSD like the SanDisk Extreme 500.    Then, one has a fast and 100% maintainable portable OS.

---

### Post by mook765 on 2016-08-10
The problem is the ISO-format. Make a bootable stick on a VFat-partition on the stick and it will work...

---

### Post by oldrocker99 on 2016-08-10
I have never used the feature, but unetbootin does allow a save partition for Ubuntu only. Just format the USB as FAT first.

---

### Post by C.S.Cameron on 2016-08-10
> **yancek said:**
> That won't work as it is a read-only filesystem.  You can copy/create all the folders/files you want and they will not be there on reboot whether it is in the root of the filesystem the /home directory or cdrom.

With a grub2/iso install, computer/isodevice is working as a read/write folder for me.

I'm not sure what is happening with computer/cdrom, I've used it  for read write in the past but it don't seem to be working now.
Perhaps I was using a persistent drive?

---

### Post by yancek on 2016-08-11
My limited efforts to test what the OP posted he did brought the same results.  Unable to access and use a second partition on the flash drive while booted to the Live system on that  same flash drive, getting the same error messages he did.  That was using dd to write the iso to the flash.  Using another Linux with it's Live USB creator, I am able to create another partition on the flash from a different installed Linux and format it and am able to use it when booted to that same flash drive.  Since, as the OP stated he wanted - no persistence -, the flash does not have persistence.  This then requires creating a mount point each time I boot it and mount it.  Any files I create on it from the flash drive or copy to it from another system will be there.  The OP might have better results using the Ubuntu usb-creator software.  Using persistence or an actual install would simplify things but the OP states he does not want to do this and explains the reasons in his initial post.

---

### Post by C.S.Cameron on 2016-08-13
With a Startup Disk Creator or UNetbootin Live install, the read/write folder computer/cdrom is locked.

It is possible to unlock this folder in 32 bit Live systems by pressing F6 when booting and under boot options type <space> persistent.
The folder can be opened using gksu nautilus or sudo nautilus.
No casper-rw persistent file or partition is required. The folder will only be writable on sessions started this way.
The folder can be accessed when plugged into a Windows machine.

you can make the folder permanently writable by adding the word persistent to txt.cfg, text.cfg or for Unetbootin syslinux.cfg.
The folder can then be written to using gksu nautilus as above.

Note that with 32 bit no persistent file or partition is required so the drive is technically not persistent.
(I have not figured out how to do this with a 64 bit system where only persistent files work, not partitions).

As mentioned in previous post, with a Live grub2/iso install, (ie MultiBootUSB), computer/isodevice can be opened as a read/write folder using gksu nautilus, (or sudo nautilus).
This folder is also read/writable with Windows.

Note that only the first partition on a flash drive can be accessed from Windows.

---

### Post by sudodus on 2016-08-13
It is possible to make a persistent live drive with ***mkusb***, and use partition #1, an NTFS partition to save and transfer files. This partition is labeled **usbdata**.

Since you do not want persistence, you can remove the menuentry with persistence from **grub.cfg** and remove or re-label the **casper-rw** partition to turn off persistence, and you have a live-only pendrive with an NTFS partition, that works well in Windows as well as in Ubuntu based linux distros. See this link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

The boot method for a drive made this way is very similar to the grub and iso method described by *C.S.Cameron*, and the whole system is created automatically by mkusb. Removing persistence should be rather easy (and it helps if you are familiar with command lines in terminal windows).

---

### Post by C.S.Cameron on 2016-08-13
+1, I would surely recommend mkusb if the op does not mind removing persistence.
mkusb has quickly become my favorite boot drive maker and it works great with 16.04 32 or 64 bit.

---

### Post by Geoffrey_Arndt on 2016-08-13
So really, what's the downside to using persistence?   Slightly less space on the device (which is not going to be used anyway)?   I don't see a downside, perhaps someone can clarify.

---

### Post by yancek on 2016-08-13
> So really, what's the downside to using persistence? 

In this case, the OP says he doesn't want persistence for security reasons so changes cannot be make to the system but data can be added on another partition.  

He wants to be able to boot the flash drive with the Live system, create a mount point and manually mount it and not have it mounted or available automatically.    That can't be done with a flash drive created with dd as the OP has done, results of trying are posted above.

---

### Post by C.S.Cameron on 2016-08-14
I have just tried adding a second partition to flash drive installs of 16.04, both 32 bit and 64 bit.

I do not have a problem reading/writing to the partition with either using sudo nautilus.
No special mounting required.

---

### Post by mook765 on 2016-08-14
Maybe this link is helpful, take a look> [http://www.easy2boot.com/make-an-easy2boot-usb-drive/make-using-linux/](http://www.easy2boot.com/make-an-easy2boot-usb-drive/make-using-linux/)

---

### Post by yancek on 2016-08-14
> I do not have a problem reading/writing to the partition with either using sudo nautilus.

Did you write the Ubuntu iso file to the flash drive with dd as the OP did?
Are you then able to access the additional partitions on the flash drive while booted to the system on the flash drive?
This was the original question.   If this was an actual, full install to a flash drive, that would be expected behavior.

There is a lot of useful information in the posts in this thread but nothing to indicate what the OP tried/wanted to do will work.  A number of answers to a question that wasn't asked.
It would seem the OP has either given up or found another solution since he hasn't posted for days.

---

### Post by C.S.Cameron on 2016-08-14
I did not understand using dd was a requirement, I used UNetbootin.
Persistence was not turned on, there was no casper-rw file or partition, just a plain Live flash drive.
The partition is read/write when booted from the flash drive using sudo nautilus.

I think this is new in 16.04 for 64 bit.

---

### Post by yancek on 2016-08-15
The OP indicates in his initial post that he used dd to create the bootable flash.  He also indicates in post 7 that he does not want persistence nor does he want the partition to be auto-mounted or available on boot but rather wants to be able to manually mount the partition on the flash drive when he is booted to the system on the flash drive.

So the problem is that using dd to put the iso on the flash, does not allow him to access or mount it.
Installing Grub2 to the flash and putting the iso file on it and booting the iso file directly comes closer.  After creating a second partition for data storage it will be available but needs to be manually mounted.  This is basically what he wants, I think.  Maybe the Ubuntu usb-creator is similar, not sure.  Of course with this method, since it is basically a Live CD, the boot files can be modified by simply using sudo so that's a problem for his concern about security.  Remastersys on older Ubuntu version or Systemback might do what he wants.

I think the OP has given up or found a solution

---

