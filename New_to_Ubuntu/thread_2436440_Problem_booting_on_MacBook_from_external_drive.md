---
title: "Problem booting on MacBook from external drive"
date: 2020-02-06
forum: New to Ubuntu
---

### Post by dorpapst on 2020-02-06
Hello,
I have been trying to install Ubuntu on an external drive which already had two bootable partitions on (an old MacOS and Manjaro). I installed it using a MacBook and an installation usb stick. (Ubuntu 18.04)

Now I am running into a weird problem and I am sure about that I did something wrong.

When booting the PC, I always come into the "grub rescue" menu".
If I type in "ls", I get:
```
(hd0), (hd1), (hd2), (hd3), (hd4), (hd5), (hd6), (hd7), (h8d), (hd9), (hd9,gpt8), (hd9,gpt7), (hd9,gpt6), (hd9,gpt5), (hd9,gpt4), (hd9,gpt3), (hd9,gpt2), (hd9,gpt1), (hd10), (hd11), (hd11,gpt2), (hd11,gpt1)
``` (Typing errors might have occurred).

I am sure about that hd11 is the internal macbook drive, while hd9 is the USB drive.
The drive looks like this (using Gparted):
[ATTACH=CONFIG]284977[/ATTACH]

sdc3 is the swap space, sdc7 is supposed to be the operation system and sdc8 the data folder. (The sizes of the partitions might look weird, but I want it like that).
sdc4 and sdc5 might be from the Manjaro system (it is old, but I use it some times) and sdc6 the macOS (because the new macOS does not allow 32bit applications...)

I originally set the mount points to / and /home at sdc7 and 8 during installation, which is weird.

When I am in the grub rescue mode, typing ls (hdX) or (hdX,y) or (hdX,gptY) outputs "File System unknown" for **all** partition except for sdc5 where it outputs btrfs correctly.

In the Internet, people write quite often, that the following is solving the problem:
set root=(hd5,7)
set prefix=(hd5,7)/boot/grub
insmod normal
normal

But the third line outputs me "no such partition".

I have really no idea what to do. I also tried to install it one more time by just deleting the partitions and doing exactly the same (sometimes it helps), but this did not help.

Many thanks in advance for everybody reading and maybe answering here :)

---

### Post by yancek on 2020-02-06
I expect there are a number of typing errors from your ls output.   According to that output you have 12 physical hard drives ( hd11,gpt2) ,  is that correct?

> (hd0), (hd1), (hd2), (hd3)

The line above lists some of the drive, the numbers referring to the physical hard drive beginning with the number zero.

> (hd9,gpt8), (hd9,gpt7)

The  above lines refer to drive 10 (hd9) and partitions 8 and 7, is that  correct?  Your other references to drives/partitions mention only sdc??   Generally a Linux system will show drives beginning with sda, then sdb,  sdc, etc.

> set root=(hd5,7) 

The set root line you posted above would mean your Ubuntu is on the 6th physical hard drive and 7th partition??

Your GParted output shows 3 Linux partitions plus an EFI partition.  Did you boot and install Ubuntu in EFI mode?  I would suggest you read at least the first part of the Ubuntu page at the link below which describes installing Ubuntu UEFFI (which your Mac is) and it tells you how you can tell if you are booting UEFI.  A lot of the rest of the info is regarding windows and irrelevant but the first part is applicable for any EFI install.

An easier way to determine if you have Ubuntu uefi is to boot the install media, open a terminal, create a mount point for the efi partition and mount it to see if you have an ubuntu folder.  If not, you don't have it install UEFI and I doubt it will boot.

Commands to use from terminal consecutively, hit the enter key after each command:  sudo mkdir /mnt/efi   sudo mount /dev/sdc1 /mnt/efi

You can then navigate to /mnt/efi to check for an ubuntu folder and see what/if anything is there.

---

### Post by dorpapst on 2020-02-08
Hi yancek,
Thank you for your answer. I have actually no idea how they counted the number of hard drives, as of the fact that there where only the internal drive, the external and the usb stick I was booting from.
Thank you for your explanation about what the output of all these things mean. 
Sorry that I did not answer before, but before reading this answer, a friend was repairing my system for me. We used the tool "Boot-Repair" which is recommended on help.ubuntu.com ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and it fixed my problems.


I will keep your advices in mind if something like this happens again.
Cheers!

---

