---
title: "Grup update problem on Xubuntu 18.04 install for Win-7 dual boot"
date: 2018-09-14
forum: New to Ubuntu
---

### Post by browser_ice2 on 2018-09-14
Hi, it has been almost 3 years since last time I had a Linux on my PC.  I tried installing Xubuntu 18.04 and create a dual boot with my Windows-7. At the end of the installation it said it could not create the bootloader.  No matter what choice I did (cancel, continue, ...) pressing the OK button did absolutly nothing. I had to reset my PC.  I am using the Live CD to write this post.  How do I successfully create the dual bootloader?  It says it is a fatal error.

My current set up is : SDA = 2nd HD, SDB = Win-7 , SDC=free

When it was time to select which device to install the bloadloader, I selected /dev/sdb.  

I just tried again choosing /dev/sdb1 but if tailed on the same thing

> Disk /dev/loop0: 1.3 GiB, 1358487552 bytes, 2653296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0001e20e

Device     Boot    Start        End    Sectors   Size Id Type
/dev/sda1           2048   31459327   31457280    15G  7 HPFS/NTFS/exFAT
/dev/sda2       31459328   39847935    8388608     4G  7 HPFS/NTFS/exFAT
/dev/sda3       39847936 1953519615 1913671680 912.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1F1B9C3E-54B2-4B2E-BA61-67C77078DDC7
[COLOR=#0000ff]
Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    206847    204800   100M EFI System
/dev/sdb2     206848    468991    262144   128M Microsoft reserved
/dev/sdb3     468992 134219775 133750784  63.8G Microsoft basic data
/dev/sdb4  134219776 488396799 354177024 168.9G Microsoft basic data[/COLOR]


Disk /dev/sdc: 55.9 GiB, 60022480896 bytes, 117231408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 72E97598-ACDD-4AB8-9E6B-0633F74D2328

Device        Start       End  Sectors  Size Type
/dev/sdc1      2048  85229567 85227520 40.7G Linux filesystem
/dev/sdc2  85229568 117229567 32000000 15.3G Linux swap


---

### Post by yancek on 2018-09-14
Your output shows a 1TB drive and a 232GB drive neither of which shows a Linux filesystem.  On which drive did you try to install Kubuntu?  I notice also that the larger drive is dos (Legacy) and the smaller drive is gpt and on the smaller drive you have an EFI partition.  Mixing a Legacy install with an EFI is always problematic.  You should do both the same, either both Legacy or both UEFI.  Generally you will need free/unallocated space on which to install a Linux system if you already have windows and that should be done from windows by shrinking the largest windows partition.  Since windows 7 by default was a Legacy rather than an EFI install, it would be best to install Kubuntu Legacy.

---

### Post by browser_ice2 on 2018-09-14
I have 3 hd
/SDB = 1TB HD
/SDA = 256GB SSD  (this is where my Windows is)
/SDC = 57GB SSD (this is where I tried to install Xubuntu and its already only for Xubuntu)

I tried to boot back to Windows but my MBR is damaged.   Just to make it more fun,  my Win-7 CD seams damaged because I cannot boot from it to repair it.  

I did not have the 1tb at the beginning. I just added it 3 year ago.  Had my Win-7 for 6 years.  I do not know how come I have both Legacy and EFI.

I am currently looking at options using Syslinux to fix my MBR but I noticed it is EFI.  Could that be the problem ?

3 years ago I had the same exact Win-7 and had a dual boot back then. But I do not recall if the MBR was an EFI or BIOS one.

Second, how can I find out if the Xubuntu ISO I got is EFI or Legacy ?


[edited]
I read else where "All systems pre-installed with Windows XP, Vista or 7 32-bit,  irrespective of Service Pack level, bitness, edition (SKU) or presence  of UEFI support in firmware, boot in BIOS/MBR mode by default." so this means my MBR should be in BIOS boot mode. I assume this is what you meant by legacy.  I do not know if my MBR got switched to EFI when I first tried to inxtalled Xubuntu 18.04 but if my MBR HAS to be in BIOS/Legacy then I need to fix this first.
So the resolution is to have everything as Legacy ?   How can I have this without reinstalling everything ?

---

### Post by browser_ice2 on 2018-09-14
I fixed the grub using boot-repair in the live CD.  Now I can boot into my installed Xubuntu.  

However, my Windows-7 is completly missing from the installed grub.

I will do research to find out how but if someone can tell me faster, I would appreciate it.

---

### Post by yancek on 2018-09-14
> I fixed the grub using boot-repair in the live CD.  Now I can boot into my installed Xubuntu.  

That's a good step, progress.  I missed the sdc when I last posted.  Your Xubuntu install there is a Legacy/MBR install but it is GPT  rather than DOS.  I'm not sure if Grub on a non-efi system will detect and create a boot entry for an EFI install of windows which is what shows on your sdb.  Try booting the installed Xubuntu and run the following command:

```
sudo update-grub
```

You will be prompted for your primary user password you just created during the install so enter that and watch the output for a windows entry.  If you see one, reboot and try booting windows.  If that fails, I would suggest running boot repair again but this time don't try any repairs but select the option to Create BootInfo Summary and when it finishes, it will give a link to post here and members here will then be able to view more details on your systems, specifically on the various boot files.

---

### Post by oldfred on 2018-09-14
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.

Since your Windows is on a gpt drive, you must have Windows 7 in UEFI boot mode. That is a bit unusual as default installs from DVD are BIOS only, but there are instructions to copy to flash drive and move/rename a couple of files to make Windows 7 installer UEFI bootable.

But both Windows & Ubuntu install in the boot mode that you boot install media. So you have to from UEFI boot menu choose UEFi or BIOS version of installer. You may need settings in UEFI to allow UEFI or BIOS boot and UEFI settings for USB to allow UEFI or BIOS boot. And then they must match your actual install.

You can have a MBR data drive with UEFI systems. But generally better to only use gpt or plan conversion to gpt for all new drives when you start using UEFI.

Part of your issue may be that sda is the MBR drive. Grub wants to install to an ESP in a gpt partitioned drive that is the first drive or sda.
And sda is mostly determined by UEFI/BIOS and then by port order on motherboard.
Best to have first boot drive, your SSD as SATA0, second SSD as SATA1 and then any data drives in later SATA ports.
Then UEFI install of Ubuntu should work without issues.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

