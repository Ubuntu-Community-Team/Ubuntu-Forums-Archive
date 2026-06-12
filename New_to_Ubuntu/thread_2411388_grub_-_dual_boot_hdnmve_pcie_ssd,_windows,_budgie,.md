---
title: "grub - dual boot hd/nmve pcie ssd, windows, budgie, legacy bios"
date: 2019-01-29
forum: New to Ubuntu
---

### Post by twelvekanaw on 2019-01-29
This is too long but here goes. Let's see.

Here's what I did:

1) Deciding to try Ubuntu, I set up a dual boot with Windows 7 without difficulty. Both lived on a 500 gb hard drive in their own partitions and GRUB ran from the boot sector on the Windows partition (I think - GRUB is what I'm really trying to understand here).

2) Liking Ubuntu and looking at different flavors, I found Ubuntu Budgie and liked that better. I also bought a used NMVe SSD and put it into a PCIe adapter to take a look at that. I know I'm off into UEFI territory here and this, partly, is what I'm trying to learn about. Windows 7 can't (easily) use the NMVe drive but I'm about to abandon MS anyway and Ubuntu has the NMVe driver I want. So, before stepping into the mysteries of UEFI, I put in the installer DVD and booted it up. The NMVe drive was found so, just feeling my way forward, I directed the installation there to see what would happen. The installation went fine but wouldn't boot. No surprise, the NMVe card was not seen at boot time by the legacy BIOS.

3) At this point I've got the original Windows 7 installation and Bionic Beaver booting with GRUB and sharing a hard drive and and Budgie on the SSD, not booting yet. I booted the Beaver (which can see the NMVe drive). I ran Boot Repair, figuring why not. The OS probe found the Budgie installation on the SSD. In Advanced Settings I chose the Windows partition as where to place GRUB - guessing that if I had a chance to boot the SSD without messing with UEFI that the BIOS would first have to find GRUB on a drive that it could see. The Windows partition has a boot flag on it as well, though I don't remember if I set that. In any case, it's there. I saved this configuration with GRUB repair and rebooted.

4) A minor surprise ensued. Grub ran and I was offered all three (Windows, Beaver, Budgie) bootable partitions to choose from. I chose Budgie on nvme0n1p1. GRUB bitched that there was no such device as the UUID I was aiming it at. So I thought, well, I didn't really expect it would work. Several seconds later some other text appeared that didn't last long enough to read and, bingo!, the SSD booted. Budgie was up and running from the NMVe drive. This is something like the desired result even if I don't understand why it worked.

5) After several days of comparing things and changing the boot order with Grub Customizer and a dozen other things, I decided the the configuration I really wanted was Windows (headed for extinction but possibly not quite dead and, anyway, one way to boot this thing is off the original Windows boot sector it seems) with Ubuntu Budgie taking the prime real estate on the SSD and without Bionic Beaver. Now, to make this original dual boot in the beginning I had used dd in a Linux Live disc to clone a 250 gb Windows drive to the first half of a 500 gb drive and, afterward, set up the first Bionic Beaver install on the remaining half of that drive. Worked great. I figured I'd (more or less) duplicate what had gotten GRUB working the first time - this time using the original Windows hard drive minus the Bionic Beaver.

6) I put the original 250 gb windows drive back into the machine figuring to reinstall GRUB using Boot Repair - and, if it went wrong somehow, the dual boot Windows/Beaver drive would still boot. (This was sound thinking because it worked just that way.) The only difference I can see in this is that GRUB was originally installed in place of the MBR by the installation of Bionic Beaver and then modified by Boot Repair to allow Budgie to boot off the SSD and here it would be reinstalled by Boot Repair. So I ran the Live Budgie DVD, went and fetched Boot Repair, and ran it. The OS probe found the SSD and asked whether it was a removable drive and I answered no. In Advanced Options, I put GRUB on the Windows partition (this is getting too long but maybe someone will be entertained enough to think about it), saved the configuration and rebooted.

7) Nothing. No such device. I tried it again in case I hadn't exactly duplicated what worked before which, of course, I hadn't somehow. I also tried it leaving the GRUB installation on the default - install it to all bootable partitions. Nothing. GRUB doesn't see either the NMVe drive or Windows. So I put the 500 gb drive with the working GRUB (and Windows and Bionic B) back in and it booted just as before. First it says, nah. No such device. Then something else very quickly. Then it boots anyway. 

So you can see what I'm wondering here. I didn't think what I did with the NMVe drive would work to begin with and I'd have to go to UEFI to do any good. I just did it to see if it would work. I don't know why it worked and I'd like a better idea about what the difference is between what I did originally and reinstalling GRUB with Boot Repair on a Windows hard drive that had not had the MBR replaced by installing Ubuntu in a dual boot to begin with. If this wasn't the kind of thing that entertains you I don't suppose you'd have read to the end. If there are questions that would clarify this, please ask. If there's something I should read or an idea I should learn about I'd appreciate the suggestion.

---

### Post by yancek on 2019-01-29
There are some mis-understanding in the way you think Grub boot code works.  One thing you never want to do is to write any Grub/Linux boot code to the windows system partition.  Since you have boot r, why not select the Create BootInfo Summary option and post the link here for members to review.  A number of members here are very knowledgeable on the subject.

---

