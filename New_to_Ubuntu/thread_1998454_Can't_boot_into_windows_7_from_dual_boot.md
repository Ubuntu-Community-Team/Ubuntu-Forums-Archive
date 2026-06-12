---
title: "Can't boot into windows 7 from dual boot"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by bottaw on 2012-06-06
I made a dual-boot for my pre-existing windows 7 OS and Ubuntu 12.04 using the LiveCD. However, for some reason there are two selections for windows 7 whenever I boot up-- One leads me to a screen that says windows is damaged and that I should insert the recovery disc. The other selection boots up like normal, but freezes before the multicolored flag appears above "starting windows." The ubuntu section is working perfectly fine. I tried using a boot-repair program I found online, but it didn't really change anything. It gave me this url to post: [http://paste.ubuntu.com/1027624/]("http://paste.ubuntu.com/1027624/") 
I don't want to have to recover my computer again (This isn't the first time I've screwed up trying to install ubuntu.) Is there anyway I can fix this? I am a newcomer to ubuntu with no prior linux experience.

---

### Post by wilee-nilee on 2012-06-06
Did you resize the windows and let it run the auto chkdsk and make sure it boots before the Ubuntu install?

Give us the details on how you installed.

Do you have a complete image/clone of the windows 7?

Do you have a W7 recovery, or install disc?

---

### Post by bottaw on 2012-06-06
I resized the windows partition using the LiveCD basic method. It didn't even let me into windows to run the auto chkdsk. I just ran the installation following the basic instructions according to [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing") 
I selected the first option and resized the disk using the slider. Everything went great, but when I tried to boot windows first like it said I should, I wasn't allowed in. I do not have a complete clone of windows 7, but I do have all of my information backed up. I currently have a set of windows 7 recovery discs, but not the installation disk because my machine had it preloaded.

---

### Post by oldfred on 2012-06-06
You seem to have all the boot files in two partitions. Normally Windows has a small boot/repair partition with 2 of the three boot files & then the main install with just the one boot file. But you have all three in the main install which makes it bootable on its own.

You will need a Windows repairCD or USB to fix Windows. Always best to use Windows partition tools to shrink the Windows partition and immediately reboot so it can run its chkdsk to update itself. If f8 does not get you into a repair console then you need the repairCD. Try f8 almost at the same time you hit the Windows entry in grub.

A bit after the fact, but if you have another computer, know someone with the same (32 or 64 bit) version of Windows:

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)


If you run auto repairs from Windows it will overwrite grub2's boot loader in the MBR. If you have the Boot-Repair that should fix it or:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by wilee-nilee on 2012-06-06
> **bottaw said:**
> I resized the windows partition using the LiveCD basic method. It didn't even let me into windows to run the auto chkdsk. I just ran the installation following the basic instructions according to [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
I selected the first option and resized the disk using the slider. Everything went great, but when I tried to boot windows first like it said I should, I wasn't allowed in. I do not have a complete clone of windows 7, but I do have all of my information backed up. I currently have a set of windows 7 recovery discs, but not the installation disk because my machine had it preloaded.

Well we can try to fix windows, but if it was me I would start over with a install of it, since you are backed up at this point.

Windows 7 has a partitioner that will run from the OS, and is the best method here. 

Then install the ubuntu.

If you do not have a recovery disc to get to the recovery section, you will have to do a reinstall I believe. The recovery disc is the first thing you should be burning with any windows install, it is in the same area, the backup is in.

You can buy a recovery on line if you like to try and fix this.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Basically you have made the same mistake many do here, the resize was run incorrectly, and you have no way to get to the recovery, so if a fix was possible you could at least get there.

If it had been me I would have resized the W7 to the wanted size with its partitioner, rebooted to make sure it was running fine. Then run the on board back up of the whole thing cloned, then installed Ubuntu.

I probably would have even cloned it ahead of time but I use clonezilla a free open source app, the OEM installs have a one time image unless it is a Windows pro or above.

I see oldfred has posted as I have so ***his advice is always solid as well***. Mine is based sometimes on ease of travel, time to fix compared with just reloading.

---

### Post by bottaw on 2012-06-06
Thank you both so much. I was hoping I wouldn't have to recover, but oh well. Even though I already have the recovery discs, part of the problem may be because I didn't know what was in the recovery partition. My machine defaults to four partitions being used every time- one for HP-TOOLS, one for recovery, one for the system-such as BIOS and startup and stuff, and one for windows. I didn't know which one I should delete to make room for Ubuntu. Do either of you have any suggestions? Or should I ask that in a new topic?

---

### Post by oldfred on 2012-06-06
Some say the full circle mag article is very good.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Since setting up, updating & housecleaning a windows install is a lot of work, best to do that and then make a full image backup. 

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by wilee-nilee on 2012-06-06
> **oldfred said:**
> Some say the full circle mag article is very good.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

+1 here.

---

