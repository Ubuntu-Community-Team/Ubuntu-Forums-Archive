---
title: "[SOLVED] Maxtor ext hard drive"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by irishy on 2008-07-22
Help please
On connecting maxtor one touch4 to my pc my distro is Hardy heron just the one message comes up cannot mount maxtor.I have looked at a few posts but nothing quite fits can anyone help please
thanks

---

### Post by ibuclaw on 2008-07-22
What is the filesystem type? would you know?

```
sudo fdisk -l
```
Regards
Iain

---

### Post by bumanie on 2008-07-22
I have read a number of posts re proprietary made external hard drives. It seems that a number of them have issues with ubuntu and the drive manufacturers say, "We don't support linux". I always use hard drives that have previoulsy been in a computer and buy a separate external case - they have always worked.

---

### Post by coffeecat on 2008-07-22
As far as I can make out, the Maxtor One Touch 4 has onboard software for data backup and synchronisation which works in Windows and Mac OS. I wonder if this is confusing Ubuntu and interfering with automounting.

If you don't need this software you may need to reformat the drive. Then it should automount OK.

The previous poster makes a good point. I have always bought USB cases to put bare drives in and then formatted them with the filesystem I want. And I can use them with Linux, Windows and MacOS, no trouble at all.

---

### Post by irishy on 2008-07-23
thanks this is the result
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47954794

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4216    33864988+   7  HPFS/NTFS
/dev/sda2            4217       30401   210331012+   5  Extended
/dev/sda5           17300       30047   102398310   83  Linux
/dev/sda6           30048       30401     2843473+  82  Linux swap / Solaris
/dev/sda7            4217       17299   105089134+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e685a77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7
```

---

### Post by ibuclaw on 2008-07-23
It doesn't seem to be formatted yet.

Try reformatting it in either Windows or Ubuntu.

In Ubuntu, download gparted
```
sudo apt-get install gparted
```

And create a partition for it.

Regards
Iain

---

### Post by kk0sse54 on 2008-07-23
Format it then and you should be fine as I have a Maxtor OneTouch4 250 GB external HD and it works perfectly for Ubuntu and every linux OS I have ever tried. Although for me I never had to format it as I just plugged it in to Windows and it automatically popped up probably because windows automatically set it to NTFS filesystem.

---

### Post by irishy on 2008-07-24
Thanks for your replies it gives me hope I do have the part magic disc I have used it previously and nervously  can you tell me specifically what needs to be done I really do struggle 
thanks in anticipation

---

### Post by ibuclaw on 2008-07-24
If you wish to use it with Windows. You'll have to boot into Windows and format it as an NTFS partition there. As I don't believe you can create them in Linux.

If you then wish to make it a Half NTFS, Half ext3/other Linux read/writeable partition. Then you can shrink the NTFS and create the new partition in the space with partition magic.

Regards
Iain

---

### Post by northern lights on 2008-07-24
I'd assume the new drive is for data storage and supposed to be accessed by both Windows and Ubuntu? If so, "ntfs" should be your choice of filesystem.

Depending on the size of the new hdd and the degree as to which your data varies in type you might wanna consider giving it more than one partition.

Anyhoo, under Windows, do this:

You have a setup of "Partition Magic"? Install and run. You should see a graphical representation of your old drive(s) and one of the new maxtor drive, which should simply be a gray bar (unallocated space). Right click somewhere on the gray area and choose "Create new partiton", pick "from the beginning of the unallocated space". If you want just one, let it go to the end. If not make it however large you want and start over by right-clicking on the leftover unallocated space.

An alternative to "Partition Magic" under Windows is "Acronis Partition Manager". Both are commercial software, though.

"gparted" under Linux works essentially the same way. You can also run it from the LiveCD...

---

### Post by irishy on 2008-07-24
Thank you all very much that has solved the problem If only everything was so easy

---

