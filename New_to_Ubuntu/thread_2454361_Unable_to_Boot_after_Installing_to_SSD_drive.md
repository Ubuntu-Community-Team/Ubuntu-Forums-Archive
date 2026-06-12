---
title: "Unable to Boot after Installing to SSD drive"
date: 2020-11-27
forum: New to Ubuntu
---

### Post by bpeck88 on 2020-11-27
Hi
I am a complete newbie to Ubuntu but have been thinking about trying it for some time and downloaded Xubuntu 20.10 and attempted to do a live USB install.
The computer I installed it to is an older home built machine circa 2007. It previously had windows 7 installed to an SSD drive and has 3 other drives in it as well. 
Everything was going great until I went to reboot after the install. At that point it tried to boot into windows 7 but said that files were corrupted or missing and I couldn't get any further. I never saw the grub boot loader. 

I have looked through the forums and wiki and found an article on [Boot-Repair ]("https://help.ubuntu.com/community/Boot-Repair")but when I ran it, it was stopped telling me I had to disable bios compatibility mode and enable UEFI booting mode for it to repair anything. I don't think my old bios is capable of supporting UEFI.

Here is a readout of the results from Boot Repair on Pastebin
[https://pastebin.com/ypX9RBAs](https://pastebin.com/ypX9RBAs)

Is there any way I can get this machine to boot again? What do I need to do?

---

### Post by rbmorse on 2020-11-27
Is your BIOS able to support an SSD drive?

---

### Post by bpeck88 on 2020-11-27
Yes. Windows 7 was installed on the SSD drive. It is also set as the first drive to boot in the bios.

---

### Post by garvinrick4 on 2020-11-28
[oldfred]("https://ubuntuforums.org/member.php?u=852711")

Ask oldfred give him a message and link.

---

### Post by Impavidus on 2020-11-28
It appears that Windows was installed on sdd (the 4th drive), which is indeed the SSD. It's gone now, as it's overwritten with Ubuntu. But there still appear Windows bootloaders on sdb and sdc, two of your other hard drives. Your Ubuntu system appears to be installed in bios mode. There is a bios-grub partition on sdd to install grub on gpt partitioned drives and drive sdd is gpt partitioned. It must have been mbr partitioned while Windows was there. An EFI partition is also present but probably unused, but that seems to be standard nowadays.

My guess: your computer is booting using the Windows boot loader in sdb or sdc, not using the Ubuntu boot loader on sdd. It probably did so already while Windows was installed. You can try and configure your computer to boot from sdd or install grub on the other harddrives.

If you have multiple hard drives, it's best to use manual partitioning ("Something else"), so you can manually choose where to install the OS, where to install the bootloader (grub) and how to use the other partitions. If for some reason you can't boot Ubuntu from sdd, but can boot it from sdc or another drive, you can alway put a /boot partition on the drive from which you can boot and put the rest of the OS on the SSD.

Drives sda, sdb and sdc all have Windows data partitions. You can access them from Ubuntu in read-write mode, but you can't fix them if damaged. Eventually you'll have to change them to native Linux partitions, which means formatting and restoring all files from a backup.

---

### Post by oldfred on 2020-11-28
You say system is from 2007, but only Macs use UEFI that far back.
Microsoft required UEFI/gpt with release of Windows 8 in 2012. 

What brand/model system or motherboard?

Since your Windows is BIOS, best to keep Ubuntu in BIOS mode. 
But if system is really UEFI, it may be better to re-install everything in UEFI mode.
Windows 7 is obsolete and should not be used, particularly should not be connected to Internet.

You can use Boot-Repair booted in BIOS mode, to reinstall grub to sdd. 
Only use Advanced mode or Boot-Repair will try to install one grub to all drives. You want to keep Windows boot loaders on other drives.
You already have a bios_grub partition on sdd, so grub-pc should correctly install into it, since drive is gpt partitioned.
I would leave ESP, so later if you convert to UEFI, you already have the ESP for UEFI boot. It is not large.

Advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by TheFu on 2020-11-28
A few comments from the peanut gallery (me). These don't override what anyone else recommends.

People new to Linux should run LTS releases, not the latest, short-support, release. The current LTS is 20.04. It has 5 yrs of support - that's more than 4 yrs longer than 20.10 support.  Non-LTS releases are "technology demonstration" releases.  They break things. It s expected. When new to Linux, the last thing you want is for the system to break  before you understand it is due to some prototype code.

When installing, if you have a specific partition/drive you want ubuntu onto AND booting from, disconnect all other storage devices during the install. This will prevent confusion and bad mistakes that often end with another OS and data wiped due to unfamiliar terms. With experience, you'll get to the point that leaving all the disks connected won't be too risky.

One last idea - the BIOS let's us pick which drive to boot from.  Have you tired pointing at different boot devices?

peanut gallery - out.

---

### Post by bpeck88 on 2020-11-28
Ok. Thanks everyone for the replies and suggestions. I am still having trouble.

The motherboard I have is an Intel DG965WH. I don't believe it supports UEFI. 

I am afraid I am not able to completely follow the instructions since I  am such a newbie and I am still stuck. Here is where I am at now. I  tried to do the manual partitioning and install as Impavidus suggested  but still was unable to boot. You can see what I tried and how sdd is  partitioned here: [https://paste.ubuntu.com/p/Fy4DsM8GfN/](https://paste.ubuntu.com/p/Fy4DsM8GfN/)

I also tried physically disconnecting sdd and doing a fresh xubuntu  install on sda2 but that has no effect. I still see no bootable device  when I tried to boot to sda. That is why you will see that ubuntu is  installed on sda3 now and sdd2. 

I have also verified that my bios boot order is correct for what I am  trying to do. (for example boot to the solid state drive first vs one of  the other drives)

What do I need to change to have the system recognize the boot loader and boot? Thanks.

---

### Post by oldfred on 2020-11-28
I also thought that motherboard would be BIOS only.
But you keep getting a FAT32 partition with UEFI boot files. And the mount of that partition in fstab as the ESP - efi system partition for UEFI boot.
And you have grub in MBR with a bios_grub partition for BIOS boot, but since fstab has efi partition, it seems that it is not set for BIOS boot?

How you boot install media UEFI or BIOS is then how it installs.
The installer for 20.10 uses grub for both UEFI & BIOS, but once installed it should be just BIOS.
Or are you installing the installer to your drives?

I agree with TheFu, better to use LTS versions. Only if you have very new hardware that must have newest kernel & drives may newer version be better.
I always use current LTS version as main working install, but normally install other versions, just to see differences.

Even Boot-Repair thinks your system is UEFI capable. But you should still be able to install in BIOS boot mode.
Use Boot-Repairs advanced mode when booted in BIOS mode and reinstall grub (grub-pc for BIOS) to MBR of sda only for install in sda.

---

### Post by Dennis N on 2020-11-28
The 20.10 installer could be buggy and may not sucessfully install in BIOS mode to an MS-DOS partitioned disk. This seems to be the conclusion in another thread:

[https://ubuntuforums.org/showthread.php?t=2452608](https://ubuntuforums.org/showthread.php?t=2452608)

It should work if you do a default "erase disk and install". In that case, it creates GPT partition table.
If your disk must remain MS-DOS partitioned, a solution is to use Ubuntu 20.04 instead.

---

### Post by bpeck88 on 2020-11-28
Thanks. I was finally able to get it booting by downloading 20.04 and doing a fresh install on my SSD. Thanks for the insight to try that version.

---

### Post by DuckHook on 2020-11-29
You may wish to read through the links in my sig: **Linux is Not Windows** and **Resources for Newcomers**. I've always found the following site to be friendly and useful for Linux newbies: [https://linuxjourney.com/](https://linuxjourney.com/)

---

