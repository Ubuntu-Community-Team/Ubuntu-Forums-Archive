---
title: "installed ubuntu alongside Windows 8. Will EFI partition @ 100 mb be an issue?"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by cadenza2 on 2014-04-23
Complete beginner here who wanted to try out Ubuntu. Have an HP pavillion 23 (nothing special). 
I previously had Windows 7, then upgraded to Windows 8 (UEFI system, but no secure boot).
Installed Ubuntu 14.04 alongside Windows 8; shrank C: disk to make seperate partitions /, /HOME, and swap (this I just followed from an easy guideline to dual-boot installation so I'm aware some of this may have been unneccessary). Pretty much had no problems there. Once installed, had my grub2 menu with windows and ubuntu options available. Have been able to boot into both without any real issues.

However, one thing did concern me was the fat32 EFI boot/partition which was 100 mb. After extensively reading about uefi, I noticed many guidelines for those needing to create an EFI partition to be atleast 300-500mb. My EFI partition was made by Windows 8 presumably, and considering it's the first partition, there doesn't seem to be any workaround to expanding it (or is there?).

Will this be an issue later on? Right now, most of the HDD (1TB) is unused (did a reformat prior to all this - so windows 8 and ubuntu basically have no apps).
Is there a way to expand this partition? Is it fine as is? Or if not, create a new one to boot one/both OS from it? I'd rather do any fixes now before it crashes down the line.

Thanks for any help.

---

### Post by oldfred on 2014-04-23
I also suggest a larger efi partition, but that is more that even a bit larger one does not use much space on new hard drives.

But even with both Windows & Ubuntu you are not using a lot of the 100GB.
It just is in the future you may want to have more UEFI based software in the efi partition. I have not seen anyone do much with that, but you can even use it as a boot partition.

If would be very difficult to expand at this point and I would not worry about it.  By the time you may want the larger efi partition, you may have a new hard drive anyway.

---

### Post by cadenza2 on 2014-04-23
So it looks like I'm just stuck with it, but it's nothing too much to worry about.

Thank you for the helpful answer.

---

### Post by simon32 on 2014-04-23
I had the problem of installing windows 8 alongside ubuntu 14.04 LTS for four days. All that time I was just following the instructions on this website and other websites but non beared fruit. I will show you how I came to manage that issue very easily.
First of all I am using Lenovo B590 with 500GB storage and a 2.20GHZ intel pentium processor.

1. My computer BIOS setup has an option for select both UEFI and Legacy(BIOS for Lenovo) so I used that default setting.
2. If you have already installed windows 8, just go to my computer then drive C: and partition another drive D: from there(use this if you had no partition in the beginning).
3. If you had a Drive D: partition, make sure it's over 50GB and it's empty.i.e you can move the contents to another drive.
4. Now I assume you have a DVD for installing ubuntu or a USB flash drive, boot the system and from BIOS menu boot from the media which you intend to install ubuntu from.
5. Once the ubuntu installation window pops up, click continue until the point where you ask to specify whether to erase the whole disk or use third party software. Please DO NOT and I repeat DO NOT select the third party software option, just leave it on erase whole disk and click continue.
6. The next window should be the Installation type window and has the option for setting partitions and so on. From the partitions displayed i.e. sda...etc, you can be able to see and recognize the partition you created in windows using the size you assigned it during partitioning. You might have noticed that the partition drive is not the same as it is in windows.
7. Select that partition and click on **change** and the **edit partition** window pops up.
8. This is where the mud that caused me to stuck for 4 days exist. On the** use disk as**...menu select ext4 journal file etc.
9. On the** mount as**...menu set like this.. **/boot** so that ubuntu will use the entire partition for swap area and so on. The instruction to partition some space for **/,/home **etc will just complicate the whole process.
10. Click Ok and the install now. The installation will complete and ubuntu will ask you to restart. **Just click Restart**
11. After restarting the ubuntu **Grub** menu for dual boot will appear, now select windows(sda.....blah!) and press Enter. Windows will just boot and after "Please wait" it will resume as normal.
12. When you log into windows and open my computer you will realize that the partition you created earlier is somehow inactive, this is because Ubuntu uses it entirely.

That's the whole simple process of creating  dual-boot machine with Ubuntu 14.04 LTS and windows 8 Pro. The better side of this simpe procedure is that you'll avoid Wibi installation and deactivating of secure boot in your BIOS.

---

### Post by cadenza2 on 2014-04-23
Wait, so is your /boot partition 50g? For both ubuntu + efi boot? I'm  not well versed in all this, so I have a very beginner's knowledge what  all this means.
How does this affect the EFI partition that Windows creates at the beginning? (100mb). 

Here's  what I did for clarification: reformatted comp with Windows 7 installed  (factory settings that came with desktop), upgraded to Windows 8.
For ubuntu install: Shrank C:/ (Windows partition) to creat unallocated space for ubuntu + /home partitions.

Partitions prior to ubuntu install: **EFI boot/100mb**, unknown 128 mb, C:/Windows, **D:/Recovery/10gb**
After ubuntu install: EFI/boot 100mb, unknown 128 mb, C:/Windows, **/ , /Home , swap** , D:/recovery
**What does creating /boot do in this situation considering one already exists?**

machine specs: hp pavillion 23-1014. 2.8ghz, 4gb ram
Thanks for any help.

---

### Post by oldfred on 2014-04-23
You cannot just have a /boot partition.
And a /boot partition is not the same as a partition with the boot flag.

And most desktops do not need /boot as a separate partition, some with server type installs using RAID or LVM especially with encryption may need a /boot.

Ubuntu's minimum requriement and default install for new users is just / (root) & swap. For new users that is all that is required. 
But if a large / partition over 25 to 50GB then splitting into / & /home or adding data partitions may make sense.

---

