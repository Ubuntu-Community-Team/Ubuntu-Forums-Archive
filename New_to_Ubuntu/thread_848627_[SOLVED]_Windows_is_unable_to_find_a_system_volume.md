---
title: "[SOLVED] Windows is unable to find a system volume that meets its criteria for instal"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by khr on 2008-07-03
This forum is probably not the right place to ask this, but I'm going to use Ubuntu to fix this. Now to the point...

I have 3 partitions(4 including swap.)
This is how it looks like in gparted:

[I]/dev/sda1 | ext3 | / | 50 GiB | (This is where I installed Ubuntu 8.04)
/dev/sda2 | ntfs |   | 50 GiB | (This is where I want to install Vista)
/dev/sda3 | ntfs |   | 50 GiB | (This is where I want to install my games or another OS)
/dev/sda4 | extended |   | 2.9 GiB |
   /dev/sda5 | linux-swap|   | 2.9 GiB |[/I]

I insert the Windows Vista Home Premium disc into my CD-ROM.
Then I do everything I need to and then continue to the place we choose where we're going to install Vista. There, I choose to install Vista on the 2nd partition, which is a _ntfs_ partition. Vista comes up with an error: **Windows is unable to find a system volume that meets its criteria for installation.**

I'm really pissed since I've tried several things, like:

1. Delete the 2nd and 3rd partitions then make and format them in the Vista installation setup. 
**Same error.**

2. Make, but not format them in GParted.
When I format them in the Vista installation setup, I get:
**Failed to format the selected partition. [Error: 0x80004005]**

I'm trying to install Vista Home Premium, just so you know it.

Please help me...

---

### Post by Xzallion on 2008-07-03
I have no experience installing vista, but with Windows XP it tends to complain if its not the first partition on the hard drive.  Since your first partition is ext3 that might be the problem.

---

### Post by Elfy on 2008-07-03
I wasn't too sure about that - which is why I put it in your other thread, if that's the case you will have to boot the livecd again and move the partitions about after deleting the ntfs.

---

### Post by defrex on 2008-07-03
I would recommend giving vista the whole drive. Then, once it's installed, use gparted to trim it's partition and make room for Linux.

Windows doesn't play well with others...

---

### Post by khr on 2008-07-03
> **Xzallion said:**
> I have no experience installing vista, but with Windows XP it tends to complain if its not the first partition on the hard drive.  Since your first partition is ext3 that might be the problem.

Ok. I hope its not like that in Vista...
But if it is, how do I move my ext3 partition to be after my partition for games?

---

### Post by wolfen69 on 2008-07-03
make sure to use the whole drive to install vista and format it ntfs beforehand.

---

### Post by Elfy on 2008-07-03
> **khr said:**
> Ok. I hope its not like that in Vista...
But if it is, how do I move my ext3 partition to be after my partition for games?

If you need to move the partitions - do as you did previously and you can use gparted to move the ext3 partition from within the livecd.

---

### Post by khr on 2008-07-03
> **forestpixie said:**
> If you need to move the partitions - do as you did previously and you can use gparted to move the ext3 partition from within the livecd.

I really don't want to uninstall Ubuntu and lose all my settings, so this is probably the best thing to do. 

You all will hear from me if it worked.

---

### Post by cariboo on 2008-07-03
Your best bet is to clear all the partitions from your hard drive, Let Vista create a partition at the start of the drive, give it enough space To do what it needs. After doing this use the LiveCD to partition the rest of the drive.

Vista uses a totally different boot loader than previuous versions. MS has created an editor called BCDEdit.exe to edit the boot loader.Check out this article here:

[http://articles.techrepublic.com.com/5100-10878_11-6169638.html](http://articles.techrepublic.com.com/5100-10878_11-6169638.html)

Jim

---

### Post by khr on 2008-07-04
It didn't work... :shock: Same error.
Now, my only option is to do like all you others are saying:
Give Vista the whole drive! :cry:

Isn't there any other options :?

EDIT:
Might I be saved?
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

EDIT2:
Now I've taken notes of everything and I'm going to try again!
This must work.

---

### Post by hyper_ch on 2008-07-04
windows normally must be installed on the first primary partition on the harddisk... not sure if that still applies for vista...

---

### Post by Elfy on 2008-07-04
I think he should have done that already. 

This is the ms support fo the error [http://support.microsoft.com/kb/927520](http://support.microsoft.com/kb/927520)

Are you sure that the partition you have for vista is a primary one - can you boot your buntu or livecd and run

```
sudo fdisk -l
```

---

### Post by khr on 2008-07-04
It worked!
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Except when I reinstalled grub with the liveCD.
Then, Ubuntu wouldn't start and Windows wasn't there yet.
I got Grub error 17 when I tried to start Ubuntu, but I found a thread discussing the error and how to fix it. I just needed to go to the menu where you choose Ubuntu, then press "e". Then choose to edit the "hd (x,x)" (or something like that) and finally just change the last number to the Ubuntu partition. To make it permanent you'll have to boot Ubuntu then open a terminal and type: 

sudo gedit /boot/grub/menu.lst

Then find Ubuntu (Between those #####) and change the "hd (x,x)" to what you used to get Ubuntu to boot.

So now that everythings up and running, shall I play games!

---

### Post by Elfy on 2008-07-04
Excellent glad you made it, =D>

---

### Post by rupert160 on 2012-09-03
I had to put Vista/Ubuntu Dual boot on a computer and it insisted on using 2nd disk for the System Volume. I discovered in the BIOS that the 2nd disk was the priority boot disk. 

Swapped this to the disk I wanted in the BIOS and all was good.

---

### Post by sffvba[e0rt on 2012-09-03
*Back to sleep **old **thread.*


404

---

