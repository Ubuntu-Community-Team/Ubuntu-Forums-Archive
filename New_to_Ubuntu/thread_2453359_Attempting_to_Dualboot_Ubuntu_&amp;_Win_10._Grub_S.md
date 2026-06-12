---
title: "Attempting to Dualboot Ubuntu &amp; Win 10. Grub Seems Broken?"
date: 2020-11-08
forum: New to Ubuntu
---

### Post by pepperjack2 on 2020-11-08
Hello!

I'm new to the whole Linux process and I'm attempting to set up dual boot on a Lenovo ThinkPad laptop with Windows 10 and Ubuntu. I'll run through my steps, or what I remember of them, because it seems to have hit a snag somewhere. 

I started with only Windows 10 installed, and had a USB with Ubuntu on it. I partitioned my hard drive (made a separate section of 100 gigs) to use for the Linux installation. To be able to install Ubuntu, I went into the BIOS and changed the boot order until the USB was at the top. Restarted.

Now Linux boots up, and I get options to try it out or to install it. I try to install by following this guide [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)
It seemed that I could only create 4 primary partitions, and Windows already used two, so I decided to use a logical partition type for the swap partition. After this, I continued on, until the installation hit an error and crashed. Something about grub2 failing to install. I managed to solve this somehow, though unfortunately the details escape me. Either way, I later manage to finish the install and restart, and now hit a black screen showing No bootable device. 

Researching that error led me here: [https://askubuntu.com/questions/921857/bootable-device-not-found-ubuntu-16-04-no-option-in-bios-to-select-an-uefi-fil](https://askubuntu.com/questions/921857/bootable-device-not-found-ubuntu-16-04-no-option-in-bios-to-select-an-uefi-fil)
I followed the guide in the first answer. Now my Ubuntu install partitions are one UEFI partition, one swap (logical type), and one with everything else (flagged with '/'). I also followed their advice to use the option to try ubuntu before installing it, so I could enter the terminal commands after installing the OS.

After all this, I seemingly manage to install the bootloader and the OS. Restarting the laptop first gives me a Lenovo screen (instead of the usual ThinkPad one), then a blank purple screen, which I believe is grub. After a few seconds, this disappears and Ubuntu starts loading up, and looks to be perfectly usable. The problem now is that I don't see any way to load Windows. I found some suggestions of running boot repair, and tried that, but it gives off the following error message:
LegacyWindows detected. Please enable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB).
[FONT=verdana][SIZE=2]So I dive back into the BIOS and set the BIOS mode from UEFI only to Both, which includes CSM/Legacy stuff. I also try the 'only Legacy' option. Both of these just give me the old No bootable device error. 

I'm thinking maybe I installed grub incorrectly? I only get that blank purple screen (before the login screen) when booting into Ubuntu. As I understand it, it's supposed to give me boot options. In fact, hitting Escape during the purple screen does give me a few options, but only to boot Ubuntu and to enter the BIOS.

That brings me here. I'm a little hesitant to continue with how little I know of what I'm doing, for fear of messing up big time, but also because I feel like the issue could stem from a million and one things. I don't really know where to look. I'd very much appreciate any help or advice you could give me in trying to clear this up.
[/SIZE][/FONT]

---

### Post by grahammechanical on 2020-11-08
This guide contains some information that your first guide does not mention. It is crucial information

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]


Questions. 1) What mode is Windows 10 installed in? 2.What mode did you install Ubuntu in? 3. Are they the same mode?

Regards

---

### Post by tea for one on 2020-11-08
> **pepperjack2 said:**
> 
I found some suggestions of running boot repair, and tried that, but it gives off the following error message:
LegacyWindows detected. 

Windows 10 requires [COLOR="#0000FF"]UEFI [/COLOR]mode and [COLOR="#0000FF"]GPT[/COLOR] (partition table).
Dual boot on one disk requires both operating systems to be installed in the [COLOR="#0000FF"]same[/COLOR] mode.

For a more seamless experience in the future:-

Back up all your data from both systems.
Prepare your disk with GPT.
Re-install Windows 10 in [COLOR="#0000FF"]UEFI [/COLOR]mode with [COLOR="#0000FF"]GPT[/COLOR]
Boot into Windows and double check the system.
Create some disk space for Ubuntu using Windows tools.
Install Ubuntu in [COLOR="#0000FF"]UEFI [/COLOR]mode with [COLOR="#0000FF"]GPT[/COLOR]
Boot into Ubuntu and double check.
Restore your data when you are happy with the set-up.

