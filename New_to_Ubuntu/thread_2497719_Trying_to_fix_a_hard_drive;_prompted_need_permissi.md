---
title: "Trying to fix a hard drive; prompted need permissions..."
date: 2024-05-15
forum: New to Ubuntu
---

### Post by Innernet on 2024-05-15
Good day.
An external hard drive pluggable to USB for my laptop used only when needed to backup about once a year _without any operative system_; none, non bootable,  and used for a decade as backup for everything is probably corrupted from a clumsy powering off. It is a Seagate Barracuda 7200.7 - 200GByte capacity.

Following web instructions to diagnose / repair; get prompted that I need permissions.
There is nobody else using my laptop, I am the owner, I am the only operator.
Reading about the subject, saw some 'file' permissions.  I want permission granted **for everything**, drives and all their contents not only files, everywhere to attempt repairing and if successful, create a second backup copy for insurance.

Tried following instructions to obtain full permissions and unable to achieve it.  Any idiotproof guidance, please ?

---

### Post by grahammechanical on 2024-05-15
It would be nice to know what version of Ubuntu you are using and what version of Ubuntu you were using when you used this drive as a backup?

Does the Disks utility see this drive and show the partition layout? Does the File Manager see this drive and show folders in the partitions? Use File Manager>Permissions to see what the partitions are on the drive and its folders.

You may need to do some work a root/administrator to change the permissions to allow you to read and write to the drive and its folders and the files in each folder.

What is it you want to do to "fix" this drive? Copy data off of it and then reformat the drive?

Regards

---

### Post by yancek on 2024-05-15
> There is nobody else using my laptop, I am the owner, I am the only operator.
  

You are missing a very basic concept of Linux which is that it is a multi-user system by design and Ubuntu and almost all other Linux systems have at least one regular user plus the 
root user.  In Ubuntu, root privileges are gained by using sudo.  

You haven't indicated if this drive was used with a Linux system, a windows system or a Mac or any combination.  What filesystem is on it?  Have you tried doing a filesystem check? 

>    I want permission granted **for everything**, 

No, that will likely destroy the system as there are many files which need root owner and permissions.  Personal data is another thing.

Since you haven't posted a link to any site which gave instructions you followed, there is no way for us to know.  A bad shutdown will often lead to a corrupt filesystem and if it is Linux, then run some variation with option of the fsck command should help.  There are literally thousand of sites explaining fsck and its use and yes, you will need sudo to use it.

---

### Post by Innernet on 2024-05-15
Thank you.
This ill external hard drive has been used only as data backup for over 10 years and only with Ubuntu.  Now with 22.04. One single partition.   Shows below by the terminal text as sdb1 ???
The disks utility where that chinese name may had been an early use of a thumb drive.  Do not know why shows here as is not plugged in now.

[ATTACH=CONFIG]293777[/ATTACH]


The terminal shows :
(image attached)

and the instructions I tried to follow say :

================================================================

How to troubleshoot Seagate Barracuda 7200.7 hard drive issues under Linux?
To diagnose a Seagate Barracuda 7200.7 with Linux, you can follow these steps:

Step 1: Identify the drive

Use the lsblk command to list all the block devices on your system, including the Seagate Barracuda 7200.7. This will help you identify the device name, such as /dev/sdb or /dev/sdc.

Step 2: Check the drive’s health

Use the smartctl command to check the drive’s health. This command will provide information about the drive’s temperature, health, and any errors that have occurred.

smartctl -a /dev/sdb
Step 3: Check the drive’s partitions

Use the fdisk command to check the drive’s partitions. This will help you identify if the drive is partitioned correctly and if there are any issues with the partition table.

fdisk -l /dev/sdb
Step 4: Check the drive’s file system

Use the fsck command to check the file system on the drive. This will help you identify if there are any issues with the file system, such as corruption or errors.

fsck -f /dev/sdb1
Step 5: Check the drive’s disk usage

Use the df command to check the drive’s disk usage. This will help you identify if the drive is full or if there are any issues with disk space.

df -h /dev/sdb1
Step 6: Check for firmware updates

Check the Seagate website for firmware updates for your specific drive model. If there are updates available, follow the instructions to update the firmware.

