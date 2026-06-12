---
title: "Trying to dual boot with Windows 8.1 and encountering BSOD"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by charles.kronk on 2014-05-26
Hey all!

I'm really new to this so I'll just jump right in.

I used this guide ([http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)) to install Ubuntu 14.04 alongside Windows 8.1. 

Things went smoothly until step 7, in which the guide said I should boot straight into Windows. Instead my computer booted into Ubuntu. I thought this was a bit odd, but I continued through the guide and used boot loader, which I believe went off without a hitch (I didn't notice any particular errors or anything).

I continued through the guide again, and when I chose boot options, the four options came up just like the guide said:

1. Ubuntu
2. Ubuntu (Advanced)
3. Windows Boot Options
4. Setup

(these might be slightly different, I didn't write them down exactly...)

However, when I would click on Windows Boot Options or try any method of loading Windows OS, it would give me BSOD and force restart immediately. The error was bad_system_config I believe, but there was no exact error code.

I have no idea where to go from here and would appreciate any and all help! Please let me know if more info is needed! Thanks!

---

### Post by oldfred on 2014-05-26
Did you leave Windows hibernated or fast boot?
Is Ubuntu in BIOS boot mode and Windows in UEFI? Both must be in same boot mode for grub entry to work.
Have you tried UEFI/BIOS and directly booting Windows or one time boot key?

Best to see details. You can install into your Ubuntu or into the Ubuntu installer.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by charles.kronk on 2014-05-26
Thanks for the quick reply! There is a chance that it might be hibernating although it resists deleting the hibernation saying that the partition is "unsafe".

I've been trying boot loader and encountered an error that linked me here: [http://paste.ubuntu.com/7526085/](http://paste.ubuntu.com/7526085/).

---

### Post by oldfred on 2014-05-26
You are showing an HP which all seem to have UEFI boot issues.
Plus you have RAID, plus you have SFS or dynamic partitions in the RAID.
Each is often a major issue.
And this says you left hibernation on, or fast boot or that Windows needs chkdsk.
>  The NTFS partition is in an unsafe state. Please resume and shutdown



In your RAID you show this:
```
 /dev/mapper/isw_dgajhbjhbb_Cache_Volume1    ?           224    14,614,751    14,614,528  40 Venix 80286
/dev/mapper/isw_dgajhbjhbb_Cache_Volume2         18,415,616 1,100,087,295 1,081,671,680   0 Empty
/dev/mapper/isw_dgajhbjhbb_Cache_Volume4   *    889,388,928   889,389,249           322  42 SFS


```

Is it really RAID or Intel SRT?
And the Venix entry is likely invalid and the SFS is from dynamic partitions. 
 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[URL="http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from"]http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from

[/URL]  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[URL="http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf"]http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf

      [/URL]
 HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)

The Intel SRT is mostly standard across vendors.

 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
      
 Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

     
 
    [URL="http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf"]
[/URL]

[URL="http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from"]
[/URL]

---

### Post by charles.kronk on 2014-05-28
I feel a little behind on the terminology and all here... I ended up contacting one of my friends and we messed with it for about 10 hours before giving up and trying to reinstall Windows from the recovery disk...

Which also didn't work (saying that there were "no drives found" and to "load drivers"). Currently we are trying to download drivers on a USB in order force the recovery to see them, but at this point idk where to go.

---

### Post by oldfred on 2014-05-28
Because you probably have Intel SRT, the drive is seen as RAID.
And depending on what Windows version you have the 7 DVD only installs in BIOS mode. You have to convert it to flash drive and update it for UEFI install.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Beyond that these formums may know more on Windows.

 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

