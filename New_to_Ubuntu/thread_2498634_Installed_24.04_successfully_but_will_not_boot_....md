---
title: "Installed 24.04 successfully but will not boot ..."
date: 2024-06-22
forum: New to Ubuntu
---

### Post by cwmoser on 2024-06-22
I just overwrote my old 22.04 and Win10 and installed 24.04 but it will not boot.

I can use the install USB and drop to the terminal and can see the partitions, but how to I make it bootable?
BIOS is set for both Legacy and EFI.

I have this running gparted ...

```

/dev/nvme0n1p1   1M       grub2.core.img
/dev/nvme0n1p2   28GB   Linux filesystem
/dev/nvme0n1p3   28GB   Linux filesystem
/dev/nvme0n1p4   182GB Linux filesystem

```

I wanted to boot to /dev/nvme0n1p2 and make /dev/nvme0n1p4 my /home partition.

---

### Post by oldfred on 2024-06-22
If you have a NVMe drive, your system is UEFI.
Better to make sure drive is gpt which it looks like it is with the bios_grub partition.
But then have first partition as the ESP - efi system partition FAT32 with boot,esp flags and deepending on size of drive and number of installs 100MB to 500MB. If only grub and one install 100MB is enough unless converting to another boot loader like systemD.

You really want UEFI install.
Microsoft required vendors to install Windows 8 in UEFI boot mode to gpt partitioned drives starting in 2012. The old BIOS/MBR configuration was just so large users of Windows could use old computers that were BIOS only with newer Windows.
New systems starting about 2020 are UEFI only.

How you boot install media, UEFI or BIOS is then how it installs. UEFI should be clearly labeled, but BIOS mode often is just name of flash drive.

---

### Post by yancek on 2024-06-22
Although the preferred installation method is described in post 2 above, there is no reason you should not be able to boot a Legacy install from a GPT drive.  If you have the unformatted partition on which core.img is placed and installed Grub code to the MBR, it should work.  If you don't resolve this, go to the boot repair site below and use the 2nd option described on that page to download it.  Do this from the install USB.  When you run it, select the Create BootInfo Summary option.  Do NOT try to make any repairs.  When boot repair finishes, you will get a link to post here so that members can view the output and try to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cwmoser on 2024-06-22
[https://paste.ubuntu.com/p/R3JSFDjP9T](https://paste.ubuntu.com/p/R3JSFDjP9T)

---

### Post by oldfred on 2024-06-22
It looks like it should boot. 
Some systems with the legacy & UEFI setting do not work with that setting.
You have to specify one or the other.

---

### Post by cwmoser on 2024-06-22
[https://paste.ubuntu.com/p/R3JSFDjP9T](https://paste.ubuntu.com/p/R3JSFDjP9T)

---

### Post by cwmoser on 2024-06-22
Still will not boot.

The Boot Menu looks like this:

ubuntu
NVMe0:  INTEL SSDPEKKF256G7L
Windows Boot Manager
PCI LAN

---

### Post by oldfred on 2024-06-22
That is the UEFI/BIOS boot menu.

If you boot from UEFI boot menu & hold shift key, do you get grub menu?
Shift key is for BIOS boot, & pressing often several time the Escape key is for UEFI boot.

If you get grub menu, try the recovery mode, or second menu entry.

---

### Post by cwmoser on 2024-06-23
Trying to install Ubuntu by establishing a separate partition for Root and Home would not work for me.
That necessary EFI boot partition proved too confusing to me.
So, I reinstalled having Ubuntu do the automatic reformat the entire disk, which was OK for me, and it created a single partition with everything.

My desktop PC I set up a few years ago to have separate partitions which was not difficult for me.
I liked having 2 root partitions that I could preserve the old Ubuntu and install new releases in the other partition.
I was wondering if installing by the "Something else" partitioning if the installer would warn and allow the EFI partition would make installs easier.
Then again, EFI to me is a confusing concept and long for the old legacy booting methodology.
I just hope installing Ubuntu does not drive away potential adopters.

I do want to think you guys who made suggestions, thank you very much.

---

### Post by oldfred on 2024-06-23
Before 2014 I multiple booted with BIOS. Originally hated grub2, but once I learned it, it actually was better.
But with one MBR, you can only have one BIOS boot loader and that will be last install. And then you boot any other installs from that grub menu. 
All installs have to be in same boot mode or all UEFI or all BIOS as UEFI & BIOS write hardware info different to HDD for operating systems. So you cannot switch boot modes once started to boot.

UEFI allows multiple boot loaders in different folders in UEFI. But if Ubuntu or any official and many unofficial flavors use /EFI/ubuntu folder, so again last install will be default &  grub can then boot other installs in UEFI boot mode.

Still strongly suggest to use gpt partitioning but with BIOS over very old MBR(msdos).
You do need a tiny 1 or 2MB bios_grub partition for grub with gpt. 
When first converting from BIOS to UEFI I had both bios_grub & ESP - efi system partition on every drive & even larger flash drives as first two partitions. I had already started converting new or reformatted drives to gpt in 2010.
The only time MBR is still required is for BIOS boot of Windows, but Microsoft has required vendors to install in UEFI/gpt mode since 2012.
New systems starting in 2020 are UEFI only, even though vendor may still call it BIOS. My Dell says BIOS, but once in BIOS, it says UEFI only.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

### Post by grahammechanical on 2024-06-23
> So, I reinstalled having Ubuntu do the automatic reformat the entire  disk, which was OK for me, and it created a single partition with  everything.

Open the Disks utility, You will see that the installer created two partitions. You will see that the first partition is /dev/nvme0n1p1 It is a FAT 32 partition. Also called EFI System partition. It will be mounted at /boot/EFI. The second partition will be /dev/nvme0n1p2 It will be a Linux partition. It is the Ubuntu partition.

Question: Does this new install boot?

Dual booting is a case of using <[COLOR=#ff0000]Synaptic Package Manager[/COLOR]> <should be [COLOR=#008000]**GParted**[/COLOR]> from a Ubuntu Try/Live session to create unallocated space and then create new partitions in the unallocated space formatted as Ext4.

*Edit: @tea-for-one  Thank you for pointing out my error.*

You can then instruct the installer to install Ubuntu in one of those new partitions. The installer will select a partition to install the boot files in. It should be nmve0n1p1. Confirms that this is so.

When you reboot you should see a Grub menu that allows you to choose which Linux you want to boot. The newest installation will be the default. If you prefer the older installation to be the default - boot into it and run

```
sudo update-grub
```

```
sudo grub-install /dev/nmve0n1p1
```

Regards

---

### Post by yancek on 2024-06-23
Line 72 in boot repair shows your computer is UEFI capable so since you have overwritten everything, it would probably be simpler to reboot the installer and select to boot it in UEFI mode and install that way. It should create an EFI partition with the proper boot files.

What are the different partitions?  The first is the BIOS_boot partition which you needed to do a Legacy install on a GPT drive.  You won't need that with EFI.  The 2nd partition is your Ubuntu system partition so what are 3 and 4?  Is one a /home partition?  If you want a separate /home partition I would expect you need to do a manual install, something else.

---