Step 7: Run a disk scan

Use the badblocks command to run a disk scan on the drive. This will help you identify if there are any bad sectors or errors on the drive.

badblocks -v /dev/sdb
Step 8: Check the drive’s SATA settings

Check the SATA settings in your BIOS or UEFI firmware to ensure that the drive is set to use the correct mode (AHCI or Legacy). Some users have reported issues with the drive not being recognized when set to AHCI mode.

By following these steps, you should be able to diagnose any issues with your Seagate Barracuda 7200.7 drive using Linux.

==================================================================

The terminal text copied and pasted is :

externet@externet-ThinkPad-T430s:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0    7:0    0     4K  1 loop /snap/bare/5
loop1    7:1    0 169.3M  1 loop /snap/brave/393
loop2    7:2    0 169.3M  1 loop /snap/brave/402
loop3    7:3    0  63.9M  1 loop /snap/core20/2182
loop4    7:4    0  63.9M  1 loop /snap/core20/2264
loop5    7:5    0  74.2M  1 loop /snap/core22/1122
loop6    7:6    0  74.2M  1 loop /snap/core22/1380
loop7    7:7    0  66.1M  1 loop /snap/cups/1044
loop8    7:8    0  66.1M  1 loop /snap/cups/1047
loop9    7:9    0 268.2M  1 loop /snap/firefox/4033
loop10   7:10   0 268.3M  1 loop /snap/firefox/4090
loop11   7:11   0   7.4M  1 loop /snap/gedit/684
loop12   7:12   0 349.7M  1 loop /snap/gnome-3-38-2004/143
loop13   7:13   0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop14   7:14   0 504.2M  1 loop /snap/gnome-42-2204/172
loop15   7:15   0 505.1M  1 loop /snap/gnome-42-2204/176
loop16   7:16   0  81.3M  1 loop /snap/gtk-common-themes/1534
loop17   7:17   0  91.7M  1 loop /snap/gtk-common-themes/1535
loop18   7:18   0 112.9M  1 loop /snap/simplenote/620
loop19   7:19   0 112.9M  1 loop /snap/simplenote/621
loop20   7:20   0  12.9M  1 loop /snap/snap-store/1113
loop21   7:21   0  12.3M  1 loop /snap/snap-store/959
loop22   7:22   0  38.7M  1 loop /snap/snapd/21465
loop23   7:23   0  39.1M  1 loop /snap/snapd/21184
loop24   7:24   0   476K  1 loop /snap/snapd-desktop-integration/157
loop25   7:25   0   452K  1 loop /snap/snapd-desktop-integration/83
loop26   7:26   0  90.8M  1 loop /snap/whatsapp-for-linux/58
loop27   7:27   0  90.8M  1 loop /snap/whatsapp-for-linux/59
sda      8:0    0  29.8G  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9500;&#9472;sda2   8:2    0   513M  0 part /boot/efi
&#9492;&#9472;sda3   8:3    0  29.3G  0 part /var/snap/firefox/common/host-hunspell
                                 /
sdb      8:16   0 186.3G  0 disk 
&#9492;&#9472;sdb1   8:17   0 186.3G  0 part 
sr0     11:0    1  1024M  0 rom  
externet@externet-ThinkPad-T430s:~$ smartctl -a /dev/sdb
Command 'smartctl' not found, but can be installed with:
sudo apt install smartmontools
externet@externet-ThinkPad-T430s:~$ sudo apt install smartmontools
[sudo] password for externet: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2 libllvm13
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  gsmartcontrol smart-notifier mailx | mailutils
The following NEW packages will be installed:
  smartmontools
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 583 kB of archives.
After this operation, 1,980 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 smartmontools amd64 7.2-1ubuntu0.1 [583 kB]
Fetched 583 kB in 0s (1,172 kB/s)     
Selecting previously unselected package smartmontools.
(Reading database ... 204782 files and directories currently installed.)
Preparing to unpack .../smartmontools_7.2-1ubuntu0.1_amd64.deb ...
Unpacking smartmontools (7.2-1ubuntu0.1) ...
Setting up smartmontools (7.2-1ubuntu0.1) ...
Created symlink /etc/systemd/system/smartd.service &#8594; /lib/systemd/system/smartmo
ntools.service.
Created symlink /etc/systemd/system/multi-user.target.wants/smartmontools.servic
e &#8594; /lib/systemd/system/smartmontools.service.
Processing triggers for man-db (2.10.2-1) ...
externet@externet-ThinkPad-T430s:~$ smartctl -a /dev/sdb
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-6.5.0-35-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Smartctl open device: /dev/sdb [USB Sunplus] failed: Permission denied
externet@externet-ThinkPad-T430s:~$ fsck -f /dev/sdb1
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext2: Permission denied while trying to open /dev/sdb1
You must have r/w access to the filesystem or be root
externet@externet-ThinkPad-T430s:~$ badblocks -v /dev/sdb
badblocks: Permission denied while trying to determine device size
externet@externet-ThinkPad-T430s:~$ sudo chmod -R 755 /media/ExternalDrive
chmod: cannot access '/media/ExternalDrive': No such file or directory
externet@externet-ThinkPad-T430s:~$ sudo chown $USER /media/ExternalDriveName
chown: cannot access '/media/ExternalDriveName': No such file or directory
externet@externet-ThinkPad-T430s:~$ 

