---
title: "Ye old boot problem"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by ItsWrecked on 2015-10-09
Hi,

Thought I would give the nixes another go, has been a while.

After Upgrading after an install, Windows 7 cannot no longer be booted, I will try and explain.

Installed latest ubuntu to an old separate hdd(sdd) I had in this box to have a look.  Immediately after install and restart, I booted into win7 as per normal on the ssd (no grub), all good I thought.

I then rebooted machine (uefi bios) and interrupted the boot to boot select the drive ubuntu was installed on, the install seemed ok and all seemed to work.  An update was initiated, and towards the end I noticed it declaring win7 boot found on sda1.  Restarted after upgrade and I could no longer boot win7, device is inaccessible.

After searching around I have tried bootrec /fixboot ..../fixmbr  with with no success, chkdsk reports all good.

Tried grub update etc with no luck either.

I tried boot-repair, with no luck [http://paste.ubuntu.com/12725635/](http://paste.ubuntu.com/12725635/)

Any help would be greatly appreciated to boot back into win7, or copy data from sda2, which for some reason I cannot mount now either.

Thanks

---

### Post by yancek on 2015-10-09
You have install Grub code in the MBR of sda which is your windows disk.  Not sure why you did that.  You also have Grub in the MBR of sdc and sdd and sdd1 is where you have Ubuntu.  sdc has only one partition and that is windows.  Not sure why you installed Grub there You need the sdd (232GB drive) set to first boot priority as it has the correct entry for Ubuntu as well as windows on sda, your 465GB drive.

Not being able to mount a windows partition from Linux often is the result of the windows system being in hibernation.  That's the default for windows 8 & 10 but since you have 7, not sure it applies

---

### Post by ItsWrecked on 2015-10-09
> **yancek said:**
> You have install Grub code in the MBR of sda which is your windows disk.  Not sure why you did that.  You also have Grub in the MBR of sdc and sdd and sdd1 is where you have Ubuntu.  sdc has only one partition and that is windows.  Not sure why you installed Grub there You need the sdd (232GB drive) set to first boot priority as it has the correct entry for Ubuntu as well as windows on sda, your 465GB drive.

Not being able to mount a windows partition from Linux often is the result of the windows system being in hibernation.  That's the default for windows 8 & 10 but since you have 7, not sure it applies

I did not install grub on sda, I would like to make that clear.  When I installed ubuntu, I gave it its own drive to use(sdd), and that is where grub was installed.  This was checked as after the installation and reboot, win7 booted as per normal (there was no 'dual boot').

I then booted into the drive ubuntu was installed on, this was the first time I saw the grub boot menu. After I configured network, I started the system upgrade, after this upgrade had finished, I could no longer boot into win7 on the separate sda drive, grub had installed/changed the other drive.  

Now after all this, when trouble shooting, upgrading grub, running boot-repair, grub may have been installed anywhere, I do not know?

---

### Post by yancek on 2015-10-09
It doesn't matter how it got there, the Grub code is there.  What happened when you set the 4th drive (sdd) to first boot priority in the BIOS?  Did you have the same four drives attached during install in the same manner as they are now?  If so, booting from sdd should give you the option to boot windows also.  If you want windows code in the MBR of sda, you need a windows installation disk.  If there are other methods, I'm not aware.  There probably are but I don't use windows so have no idea.

---

### Post by sandyd on 2015-10-09
Try this:

Run boot-repair, and open up Advanced Options.
Where it says "Reinstall Grub", check the box next to it called "Restore MBR"
Click on the "MBR Options" Tab, and make sure that the drives and partitions are right.

Apply it, and you should be good to go.

---

### Post by ItsWrecked on 2015-10-09
> **yancek said:**
> It doesn't matter how it got there, the Grub code is there.  What happened when you set the 4th drive (sdd) to first boot priority in the BIOS?  

The first boot priority has always been sda

> **yancek said:**
> Did you have the same four drives attached during install in the same manner as they are now?

yes.

  > **yancek said:**
>  If so, booting from sdd should give you the option to boot windows also.  

Yes I have the option, but windows will not boot, gives the error that a device is inaccessible when chosen.

> **yancek said:**
> If you want windows code in the MBR of sda, you need a windows installation disk.  If there are other methods, I'm not aware.  There probably are but I don't use windows so have no idea.

Yes I have tried that, with no result. /fixboot and /fixmbr did not error.  chkdsk showed no errors, but when chkdsk /f was used it errored saying disk was not writable.

> **sandyd said:**
> Try this:

Run boot-repair, and open up Advanced Options.
Where it says "Reinstall Grub", check the box next to it called "Restore MBR"

I do not have that option

> **sandyd said:**
> 
Click on the "MBR Options" Tab, and make sure that the drives and partitions are right.

The tab is grayed out and has no content when selected.

[ATTACH=CONFIG]264882[/ATTACH][ATTACH=CONFIG]264883[/ATTACH][ATTACH=CONFIG]264884[/ATTACH][ATTACH=CONFIG]264885[/ATTACH][ATTACH=CONFIG]264886[/ATTACH]

I have just realised that sdc will have an os on it(win7 maybe xp), as well as sda, I could disable both sdb and sdc in bios and retry repair?


edit: naaa disregard, thinking of another drive.

---

### Post by yancek on 2015-10-10
Reviewing your posts, I'm not sure what you have done.  I asked if you were able to boot from sdd where Ubuntu is installed but you indicate when you select to boot windows you get an error from the windows bootloader that the device is inaccessible.  In that same post, you indicate the first boot priority has always been sda.  So have you changed the boot priority to sdd as suggested in the boot repair output and is the result the same?

If when you ran chkdsk /f you got an error saying the disk was not writable, you might take a look at some windows forums or the microsoft site.  Did you reboot windows twice after initially running the chkdsk as suggested in boot repair?  I don't know why you would need that but apparently you do.  I'm surprised the fixmbr and related commands had no effect.

I don't know why doing an update/upgrade immediately after install would change the bootloader location.  If i have  bootloader code in the MBR of drive A and update a system on drive B, it will not make any changes to drive A.  Done this many times.  Back to why you have Grub code on all the drives, I believe one of the options on the boot repair installs Grub to the MBR of all drives.  I don't use boot repair myself but I've read that here so I expect that is what happened in your case.

---

### Post by oldfred on 2015-10-10
If you run the auto fix in Boot-Repair it does install grub to the MBR of every drive. If you have more than one drive you never want to run the auto repair.

In advanced options you choose an operating system and the drive's MBR to install boot loader into.
Install Windows boot loader to sda and Ubuntu boot loader to sdd, if grub not currently working.

You may need to move boot flag to sda1, which is Windows boot partition. Boot-Repair is not showing sda2 which probably means it is hibernated or corrupted. If hibernated directly booting from sda's MBR with a Windows boot loader to the sda1 Boot partition may boot Windows or give you the chance to press f8 to get into internal repair console. 

Grub only boots working Windows, so if Windows does not need chkdsk nor is hibernated, you can change BIOS to boot sdd and grub. And from that boot either Windows or Ubuntu.

---

### Post by virgosun on 2015-10-10
I am faceing the same problem and boot-repair not work. I suggest you boot from Windows Installation CD and --> choose to repair  --> command line --> chskdisk

---