Please note:-
How you boot your installation media is how it installs i.e.
Boot USB in UEFI mode = Install in UEFI mode

Here is a link to help you further [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Whoops - Aced by grahammechanical

---

### Post by garvinrick4 on 2020-11-08
Open a terminal:
> blkid
##Mine looks as such.
rick@rick:~$ blkid
/dev/sda7: UUID="ab04e284-0964-42d9-88cd-33214feb2059" TYPE="ext4" PARTLABEL="20.04" PARTUUID="98f563c4-9bbe-4189-b1b9-35dd8c2f9847"
/dev/sda1: UUID="8EEB-4DAA" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="36669f69-0c37-47e3-97c1-d082811c3159"
/dev/sda3: LABEL="Windows" UUID="6AE0CF57E0CF27E1" TYPE="ntfs" PARTLABEL="Windows 10" PARTUUID="3dc97bb3-e056-46f7-88cd-2dd549647fd1"
/dev/sda4: UUID="1e1d7cc0-10ad-46b7-9f08-b866956fde59" TYPE="ext4" PARTLABEL="18.04" PARTUUID="30683286-bc18-45f9-8ea8-90c75664c243"
/dev/sda5: LABEL="Windows RE tools" UUID="021A7AF91A7AE8D5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="57a4ac31-ddfd-4807-9bf3-2213501854f2"
/dev/sda6: LABEL="RECOVERY" UUID="00AED764AED750B0" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="20c16088-7198-41f5-9f7b-b6267ed1f2a8"
rick@rick:~$ 
## Copy and paste yours.

---

### Post by pepperjack2 on 2020-11-08
I'm already glad I posted. I had no idea about the matching types. The tricky part is that it's a little hard to find out now that Windows won't boot. Ubuntu is installed in UEFI mode, I can tell you that much. From what I read, newer Windows computers shipped with Win 8 and above usually use UEFI? I'd say it's pretty likely that mine's using UEFI, in that case. It's only a couple years old, and shipped with Windows 8.

I ran the blkid command. Here's what I got:

/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM_DRV" UUID="A4FCAB88FCAB52FA" TYPE="ntfs" PARTUUID="b362e933-01"
/dev/sda2: LABEL="Windows7_OS" UUID="F8ACAD3FACACF8F0" TYPE="ntfs" PARTUUID="b362e933-02"
/dev/sda3: UUID="9098-2CE7" TYPE="vfat" PARTUUID="b362e933-03"
/dev/sda5: UUID="a8bef615-6adb-496f-a82347abf158" TYPE="swap" PARTUUID="b362e933-05"
/dev/sda6: UUID="5c8bd7aa-b118-4e42-aee5-e32e3295b3fb" TYPE="ext4" PARTUUID="b362e933-06"

Not sure what all the loops are about. Maybe they come from that for-loop command from one of the guides? I also see it says Windows 7, interestingly. Maybe the company I bought it from started with 7, before installing 8? Anyway, sda1 and sda2 are my two Windows partitions. sda3 is the EFI partition for Ubuntu. sda5 is the swap partition, of logical type. And sda6 is the main partition for Ubuntu.

---

### Post by garvinrick4 on 2020-11-09
> sudo fdisk -l

Here is mine:
ick@rick:~$ sudo fdisk -l
[sudo] password for rick: 
Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD10EZEX-60W
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: [COLOR=#ff0000]gpt[/COLOR]
Disk identifier: 55C7F0EE-AA87-42F6-8B2B-7FAA05434F98

Device          Start        End    Sectors   Size Type
[COLOR=#b22222]/dev/sda1        2048     534527     532480   260M [/COLOR][COLOR=#b22222]EFI System[/COLOR]
/dev/sda2      534528     567295      32768    16M Microsoft reserved
/dev/sda3      567296 1748987903 1748420608 833.7G Microsoft basic data
/dev/sda4  1833293824 1927498902   94205079  44.9G Microsoft basic data
/dev/sda5  1927501824 1929508863    2007040   980M Windows recovery environment
/dev/sda6  1929508864 1953511423   24002560  11.5G Microsoft basic data
/dev/sda7  1749049344 1833293484   84244141  40.2G Linux filesystem

Partition table entries are not in disk order.

#Notice the difference between the two both dual booting with Windows :
#Your sda1 is the windows recovery partition that part is fine just the way some are installed.
#Highlighted lines notice EFI and above gpt

---

### Post by pepperjack2 on 2020-11-09
Here's my fdisk command run:

Disk /dev/loop0: 34,7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 2,3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 14,5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 140,9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 86,9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 3,7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb362e933

Device       Boot  Start         End           Sectors      Size      Id   Type
/dev/sda1          2048          6219775     6217728     3G       7    HPFS/NTFS/exFAT
/dev/sda2          6219776     290196143  283976368  135,4G 7    HPFS/NTFS/exFAT
/dev/sda3  *      290197504  290586623  389120       190M   ef   EFI (FAT-12/16/32)
/dev/sda4          290588670  500117503  209528834  99,9G  5     Extended
/dev/sda5          290588672  298399743  7811072     3,7G    82   Linux swap / Solaris
/dev/sda6          298401792  500117503  201715712  96,2G  83   Linux

Does the EFI partition have to be sda1? Is it possible to rearrange partitions like that without messing up the data within?

---

### Post by garvinrick4 on 2020-11-09
Notice the disk label dos which means the old mbr instead of gpt and an EFI on sda3 
As stated before me by "tea for one" Windows 10 needs gpt.
You wont need extended partition with logicals inside with gpt can handle all primaries.
You have to do what "tea for one" stated where windows has EUFI also .
Wanted to show you how to check to see what is wrong so you understood why. 
Do you have your Windows install disk?

---

### Post by yancek on 2020-11-09
I would suggest you read through the link to the official Ubuntu documentation on dual booting wiith windows from the link in post 2.  Your last post clearly shows you have a Legacy/MBR install of windows:  Disklabel type: dos

If you look at your last post, the fdisk output also shows an Extended partition which means a Legacy install as Extended partitions are not used on GPT disks.  Set your BIOS to enable Legacy/CSM and reinstall Ubuntu.

---

### Post by pepperjack2 on 2020-11-12
Had a couple busy days, but I'm back and ready to keep tackling it.

Absolutely, garvin, and I appreciate the opportunity to learn more about it! 
As for an install disk, I'm afraid not. The laptop came with Windows 8 preinstalled. (Which I later upgraded to 10)

So, from yours and yancek's replies, you've informed me that Windows did in fact use the Legacy version, not UEFI. I'm going to take your advice and try to reinstall Ubuntu in Legacy mode. Luckily, in the UEFI link up above, there's a section about converting Ubuntu from UEFI to Legacy mode. I'll give that a shot, and see what happens.


Update: I followed the instructions there, but there wasn't much to report. 1. was skipped because I have no GPT disk. 2-4 didn't need changing, because the Separate /boot/efi option was already unticked. So I just switched the BIOS boot option from UEFI to Legacy, and we're back to the No bootable disk error. Looks like I'll have to reinstall Ubuntu. 

I was a little unsure about the partition scheme now that I presumably didn't need the EFI partition anymore, so I found this guide to follow: [https://medium.com/isdanni/ubuntu-18-04-lts-dual-boot-with-win10-bios-legacy-mbr-c2d12308374c](https://medium.com/isdanni/ubuntu-18-04-lts-dual-boot-with-win10-bios-legacy-mbr-c2d12308374c)

However, I seem to have run into the same problem I had before. The installer crashes citing an error: GRUB installation failed. It reads: The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.

---

### Post by CelticWarrior on 2020-11-12
Unlike Windows, Ubuntu is very flexible about installation modes. Your drive is already "msdos" (MBR) so all it takes is uninstall the UEFI bootloader and install the BIOS/Legacy bootloader in the MBR.

But, again, it's better to have both in UEFI mode.
It's unusual to have a preinstalled Windows 8 in Legacy mode (on UEFI hardware). Have you bought it used/refurbished? If so then it can be anything. Otherwise, Microsoft forced all manufacturers to install in the proper (UEFI) mode since 2012.

---

### Post by pepperjack2 on 2020-11-12
As far as I know, it's not used or refurbished, but the company I bought it from did make some basic installations of operating systems and whatnot. If it's better to have both in UEFI mode, I could change it to that, but I'd probably need to be able to access Windows to do so. Right now, I can only get Ubuntu to boot, and I can only get Ubuntu to install correctly in UEFI mode.

---

### Post by CelticWarrior on 2020-11-12
No, you don't need access to the installed Windows in order to install Windows in UEFI mode. Actually you can't change it to UEFI, unlike Ubuntu.

---

