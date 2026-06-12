---
title: "Error mounting /dev/sda3"
date: 2015-11-16
forum: New to Ubuntu
---

### Post by Rebelde on 2015-11-16
Hi, I have problems accesing my ubuntu partition containing a second Ubuntu OS (Studio) which I was only using as storage of photos, videos and sound files. For whatever reason the partition become inaccessible and I am now stuck trying to fix my situation, Any help will be appreciated. 

The whole error message reads: 

Unable to access "127GB Volume"

Error mounting /dev/sda3 at /media/orlando/2a4e9941-4ce9-4ea0-b836-6ec5a46f042f: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda3" "/media/orlando/2a4e9941-4ce9-4ea0-b836-6ec5a46f042f"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by oldfred on 2015-11-16
May just need fsck. But it may be a permissions issue.

If booted in separate install, so that partition is not mounted you do not need live installer. Just be sure it is not mounted.
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Often if dual booting better to use a shared data partition and mount the folders in each install using links.
      
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by Rebelde on 2015-11-17
Hi oldfred, thanks for the reply! Unfortunately I am not an expert on UBUNTU... in spite of my years using it! I am starting to read all the information you've mentioned. However, I have to say that my computer had the dual boot Ubuntu/Studio which were normally running until a couple of weeks ago. I remember the only suspicious event was to remove an external USB-HD after a while... I removed it using the usual way (unmount safely remove) but when I turned the computer off some errors messages appeared... As I said I am not the best UBUNTU practitioner around so I will need possibly a lot of help. Thanks!

---

### Post by oldfred on 2015-11-17
Did you run the fsck commands I posted, but example was for a first partition on a second drive, you have to use your partition(s).

---

### Post by Rebelde on 2015-11-17
I did not run the commands as I prefer to be careful and understand a bit what and why I am doing something... Sorry, nothing to do with trust here but with better understanding and learning for myself :o)

I am using only one disk with two main partitions. I am not sure how to determine it is the first or second. If I run the Gparted I can see my functional partition is in third place (after the swap and inaccessible partition with Ubuntu Studio). There is a message I just notice... quite long, but in the end the following message:


<i>Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.</i>

---

### Post by oldfred on 2015-11-17
See man fsck or man e2fsck.
Same as chkdsk is in Windows. It checks for file corruption and tries to repair it.

---

### Post by Rebelde on 2015-11-27
Thanks a lot olfred! Please don't give up on me! I am currently quite busy and did not have the chance to start exploring the solutions you proposed for my hard disk. I need a couple of weeks more to fix my situation and will definitely be back to continue to find a solution to my problem. Thanks again for the support!

---

### Post by Rebelde on 2015-11-28
Okay, here is the thing. I tried "fsck" directly and received a warning signal ensuring me that IF I continue my system "WILL BE DAMAGED SEVERELY" and of course I decided to abort. How can I check the error and repair the partition I have and I cannot access as I use to before without risking my functional partition? It seems I don't have the inaccessible partition as mounted... Plus, it seems I need to specify which partition. Although I have read a the description of this "fsck" command I am not completely sure whether I can operate it without compromising my system... Any help will be appreciated, and remember I am not an expert in UBUNTU (although I would very much like to say the contrary!).

---

### Post by oldfred on 2015-11-28
Are you running it from a live installer as posted. You can damage a system if it is not unmounted.
And are you running on the correct partition that is Linux ext formatted?
to see partitions and which you should run e2fsck on:
sudo parted -l

I just ran it on one of my sdb drive's partition which I know are not mounted normally. And it did not give any messages, just ran.

---

### Post by Rebelde on 2015-11-29
This is the message I got after running "sudo parted -l":

Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?

I have also read the info for "e2fsck" and sounds really nice. I will still need your support to continue forward though... :o)

---

### Post by Rebelde on 2015-11-29
Also... message after fsck:

fsck from util-linux 2.20.1

??

---

### Post by Rebelde on 2015-11-29
Also... after fsck:

fsck from util-linux 2.20.1

????

---

### Post by oldfred on 2015-11-29
Please post your parted or fdisk & fsck commands as entered terminal like this:

fred@trusy-ar:~$ sudo e2fsck -C0 -p -f -v /dev/sdb3
[sudo] password for fred: 

Mine shows progress then posts details on file structure.

---

### Post by Rebelde on 2015-11-29
Thanks!

This is the response...

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb3
e2fsck: No such file or directory while trying to open /dev/sdb3
Possibly non-existent device?

---

