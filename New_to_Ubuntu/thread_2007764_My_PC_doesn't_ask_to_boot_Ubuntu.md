---
title: "My PC doesn't ask to boot Ubuntu"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by Killya on 2012-06-21
So, I have seen so many of these threads after searching, but none are understandable for me or are a tad different. 

So I was using Windows Vista (Which is on the C:/ drive) until I found out about Ubuntu. Now I still need some programs desperately which only run on Windows, and I want to be able to boot both, since I do not fully understand wine yet. I had Ubuntu installed on C:/ through the wubi installer and everything worked fine. Only I soon found out that the " 8GB install"  I choose meant that I only could use 8GB of space on Ubuntu. I had a 2nd drive D:/ which I didn't really use, so I thought; I'm going to install a full Ubuntu on there.

So I downloaded the ISO, installed the ISO on USB. Rebooted, installed Ubuntu on the D:/ drive. Everything was fine! Then I rebooted, thinking the question would pop up which OS I wanted to boot, but it didn't. It immediately boots Windows, no questions asked. I ran the boot script I found on this forum, and it does see the Ubuntu OS on the D:/ drive (partitions sda5)

```
sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 401845440 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

So how do I make my PC ask me everytime I start it what to boot?

Ciao! And many thanks :D

---

### Post by rukiaEnix on 2012-06-21
Hello,

Did you accept the grub loader to be installed when you were installing Ubuntu?

And also... what Ubuntu is that, I've never heard of an Ubuntu that can only be installed with 8GB

---

### Post by Killya on 2012-06-21
> **rukiaEnix said:**
> Hello,

Did you accept the grub loader to be installed when you were installing Ubuntu?

And also... what Ubuntu is that, I've never heard of an Ubuntu that can only be installed with 8GB

I never saw any questions on the grub loader. Should I re-install Ubuntu completely, or can I install this seperatly?

And there is a windows-installer for Ubuntu, so you don't have to use an USB or CD. This installer only gives an amount of space to the OS, which the installer can choose

Thanks!

---

### Post by rukiaEnix on 2012-06-21
I'll be honest. I recommend you to download a full ISO if you don't want to use a CD create a boot usb with the ISO. So yes reinstall it again. 

With a full install you can manage better your disk space. But if you are new I also recommend not to play with your Windows partition at installation time.

Though Ubuntu already has an option for installing without touching your Windows partition in an almost automatically way with the full install ISO.

---

### Post by Killya on 2012-06-21
> **rukiaEnix said:**
> I'll be honest. I recommend you to download a full ISO if you don't want to use a CD create a boot usb with the ISO. So yes reinstall it again. 

With a full install you can manage better your disk space. But if you are new I also recommend not to play with your Windows partition at installation time.

Though Ubuntu already has an option for installing without touching your Windows partition in an almost automatically way with the full install ISO.

Allright, re-installed, but no question about the grub launcher came up, I'm sure. I got the ISO from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

So that should be the correct one right?

---

### Post by rukiaEnix on 2012-06-21
OK, that ISO is fine but I really recommend you to install it as a boot CD or USB. 

Not from Windows. As I told you Ubuntu has made the installation really easy to do. Is like just answering some questions and the installation will do almost everything.

---

### Post by Mark Phelps on 2012-06-21
If Vista came preinstalled on your PC, it's likely the PC builder already used the maximum of 4 Primary partitions -- in which case, you can't create another one.

To see the disk partitions, boot into Vista and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Vista Disk Management utility to shrink the Vista OS partition to make room on the drive. Vista, like Win7, is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Vista unbootable.

And, after you create some free space, do NOT format it using the Vista Disk Management utility; leave it as free space. When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

