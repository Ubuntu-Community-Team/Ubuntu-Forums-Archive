---
title: "Cannot boot Ubuntu 12.10 - get windows error?"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by Tom McD on 2012-12-24
Installed 12.10 64-bit secure-remix to a new hard drive. Computer is Win 8 UEFI Secure_boot.
 
This gave me a text-based boot menu at restart.
 
Windows 8 booted normally.
Selecting ubuntu gives an error message: file damaged or missing:
 
\NST\AutoNeoGrub0.mbr
status:  0xc000007b
 
Hitting escape then allowed boot to Ubuntu from HD.
 
Booted Live-USB and ran Boot Repair (cut and paste commands to terminal) did not change symptoms.
 
Attempted repair with EasyBCD 2.2 (understands UEFI, GPT).
Deleted all boot selections, added back Windows and Ubuntu.
Ubuntu: GRUB 2, correct partition auto selected.
Resulting in unbootable system.
 
Restored Win 8 to factory image (sigh). Boots Win 8.
 
Booting from Live-USB, ran boot info, here is the URL:
 
[http://paste.ubuntu.com/1462575](http://paste.ubuntu.com/1462575)
 
Thanks for any help that may be able to be provided.

---

### Post by squakie on 2012-12-24
I myself am not versed in the nuances of UEFI with the secure boot, however I have read some of the threads here about that.  If I remember correctly, there are some things you have to do before you can install.  I would try a net search using the following search string:

ubuntu install UEFI secure boot

---

### Post by Tom McD on 2012-12-24
Thanks. The install itself went fine. The image is on the drive and works (or it used to, but with boot error messages). I just can not get to it to boot.
 
-- Tom

---

### Post by oldfred on 2012-12-24
Even Boot-Repair is having issues figuring out your system.

It looks like you have Intel SRT with a 32GB SSD and that uses some sort of RAID that confuses things. But you also seem to have  two 2GB hard drives.

Usually we are seeing the Intel SRT on high end laptops. I do not have it, but some have posted what they have done.

Is your second 2TB drive totally separate from Intel SRT and is that where you want to install?

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

    
       Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.


       
 You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)


       
 UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by Tom McD on 2012-12-24