### Post by oldfred on 2015-11-29
I have a ext4 partition that is sdb3, you do not.
I just posted my example, you have to use your partition(s) that are ext2, ext3, or ext4. And you should run on all of them. 
Your title says sda3, but reconfirm that still seen as sda3 when you boot live installer with sudo parted -l, and do no click on it with Nautilus or you mount it. It must not be mounted.

If still in same terminal, not rebooted, you can just press up arrow and see previous commands. You then can edit. This is only correct if your partition is still seen as sda3 by live installer. Some systems may change drive order.
sudo e2fsck -C0 -p -f -v /dev/sda3

---

### Post by Rebelde on 2015-11-29
Sorry for the obvious mistake!

Here it is...


ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda3 
Error reading block 15237120 (Attempt to read block from filesystem resulted in short read).  

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

---

### Post by oldfred on 2015-11-29
Did you then try as suggested without the -p?

And try this:
 #if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda3

More advanced, but examples, you must change to your data.

 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda3 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda3
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Rebelde on 2015-11-30
Strange... Something must being happening and I cannot really understand what. Yesterday when I tried "sudo e2fsck -f -y -v /dev/sda3" it did not run, as pointed out above. I assumed no mounting occurred, however, I tried "sudo parted -l" to check. An error message says there is something wrong with the partition table... which is not a partition table?! As I am sure I did not modified (at least not intentionally) the partition table I find at a loss at this point and answered no. Below all the processes:


ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MK2546GS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  5000MB  4999MB  primary   linux-swap(v1)  boot
 3      5000MB  132GB   127GB   primary   ext4
 2      132GB   250GB   118GB   extended
 5      132GB   250GB   118GB   logical   ext4


Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? n                                                                 

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.42.9 (4-Feb-2014)
Error reading block 15237120 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Superblock has an invalid journal (inode 8).
Clear? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Superblock has_journal flag is clear, but a journal inode is present.
Clear? yes

Pass 1: Checking inodes, blocks, and sizes
Journal inode is not in use, but contains data.  Clear? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(15237120--15269887)
Fix? yes

Free blocks count wrong for group #465 (0, counted=32768).
Fix? yes

Free blocks count wrong (7400859, counted=7433627).
Fix? yes

Recreate journal? yes

Creating journal (32768 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***

/dev/sda3: ***** FILE SYSTEM WAS MODIFIED *****

      324123 inodes used (4.18%, out of 7749632)
        1080 non-contiguous files (0.3%)
         298 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 274540/76
    23590501 blocks used (76.12%, out of 30991360)
           0 bad blocks
           5 large files

      226781 regular files
       37814 directories
          57 character device files
          25 block device files
           0 fifos
          26 links
       59436 symbolic links (49415 fast symbolic links)
           1 socket
------------
      324140 files
ubuntu@ubuntu:~$

---

### Post by oldfred on 2015-11-30
I do not understand why it says ext3 if it should be ext4.

But you should not have a drive with both MBR & gpt signatures. It is allows and called a hybrid drive, and used with Mac which are UEFI/gpt to boot Windows in BIOS mode which must be MBR.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

Best to use fixparts and clear gpt signatures, to make drive MBR(msdos) only.
       
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I do prefer gpt now as MBR is 35 years old from original IBM PC. But that typically requires total backup, and conversion of drive.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by Rebelde on 2015-11-30
Thanks! The procedure to follow from here seem quite more complex than I expected... I will need to read first all the info and come back with some results. I was wondering whether trying to fix my problem is worthed or not. I had some data (sound, video, image, text) stored in the non functional partition. It would be nice if there is a way to recover the complete data prior to performing a fresh installation. I am pressed by time to recover those files at the moment, so I think my request would be that one: How to recover the data stored in the non functional partition? Thanks olfred, and sorry for not having more experience with Ubuntu...

---

### Post by oldfred on 2015-11-30
Can you mount from live installer the other partition? Or does it have the same issues?
Testdisk sometimes with deeper search shows files & lets you copy them to another device.
Otherwise photorec allows you to recover files, but only by extension or type, not full file name. It just scans drive for anything that may look like a file type. 

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS
[/URL]
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

---

### Post by Geoffrey_Arndt on 2015-12-01
Just to verify a couple things:   

>   the sdb drive is a portable usb-stick, and that has the GPT partitioning . . . . not the sda drive which was/is ext3?

>   now that fsck has run in sda successfully - - the partition is still not mounting when you click on it using the file manager (presumably nautilus)?

One last thing, it seems, if I remember right, that there is a file recovery tool in the gparted program (have to unmount partition first of course) . . . have you tried it IF above not functioning?

---

### Post by oldfred on 2015-12-01
I have only seen parted rescue which is somewhat like testdisk in recovering missing partitions. I did not know gparted has a file recovery tool also. 
Testdisk has deeper search on missing partitions to look for files.

---

### Post by Geoffrey_Arndt on 2015-12-01
Fred, yes it has "device>attempt data rescue" but I've never tried it and don't know what it's based on . . . . ?    It's so hard to tell what these OP's have done, or are doing . . . it's simply amazing the results you've helped them achieve.

Can voltage irregularities account for some of these disk/partition errors?   Disk starting to age? . . . and nothing the user actually did  . . . ?

If the data can be copied off to another usb hdd or stick, then it seems a full reinstall would be a good option re moving forward to a stable system.

---

### Post by oldfred on 2015-12-01
We love to fix things, even if it takes weeks, months, years. :)
(And new install on my new SSD based system with fast Internet takes 10 minutes.) Even old slower systems can be installed in an hour or so, so re-install is always an option. And often a better option if major issues that are not hardware related, and if you have good backups of your data.

