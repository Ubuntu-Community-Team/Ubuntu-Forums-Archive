---
title: "Reformatting Ubuntu"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-07-06
I have to go back to Windows for awhile. I tried booting up my Windows XP cd and I got an error saying no previous versions of Windows were detected and there was a disk read error. I think my disk is fine and I believe this is because I have Ubuntu on my HD. How can I reformat Ubuntu and make my hard drive clean/empty?

Thanks

---

### Post by Sef on 2008-07-06
Let's check your partitions:

```
sudo fdisk -l
```  Small L,  then Copy and paste the results.

---

### Post by Locutus_of_Borg on 2008-07-06
boot form livecd

dd if=/dev/zero of=/dev/sda (or hda if thats what you have)

that will create a blank hardrive, unformatted, with nothing on it.

to format it to ntfs (why you would want to, i dont know) put in a windows cd and use cfdisk to create partitions/format them

or

 mkntfs while still booted with livecd

---

### Post by JimmyJim on 2008-07-06
> **Sef said:**
> Let's check your partitions:

```
sudo fdisk -l
```  Small L,  then Copy and paste the results.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20962096

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
```

---

### Post by cariboo on 2008-07-06
It looks like you don't have a winxp partition any more. To install xp boot from your CD and let it go through all the things it has to until it gets to the partition screen. Just delete the partitions that are already there and the you can set up your partitions any way you want.

Jim

---

### Post by JimmyJim on 2008-07-06
> **cariboo907 said:**
> It looks like you don't have a winxp partition any more. To install xp boot from your CD and let it go through all the things it has to until it gets to the partition screen. Just delete the partitions that are already there and the you can set up your partitions any way you want.

Jim

I know I don't have the Windows XP partition. Something must be wrong with the disc then because I can't get to the partition screen without error.

---

### Post by JimmyJim on 2008-07-06
I checked the disk on another computer and it reads fine. The problem is that Ubuntu is installed. How can I completely format my hard drive so it is blank? 

Thanks

---

### Post by nig_nig_the_conqueror on 2008-07-06
> **JimmyJim said:**
> I checked the disk on another computer and it reads fine. The problem is that Ubuntu is installed. How can I completely format my hard drive so it is blank? 

Thanks

I (highly) doubt that the Ubuntu install is your problem.  It might be your optical drive.

---

### Post by JimmyJim on 2008-07-06
> **nig_nig_the_conqueror said:**
> I (highly) doubt that the Ubuntu install is your problem.  It might be your optical drive.

I've had issues before where the disk wouldn't read because a different version of Windows (different from the disk) was installed. I've used this disk on my computer many times before Ubuntu. The other computer that I tried the disk on has a very old, poor optical drive and it read fine. I just burnt a DVD with my optical drive. I highly doubt that my optical drive is the issue.

Regardless of the cause, how can I completely reformat my hard drive so it is clean? Thanks

---

### Post by nig_nig_the_conqueror on 2008-07-06
> **JimmyJim said:**
> I've had issues before where the disk wouldn't read because a different version of Windows (different from the disk) was installed. I've used this disk on my computer many times before Ubuntu. The other computer that I tried the disk on has a very old, poor optical drive and it read fine. I just burnt a DVD with my optical drive. I highly doubt that my optical drive is the issue.

Regardless of the cause, how can I completely reformat my hard drive so it is clean? Thanks

Use GParted.  It's a live cd and should do what you need.

[COLOR="DarkSlateBlue"][http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")[/COLOR]


EDIT:  I just realized...I don't think Gparted can create NTSF partitions, but you can try creating a FAT32 partition and the Windows install disk should be able to format it to NTSF.  Hope this helps.

---

### Post by swisscow on 2008-07-06
> **nig_nig_the_conqueror said:**
> Use GParted.  It's a live cd and should do what you need.

[COLOR="DarkSlateBlue"][http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")[/COLOR]

Just boot with the ubuntu livecd. Gparted is on that.

---

### Post by nig_nig_the_conqueror on 2008-07-06
> **swisscow said:**
> Just boot with the ubuntu livecd. Gparted is on that.

Yep, he's right.  I forgot about that. But please note the edit on my last post that I'm pretty sure Gparted can't create NTFS partitions, so you'll need to format it as FAT32 or something. Then the Windows install disk should format it for you.

---

### Post by JimmyJim on 2008-07-06
sorry, I meant to edit, not reply :-\"

---

### Post by JimmyJim on 2008-07-06
Can I get confirmation that the Windows installation CD will be able to format FAT32 to NTFS? Thanks; I just don't want to format my HD to FAT32 and then find out the Windows disc won't accept it.

I already have a Livecd burnt, so I'll use that.

---

### Post by akiratheoni on 2008-07-06
I don't think it'll convert it, I think it'll just overwrite it.

---

### Post by Frak on 2008-07-06
> **nig_nig_the_conqueror said:**
> I (highly) doubt that the Ubuntu install is your problem.  It might be your optical drive.
The infamous Black Screen of Death can occur if the WinXP Installation CD cannot recognize the partitions on the HD. It basically lock's up and dies.

---

### Post by JimmyJim on 2008-07-06
> **akiratheoni said:**
> I don't think it'll convert it, I think it'll just overwrite it.

I would like confirmation. I need to know this will work for sure, because if it doesn't, I'm stuck.

---

### Post by Frak on 2008-07-06
> **JimmyJim said:**
> I would like confirmation. I need to know this will work for sure, because if it doesn't, I'm stuck.
Yes, it can.

EDIT
You can actually boot into the recovery and run this

```
convert c: /fs:ntfs
```

To convert it

---

### Post by JimmyJim on 2008-07-06
> **Frak said:**
> Yes, it can.

EDIT
You can actually boot into the recovery and run this

```
convert c: /fs:ntfs
```

To convert it

OK, thanks a lot. Now back to windoze for awhile. =P~

---

### Post by nig_nig_the_conqueror on 2008-07-06
> **Frak said:**
> The infamous Black Screen of Death can occur if the WinXP Installation CD cannot recognize the partitions on the HD. It basically lock's up and dies.

I've never run into that.  Can XP not recognize an ext3 partition?

> Yes, it can.

EDIT
You can actually boot into the recovery and run this

Code:
```
convert c: /fs:ntfs

```
To convert it 

Or if you really want to NUKE the contents of your hdd:

[http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

---

### Post by Frak on 2008-07-06
> **nig_nig_the_conqueror said:**
> I've never run into that.  Can XP not recognize an ext3 partition?

Nope. It can see some weird types of partitions, but nothing native to Linux, Unix, or OS X are able to be seen.

---

