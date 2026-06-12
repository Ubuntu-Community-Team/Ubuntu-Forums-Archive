---
title: "Need help with grub removal or configuration (?)"
date: 2017-07-01
forum: New to Ubuntu
---

### Post by hadavis212 on 2017-07-01
Hi All.

I am a pretty inexperienced Ubuntu user trying to RMA a failing hard disk (SMART error)  that happens to have ubuntu on it.  The desktop in question has Win10 and WinXP on separate hard drives, so three drives plus a backup drive for Win10 are in the system.  Ubuntu is the latest one installed and so its boot loader is the one I see to choose which OS I want to start with.  I think that is part of Grub.
I have hunted around in the bios trying to figure out how to tell it to boot from the drive with Win10 until I can reinstall ubuntu on a new drive, but no dice.  If I physically remove the bad drive, the system won't do much of anything, so I think grub is on that drive, but don't know what to do with that knowledge.

Could someone please guide me through this?

---

### Post by yancek on 2017-07-01
Are you able to boot the installed Ubuntu?  Do you see an option for whichever windows in the boot menu?  Are you able to boot either windows?  If you can boot the installed Ubuntu, have you run sudo update-grub and watched the output for a windows entry.  I would suggest that you boot either the installed Ubuntu or the Ubuntu installation media and download and run boot repair according to the instructions at the  site below.  And make sure when you do that, you select the option to "Create BootInfo Summary" and do NOT try to make any repairs.  Post a link to the output here as this will provide some details on your system and improve your chances of getting help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hadavis212 on 2017-07-01
I am able to boot the installed ubuntu or windows 10 from the boot menu.  I installed boot-repair successfully in ubuntu.  I have run boot repair--several times actually, but contrary to the instructions in your provided link, I am not seeing a way to get it to show me the paste2 link to the bootinfo summary as I understood it. As I watch it running, I see it says it is creating that link, though.  The instructions for boot-repair say that it won't create the link if the PC doesn't have a web connection.  I don't think that's relevant here (could be wrong) because I am posting this via the ubuntu install in question.

---

### Post by oldfred on 2017-07-01
Some (including me) have had issues getting auto upload to pastebin to work from an install.
You can manually upload to any paste bin type site you like. Report is generally too large to attach or post directly to forum.
[https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778)
You can add your issue to above bug report. More complained get faster fixes.

Most using live installer seem to have it work. Not sure of difference. Have not tried live installer recently myself.

With multiple drives & multiple installs, you need to have a current version repair or live installer for every installed system. And then using Boot-Repair or your Windows repair disk have a Windows boot loader on all Windows drives and grub for version of Ubuntu on Ubuntu drives whether UEFI or BIOS. But UEFI more difficult to set up that way as you have to plan ahead before partitioning drive to include an ESP.

Is system BIOS or UEFI?
UEFI often only boots from one ESP - efi system partition or the FAT32formatted partition on sda.

---

### Post by hadavis212 on 2017-07-01
Well, this seems to have worked:

[http://paste.ubuntu.com/24998206/](http://paste.ubuntu.com/24998206/)

As far as I know, I have BIOS.

OldFred, to your point about repair disks for each installed system, is that intended to mean that I will need those now in my current situation or if I have trouble with specific OSes or devices down the line?

The way my system has worked up until now, I can choose win10 from the grub menu, from which time I am taken to a different boot menu for the two windows OSes available.  Does that change anything?

---

### Post by oldfred on 2017-07-01
I suggest you have a repair or live disk for current version of every system at all times.
I have several Linux repair flash drives with multiple versions of Linux, Ubuntu, Knoppix, gparted, Boot-Repair, SuperGrub and maybe others not as current.
When I had XP, I had the original install disks but also had a Windows 7 repair flash drive. 

Any auto install of grub, installs it to MBR of sda. But if multiple drives, better to only use Something Else install option and install grub to MBR of same drive (combo box at bottom of partitioning screen).

Since you only have Windows on sda, your sda's MBR should have a Windows MBR boot loader. But install in sda does not have a BCD?
Install in sdc looks like it may have been sda drive at one time. It shows both XP & Windows 7 or later boot files. 
So sdc should have Windows boot loader.

And then grub should only be in MBR of sdd and BIOS set to default boot sdd. Only then if issues with Windows might you want to change to directly boot Windows from its drive. Grub really only boots working Windows or Windows cannot be hibernated nor need chkdsk.

If already installed you can run Windows repairs on each install to update to have complete set of Windows boot files. Also then grub can find each install and offer to directly boot from grub menu.
 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

