---
title: "Unetbootin version 494 - cannot open"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by CraigD92 on 2013-01-25
Hi guys,

I'm trying to create a dual boot with Windows 7 (an iso I downloaded (legally) from My Digital Life) and Ubuntu.

I am doing this by first installing Windows 7 with a Live USB, and then re-installing Ubuntu. After reading up I found out that you need to format the USB to NTFS. I have done this using GParted. However, the current version of Unetbootin does not recognise NTFS. So, I downloaded version 494 which does regonise NTFS. 

I market the file as executable in Properties, but when I click the icon nothing happens. Unetbootin does not start. 

Am I doing something wrong?

(Edit: I am using Ubuntu 12.04)

---

### Post by cariboo on 2013-01-27
When you try to start unetbootin in a terminal, what errors do you get?

---

### Post by NikTh on 2013-01-27
As cariboo907 said , try from terminal with a command like this 

```
gksudo ~/Downloads/unetbootin-linux-494
``` 

In above command I assume that the file is in Downloads folder

Thanks

---

### Post by Edified on 2013-03-03
I couldn't get 494 to start either, it would just silently not start.  In the end I thought if gparted is doing the partitioning and marking the boot flag then what is left for netbootin to do?  It's not doing a block copy so it's probably just copying files.

So I tested and found that you don't need netbootin at all to make a windows install usb stick.  Here's what I did:

[B]1. Download the appropriate windows iso
[/B]-I got mine from digital river: [https://www.google.com/search?q=digital+river+windows+7](https://www.google.com/search?q=digital+river+windows+7)

[B]2. Use gparted to format a usb flash drive to NTFS and set the boot flag
[/B] -You'll need to have ntfs-3g installed but I think it's installed by default these days
 -To set the boot flag, right click on the partition and choose "Manage Flags"...
[B]
3. Mount the windows iso 
[/B] -I right clicked the iso and chose open with Image Mounter
[B]
4. Drag all the files from the mounted iso onto the flash drive
[/B]
When they're done copying you've got a bootable USB drive!  
Very easy, and I've already tested it.

---

