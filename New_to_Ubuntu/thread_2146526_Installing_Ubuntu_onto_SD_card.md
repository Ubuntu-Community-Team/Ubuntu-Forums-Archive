---
title: "Installing Ubuntu onto SD card"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by Danja91 on 2013-05-18
Hello,

I'm trying to install Ubuntu onto an SD card on my Surface Pro. I'd like your help to make sure that I don't overwrite my existing Windows installation. Currently, the disks connected to the computer are:
 
128 GB SSD (Windows 8 Installation)
8 GB USB drive (Ubuntu 13.04 Live CD)
32 GB MicroSD card (Where I'd like to install Ubuntu)

I'm currently being asked where to install the bootloader. I think that goes on the main drive, but I'm not sure exactly where. Furthermore, the fact that it says "install now" rather than "continue" makes me worried that it'll install the OS, as well as the main drive, on the SSD. Please tell me which option I should select. I've attached a picture of the screen.

[ATTACH=CONFIG]242738[/ATTACH][ATTACH=CONFIG]242739[/ATTACH]

Thank you very much for your help.

---

### Post by Danja91 on 2013-05-18
Ah, in the menu of the partitions, I didn't realize that I could scroll down. Right underneath /dev/sda5 there's an option for /dev/sdc1, a 32 GB partition which I assumed is the SD card. Is the correct course of action to highlight /dev/sdc1 and leave /dev/sda as the bootloader partition?

---

### Post by afz12 on 2013-05-18
I am interested to see how far you get Danja91. I have had good success getting Ubuntu (and Mint) to run on external USB drives on boot-up, after changing the BIOS bootorder for this. From memory, the host notebook was visible as a USB drive would be, so using a part of it for swap etc might actually work. However I haven't been able to run anyLinux from a SD card (32 GB grade 10) so there might be some anamolies. I suspect it could be used for swap space but I guess there would be no advantage doing so, as hard drives may be a lot faster and drive space is cheap these days.

---

### Post by cortman on 2013-05-18
To be honest it's probably easiest to do this in Windows. Download [LinuxLiveUSB Creator]("http://www.linuxliveusb.com/") (Lili) and install the ISO image to the SDCard with it. That's the safest way to do it.

---

### Post by ehsanoo on 2013-05-18
On linux, you can also use "dd" command:
dd bs=4M if=/path/to/iso of=/dev/sdc1

This command will "write" the iso file on your SD card, your currently stored data will be lost on SD card and you need to format the SD card later using something like Disk Utility.

---

### Post by Danja91 on 2013-05-19
> **cortman said:**
> To be honest it's probably easiest to do this in Windows. Download [LinuxLiveUSB Creator]("http://www.linuxliveusb.com/") (Lili) and install the ISO image to the SDCard with it. That's the safest way to do it.

But then I'm limited to a 4 GB filesystem. That won't do; the whole reason I'd like to boot from the SD card is the 32GB of space that I'd have

> **ehsanoo said:**
> On linux, you can also use "dd" command:
dd bs=4M if=/path/to/iso of=/dev/sdc1

This command will "write" the iso file on your SD card, your currently stored data will be lost on SD card and you need to format the SD card later using something like Disk Utility.

I tried that and the terminal said the operation completed, but there were no changes made to the device. What do you mean by "you need to format the SD card later"? Wouldn't the formatting overwrite the ISO?

I ended up trying to install from the Live Ubuntu USB, but it didn't work. The installer told me the procedure completed, but it failed to terminate all processes and I had to shut down manually via holding the power button. When I rebooted, it went into the normal Windows bootloader instead of the Ubuntu one. Any suggestions?

---

### Post by sudodus on 2013-05-19
> **Danja91 said:**
> Hello,

I'm trying to install Ubuntu onto an SD card on my Surface Pro. I'd like your help to make sure that I don't overwrite my existing Windows installation. Currently, the disks connected to the computer are:
 
128 GB SSD (Windows 8 Installation)
8 GB USB drive (Ubuntu 13.04 Live CD)
32 GB MicroSD card (Where I'd like to install Ubuntu)

I'm currently being asked where to install the bootloader. I think that goes on the main drive, but I'm not sure exactly where. Furthermore, the fact that it says "install now" rather than "continue" makes me worried that it'll install the OS, as well as the main drive, on the SSD. Please tell me which option I should select. I've attached a picture of the screen.

[ATTACH=CONFIG]242738[/ATTACH][ATTACH=CONFIG]242739[/ATTACH]

Thank you very much for your help.

It is possible to do what you want, at least many computers can boot from a flash card as well as from any other drive.

1. You should ***backup*** at least all your personal data (documents, pictures ...), because you might write to the wrong drive.

2. Device for boot loader installation:

When you are sure where to put the new system itself (the 32 GB drive), you should put the system into a (the) partition on that device, and write to the MBR of that same device (not to a partition).

So if the new system is written to **[FONT=courier new]/dev/sdc1[/FONT]** you should write the boot loader to the MBR (the head) of that device, that is [SIZE=3]**[FONT=courier new]/dev/sdc[/FONT]**[/SIZE]

---

### Post by sudodus on 2013-05-19
> **Danja91 said:**
> But then I'm limited to a 4 GB filesystem. That won't do; the whole reason I'd like to boot from the SD card is the 32GB of space that I'd have



I tried that and the terminal said the operation completed, but there were no changes made to the device. What do you mean by "you need to format the SD card later"? Wouldn't the formatting overwrite the ISO?

I ended up trying to install from the Live Ubuntu USB, but it didn't work. The installer told me the procedure completed, but it failed to terminate all processes and I had to shut down manually via holding the power button. When I rebooted, it went into the normal Windows bootloader instead of the Ubuntu one. Any suggestions?

Try with YannBuntu's Boot-Repair script. See this link

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by fantab on 2013-05-19
> **Danja91 said:**
> Ah, in the menu of the partitions, I didn't realize that I could scroll down. Right underneath /dev/sda5 there's an option for /dev/sdc1, a 32 GB partition which I assumed is the SD card. Is the correct course of action to highlight /dev/sdc1 and leave /dev/sda as the bootloader partition?

NO. The correct thing will be to install boot-loader on /dev/sdc not /dev/sdc1, if you want to use GRUB. /dev/sdc1 is the partition. However, if you want to use [EasyBCD]("https://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home") then that is probably correct.

If you install GRUB on /dev/sda then your windows MBR will get overwritten by Grub and if you ever remove Ubuntu then you will have to fix the Windows MBR before you can boot into windows.

But first, does your BIOS detect SD card? Some BIOS do not recognize SD card as a boot option. Confirm that first.

---

### Post by Danja91 on 2013-05-19
> **sudodus said:**
> Try with YannBuntu's Boot-Repair script. See this link

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Does this script work with EFI partitions? I'm afraid of losing the Windows 8 installation and getting completely locked out of my Surface.

So far I've been wildly unsuccessful in my installationg attempt. I set up the following partitions using the Ubuntu installation manager:

sdc1: EFI partition (200 mb)
sdc2: swap (600 mb)
sdc3: ext4 (the rest of available space)

And installed ubuntu onto sdc3 with the bootmanager installed on sdc. Upon completion, it rebooted into Windows with no further fanfare. I don't understand why it doesn't see GRUB. Is GRUB capable of loading EFI Win 8?

Also, I googled the issue a bit and found suggestions to simply virtualize linux instead of dual booting it. I tried that and all I can say is wow... how do people work on something so slooooow?

---

### Post by oldfred on 2013-05-19
I know the Surface RT versions are UEFI and totally locked down. You cannot boot anything else unless someone jail breaks it.
But can the Pro model even be booted with another system or is it also locked down? Does its UEFI offer a BIOS boot option or let you boot from the SD card. Only a few newer computers can even boot from SD cards.

Boot-Repair just about has to be run on any UEFI install as many UEFI systems have bugs and Boot-Repair has work arounds for most of them.

 [http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge](http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge)

If booting in UEFI mode is possible it would be better to make SD card gpt partitioned and have its own efi partition to boot from. Installing Ubuntu/grub to Windows efi partition may be possible, but it looks very small at only 33MB, normally if multiple booting we suggest 200  to 300MB. I bet it is designed not to multi-Boot.
And I bet it has some hardware that there is not a Linux driver for.

It is meant to compete with iPads which also are locked down.

---

### Post by Danja91 on 2013-05-19
> **oldfred said:**
> I know the Surface RT versions are UEFI and totally locked down. You cannot boot anything else unless someone jail breaks it.
But can the Pro model even be booted with another system or is it also locked down? Does its UEFI offer a BIOS boot option or let you boot from the SD card. Only a few newer computers can even boot from SD cards.

Boot-Repair just about has to be run on any UEFI install as many UEFI systems have bugs and Boot-Repair has work arounds for most of them.

 [http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge](http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge)

If booting in UEFI mode is possible it would be better to make SD card gpt partitioned and have its own efi partition to boot from. Installing Ubuntu/grub to Windows efi partition may be possible, but it looks very small at only 33MB, normally if multiple booting we suggest 200  to 300MB. I bet it is designed not to multi-Boot.
And I bet it has some hardware that there is not a Linux driver for.

It is meant to compete with iPads which also are locked down.

Thank you for the information. Could you fill in some details for me so that I could try another installation?

The Surface Pro is not locked down; I entered the BIOS and disabled secure boot. Other people have described a procedure for dual booting Ubuntu; however, they installed it to the main hard disk. The tutorial, which I tried to emulate, is [http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu). Instead of resizing my partition and making a bootable SD card, I made a bootable USB and attempted installation on the SD card. 

As an experiment, I instead tried to make a bootable Ubuntu SD card. I forced the surface to boot from it and obtained the following image:

[ATTACH=CONFIG]242789[/ATTACH]

What does this mean?

---

### Post by oldfred on 2013-05-19
That is grub starting to boot but not finding the rest of grub - grub.cfg and kernels.

But is it booting in BIOS mode, or UEFI mode.

How you boot installer, either UEFI or BIOS is how it installs. And if SD card is MBR(msdos) then it will boot in BIOS mode.
I only have BIOS but use gpt partitioning on several drives including flash drives. I would expect you can add the efi partition to the SD card and boot from that just like you do when booting the Live install version. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

I only have BIOS but plan a new UEFI system soon. So I formatted my newest flash drive as gpt and have both the efi partition for future efi boot and bios_grub for current BIOS boot.

```
Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 60532992 sectors, 28.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 65753959-2C89-4600-B150-6C72AADC6B50
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 60532958
Partitions will be aligned on 8-sector boundaries
Total free space is 229 sectors (114.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          976895   477.0 MiB   EF00  EFI System
   2          976896          978943   1024.0 KiB  EF02  
   3          978944        29650943   13.7 GiB    0700  sys
   4        29650944        60532735   14.7 GiB    0700  sys
 
```

---

### Post by complearning123 on 2014-02-07
I just want to say a big thank you for the information about the LinuxLiveUSB Creator.  It saved me.  Thanks again!


Stephen aka complearning123

---

