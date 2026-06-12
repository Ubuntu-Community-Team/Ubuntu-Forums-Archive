---
title: "Ubuntu desktop 14.04 64 bit installation"
date: 2014-11-05
forum: New to Ubuntu
---

### Post by kerczek7 on 2014-11-05
I have a new HP laptop with a intel i3 64 bit processor. It has windows 7 professional installed. I want to dual boot it with Ubunto 14.04. At the disk partitioning install window it does not seem to give a choice for dual boot. What do I do to get a dual boot.
;)

---

### Post by SuperFreak on 2014-11-05
HP usually uses 4 primary partitions (check yours with GParted or other partition editor) . unless you are using gpt partion tables (your computer is Win7 so good chance it is MSDOS partition table) you are only allowed a max of 4 primary partitions. This may be why the option is unavaialble. I will post  directiions I used in a similar situation with HP Win 7 computer

---

### Post by SuperFreak on 2014-11-05
Install Dual Boot on HP DV7 Pavillion and keep all 4 HP Partitions when in MSDOS partitioning and BIOS (not EFI) mode(these are things you need to check on first)

   

    I successfully installed Ubuntu on my laptop and Windows is intact, including the HP Tools partition. Most of the instructions I found on the web indicated this partition had to be deleted in order to install Ubuntu in a Dual boot with Win 7. I didn't want to do that because HP Tools contains some useful tools but ,more importantly it contains a back up of the BIOS. Just in case anyone else wonders how I did this here is a brief run down:

    1a) Back up all your important files
    1b) Defrag Windows partition
    2) Make a set of recovery disks in Windows and as Mark pointed out make a repair disk also
    3) Install Easus Partition Manager (for Home use) a free download HERE.
    4)With Easus change the HP_Tools partition to logical (you will have to click apply to confirm action)
    5)With Easus,Copy HP_TOOLS partition to a USB Key formatted to FAT 32. Make sure it remains logical. System may reboot
    6)With Easus delete HP_Tools on your hard drive(making sure that the copy to USB ocurred). System may reboot
    7a)Resize the C drive with Easus or Windows Disk management so you have an unallocated space available for Ubuntu ( I would say you need at least 12 GB but I made mine 120 GB). Again you may be asked to reboot.
7b)Reboot a couple of times into Windows so Chdsk runs and corrects any errors
    8)Copy HP_Tools from the USB Key to the new unallocated space with Easus. Make sure you move HP_Tools to the far right side of the unallocated space. Make sure HP_Tools is logical.System may reboot
    9)Using Gparted (You can obtain Gparted separately or use a Live Ubuntu disk and install it temporarily) enlarge Extended Partition(not the HP Tools partition) that is around HP Tools so it encloses all the unallocated space to the left.
    10)Using Gparted divide the unallocated space as required for Ubuntu(I used 35 GB for Root, 80 Gb for Home and 6GB for Swap)
11) reboot into Ubuntu Live Disc and install making sure you choose Something else as the install method when asked (otherwise you risk wiping out Windows). Install in the choosen partitions


[http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions](http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions)

---

### Post by kerczek7 on 2014-11-07
Thanks. This seems a bit complicated for me. What advantage is there in keeping the HP Tools partion? It seems easier to simply delete this partition and resize it to accept UBUNTU. Do I really need HP Tools for the following way that I use my computer. My use of this computer is only for writing (by way Libre Office), technical computing (by way of Scilab) and web browsing and email. I find UBUNTU, which I have on my old computer, much easier to use and not having all the garbage that keeps popping up on windows.

---

### Post by SuperFreak on 2014-11-07
Of course you are right that you can dispense with the HPTools partitionn but I believe it does contain a back up of the BIOS
More importantly you should find out how the drive is partitioned (MSDOS or GPT) by using GParted and also whether your BIOS is UEFI or legacy BIOS. Both of these will have an impact on your install. In the case of UEFI you will need to create an EFI partition

---

### Post by coffeecat on 2014-11-07
> **kerczek7 said:**
> This seems a bit complicated

I agree. You can make things much simpler.

I&#8217;m 99% sure that the HP_TOOLS partition is there simply for BIOS updates and diagnostics. When I had a HP laptop I backed up the contents of the HP_TOOLS partition and then deleted it. It&#8217;s right up at the end of the hard drive, so you have a little wasted space, but very little &#8211; nothing to worry about. When does one every need to update the BIOS? Far less than many people think necessary. :)

And I wouldn&#8217;t bother with Easus. Windows 7 and Ubuntu have everything you need for partition manipulation.

This is what I would do.

[list=1][*]Create a set of recovery DVDs as a second line in case your recovery partition fails to function if you ever need to restore the machine to factory defaults.
[*]Backup and then delete the HP_TOOLS partition.
[*]Use the Windows 7 Disk Management utility to shrink your Windows C: partition. You don&#8217;t need a 3rd party tool for this.
[*]Use Gparted in the live session to create an extended partition in the space you have made between the C: partition and the recovery partition.
[*]Now use Gparted to create your Ubuntu partitions in preparation for installation. Minimum one ext4 partition for / and a swap partition. If you prefer a separate /home partition, create that as well, but don&#8217;t bother with a /boot partition. Let us know if you need help with that.
[*]Install Ubuntu and choose &#8220;something else&#8221; at the partitioning stage to install Ubuntu to the partitions you have already created with Gparted.
[*]Enjoy your dual-boot![/list]

That's all assuming you have a mbr partition table, but since you seem to have run into the 4 partition limit problem, that will be the case.

---

### Post by kerczek7 on 2014-11-08
Thanks. I'll give it a shot.

---

