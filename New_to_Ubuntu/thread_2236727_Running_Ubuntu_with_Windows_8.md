---
title: "Running Ubuntu with Windows 8?"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by Mike_Hawthorne on 2014-07-28
Hi 

I'm new here.

I've used Ubuntu for an emergency backup to Windows for a long time.
But I've always run it from a DVD, not installed on my hard drive.

When I look at dual booting with Windows 8 there it always seems to be a very involved process to get it to work.

What I don't get is, since I can always boot to the Disk with no problems, why can't I just copy the disk to a small partition on one of my hard drives or even a folder (I have 4 internal 500 Gig drives) and add it to the boot menu using EasyBCD or something like that.

Couldn't I just select Boot to Ubuntu, and have it do that just as it would from the DVD?

There's probably a reason this won't work or everyone would do that, but I wanted to ask before I tried it myself.

I'm running Windows 8 with the UEFI bios.

Mike

---

### Post by yancek on 2014-07-28
> What I don't get is, since I can always boot to the Disk with no  problems, why can't I just copy the disk to a small partition on one of  my hard drives or even a folder 

You could have with wubi (Windows UBuntu installer) but that is no longer supported when using windows 8, due to the changes made to windows 8.  Wubi is not supported any longer because of this and from what I have read will not work at all on a system with windows 8.

You can install VirtualBox or other virtual software and use Ubuntu that way.

You could do what is referred to as a 'frugal install' which is basically the Live CD on a hard drive and boot it with Grub Legacy or Grub2 but I seriously doubt that would work with EasyBCD as a bootloader.

If you don't want to install on your hard drive, why don't you just create a persistent flash drive install with unetbootin or similar software?

---

### Post by Mike_Hawthorne on 2014-07-28
Hi

Thanks for the reply.

I didn't really think about just using a USB drive instead of the DVD, that would speed things up a bit.
Maybe I'll give that a try.

I'll also have a look at Grub, I've never messed with it but I know what it is.

I've dual booted several operating systems in the past, even in Windows 8, and never had to do much but install it and set it up with EasyBCD.
I wish it was that easy with Ubuntu.

Mike

---

### Post by oldfred on 2014-07-28
Are your data drives gpt partitioned like the Windows system drive?

Since I have multiple drives I created a partition and ISO folder. I copy all the install ISO of Ubuntu, gparted, Knoppix and other repair tools into that ISO folder and use grub to directly boot the ISO. That is even faster than booting flash drive. But you do have to install grub.

Better if grub is installed in UEFI mode, but if you boot from UEFI menu or one time boot key you could just install grub to any drive and boot the ISO. Does require a bit of command line work to install, but very doable if you have used Ubuntu some. 

I only have BIOS, but now use gpt for all new drives and include an efi partition at beginning of drive for future use and a bios_grub to boot in BIOS mode now. 

Does not even have to be flash drive, could be any drive.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

      
 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by Mike_Hawthorne on 2014-08-19
Hi

Thanks for the reply, I'm still looking at it.
I installed VirtualBox but haven't yet tried installing Ubuntu using it.
As soon a I make a new System Image I have a go at it.

Mike

---