================================================================
[ATTACH=CONFIG]293778[/ATTACH]

---

### Post by ubfan1 on 2024-05-15
Use sudo on those commands needing permissions: e.g. sudo smartctl -a /dev/sdb
Most system changes require root permission which is available through sudo for the default user created at installation.

---

### Post by Innernet on 2024-05-15
Took almost 2 hours :

======================================================

externet@externet-ThinkPad-T430s:~$ sudo  badblocks -v /dev/sdb
[sudo] password for externet: 
Checking blocks 0 to 195360983
Checking for bad blocks (read-only test): 10104040
10104041
10104042
10104043
27876832
27876833
27876834
27876835
done                                                 
Pass completed, 8 bad blocks found. (8/0/0 errors)
externet@externet-ThinkPad-T430s:~$ 

===================================================

What is the next action to repair, or lock them out, or ?

---

### Post by ubfan1 on 2024-05-15
See [https://askubuntu.com/questions/857936/how-to-read-the-current-bad-blocks-list-for-the-disk](https://askubuntu.com/questions/857936/how-to-read-the-current-bad-blocks-list-for-the-disk)  Check the sudo smartctl -a /dev/sdb for reallocated sectors.  I suppose you could remake the filesystem and give it the bad block list to skip, then restore from backups.  Probably would then need to check places using the UUIDs for mounts (/etc/fstab, /boot/efi/EFI/ubuntu/grub.cfg,....). Also see [https://askubuntu.com/questions/857936/how-to-read-the-current-bad-blocks-list-for-the-disk](https://askubuntu.com/questions/857936/how-to-read-the-current-bad-blocks-list-for-the-disk)   The e2fsck -fccky /dev/sdbx  seems a promising way to add bad blocks to an existing bad block list.

---

### Post by yancek on 2024-05-16
>  sudo chmod -R 755 /media/ExternalDrive 

The above command gave you a message of 'no such file or directory'.  Were you using an example from some web site?  You need to use the actual mount point so in the case above, there would need to be a directory named 'ExternalDrive' in your /media directory.

You also need to use sudo for many commands, in particular running fsck or it won't run as you see in your message.  Your other tools report there are bad blocks.

---

### Post by Innernet on 2024-05-16
Thanks 
ubfan1 
Maybe too much for my poor skills.  Seems both of your links are the same.  And they are around formatting or after formatted.  
I prefer not to format and lose everything; but attempt something to gain access to the vast majority of not bad blocks to recover at least the data in those good blocks.  The hard drive itself is not worth half a penny to me; I have a dozen of other drives to take its place.  The thing is accessing the not corrupted data, fixing, recovering it.  

Twenty years ago; at work I used often a program "Spinrite" very capable of fixing/recovering drives but worked on DOS.  I have an old version of it but no brain to put it to use on Ubuntu.  Is there something similar now ?


yancek.  Yes, now I realize i wrongly used an example from some site, and explains how dumb am I.   But do not know what mount point or how to enter or manage commands if that is the path to recover the data for this hard drive that does not show to be active.   I do not even know what is a mount point. :(   When I click 'mount' for the sick drive does some clicking and nothing else.

---

### Post by harald-prasse on 2024-05-16
Hi innernet,
you might want to look through this post: [https://askubuntu.com/questions/865834/formatted-drive-recovery](https://askubuntu.com/questions/865834/formatted-drive-recovery)
I used the "Photorec" part myself and it worked like a charme. Lost the filenames but most of the data was back. Good luck

---

### Post by ubfan1 on 2024-05-16
Sorry about the dup link. the other link is [https://askubuntu.com/questions/1278032/fixing-bad-sectors-of-a-hard-drive](https://askubuntu.com/questions/1278032/fixing-bad-sectors-of-a-hard-drive)  and the accepted answer has the recommended non-destructive command to add bad blocks to the existing bad block list: sudo e2fsck -fccky /dev/sda2 (for example checking sda2). Read the man page for e2fsck to see what the -fccky does, or see the explanation in the accept answer.

---

### Post by yancek on 2024-05-16
> Yes, now I realize i wrongly used an example from some site, and explains how dumb am I.    

Doesn't have anything to do with intelligence, just a lack of knowledge on a particular subject.  We're all ignorant about some things.

Mounting basically means to make accessible and there are many sites with detailed explanations of it such as the one at the link below.  A mount point is a directory and you mount to make a particular device available to view and interact with.

 [https://linuxize.com/post/how-to-mount-and-unmount-file-systems-in-linux/](https://linuxize.com/post/how-to-mount-and-unmount-file-systems-in-linux/)

If the link below isn't satisfactory, just do an online search on how to create a mount point and mount a partition.  You can use sudo fdisk -l to list devices/partitions or blkid or lsblk commands to know which device partition to mount.

Another site below.

[https://superuser.com/questions/134734/how-to-mount-a-drive-from-terminal-in-ubuntu](https://superuser.com/questions/134734/how-to-mount-a-drive-from-terminal-in-ubuntu)

---

### Post by TheFu on 2024-05-16
Typically, HDDs are like car tires.  10 yrs is beyond the expected lifespan and with things start failing, it is time to replace the HDD.  10 yr old car tires and the rubber has already started breaking down, even if there is tread life remaining.  It becomes a safety issue both for your data and the vehicle.

When blocks start going bad, they tend to start going bad more and more and more and in a few weeks, you'll find that the drive won't be seen by the OS or the BIOS and all that data in gone.   Best to move off the failing device in advance, then use it only for unimportant things, perhaps a 2nd backup or for a sneaker*net need.

---

### Post by Innernet on 2024-05-18
Thanks, TheFu.
This HDD has been used about 100 hours in its entire existance of ~12 years..  Been off, living in a drawer and used few minutes per year backing-up. The problem occurred when power was turned off at a wrong moment.

What did I do wrong this time ?  If supposed to repair with the -n and -s ; why does not report such at the end of 10 hours ?  Or where they fixed by executing the command  but better not tell the user ?  When are 'blocks'  the same as 'sectors', or when to use each term ?

[ATTACH=CONFIG]293786[/ATTACH]

---

### Post by yancek on 2024-05-18
>  This HDD has been used about 100 hours in its entire existance of ~12  years..  Been off, living in a drawer and used few minutes per year  backing-up. 

Doesn't matter really.  The best environment for computer hardware is a dry, cool well ventilated location but your problem is likely a result of the power loss while it was in use.  Did you also try to run any fsck variation on the filesystem?  None of this software will actually 'repair' the hardware but the blocks are 'marked' so the system does not try to use them.

I can't answer your last question as I've never used that particularl software.

---

### Post by TheFu on 2024-05-18
As I said, time of use doesn't matter.  Date from manufacture does.  

To know about the health of a HDD, use SMART data.  **smartctl** is the tool for that.   SMART data is only helpful about 78% of the time according to massive and long term data by vendors that use 10s of thousands of HDDs.  That means 12% of the time, a HDD will fail without any known reason.

I've found zero use for badblocks since the 1990s.

---

### Post by MAFoElffen on 2024-05-18
+1 with TheFu.

The original Warranty of that HDD drive was 3 years. The life expectancy when they came out was 5-7 years. before 2008, Seagate had them warrantied for 5 years, but it was found that many didn't live that long, so changed the warranty from 5 to 3 years. (Expected life-span of SDD and NVMe is now 10 years.)

That drive is 12+ years old. It is starting to get bad sectors. When a drive starts to fail, it's like a cascading effect. Be prepared for more sectors to fail.

Storage prices have fallen sharply since that drive came out. You can now buy a drive 10x the size for less than half the price. You can buy an SSD 10x the size for less than you paid for that 12 years ago...

Being cost-worthy is one thing. Being realistic on a cost-benefit is another thing when it is storing backups... Those are important for the what-if's. TheFu and I push Users to do backups. I, and I think TheFu would agree, [COLOR=#ff0000]***I applaud that you "do" backups, and feel they are important.***[/COLOR] That is a big thing. That is what saves us when the unexpected happens. If your computer's main drive(s) had this problem, you could replace your drive, and restore things from your backups...

If you have a sentimental attachment to something like that, put it in a frame... but it's useful life has it's day's numbered. And it has started telling you that the end is near. 'Lucky' about that. Some drives give no warning before failure. Count your blessings.

---

### Post by Innernet on 2024-05-18
> **TheFu said:**
>  ... To know about the health of a HDD, use SMART data.  **smartclt** is the tool for that...

Come on, TheFu... you are waaaaay better helping than sending me chasing for smartclt !  Is it smartctl instead ?  ](*,)  Any extensions to the command ?  
"To know the health of a HDD..." 
Corruption of (8) sectors, blocks or clusters or ? is known, listed, confirmed and identified.  What am after is allowing the drive to mount to extract the not-corrupted data.

Checked with -i and my ill hard drive **has** the smart feature _available and enabled_.

---

### Post by TheFu on 2024-05-18
I saw a quality 1TB SSD for $40 last week.  It will last longer and be at least 5x faster.  

Just get one with a SATA connector - in Samsung SSDs, the models that begin with an "8xx" are SATA.  I have an 860 in an old laptop with a 2.5inch form-factor. It looks like a laptop HDD.   NVMe drives which use m.2 interfaces and directly connect to the PCIe bus in newer computers cost about the same as the SATA SSDs now and are 10x faster than the SATA SSDs.  All of them have 5+ yr warranties and are expected to last over 10 yrs, if they make it past the first 30-60 days. Early failures still happen.   Some of the SSDs will use the SATA protocol, but also have an m.2 connection, so be very clear what your system needs.  

There are external SSD-to-USB3 enclosures for $10-$30 too.  I have a m.2 + SATA SSD in one of those cheap enclosures that gets used for Sneaker*Net needs.  The SSD spent 3 yrs inside a server before I moved it to the external enclosure.  Enclosures for both m.2 SATA and m.2 NVMe SSDs are available.   If all you need is a few hundred GB for backup, there's little reason to go with a spinning HDD.  For spinning HDDs, anything smaller than 2-4TB just isn't cost effective.  For SSDs, anything larger than 1TB starts becoming too expensive.  

For my backups, I use 4TB and 8TB HDDs.  I keep all backup "spaces" below 4TB as a standard.  For reference:
```
Type  Size  Used Avail Use% Mounted on
ext4  3.5T  3.5T   21G 100% /d/D1
ext4  3.6T  3.6T  5.2G 100% /d/D2
ext4  3.6T  3.6T   33G 100% /d/D3
ext4  3.6T  3.3T  164G  96% /d/D6
ext4  3.6T  1.4T  2.1T  40% /d/D7
ext4  3.6T  3.5T  131G  97% /d/b-D1
ext4  3.6T  3.6T  9.1G 100% /d/b-D2
ext4  3.6T  3.6T   38G  99% /d/b-D3
ext4  3.6T  3.3T  156G  96% /d/b-D6
ext4  3.4T  1.4T  1.9T  43% /d/b-D7

```
I follow the K.I.S.S. principle.  [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle) . You can guess which are primary and which are backup storage mounts, right?
No need to make backups THAT hard for data that seldom changes.  Of course, for documents and things that do change often (more than once every 2+ yrs), I use a real backup tool that has versioning.

---

