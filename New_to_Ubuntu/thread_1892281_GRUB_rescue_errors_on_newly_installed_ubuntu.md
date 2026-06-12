---
title: "GRUB rescue errors on newly installed ubuntu"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by arnab321 on 2011-12-07
hi, i am trying to install ubuntu 11.04 on an external hdd. i have already disabled the internal hdd from BIOS. im using unetbootin method to install it from a thumb drive. does that make any difference?

these are my partitions:
(sda is the thumb drive im installing from)

sdb1 - ntfs, about 900 gb (imp. files here, so i cant delete this)
sdb2 - ext3 /boot , 100mb
sdb3 - swap 3gb
sdb4 - ext4 / 70gb

on booting, i get a grub rescue prompt saying "no such partition"
i tried installing a second time, but the same thing happens.

---

### Post by BC59 on 2011-12-07
I don't see where is the problem. Try it again and follow these instructions, if you already didn't follow them:

[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

---

### Post by arnab321 on 2011-12-07
> **BC59 said:**
> I don't see where is the problem. Try it again and follow these instructions, if you already didn't follow them:

[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/) i went through it but i don't think I'm doing anything wrong. Is it necessary to create a separete partition for /home?

Tried again.this time, i used CD, thinking that the thumb drive was causing something...deleted and recreated those last 3 partitions. Same thing happens.

I'm installing both GRUB and Linux on the external drive. I have disabled all other drives except cdrom, so that grub can boot.

---

### Post by westie457 on 2011-12-07
Hi boot into a Live Desktop in try mode. 

Go to here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
follow the instructions to download and use the file. 

Post the RESULTS.TXT here, this will give us a better idea of what the situation is.

---

### Post by arnab321 on 2011-12-08
> **westie457 said:**
> Hi boot into a Live Desktop in try mode. 

Go to here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
follow the instructions to download and use the file. 

Post the RESULTS.TXT here, this will give us a better idea of what the situation is.
attatched.

---

### Post by BC59 on 2011-12-08
> **arnab321 said:**
>  im using unetbootin method to install it from a thumb drive. does that make any difference?

Yes this is making the difference. Try the installation using a CD.

---

### Post by arnab321 on 2011-12-08
> **BC59 said:**
> Yes this is making the difference. Try the installation using a CD.

Read the third post. I did try using CD

---

### Post by BC59 on 2011-12-08
Yes you have right. Then look here to see if you can do something from a similar thread:

[http://ubuntuforums.org/archive/index.php/t-1808565.html](http://ubuntuforums.org/archive/index.php/t-1808565.html)

---

### Post by arnab321 on 2011-12-08
hey, im a bit frightened with what i just saw...... because i had bought SEAGATE Freeagent Goflex 1TB, just a month ago,  specifically to install ubuntu on it.

i partitioned another thumb drive into an ext3, an ext4, and a fat32 partitions and put some files in them.

i booted from the external hdd. these were what i saw in grub rescue.

**ls:**
(hd0), (hd0,msdos1), (hd1) (hd1, msdos1) (hd1, msdos2) (hd1, msdos3)

// here hd0 is the external hdd with ubuntu installed, which has 4 partitions, but **they are not showing up**.  (hd0,msdos1) is the ntfs partition, most probably, because ** ls (hd0,msdos1)/ **gives **"unknown filesystem"**

(hd1) is the thumb drive, which i connected just to test if grub was detecting its partitions. doing **ls** in **(hd1, msdos2) (hd1, msdos3) **shows the files in them, while** (hd1, msdos1) **is FAT, which means nothing is wrong with grub, but something  is, with my...... 

anyways, when i run ubuntu live session, all the partitions in the eternal hdd are accessible, as u can already see in the RESULTS.txt of previous post. Can u interpret whats going on?

---

### Post by westie457 on 2011-12-08
It looks like the best thing to do is completely remove Grub from your system and reinstall Grub to the external hard drive. Take a look at this link [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) for guidance. Personally I would try the solutions in the order they are written.

Hope this helps.

---

### Post by fantab on 2011-12-08
> **arnab321 said:**
> hi, i am trying to install ubuntu 11.04 on an external hdd. i have already disabled the internal hdd from BIOS. im using unetbootin method to install it from a thumb drive. does that make any difference?

these are my partitions:
(> sda is the thumb drive im installing from)

sdb1 - ntfs, about 900 gb (imp. files here, so i cant delete this)
sdb2 - ext3 /boot , 100mb
sdb3 - swap 3gb
sdb4 - ext4 / 70gb
on booting, i get a grub rescue prompt saying "no such partition"
i tried installing a second time, but the same thing happens.

When you boot with your USB disk it is taking the HD no. /dev/sda and your HDD becomes /dev/sdb, so what happens when you don't have the USB drive plugged in?
Does your HDD becomes /dev/sda? (If yes, then there is your problem).

Reset your BIOS defaults and use CD to install Ubuntu. Delete partition /dev/sdb2 - /boot you don't need this. Install grub to the hard drive.

---

### Post by arnab321 on 2011-12-08
well, i removed the /boot partition and installed again using CD
i created all partitons as primary. there are 3 partitons now- ntfs, swap and ext4.  previously, i was making them logical, so, grub wasnt listing them.

i boot, and now a new grub rescue error - **unknown filesystem**

this is what i get:
ls:
(hd0) (hd0, msdos1) (hd0, msdos2) (hd0, msdos3)

(finally detects all partitons)

ls (hd0, msdos1)
unknown filesystem

ls (hd0, msdos2)
unknown filesystem

ls (hd0, msdos3)
unknown filesystem

WTF?

i read that Goflex hdd's has an inbuilt ntfs driver for Mac, and here is an extract from Seagate Goflex's page:
> 
Works interchangeably on both PC and Mac® computers

Whether you have a PC or a Mac® computer–or if you go back and forth between the two–you can access and save files on the same portable hard drive anytime without reformatting*.
*Reformatting to HFS+ required to use backup software for Mac or Time Machine® software


what i interpret so far is that its drivers are messing up the filesystems, or is trying to emulate ext4 as ntfs. but ubuntu live session/ gparted still shows all the partitions correctly.....

---

### Post by fantab on 2011-12-08
> **arnab321 said:**
> i read that Goflex hdd's has an inbuilt ntfs driver for Mac, and here is an extract from Seagate Goflex's page:


what i interpret so far is that its **drivers are messing up the filesystems,** or is trying to emulate ext4 as ntfs. but ubuntu live session/ gparted still shows all the partitions correctly.....

Perhaps your guesswork is in the right direction. I am sure that there will be a Seagate folder on your drive. Copy it somewhere else as backup and delete the folder from your drive. And try again leaving some unallocated space in front of the NTFS [in Gparted terms], about 1-10mb. Generally Grub installs itself to the first sector of the drive and sometimes when the first sector is preoccupied with data it may cause problems. 

OR if its not too much pain, I suggest you BACK UP the important data on the drive, delete all partitions and reformat the drive with [Gparted Live]("http://gparted.sourceforge.net/livecd.php")CD (This is a better way of managing Partitions). And doing so create your NTFS main partition at the end. Make the first partition "/" ext4 followed by swap.

---

