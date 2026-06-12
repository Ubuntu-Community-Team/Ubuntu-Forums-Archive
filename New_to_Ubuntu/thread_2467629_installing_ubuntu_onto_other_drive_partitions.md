---
title: "installing ubuntu onto other drive partitions"
date: 2021-10-02
forum: New to Ubuntu
---

### Post by torrtoise on 2021-10-02
i have a 512gb SSD mid-range laptop running on windows, and have been for a long time. i'm thinking of making a dual boot, and I want to install the ubuntu files onto my other drive partition (for example, right now i'm using the C: partition as my main one, with ~400 gigs in size, and then another ~100 gb D: partition, running on the same SSD, both formatted in NTFS). is it possible to install it onto there instead of on the entire SSD? just asking, since i don't want to accidentally install it onto my main C: drive.

keep in mind i'm not very talented with ubuntu.

---

### Post by psychohermit on 2021-10-02
You can install to the D partition but it's going to have to be formatted for Linux.  The installer will give you the opportunity to format it.

---

### Post by tea for one on 2021-10-02
Here is a little check list for dual booting.
The info was gleaned via an array of forum posts relevant to dual booting.
Not all are applicable in every case.

_General Observations for Dual Boot Windows 10 & Ubuntu Family_

Backup your data
Both systems in UEFI mode with GPT
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

_UEFI settings_

Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM
Disable Optane memory and storage

_Windows 10_

Backup your data
Turn off Bitlocker 
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

_Ubuntu Family_

Boot into a live session in UEFI mode (how you boot determines the installation mode)
Check wifi, sound, graphics, mouse, keypad etc
Install Ubuntu in the free space previously created (or your own partition scheme e.g. separate root and home)
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Grub will find the EFI partition already used by Windows
Sometimes (although very rare) internet connection prevents clean installation

---

### Post by torrtoise on 2021-10-02
Can I use some external tool to quickly format it for Linux instead of doing it in the installer?

---

### Post by grahammechanical on 2021-10-02
I am a bit confused? How many drives do you have? One 512GB SSD? And another drive?

Please keep in mind that we use Windows tools to create, move, shrink, expand or delete Windows partitions. And we use Linux tools to create, move, shrink, expand or delete Linux partitions.

With spinning disks it is always best to defrag Windows before and after doing things to the partitions. Also make sure that Windows is still loading. I am not familiar with Solid State Drives. So, I do not know if the advice to defrag is still relevant.

You will need to create unallocated space by shrinking and moving Windows partitions. Into that space we use a Linux partition manager to create one, two or three Linux partitions that can be used by Ubuntu.

A single 100GB partition for Ubuntu is the most simple case for installing Ubuntu. Some of us prefer to have at least two partitions. One 25GB (minimal) partition for Ubuntu and the rest for the user's home partition. The user's home partition will be where the user's configuration files and documents will go. It makes it easier to re-install Ubuntu without loosing data and documents.

Regards

---

### Post by torrtoise on 2021-10-02
> **grahammechanical said:**
> I am a bit confused? How many drives do you have? One 512GB SSD? And another drive?

Please keep in mind that we use Windows tools to create, move, shrink, expand or delete Windows partitions. And we use Linux tools to create, move, shrink, expand or delete Linux partitions.

With spinning disks it is always best to defrag Windows before and after doing things to the partitions. Also make sure that Windows is still loading. I am not familiar with Solid State Drives. So, I do not know if the advice to defrag is still relevant.

You will need to create unallocated space by shrinking and moving Windows partitions. Into that space we use a Linux partition manager to create one, two or three Linux partitions that can be used by Ubuntu.

A single 100GB partition for Ubuntu is the most simple case for installing Ubuntu. Some of us prefer to have at least two partitions. One 25GB (minimal) partition for Ubuntu and the rest for the user's home partition. The user's home partition will be where the user's configuration files and documents will go. It makes it easier to re-install Ubuntu without loosing data and documents.

Regards

