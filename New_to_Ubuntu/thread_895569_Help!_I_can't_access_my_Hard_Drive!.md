---
title: "Help! I can't access my Hard Drive!"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by WastePotato- on 2008-08-20
Help!

I'm in need of dire help. I can't access my Hard Drive. I am currently writing this from a Ubuntu Live CD. Recently my XP installation has been failing to start, so I put in my restore disk and set to repair the boot sectors of my drive. When I tried to mount my drive in Ubuntu I recieved this message:

Unable to mount volume: /dev/sda1/ Can't read superblock.

Someone please help me as I have valuable files on this disk!

Thanks.

---

### Post by bobnutfield on 2008-08-20
Open a terminal in the live cd and type:

> sudo fdisk -l

The results will reveal if you have a corrupt superblock.  If so, it is possibly repairable.

---

### Post by WastePotato- on 2008-08-20
I get this message:

> o run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04c204c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4687    37642400    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 



---

### Post by bobnutfield on 2008-08-20
[https://help.ubuntu.com/community/SystemAdministration/Fsck]("https://help.ubuntu.com/community/SystemAdministration/Fsck")

The above link describes how to use fsck from Ubuntu.  I may be possible to repair the filesystem with fsck.  I have never used it on a Windows partition, but according to the instructions in the above link, it appears to be possible.

It appears that you only have Windows installed on your disk.  There is also a recovery program on your XP disk.  Have you tried that (other than trying repair the boot sector)?  Hopefully, someoe who has repaired just such a problem will chime in.

---

### Post by WastePotato on 2008-08-20
When I type > fsck -F ufs /dev/sda

I get this:

> ubuntu@ubuntu:~$ fsck -F ufs /dev/sda
fsck 1.40.8 (13-Mar-2008)
Usage: fsck.ext2 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list


Which options should I choose?

---

### Post by WastePotato- on 2008-08-20
Bump...

---

### Post by Titan8990 on 2008-08-20
fdisk is not recognizing the existence of your HDD. Is your HDD displayed in your BIOS?

Do you have thumb drive plugged in?

fsck would not work because /dev/sda1 is FAT32 while fsck is for ext2 and ext3 filesystems.

---

### Post by WastePotato on 2008-08-20
Yes. My Hard Drive shows up in my BIOS. I'm currently using a LiveCD.

---

### Post by Titan8990 on 2008-08-20
and it is formatted in fat32? To view this hard drive:


sudo mkdir /media/sda1

sudo mount /dev/sda1 /media/sda1

cd /media/sda1


and you should now be viewing your FAT32 volume.

---

### Post by WastePotato on 2008-08-20
It's formatted in NTFS. 

Should I just reformat it and attempt to use a file recovery program afterwards?

---

### Post by Titan8990 on 2008-08-20
No, you shouldn't. What device do you have formatted in FAT32? Is that a different partition on the same drive?

---

### Post by WastePotato on 2008-08-20
That's odd.

I don't have anything formatted in FAT32. (Apart from USB drives, but they weren't plugged in at the time).

---

### Post by Victormd on 2008-08-20
Do you have another HD that you can connect, install windows and see if you can access it from there, then run checkdisk to fix any errors since Ubuntu won't check NTFS for errors (I don't think - someone please correct me if I'm wrong here). Nonetheless, it does sound like your HD died on you...

---

### Post by WastePotato on 2008-08-21
UPDATE: It turns out that my HD didn't die on me. The combination of my parents hard shutting (holiding the power button down) and ironically, my OEM's restore disk corrupted the files on my HD.

This whole problem started because "someone" ¬¬ in my family hard shut (held the power button down) the computer while I was running a Disk Cleanup. When I came back and found that the computer had been shut off without my knowledge, I started the computer only to find that some Vital Windows files had been corrupted, presumably from the HD being shut down while moving files.

Not having a "true" Xp disk, I used my OEM's Restore disk to "repair boot sectors". This only made the problem worse, as it reset all of the logs and MBR records on my HD. It also turned my HD into FAT32, without converting files. (I used NTFS)

Thinking all was lost, I used my last sign of hope: My Ubuntu CD. And it worked. It installed without failure, giving me hope that the HD hadn't died. The only problem is that it formatted my drive. 

But from what I understand, formatting only marks the files as deleted, and doesn't actually delete them, and from what I remember, my HD was very fragmented (we hadn't done a defragmentation in over two months) so there may be hope of recovering my files.

So I have to ask:

Are there any good file recovery programs for linux?

Thanks.

---

### Post by WastePotato on 2008-08-22
Anyone?

---

### Post by Gannon8 on 2008-08-22
Photorec is a good one that I have found, but It only looks for certain file types. Comes with Testdisk, a tool for recovering lost partitions, but it didn't work for me...

Anyway, [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Victormd on 2008-08-22
Well, at least you didn't have to get a new HD.

I don't want to disencourage you, but as far as recovering your data, I think it's going to be very dificult. You had a NTFS HD that was converted to FAT 32 during windows recovery, then you installed Ubuntu, converting your HD to EXT3. This changes the whole "mark as deleted" concept. If you have a NTFS and format NTFS, it's not that hard to recover, but if you change the file system, the structure of the file allocation table will most likely change and recovery will not be so easy.

You also mention that your HD was pretty fragmented. This is not a good thing when recovering files because the chances of small parts of the files getting overwritten increases, and again, recovery possibilities decrease.

Nonetheless, give it a shot and let us know how it works out. When I get home I'm going to see if I can find any open-source recovery packages for you and if I do, I'll post them here.

Good luck

EDIT: This link might help you:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

