---
title: "Convert ext3 to ext4 because of Dropbox"
date: 2018-11-06
forum: New to Ubuntu
---

### Post by stevemid on 2018-11-06
I'm trying to comply with Dropbox's demand to sit on an ext4 partition.
My (dual boot)  system is set up Ubuntu /boot on the SSD and  /home on the HDD.

I've included screen prints of my existing partions.

Question 1.  Would it be possible to move my existing dropbox folder from /home to / (since / is already and ext4 partition)?

I tried this using the Dropbox facility to move the location of its folder and the app balked so I assume running things from the root directory is wrong.

Question 2.  Can I convert /dev/sdb1 from ext3 to ext4 following these instructions: [https://www.howtoforge.com/tutorial/migrate-ext2-ext3-filesystem-to-ext4/](https://www.howtoforge.com/tutorial/migrate-ext2-ext3-filesystem-to-ext4/)

I have a bootable copy of Ubuntu 16.04 on a usb stick.  Would it be OK to use this to do the conversion even though my system is at 18.04.1?

Any suggestions or alternate approaches would be appreciated.

Steve

---

### Post by Impavidus on 2018-11-07
You could probably move dropbox to your root partition, provided you give it a directory owned by you where you have read, write and execute rights, but I don't think that's a very clean solution and I don't know dropbox, so maybe it has a problem with that. And it's probably best to get your /home on ext4 anyway.

It's possible to convert ext3 to ext4. I'm somewhat suspicious about the guide you linked too, as it asks you to update grub using the **update grub** command, which doesn't exist – grub is normally updated with **update-grub**. It's a bit sloppy. I suggest you try this guide on the official Ubuntu help page, which doesn't even require you to use a live disk: [https://help.ubuntu.com/community/ConvertFilesystemToExt4](https://help.ubuntu.com/community/ConvertFilesystemToExt4)
As you don't want to convert the root partition, you can skip step 3.

There's also [this guide](https://ext4.wiki.kernel.org/index.php/UpgradeToExt4), linked from the other help page, explaining more or less the same.

A 16.04 live disk can be used to deal with 18.04, but it's recommended you've got a live disk of your currently installed Ubuntu, just in case. It's also recommended you've got backups of all your important files, just in case.

---

### Post by stevemid on 2018-11-07
I read both recommendations and surmised that I could take backups, upgrade my /home partition to ext4 and then restore the backups of /home
Obviously this was incorrect.
However, I made backups of /home 
I rebooted on to a live usb stick and ran gparted and made the changes I wanted to make:
  I shrunk the partition from 1.76 TB to 1.0TB (to create space for my windows 10 system)
  I re-formatted the ext3 partition to ext4 (I knew this would have destroyed the /home directory)
  I formatted the unallocated space to NTSB 

When I Rebooted.  The system would not boot.

I farted around with instructions here [https://www.maketecheasier.com/move-home-folder-ubuntu/](https://www.maketecheasier.com/move-home-folder-ubuntu/) for moving the /home folder to a new partition. I started from Migrating the /Home folder.
I think I made some mistakes because it seems not that fstab is pointing to a temproary Ubuntu folder created by the live usb instance.
Working on it.

---

### Post by Impavidus on 2018-11-08
A few possibilities:
- Did you update the /etc/fstab of the installed system (not the live system) to use ext4 instead of ext3?
- Did you update the /etc/fstab of the installed system to use the new UUID of your /home partition? You have to use the UUID, not the device. I already see that it was /dev/sdc1 before, and now it's /dev/sda1. Device names with multiple hard drives can change randomly.
- Is the mount point of the /home partition in the /etc/fstab of the installed system still set to /home?
- When making a backup, then restoring it, did you make sure all file ownership and permissions were retained? If you made the backup on an external NTFS formatted drive, they probably were not. It shouldn't be too hard to fix this manually, as we're just dealing with a /home partition. But if this is what went wrong, Ubuntu should still boot, just login should fail.

It shouldn't be too hard to fix this from a live system. If in doubt, post the contents of the /etc/fstab of your installed system. Also show the output of```
sudo blkid
sudo parted -l
```

---

### Post by stevemid on 2018-11-08
Thanks so much for your help.  If you like, and if it will be easier, I have downloaded a fresh iso image, so we could go that way if this takes up too much of your time.  But here is the information you asked for.  The answers to your other questions are at the end.
===========================================
The contents of fstab from the installed system:
ubuntu@ubuntu:~$ sudo cat '/media/ubuntu/49bc44d4-f8ae-493b-9186-3a04051217e1/etc/fstab' 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=49bc44d4-f8ae-493b-9186-3a04051217e1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
#UUID=26D7-AB37  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb7 during installation
UUID=3a621817-23be-4f85-ade7-8913593f927c none            swap    sw              0       0
UUID=a32cd6cb-5e06-4430-98f6-35841aa87e1f /home	ext4 defaults 0 2
UUID=26D7-AB37	/boot/efi	vfat	defaults	0	1
ubuntu@ubuntu:~$ 
===========================================
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="a32cd6cb-5e06-4430-98f6-35841aa87e1f" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="cc7e6ea1-da09-407c-9d91-fb2d47aa4669"
/dev/sda2: LABEL="Recover" UUID="CC705003704FF32E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="33538074-de5b-47a4-99ef-217f6153c63d"
/dev/sda3: UUID="11AB90EE220C19F5" TYPE="ntfs" PARTUUID="0f2613f2-a74e-418a-a166-f78d902bcc77"
/dev/sdb1: UUID="26D7-AB37" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="30404f2e-e518-4e19-82bb-5e549acca117"
/dev/sdb3: LABEL="Boot" UUID="0C3CD6DC3CD6BFBE" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1d5fb9ce-89cd-4161-861d-d1a26392b25b"
/dev/sdb4: UUID="C892ABDF92ABCFEC" TYPE="ntfs" PARTUUID="0cea787d-7f6d-4b3d-8936-14fbf4b36470"
/dev/sdb5: UUID="49bc44d4-f8ae-493b-9186-3a04051217e1" TYPE="ext4" PARTUUID="2ece0995-5ed0-4e65-be73-0b6d4750fe5e"
/dev/sdb7: LABEL="PRC_RP" UUID="2E61-13ED" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="4e4988a5-5fcd-42b7-ad3f-f04e940c3dc8"
/dev/sdc1: LABEL="Seagate Backup Plus Drive" UUID="A470179770176EF4" TYPE="ntfs" PARTUUID="9a8fe83a-01"
/dev/sdd1: LABEL="UBUNTU 16_0" UUID="E0B2-F7B9" TYPE="vfat" PARTUUID="005c81e2-01"
/dev/loop0: TYPE="squashfs"
/dev/sdb2: PARTLABEL="Microsoft reserved partition" PARTUUID="c1113f05-7e16-406b-8aef-c32f2af734bb"
/dev/sdb6: UUID="3a621817-23be-4f85-ade7-8913593f927c" TYPE="swap" PARTUUID="b9f0dadb-5140-491b-b7cb-446abbadee8e"
ubuntu@ubuntu:~$
===========================================

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  1061GB  1061GB  ext4         Basic data partition  msftdata
 3      1061GB  1936GB  875GB   ntfs                               msftdata
 2      1936GB  2000GB  64.4GB  ntfs         Basic data partition  msftdata


Model: ATA SAMSUNG MZNLF128 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  106MB   105MB   fat32           EFI system partition          boot, esp
 2      106MB   123MB   16.8MB                  Microsoft reserved partition  msftres
 3      123MB   78.2GB  78.0GB  ntfs            Basic data partition          msftdata
 4      78.2GB  79.1GB  900MB   ntfs                                          hidden, diag
 5      79.1GB  118GB   38.9GB  ext4
 6      118GB   126GB   8502MB  linux-swap(v1)
 7      127GB   128GB   1074MB  fat32           Basic data partition          hidden


Model: Seagate Backup+ Desk (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      8389kB  2000GB  2000GB  primary  ntfs         boot


Model: Lexar JD FireFly (scsi)
Disk /dev/sdd: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4010MB  4009MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ 
===========================================
 Q: Did you update the /etc/fstab of the installed system (not the live system) to use ext4 instead of ext3?
A: Yes.  I changed the UUID entry in the installed system to reflect the partition that formerly was ext3 and held /home to ext 4

Q:Is the mount point of the /home partition in the /etc/fstab of the installed system still set to /home?
A: It is by looking at the fstab (in the line I mentioned above) of the installed system, yes /home is there.  [COLOR="#FF0000"]HOWEVER looking at that partition in Gparted, right now  there is NO mount point listed for that partition (/dev/sda1).  Looking at the Gparted screen prints attached earlier to this thread, pre upgrade, the partition was then called /dev/sb1 and it did show a mount point of /home. [/COLOR] I will attach that image later, I don't seem to be able to save screen prints from this live usb session.

Q:- When making a backup, then restoring it, did you make sure all file ownership and permissions were retained? 
A: I believe I accepted the Grsync defaults I'm not sure as I can no longer get to the app on the installed system.  However, of the two backups, one is to an NTFS drive, the other to a FAT 32 drive.

Thanks again for your help and,
Kind regards,
Steve

---

### Post by Impavidus on 2018-11-09
All seems OK. Ubuntu should mount that /home partition during boot.
> **stevemid said:**
> 
A: It is by looking at the fstab (in the line I mentioned above) of the installed system, yes /home is there.  [COLOR=#FF0000]HOWEVER looking at that partition in Gparted, right now  there is NO mount point listed for that partition (/dev/sda1).  Looking at the Gparted screen prints attached earlier to this thread, pre upgrade, the partition was then called /dev/sb1 and it did show a mount point of /home. [/COLOR] I will attach that image later, I don't seem to be able to save screen prints from this live usb session.When using a live disk, the partition will not be mounted, so no mountpoint will be shown, unless you mount is yourself. So this is normal.

> A: I believe I accepted the Grsync defaults I'm not sure as I can no longer get to the app on the installed system.  However, of the two backups, one is to an NTFS drive, the other to a FAT 32 drive.
FAT32 and NTFS don't support UNIX permissions, so the permissions on your /home partition are probably messed up. Check that. If they are indeed messed up, you can go to where you find your home directory in the live session. That should be, assuming your username is foo, something like```
cd /media/ubuntu/a32cd6cb-5e06-4430-98f6-35841aa87e1f/foo
```Then make your home directory owned by your user and group. Assuming you are the first (or only) ordinary user of your system, that's```
sudo chown -R 1000:1000 .
```Maybe you had a few files with different owner/group. You can fix those later. If there are other users on the system, you can fix them later.

Then set the right permissions on the directories:```
sudo find -type d -exec chmod 0750 {} \;
```That should give all directories permissions 0750. This may not always be what you want, but it's close enough to the defaults that it should work for a home directory.

Then set the right permissions on the ordinary files:```
sudo find -type f -exec chmod 0640 {} \;
```Permissions 0640 should be good enough for most files. If you had any executables in your home directory, you'll have to fix them later.

---

### Post by stevemid on 2018-11-10
Thank you for your response.  I just want to clarify that...My system will not boot. You remembered that?  

So I booted from the liveusb and executed the following as you prescribed:
ubuntu@ubuntu:/media/ubuntu/a32cd6cb-5e06-4430-98f6-35841aa87e1f/home/medion$ sudo chown -R 1000:1000 .
ubuntu@ubuntu:/media/ubuntu/a32cd6cb-5e06-4430-98f6-35841aa87e1f/home/medion$ sudo find -type d -exec chmod 0750 {} \;
ubuntu@ubuntu:/media/ubuntu/a32cd6cb-5e06-4430-98f6-35841aa87e1f/home/medion$ sudo find -type f -exec chmod 0640 {} \;
ubuntu@ubuntu:/media/ubuntu/a32cd6cb-5e06-4430-98f6-35841aa87e1f/home/medion$ ^C
ubuntu@ubuntu:/media/ubuntu/a32cd6cb-5e06-4430-98f6-35841aa87e1f/home/medion$

I then attempted to boot into my normal system.

I get as far as the login screen (see attached) If I enter the correct password, it returns to the log-in screen. If I enter the wrong password it gives me an error.
At the Grub stage, I can go in to recovery mode and drop into terminal mode.  I've also attached a picture of that.  You'll notice that I have two "home" folders.  Possibly that's part of my boot problem?

Again, thank you for staying with me on this

---

### Post by Impavidus on 2018-11-10
To be pedantic, you don't have a boot problem, you have a login problem. The computer boots, it reaches the login screen, but login fails as the user's home directory is not where the system expects it to be. And thanks for that last screenshot; it explains everything (almost).

So you backed up the entire /home directory, then restored it into the /home directory, so you got a /home/home directory. That can be fixed. At least the ownership and permissions issue for medion seems to be fixed now. It has normal colours in your screenshot, whilst anon and lost+found have a greenish background, which means they are world-writable, which is wrong.

Boot into recovery mode, just as you did in your last screenshot. Make sure the home partition is mounted in read-write mode. Use```
mount -a
```if necessary. Go to the /home/home directory, then move the medion directory one level down. Fix ownership and permissions for user anon and move it one level down too, then fix lost+found and move it down while renaming it, to prevent a name collision with the existing lost+found directory. Then delete /home/home.```
cd /home/home
mv medion/ ..
chown -R anon:anon anon
find anon -type d -exec chmod 0750 {} \;
find anon -type f -exec chmod 0640 {} \;
mv anon/ ..
chown -R root:root lost+found
mv lost+found/ ../lost+found2
cd ..
rmdir home
```
With a bit of luck, now both users can log in.

You'll then have two lost+found directories. lost+found is used to store bits of files recovered during file system checks. They are probably empty. Have a look what's inside. If there's nothing in that you want to keep, you can delete /home/lost+found2. Any executable files you keep in /home/medion or /home/anon have to be fixed by giving them execute permissions.

There's also a home directory for user ubuntu (/home/ubuntu), who according to the login screen doesn't exist. It's your username in a live session. I don't know where that directory came from. Try renaming it. If that causes a problem, restore it. If no problem, recover any files you want to keep and delete the directory.

---

### Post by stevemid on 2018-11-10
It&#8217;s not pedantic at all.

That worked.  I'm now logged on.

Thank you so much; you've been very generous with your time.

I do not have permission to cd into /home/lost+found but let me educate myself a bit about file permissions etc, before asking you to take more of your time.
drwxr-x--- 14 anon         anon          4096 Oct 10  2016 anon
drwx------  3 root         root         16384 Nov 11 05:54 lost+found
drwxr-x--- 38 medion       medion       12288 Nov 11 07:30 medion
drwxr-xr-x 17 guest-phfgbe guest-phfgbe  4096 Nov  8 16:02 ubuntu

Once I have a better understanding and if I can't follow your last instructions, I'll come back to you then.

Thanks again for your support.
Steve

---

### Post by stevemid on 2018-11-10
Attached is a screen print of my Grsync settings. I notice that preserve owner is not ticked.  Should that be ticked?  I guess the real issue for me was that I was backing up to partitions that couldn't preserve Unix permissions anyway.  So I plan to reformat first one then the other of my backup media to ext4.  

I've spent the past few hours reading about file permissions. It's really pretty confusing.  I'm the only user on this system.  Could you please help me find and change permissions on any executable files.  I only backed up and deleted, then restored /home

---

### Post by stevemid on 2018-11-10
Hold that.  Pictures are there.  There must just have a delay reading the folder contents.

---

### Post by Impavidus on 2018-11-11
You indeed have no permissions to cd into lost+found. Only root has permissions to do anything in lost+found. This makes sense. That directory can contain any stuff recovered during file system checks. As these files may come from any user and may have had any permissions, and being recovered by a file system check should never allow anyone to read a file that they couldn't read before the file system was damaged, nobody should have access to these files except the root user. To see what's inside, use sudo:```
sudo ls /home/lost+found
# Or if you want a shell to look around:
sudo -i
cd /home/lost+found
# Do some stuff
exit
```
To make a proper backup with rsync (or its GUI version grsync), you have to preserve everything: owner, group, permissions, time. You can only preserve the owner when you run rsync as root. But it won't work when copying to a non-Linux filesystem. And before you convert all your backup drives to ext4, keep in mind that Windows can't handle Linux filesystems. So keep one backup partition as NTFS, so you can use it from Windows.

You only have to fix permissions on your executable files in /home if you had any. By default there are no executable files in /home, so there can only be some if you put them there yourself.

You may be the only human who uses your computer, but according to the login screen, there is a second user, named Anon. There are also separate users for background processes. These background processes have their own user so they can run with very specific permissions, which is just another layer of security.

---

### Post by stevemid on 2018-11-12
OK all done.  The two "executables" if they can be called that, that I lost were my Firefox profile and the Dropbox daemon.  I just downloaded and reinstalled those two apps and all is good. 

Thanks again.  Let me know if I have to do anything to "close" this issue.  Thanks very much for your help.

---

### Post by Impavidus on 2018-11-13
You can mark this thread as solved. Click on thread tools (above the first post of the page) &#8594; mark as solved.

---