### Post by twelvekanaw on 2019-01-29
Thanks for reading all that. You are correct that I don't understand very well how GRUB works. I was trying to get the details right but I did say one thing that's not correct. Nothing to do with GRUB was written to the Windows partition. It was placed on the drive that has the Windows partition on it. I think I know how to make a Bootinfo Summary. I'll do that in the morning and post it. I'm very curious to learn why this boot arrangement works at all. I really didn't expect it to.

---

### Post by twelvekanaw on 2019-01-29
Ok, that was easier than I thought I remembered. Try this: [http://paste.ubuntu.com/p/N4cRfsXvJ6/](http://paste.ubuntu.com/p/N4cRfsXvJ6/)

---

### Post by twelvekanaw on 2019-01-29
One more quick detail. In that report, /dev/sda is a clone of /dev/sdb. Sda is in an external usb dock. I should have unplugged it before making the report. Sdb is the boot device with Windows and Bionic Beaver on it. Budgie is on the SSD.  Thanks.

---

### Post by oldfred on 2019-01-29
Do not run auto fix.
If you do run Boot-Repair, only use advanced mode and install one boot loader to same drive as install.
With multiple drives, Boot-Repair installs one grub to the MBR of all drives so system will boot no matter what drive is set as default in BIOS.

You have BIOS boot. I do not see any ESP - efi system partition.
But report is not yet updated to show all the details on NVMe drives.

You are showing corruption, hibernation or some issue on your Windows partitions. Perhaps even dynamic drives?
You will need a Windows repair disk to fix those issues and do that first.

If you clone a drive/partition, you cannot have it plugged in when you reboot.
Duplicate partitions create all sorts of issues. Some may boot from one drive or the other on reboot depending on which drive BIOS brings up first. And then drives get out of sync and not cloned.

```
/dev/sda1        59276DA6532B9F1F                       ntfs       
/dev/sda2                                                          
/dev/sdb1        59276DA6532B9F1F                       ntfs    
```

---

### Post by twelvekanaw on 2019-01-29
Thanks. The clone is in a usb dock but I won't reboot with it in there. I forgot it was there. Also, this report is using the sata drive (/dev/sdb) that boots the SSD in a roundabout fashion. I'll put the drive in that has only Windows on it, that I attempted without success to get GRUB working on, and make another report. I'll have to do that tomorrow. I know this is overly complicated but I'm just trying to learn something. I could pull it all out by the roots and just switch over to UEFI and install Budgie on the SSD properly and maybe I'll end up doing that. I'll post the other report soon.

---

### Post by twelvekanaw on 2019-01-30
Here's a link to the Bootinfo summary using the Windows 7 only drive that I installed GRUB onto but which won't boot. [http://paste.ubuntu.com/p/XK7ZkjgFXQ/](http://paste.ubuntu.com/p/XK7ZkjgFXQ/)
I'll also read that UEFI thread that oldfred gave. Thanks for your attention. I hope this amuses someone with advice to share as much as it amuses me.

---

### Post by oldfred on 2019-01-30
You have two MBR(msdos) drives and one gpt partitioned drive.
If staying with BIOS, I would add a bios_grub partition, 1 or 2MB unformatted with bios_grub flag on your gpt drive, sdb.
You may use Boot-Repair to add grub to sdb, but if you can boot into sdb, just install grub to MBR of sdb, but since gpt must have bios_grub partition first.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 
    
I would also then install a Windows or Windows type boot loader to the MBR of sda. Windows 7 has fewer issues than Windows 8 or 10, but still may get corruption needing chkdsk. Then grub will not boot it. If you have Windows in MBR, you may be able to boot directly from BIOS, and use f8 to get into repair console. But always best to have separate repair flash drive for current version of every operating system you have installed.
Boot-Repair's advanced mode may install the syslinux boot loader which works like Windows. Or use Windows repair disk and run fixMBR command from repair console.

Have you updated UEFI/BIOS to latest version from vendor? And updated SSD firmware? Even new systems have required these updates for SSD to be correctly seen.
BIOS/UEFI must be in AHCI mode for SSD drives also, not old IDE, not RAID or Intel SRT which some systems seem to use even if one drive.

I prefer gpt partitioning and started using it on my old BIOS only system back in 2010. Windows XP was on MBR drive, and I converted another drive to gpt and installed Ubuntu. After that all new or reformatted drives have been gpt including larger flash drives. But I typically have at least a small Ubuntu install on every drive for emergency boot.
When Windows made vendors use UEFI with Windows 8 release, I started to add both bios_grub and ESP - efi system partition to every new or reformatted drive on the chance I might move drive to a new UEFI system. But you really only need one or the other, depending on boot mode. But my internal drives are so large, that a few MB for future use seemed like a good option.

Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt. So Windows drives must be partitioned to match boot mode.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by twelvekanaw on 2019-01-30
Ok, I *just about* understood that. Maybe. There's not a lot at stake here because 1) What I'm mainly after is to understand GRUB/UEFI/NVME/BIOS differences and operations and 2) I've cloned the working boot setup I now have so I can always boot it. I'll see if I can make any progress with this and maybe (probably) ask more questions. Thanks.

---

### Post by oldfred on 2019-01-30
UEFI and BIOS are totally different, for both Windows & Ubuntu.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    
I thought Windows 7 DVD had to be converted to flash drive & files renamed to make it work for UEFI installs. But one user posted that the updated Windows 7 installer will work for UEFI or BIOS.

UEFI & BIOS are not compatible, but UEFI has a mode for backwards compatibility.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

