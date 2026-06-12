---
title: "How can I delete the Ubuntu option that is within my BIOS?"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-15
Here's what I have for hardware...
Gigabyte 970A-D3 Rev 3.0 motherboard
NVidia GeForce GTX 650 Ti Boost video/graphics card
AMD FX 6300 Six Core Processor
32gb of RAM(4x8gb sticks) Corsair Vengence
Asus DVD/Blu-Ray
1tb Hard Drive "00RKKA0"(With Windows 7 Professional)
1tb Hard Drive "07ZF5A0"(With Ubuntu 12.04 Precise Pangolin)
75gb Hard Drive "00FLA1"(No OS)

I installed Ubuntu 12.04 onto the hard drive "07ZF5A0" and had some errors. I decided to reinstall Ubuntu and now I have an Ubuntu boot option in my BIOS that is left over from the first installation.  When I select it, the screen blinks and just goes right back to the same screen above. I need to know how to delete this option from this BIOS. I would prefer to just have the drives(the three hard drives and the DVD/Blu-Ray drive) as BIOS boot options.  How can I delete the Ubuntu option from the BIOS boot menu?

Right now, if I choose Hard Drive "00RKKA0", it'll boot into Windows 7, which is what I want. If I chose Hard Drive "07ZF5A0", I get the GRUB menu, but it looks big and bulky. Is there anyway to configure it so that it looks a little bit sharper?

---

### Post by oldfred on 2013-09-16
UEFI has its own memory. You have to delete from UEFI menu or if not available you can use the command line.

              
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples $5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

    
One user posted this on how he gets into UEFI to maintain it.

 Enter your UEFI menu, select "Boot maintenance manager", then "Boot options"

---

### Post by ImTroyMiller on 2013-09-17
I get "efibootmgr: command not found" from the live CD.

---

### Post by oldfred on 2013-09-17
I have no idea how to get to it from Windows.

Or you may have to download it. It is in repository.
sudo apt-get install efibootmgr

---

### Post by ImTroyMiller on 2013-09-18
I was doing that from the Ubuntu live CD.

I downloaded it, but it gave me an error when I tried to run it.

"Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root."

---

### Post by oldfred on 2013-09-18
Did you boot liveDVD or flash in UEFI mode? BIOS mode would not show efi vars.

---

### Post by grahammechanical on 2013-09-18
What happens if you select the item but do not click. Do you get new options in the side panels? Is there a motherboard user guide that explains the options in the UEFI boot system settings? What does that say in regard to this subject?

The panel on the right says to use the up and down arrow keys to move to an item and then the + and - keys to change options. Does doing that give you an option to delete?

Regards

---

### Post by ImTroyMiller on 2013-09-21
I booted live DVD not flash.  My BIOS boot mode selection is set for UEFI and Legacy.

I get no options when selecting the item and not clicking on it.  The user guide for my motherboard doesn't say much regarding this subject and moving the options up/down is only for changing the boot order(no options to delete).

---

### Post by oldfred on 2013-09-21
When you have UEFI & Legacy, you should see two different boot options for DVD, I know you do for flash drives. One should be UEFI and the other Legacy, but often it shows some hardware data that is not totally clear on which mode you are booting with.
If you get purple accessibility screen that is BIOS. If a grub menu that is UEFI. Screens shown here:
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ImTroyMiller on 2013-09-21
Got it!  Thank you.

I guess I installed both OS under Legacy.  Should I have gone with UEFI, or does it matter?

---

### Post by oldfred on 2013-09-21
Both need to be the same it the most important part now. But BIOS is 30 plus years old and that is why UEFI now calls it legacy. But you do not need to change.

Since Windows only boots from gpt with UEFI, I would not consider changing to gpt for a Windows drive. But Ubuntu will boot with BIOS or UEFI with gpt partitioning. You may want to use gpt even if BIOS mode currently. But that would probably require a reinstall. There are some tools to convert from MBR to gpt and then reinstall grub if really interested.

I am now using gpt on all new drives. And creating an efi partition at beginning of every drive for future use as I only boot with BIOS. But hope to have new UEFI system soon and then could use old drives on new system.

---