I tried to attach an image on how my stuff looks. I have this C: drive, A: drive, and another (not shown) F: drive, with 60 and 40 gb respectively, totaling to 100gb (i was planning on merging them) and then an USB with 32 gigs, that I will be installing Ubuntu from. I wanted to know if I can put the Ubuntu files on the A: or F: drive (or alternatively D: drive), instead of my C: drive.

---

### Post by torrtoise on 2021-10-02
Oh, yeah, my disk management looks like this.

---

### Post by grahammechanical on 2021-10-02
> Can I use some external tool to quickly format it for Linux instead of doing it in the installer?

Yes, but forget about quickly as that is when mistakes happen. We install Ubuntu from a USB memory stick that has had a Ubuntu ISO image burned to it. How to do this from Windows:

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

We boot from the Ubuntu memory stick and run the TRY Ubuntu session and then we use a utility called GParted.  

[https://gparted.org/](https://gparted.org/)

This is an official installation guide.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Edit: Please download and study the GParted manual. This utility is included in the Ubuntu installer. No need to download it.

Regards

---

### Post by tea for one on 2021-10-02
> **torrtoise said:**
> Oh, yeah, my disk management looks like this.

Where is the 100GB partition mentioned in Post no. 1?

---

### Post by ajgreeny on 2021-10-02
Also remember that when Windows mentions Disks, eg C:/ and D:/ etc etc it usually means partitions, not drives at all, totally confusing those of us who don't use Windows any more and use Linux only.

Once you have booted to a live Ubuntu system as recommended by [COLOR="#B22222"]grahammechanical[/COLOR] open a terminal with Ctrl+Alt+T and run command ```
sudo fdisk -l
``` then copy back here all of the output you see by highlighting the text in terminal with the mouse, right clicking and choosing Copy, then coming back here to paste it into your reply.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by ActionParsnip on 2021-10-02
Yeah the whole misnaming of "drives" in Windows is very annoying and inaccurate.
Linux cannot be installed into NTFS so you'll need to make some room for the OS. If you use the Windows disk manager and shrink one of your NTFS partitions then you can tell the installer to use the free space for Ubuntu. I suggest about 40Gb to be comfortable. Depends what you want to use Ubuntu for. Obviously more space is better.
As stated before, run a final full backup of the data you need as you are making a huge change to the system.

---

### Post by torrtoise on 2021-10-02
I have 1 40 and 1 60 gb partition, that I was planning on putting together.

---

### Post by torrtoise on 2021-10-02
> **ActionParsnip said:**
> Yeah the whole misnaming of "drives" in Windows is very annoying and inaccurate.
Linux cannot be installed into NTFS so you'll need to make some room for the OS. If you use the Windows disk manager and shrink one of your NTFS partitions then you can tell the installer to use the free space for Ubuntu. I suggest about 40Gb to be comfortable. Depends what you want to use Ubuntu for. Obviously more space is better.
As stated before, run a final full backup of the data you need as you are making a huge change to the system.


Sorry, I didn't know Windows named them differently. Sounds dumb. Thanks, though.

---

### Post by indirbak on 2021-10-02
thank you this information. I want to install usb. how do &#305; install?

---

### Post by torrtoise on 2021-10-02
> **ajgreeny said:**
> Also remember that when Windows mentions Disks, eg C:/ and D:/ etc etc it usually means partitions, not drives at all, totally confusing those of us who don't use Windows any more and use Linux only.

Once you have booted to a live Ubuntu system as recommended by [COLOR=#B22222]grahammechanical[/COLOR] open a terminal with Ctrl+Alt+T and run command ```
sudo fdisk -l
``` then copy back here all of the output you see by highlighting the text in terminal with the mouse, right clicking and choosing Copy, then coming back here to paste it into your reply.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

```

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 2.06 GiB, 2213470208 bytes, 4323184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.45 MiB, 58142720 bytes, 113560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 32.27 MiB, 33841152 bytes, 66096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 51.04 MiB, 53522432 bytes, 104536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 218.99 MiB, 229629952 bytes, 448496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 64.77 MiB, 67915776 bytes, 132648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: WDC PC SN720 SDAPNTW-512G-1006          
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7A42623D-EFB7-4570-AD4D-2D1B6C2E7249

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     534527    532480   260M EFI System
/dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296  874428095 873860800 416.7G Microsoft basic data
/dev/nvme0n1p4 874428416  875640831   1212416   592M Windows recovery environmen
/dev/nvme0n1p5 875640832 1000212479 124571648  59.4G Microsoft basic data


Disk /dev/sda: 28.91 GiB, 31042043904 bytes, 60628992 sectors
Disk model: USB DISK 2.0    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00ff1d34

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 60628991 60626944 28.9G  c W95 FAT32 (LBA)


Disk /dev/sdb: 14.84 GiB, 15931539456 bytes, 31116288 sectors
Disk model: MassStorageClass
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1        8192 31116287 31108096 14.8G  c W95 FAT32 (LBA)

```

Does that work?

---

### Post by grahammechanical on 2021-10-02
@indirbak

Please start your own thread and then we can give advice that is relevant to your situation and needs. I have learnt a lot from reading threads in this forum. In my second post in this thread I gave links to ubuntu.com that held instructions on how to do what you want. Or, go to ubuntu.com and click on Downloads and a page will open that will give you links to the information you ask for. For advice specific to your needs, please, open your own thread.

Regards

---

### Post by torrtoise on 2021-10-02
Okay, slight update: I'm typing this from a live USB. I formatted my partition with the fdisk command (I sincerely hope that works). Now, how do I choose it if I run the installer?

---

### Post by westie457 on 2021-10-02
Before you go any further, which partition did you format? 
Your previous post did not show any Linux partitions. 
Please post another ```
sudo fdisk -l
```

---

### Post by ajgreeny on 2021-10-02
Well, you have only the one drive in the machine, probably a Western Digital 500G SSD
```
Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: WDC PC SN720 SDAPNTW-512G-1006
```
and two USB drives detected.

If you decide to dual boot you will need to shrink one of the current partitions on the SSD, the largest being ***[I]/dev/nvme0n1p3*[/I]** at 416.7G, but I do not know enough about Windows to be sure that is the one to shrink. I will leave others to advise you on that.

However, whichever partition you do eventually shrink, leave it as unallocated free space, and **do not attempt to create a new partition in that free space while running Windows**, as it may create a Windows dynamic partition, totally unusable by Linux.

---

### Post by tea for one on 2021-10-02
```
Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     534527    532480   260M EFI System
/dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296  874428095 873860800 416.7G Microsoft basic data
/dev/nvme0n1p4 874428416  875640831   1212416   592M Windows recovery environmen
/dev/nvme0n1p5 875640832 1000212479 124571648  59.4G Microsoft basic data - [COLOR="#0000FF"]Is this for Ubuntu?[/COLOR]
```

You have 59.4GB for Ubuntu?
You originally mentioned 100GB and it is not visible?

Please spell out exactly where you wish to install Ubuntu?
Have you already backed up your Windows personal data - this is essential?

---

### Post by C.S.Cameron on 2021-10-02
tea for one

Nice checklist.

The only thing I would add is to use Windows Disk Management to make new space for the Ubuntu partition and not GParted.

---

### Post by tea for one on 2021-10-03
@C.S.Cameron

Thank you for your kind comment.
I did mention Windows tools in my little list (under Windows 10 section)
> Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
I would love to add more pertinent details to the list if you can think of any.

---

### Post by yancek on 2021-10-03
As has been pointed out above, the Drive/Partition Labels using letters of the English alphabet is specific to windows and refers to partitions.  A C:\ drive is a partition but can take up the whole drive.  This labeling system is something microsoft copied from CP\M and IBM systems which were more commonly used in the 1970's.  And also, remember as stated above, you can't install and have any functioning Linux system on these partitions as any partitions with a label such as this is a windows formatted drive.  Windows does not give labels such as D C to Linux partitions.

Since you are using windows 10 and you have a UEFI installation of windows, you need to install Ubuntu UEFI.  The site at the link below is the official Ubuntu documentation on dual booting windows with Ubuntu in UEFI mode so I would certainly suggest you read that if you have not (the link is posted above also in post 3).  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

