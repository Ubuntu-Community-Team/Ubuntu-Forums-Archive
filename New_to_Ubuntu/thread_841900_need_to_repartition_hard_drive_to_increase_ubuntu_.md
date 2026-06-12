---
title: "need to repartition hard drive to increase ubuntu part."
date: 2008-06-26
forum: New to Ubuntu
---

### Post by bharper34 on 2008-06-26
I loaded edubuntu on a notebook with a 64 GB HD...now windows XP is taking up all the free space and I want to work exclusively in edubuntu without uninstalling XP...please help...I need step by step by step by step instructions...I do not know linux, but am willing to learn...Thank you.

---

### Post by logos34 on 2008-06-26
You should be able to use gparted to shrink windows and expand edubuntu root.

Can you post:

sudo fdisk -l

and

df -h

or better yet a screenshot of Gparted (settings>admin>partition editor)

---

### Post by Excalibre on 2008-06-26
> **bharper34 said:**
> I loaded edubuntu on a notebook with a 64 GB HD...now windows XP is taking up all the free space and I want to work exclusively in edubuntu without uninstalling XP...please help...I need step by step by step by step instructions...I do not know linux, but am willing to learn...Thank you.
The easiest way to deal with it will be to google "partedmagic" and download the partedmagic LiveCD which will allow you to alter your partition table, taking some space from XP and giving it to Ubuntu.

Download the disc image to your desktop, right-click it, and you should get an option in the menu to burn it to a CD. You'll then boot from that CD (you may have to access your BIOS settings to tell it to check for a bootable CD before it looks for a hard drive -- this is the same thing you probably did to install Edubuntu from the installation CD in the first place.)

The CD will allow you to resize your partitions, giving less disk space to XP and more to Edubuntu. There's a fairly simple graphical tool on the partedmagic CD to do this, and lots of useful documentation. But basically, if you installed Edubuntu yourself, you've already screwed around with partitions. This is the same basic process. If you need more explicit instructions, let me know.

---

### Post by Hashmere on 2008-06-26
I recently needed to do what you are trying to do and I used Paragon Partition Manager. 

