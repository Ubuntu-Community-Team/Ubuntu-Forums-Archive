---
title: "Ubuntu studio 24.10. newby"
date: 2024-10-22
forum: New to Ubuntu
---

### Post by planemad on 2024-10-22
Hi . I'm new to Linux. I'd like to try the latest Ubuntu studio, installed on USB drive with persistence. 
I'm trying to install to my surface pro 5.
USB drives, 32gb and 128gb(new)
I've tried both drives. Flashed the iso with rudus, booted, got to the manual partitioning page of the install, but can't get any further. I can't check the boxes for the drives..
I managed to get gparted installed, by copying the iso to the drives and install from the terminal commands. The drives are already unmounted .
The drives are on a USB hub, as the surface pro only has the one usb3 port.
If anyone has some ideas I can try that would be great thanks in advance.

---

### Post by TheFu on 2024-10-23
So, people new to Linux shouldn't use non-LTS releases.  There are too many reasons for this, but at least you've been told.  The most recent LTS release is 24.04.x.  That's what most people should install.  If you don't, be ready to do a fresh OS install every 6 months for the next 18 months until the next LTS release happens and provides 3 yrs of support.

Trying to run any Linux off check flash storage will be slow. Perhaps you would be better off using a USB SSD instead and doing a proper install.  Trying to use persistent storage for with an ISO is going to become a hassle after about a month as more and more patches have to be overlay-ed.

There's a reason some things aren't generally done.  It would be smart to pay attention, especially when you are knew to Linux.

BTW, USB hubs tend to break things, so that's another consideration.

I didn't mean to be so negative, but best to be told the truth before you waste so much time on a poor solution at best or in multiple failed attempts at worst.

---

### Post by grahammechanical on 2024-10-23
> but can't get any further. I can't check the boxes for the drives..

I think that you have to first select the drive to install the bootloader files. Then you should be able to select a drive or partition and click Change.

Regards

---

### Post by planemad on 2024-10-24
Awesome. Thanks for the help! &#55357;&#56898;

---

### Post by planemad on 2024-10-26
Oh well. That didn't work. Just trying a test installation away from the internal SSD, to see if I can install it.
I flashed 24.04. can't get past the manual partitioning page. Can't check any boxes, can select anything to install boot loader and next button stays greyed out. Any suggestions would be great. Thanx

---