When I built new system, I tried to reuse power supply. It was 5 years old and ATX standard, but motherboard gave errors on memory. Took it to MicroCenter where I purchased most of system and paid $10 to test it. Of course it it booted immediately and they sold me a new power supply that worked without issue.

---

### Post by Rebelde on 2015-12-02
Thanks oldfred for the powerful analysis, and thanks Geoffrey_Arndt too for the additional comments! I also would very much like to repair my current installation and so learn more about my system... Unfortunately, there are some files (a great deal of them) I need to recover from my partitions. I started now making a backup from my "healthy" partition, and by following some of oldfred's suggestions, my next step is try to recover my files from the other partition. I feel my final step would be a fresh installation in a whole partition rather than more than one partition... also no more dual boot. Just because my system is getting older. It would be great if I can leave this thread open until I managed to recover all possible files :p 

Again, thanks a lot guys!

---

### Post by Rebelde on 2015-12-03
Dear all... Working hard here! I started with TestDisk, as suggested by oldfred. Please bear with me and be on the alert... I may need extra support from you ;)

---

### Post by Rebelde on 2015-12-03
Dear oldfred, you are the best! Thanks a lot for all the help! I have managed to save all my files from the damaged partition using TestDisk!! Now I am in the backup process and will thereafter proceed to perform a fresh installation without partitions nor dual boot (at least nor for now in this computer). Do you have a suggestion on the best way to prepare a system for a perfect UBUNTU installation? I have realised that my current installation may not be perfect. Thanks again!

---

### Post by oldfred on 2015-12-03
Each user has there own preference and depending on your use perhaps different install options may be better.

I prefer to have multiple drives, small system partitions of 25GB on every drive, often several versions of Ubuntu and large data & back up partitions to backup data from one drive to another. And then copies of data on DVDs & flash drives so if copy on other drive is also changed, an older copy may be available.

I also changed to only use gpt partitioning for drives that are only Linux. My older system had MBR partitions just for the XP install, now long obsolete. The gpt partitioning has a backup partition table so less often totally damaged.

---

### Post by Rebelde on 2015-12-06
Dear oldfred, you really made me reconsider my decision to wipe out my system and start from scratch all over :)  I thought that an option for me (as I have recovered all my files) would be to keep my current functional system (Ubuntu 14.04 LTS), update it, upgrade it and convert my 2-partition drive with dual boot (Ubuntu+Studio) in just one OS (updated+upgraded) and other for storage. However, as you pointed out above, my partitions and other installation details may not be the most appropriate... that may also explain why I cannot upgrade my current Ubuntu system... I was planning this for another post, but the problem may be related. Do you thing this project is worth analysing, oldfred? As you said, it may take weeks, months or years... :) but I am up for the challenge if there is the chance to get some support from you, and probably others in this forum. Thanks!! :o)

---

### Post by oldfred on 2015-12-06
As long as you keep asking questions we will try to provide answers. 
Often best to have title of thread related to problem and post as many details in thread as you can. Then those users most familiar with issue are more likely to respond.  On many issues I know just enough to be dangerous (or offer minor help).

I posted many threads on my configuration, but even that is best for me only for a few years. So what you may want now may change. But I only trust hard driver for a few years, so usually a new drive and newer configuration.

I do now prefer smaller system partitions (particularly since I have multiple installs) and larger data partitions. I also like multiple drives so I can have some most critical data copied to another drive. I do not consider that my main backup as files may still change I want an older version. So I also backup to DVD & flash drives.

---

### Post by Rebelde on 2016-01-10
Dear all, I have fixed the problem I had to access my HD partition following oldfred's suggestions. Thanks for all your replies! I will close this post and start a different as I still think I have problems with my current system, of a different nature to the one I described to start this thread. Hopefully I will succeed on that too. Thanks again!

---