[http://www.partition-manager.com/](http://www.partition-manager.com/)

I used to the full version but i heard the trial part works for what you are trying to do. You may want to confirm that statement though.

It can repartition without deleting anything from your computer.

---

### Post by Gannon8 on 2008-06-26
Why not pay nothing and use GParted?
And before you do anything, DEFRAGMENT YOUR WINDOWS DRIVE UBER-WELL FIRST (Right click on your C: drive, select properties, go to the tools tab, and click the button under defragment. Then just run it, perhaps a couple of times.)
If you don't you could lose files.

---

### Post by bharper34 on 2008-06-27
Thank you everyone for offering advice.  I am trying to go down the GParted route despite the fact that I have no idea what I am doing.  Please take a look at the following information and let me know what comes next.  I do not have a cd drive on this machine, but do have a flash drive I could use if necessary...

In Gparted I get two drives:

/dev/sda1    fat 16   70.57 MiB  used 8.46 MiB  unused 62.11 MiB

/dev/sda2 (with a lock) ntfs  /boot,/host   29.75Gib  used 17.69 Gib  unused 12.06 GiB  Boot

I want my edubuntu to have the book of the drive space...I currently only have music files on edubuntu and nothing on XP, so loss of data is not a concern...thank you.

---

### Post by Excalibre on 2008-06-27
> **bharper34 said:**
> Thank you everyone for offering advice.  I am trying to go down the GParted route despite the fact that I have no idea what I am doing.  Please take a look at the following information and let me know what comes next.  I do not have a cd drive on this machine, but do have a flash drive I could use if necessary...

In Gparted I get two drives:

/dev/sda1    fat 16   70.57 MiB  used 8.46 MiB  unused 62.11 MiB

/dev/sda2 (with a lock) ntfs  /boot,/host   29.75Gib  used 17.69 Gib  unused 12.06 GiB  Boot

I want my edubuntu to have the book of the drive space...I currently only have music files on edubuntu and nothing on XP, so loss of data is not a concern...thank you.
That's . . . odd. I take it this is a Dell computer? Because they tend to have a small fat 16 partition first on the disk like you're describing here. But there should be a third partition, sda3, in which Edubuntu is installed.

Go to a terminal prompt and type "sudo fdisk -l". That will show your partition table, which you can copy and paste here so we can all take a look. You should get something like this (which is mine.)

```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2454    19711723+   7  HPFS/NTFS
/dev/sda2            2455       16198   110398680    5  Extended
/dev/sda3           25173       30394    41945715   83  Linux
/dev/sda5            2455       15154   102012718+  83  Linux
/dev/sda6           15155       16198     8385898+  82  Linux swap / Solaris

```

There's no reason you should have to lose any data in this process, by the way. There's always a risk when you screw with your partition table and ideally everything should be backed up but if nothing you have on there is important, then I guess that's not a big deal.

Incidentally, you won't be able to do what you're trying to do by running gparted from Edubuntu. gparted can't alter any partition that's currently mounted (that is, any partition that you have access to at the time) and if you're running Edubuntu, you can't unmount the partition you're running it from. The partedmagic Live CD allows you to boot from it instead of from Edubuntu so all your partitions will be unmounted and you'll be able to alter them all however you like with its included copy of gparted.

---

### Post by kansasnoob on 2008-06-27
I see that Gparted is available in a Stable Live USB form, but I've never used it:

[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

I also see you can put GParted Live on a harddisk:

[http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)

Again, I've tried neither!

---

### Post by Excalibre on 2008-06-27
> **kansasnoob said:**
> I see that Gparted is available in a Stable Live USB form, but I've never used it:

[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

I also see you can put GParted Live on a harddisk:

[http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)

Again, I've tried neither!
Look, the partedmagic live CD is free, and it's vastly better than the gparted live CD. I can't imagine that the gparted live USB thing is any better than their live CD.

If you haven't used either, is it really a good idea to recommend them to someone?

---

### Post by bharper34 on 2008-06-27
Thank you...here you go...

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10        3892    31190197+   7  HPFS/NTFS

---

### Post by Excalibre on 2008-06-27
Okay, it doesn't look like you have an edubuntu partition at all. Have you just been running it from the Live CD? Or have you actually installed it somewhere (on an external hard drive, maybe?)

---

### Post by kansasnoob on 2008-06-27
> **Excalibre said:**
> Look, the partedmagic live CD is free, and it's vastly better than the gparted live CD. I can't imagine that the gparted live USB thing is any better than their live CD.

If you haven't used either, is it really a good idea to recommend them to someone?

Uh, I was replying to this:

"I do not have a cd drive on this machine, but do have a flash drive I could use if necessary..."

Pretty hard to run a live CD without a CD drive isn't it:confused:

I was only looking for alternatives, and I made it clear that I hadn't personally tried it, therefore I can't profess to it's efficiency.

---

### Post by bharper34 on 2008-06-27
No I do not believe I installed from Live CD...this notebook doesn't have an external drive or CD drive at all.  I installed from within XP using a flash drive that had the copy of Ubuntu on it.

---

### Post by Duck2006 on 2008-06-27
So you did a Wbui install then?

---

### Post by kansasnoob on 2008-06-27
I wonder then if it's a Wubi install. I tried Wubi once just to see what it was like but don't know much about it.

One dumb question, Ubuntu does run with the flash drive unplugged, eh?

---

### Post by kansasnoob on 2008-06-27
[http://wubi-installer.org/support.php](http://wubi-installer.org/support.php)

---

### Post by bharper34 on 2008-06-27
yes, it does.  I used Wubi...one update...I only have a 32GB SSD drive...

---

### Post by Excalibre on 2008-06-27
> **kansasnoob said:**
> Uh, I was replying to this:

"I do not have a cd drive on this machine, but do have a flash drive I could use if necessary..."

Pretty hard to run a live CD without a CD drive isn't it:confused:

I was only looking for alternatives, and I made it clear that I hadn't personally tried it, therefore I can't profess to it's efficiency.
I'm sorry, you're right. I totally missed what he said. I apologize for my tone, it was unwarranted.

---

### Post by Excalibre on 2008-06-27
> **bharper34 said:**
> yes, it does.  I used Wubi...one update...I only have a 32GB SSD drive...
So, to summarize, you don't actually have an Ubuntu partition, you're running it from a virtual disk which is somewhere on the Windows partition. And you want to increase the size of that virtual disk.

I can't help you with that, but the [Wubi Guide](http://wiki.ubuntu.com/WubiGuide) has some instructions. It's probably not too hard to do. Good luck!

---

### Post by youthforlinux on 2008-06-27
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) contains a guide on transfering a Wubi virtual partition to a real one.

---

### Post by logos34 on 2008-06-27
If a Wubi install is what you have, and you want to increase edubuntu's space without tranferrring it to a new, dedicated partition, then you want to look at this LVPM page:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
(-->'Resizing virtual disks using LVPM')

There's been quite a few requests for that lately

---

### Post by bharper34 on 2008-06-27
Man...if only I had your post 35 minutes ago...at this point I uninstalled and re-installed the whole thing to increase the disk size at the first screen of WUBI...Thank you though, that was an extremely thourough walk through of how to completely solve my issue.  Thank you to everyone for your help.:)

---