### Post by davetheoldcoder on 2024-10-26
I recall that the 24.04 Manual Partitioning page was tricky, and the documentation doesn't help. It only says:
> Manual partitioning is designed for advanced users who want to create  specific configurations for their use-cases. As such we assume that  these users will be comfortable with this interface and will not go into  detail during this tutorial on specific setups.
[https://ubuntu.com/tutorials/install-ubuntu-desktop#manual-partitioning](https://ubuntu.com/tutorials/install-ubuntu-desktop#manual-partitioning)

Unfortunately, I didn't take notes. But if I recall correctly, it doesn't let you select existing partitions, but rather it forces you to create the partitions using its interface, in a specific order.

If you can post a screenshot or photo of the place where you're stuck, that might jog my memory.

---

### Post by planemad on 2024-10-26
Hi. Thanks for the reply.

---

### Post by planemad on 2024-10-26
Thanks for the reply. It's a bootable USB drive with the Ubuntu iso, so i don't understand the bitlocker bit, and the manual partitioning page/photo.. I can't do anything there, nothing seems to work there.? Thanks

---

### Post by tea for one on 2024-10-26
> **planemad said:**
>  i don't understand the bitlocker bit, and the manual partitioning page/photo.
> Disabling Windows BitLocker is not required when fully erasing Windows or when there is a separate, unencrypted drive available for Ubuntu

More info here (especially sections 6 and 13) [https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation)

Please specify what you wish to do:-
Install to another disk?
Remove Windows completely and install Ubuntu 24.10 to your internal nvme disk?

Also, have a look at further information about your device
[https://github.com/linux-surface/linux-surface](https://github.com/linux-surface/linux-surface)
[https://github.com/linux-surface/linux-surface/wiki/Supported-Devices-and-Features#feature-matrix](https://github.com/linux-surface/linux-surface/wiki/Supported-Devices-and-Features#feature-matrix)

---

### Post by TheFu on 2024-10-26
> **planemad said:**
> Thanks for the reply. It's a bootable USB drive with the Ubuntu iso, so i don't understand the bitlocker bit, and the manual partitioning page/photo.. I can't do anything there, nothing seems to work there.? Thanks

You can't install to the same flash drive that is running the installation ISO.  You need 2 flash drives.  ISOs are read-only, even when placed onto re-write media like a flash drive.

---

### Post by planemad on 2024-10-26
Thanks for the reply. Yes. I watched a YouTube vid about the 2 USB drives. I think it was one of the first things I tried a week or so ago. Thanks for the reminder. I'll revisit that process and see if I have more luck. I bought a new 128gb USB drive to try that. Is there any prep I should be aware of for that drive? Thanx&#55357;&#56898;

---

### Post by planemad on 2024-10-26
Thanks for the replies. I'm definately going for separate install to external USB drive or ssd. I don't want to risk interfere with the internal or windows. My surface pro has an internal SSD. An external SSD has comparable specs, plus I can try it on my old Dell XPS. It's a test process really, performance etc. Thanks:P

---

### Post by tea for one on 2024-10-26
> **planemad said:**
>  I'm definately going for separate install to external USB drive or ssd. I don't want to risk interfere with the internal or windows.
Are you completely familiar with the task?
One USB disk containing the Ubuntu installer and a target destination disk, where the installed system will eventually reside.
If so, boot the installer, open a terminal and enter:-
```
sudo parted -l
```
Please post the command and output in code tags.
This will show if your target disk is accessible.

---

### Post by TheFu on 2024-10-26
Generally, there's only one UEFI partition for a system and it would be shared by all OSes that can be booted.  I suppose there's an EFI boot manager screen on some systems to allow selecting which OS to be booted. I know nothing about those.   

I've seen recommendations that the drive you don't want touched to be disconnected during an install to ensure it isn't touched. Can you do that?

---

### Post by planemad on 2024-10-27
Thanks for the reply. I remember, and I tried that. I've tried again. The 2nd USB drive doesn't show up as an option in install, just the main internal drive. I've tried 2nd drive mounted, unmounted. It's 128gb formatted to fat 32

---

### Post by planemad on 2024-10-27
sudo parted -"l"
i dont think ive ever seen that symbol on the end

---

### Post by davetheoldcoder on 2024-10-27
> sudo parted -"l"

That should be:
```
sudo parted -l
```
or:
```
sudo parted --list
```

---

### Post by oldfred on 2024-10-27
While the installer uses FAT32 for boot, an install must be a Linux partition, default is ext4.

But if installing to an external flash drive or SSD, best to use gpt partitioning & have ESP - efi system partition and the LInux partition on external drive. Default typically is to to install boot loader (grub) to first drive or internal drive. That is why we often suggest disconnecting all other drives. Some UEFI allow turning off/disabling a drive in UEFI settings.

If you have ESP on external drive, then you can boot it just like you boot live installer on any system using  a drive entry by label/brand or drive. If always using with one system then you typically have an "ubuntu" entry.

My external M.2 SSD, internal NVMe drive is now just Windows. I do use a data partition and keep / (root) a bit smaller, but new users probably should just have /, unless drive is very large.
```
[FONT=monospace][COLOR=#54ff54]**fred@m2-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblkt [/COLOR]
MODEL                         NAME        FSTYPE   SIZE FSUSED LABEL       PARTLABEL                    MOUNTPOIN UUID 
Samsung SSD 850 EVO M.2 250GB sda                232.9G                                                            
                              &#9500;&#9472;sda1      vfat     510M  10.4M             EFI System Partition         /boot/efi A02D-F0F6 
                              &#9500;&#9472;sda2      vfat     5.9G        m2_fat      m2_fat                                 4738-7B8C 
                              &#9500;&#9472;sda3      ext4    35.2G   9.7G m2-noble    m2_noble                     /         09a68bbd-3d26-4630-b18e-7c687761aa36 
                              &#9492;&#9472;sda5      ext4   127.4G  22.6G m2_data     m2_data                      /mnt/data 0c374965-53c6-437c-a2ad-f0508486f9d5
[/FONT]
```

---

### Post by tea for one on 2024-10-27
> **planemad said:**
> Thanks for the reply. I remember, and I tried that. I've tried again. The 2nd USB drive doesn't show up as an option in install, just the main internal drive. I've tried 2nd drive mounted, unmounted. It's 128gb formatted to fat 32
Power off
Attach both external disks (installer disk and target disk)
Access your UEFI settings via your PC dedicated key
Does the PC recognise both the external USB devices?

> **planemad said:**
>  My surface pro has an internal SSD. An external SSD has comparable specs, plus I can try it on my old Dell XPS.
Any joy with your Dell XPS?

---

### Post by planemad on 2024-10-28
Thank you for the replies. I'll put more time into it shortly. I've got gparted iso and zip. I'm not too sure how to install it tho. I've tried sudo apt-get install gparted. Sum errors come up at the bottom of the code. But anyway awesome helpful suggestions. Thanks!

---

### Post by planemad on 2024-10-28
Installation on the XPS nearly worked. Managed to start install to the 2nd drive(new Kingston 128gb). I guess it froze somewhere, black screen and definately couldn't assign that drive in the boot order in the bios. It shows up but can't be put into a bootable option

---

### Post by planemad on 2024-10-28
I managed to start installation to the 2nd drive(new Kingston 128gb) on the XPS, but ended up black screen and couldn't set the Kingston drive as a boot option in the bios

---

### Post by planemad on 2024-10-30
I think I finished install to 2nd flash drive(128 new Kingston). Couldn't get past the password at the end. & Can't boot into it at startup. Progress, any way

---