Thank you.  The 2nd hard drive (Ubuntu) is totally separate from the SSD accelerator on the first drive (Win 8) and the Ubuntu drive is not RAIDed.  I reinstalled Windows 8 to get it to boot. Then rebooted from the USB-Live stick.  I ran boot repair.  This created a GRUB2 boot menu (first time I've gotten a GRUB2 boot menu). In UEFI-BIOS this made GRUB2 the first in the boot sequence before Windows Boot manager. GRUB2 is able to start Ubuntu. Unfortunately it cannot start windows (Error: Secure boot prevents starting Windows).
 
I went into the UEFI (Bios) and swapped the boot order, so Windows boot manager is 
first It boots windows OK, but of course not Ubuntu.
 
-- Tom
 
 
> **oldfred said:**
> Even Boot-Repair is having issues figuring out your system.
 
It looks like you have Intel SRT with a 32GB SSD and that uses some sort of RAID that confuses things. But you also seem to have two 2GB hard drives.
 
Usually we are seeing the Intel SRT on high end laptops. I do not have it, but some have posted what they have done.
 
Is your second 2TB drive totally separate from Intel SRT and is that where you want to install?
 
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
 
 
Some info on re-instating details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
 
 
 
 
 
You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
 
 
 
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by oldfred on 2012-12-25
Is Ubuntu in UEFI mode or BIOS mode?

If Ubuntu is installed in UEFI, you can chainload to Windows efi on the other drive or are both using the same efi partition. Best if each has own efi partition.

Install this and then rerun BootInfo report & post new link. Either from your install or live system used to install.
       sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils

    
Grub2's os-prober has a bug and creates BIOS type chain load entries that do not work with UEFI. But Boot-Repair can create a correct chain load entry, but I am not sure it does with two drives. You may have to change UUID from one to the other to work.

Solved with others with two drives.
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

    
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'

---

### Post by squakie on 2012-12-25
+1.

---

### Post by Tom McD on 2012-12-25
Thanks, Installed the tools and reran boot repair report-only. I can successfully boot either OS by hitting F12 during boot (which brings up the BIOS BOOT MENU), and selecting either [UEFI-win] or [UEFI-Ubuntu] from the boot selection menu. Bios boot is in secure mode [ENABLED]. That indicates the Ubuntu is successfully installed in UEFI & SECURE modes. Seems the issue revolves just around the boot problems.
 
sda (Win 8) boots UEFI, it has a UEFI boot partition - Win Boot manager, and Win 8 boot (according to EasyBCD). sdb is the 32-gig SSD cache for sda (uses Intel SRT, which has the controller configured for RAID0 between sda and sdb).
 
sdc (Ubuntu 12.10) has it's own UEFI partition (separate from the Win 8 UEFI boot partition on sda).
 
sdc has a total of 4 partitions:
 
/boot/efi
/
/home
swap
 
There are the memory-card readers, which Dell assigns drive letters to but they aren't hard drives.
 
The output of the boot repair report is:
 
[http://paste.ubuntu.com/1465231](http://paste.ubuntu.com/1465231)
 
Thank you for your help!
 
-- Tom

---

### Post by oldfred on 2012-12-25
You will have to manually add a chain load entry from grub to the Windows efi partition. But I do not know the exact configuration for your RAID. Grub has a bunch of .mod files in its sub-directory to load extra drives. We often load fat or ntfs and gpt, but there are several for raid and you may have to experiment.

These are typical entires without RAID. You can specify root by hd or search for root. 
```
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   
menuentry "Windows 7 UEFI" {
   search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

    
```Your entry may be more like this where your raid is the UUID
isw_defbbagaca_1Z2E24NN1 has UUD =  6A09-8861   

Possible RAID modules in grub. 
dm_nv.mod
raid.mod
raid5rec.mod
raid6rec.mod

```
menuentry "Windows 8 UEFI" {
insmod dm_nv
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 6A09-8861   
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
```       #Add menu entry to 40_custom, you can add more than one test version and test to see if one or the other works or from grub menu, use e and manually edit insmod RAID entry to each version until hopefully one works.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub

---

### Post by YannBuntu on 2012-12-26
> **oldfred said:**
> Boot-Repair can create a correct chain load entry, but I am not sure it does with two drives.

it does with 1, 2 or more ;)

---

### Post by Tom McD on 2012-12-27
Spent two days trying to make this work. Every step breaks something else.
 
Ran boot repair, and selected the RAID drive isw_defbbagaca_1Z2E24NN1 as the
location for grub2 (it is one of two locations in the drop-down menu). This gives me
a Grub2 menu at boot time. Selecting Windows still gives the secure boot failure.
Selecting Ubuntu gives error:
file not found: /boot/vmlinuz-3.5.0.21-generic.efi.signed not found
 
This requires repair by booting from USB-line and following recommended boot repair with no alternations. 
 
Which puts me right back to square one. The UEFI-Bios seems to know the right thing
to do, I just cant get winBootMgr or grub2 to do the right thing.
 
I was not able to understand the instructions from oldfred. The grub entries to be edited do not seem to look like the text in your message. Each xx_filename in the etc/grub.d directory look like large scripting files of several hundred lines, so I didn't change them.
 
-- Tom

---

### Post by YannBuntu on 2012-12-27
Please follow this procedure: [http://ubuntuforums.org/showpost.php?p=12406192&postcount=687](http://ubuntuforums.org/showpost.php?p=12406192&postcount=687)

Don't forget to update Boot-Repair (connect internet, then type 'sudo apt-get update; sudo apt-get install -y boot-sav' in a terminal) before each use.

---

### Post by oldfred on 2012-12-27
If you have secure boot errors, turn secure boot off.

Use Boot-Repair to fix your install. Grub should only be installed to efi partition with UEFI, I thought it did not even give any options, but Boot-Repair will handle that. 

What I do not know is what type of RAID you have,  or conversely what RAID driver grub needs to load to be able to "see" you partitions. Again I trust Boot-Repair.

---

