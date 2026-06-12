---
title: "Ubuntu 20.04 wont boot from UEFI HHD, safe mode shows drive and exit starts Ubuntu"
date: 2020-12-15
forum: New to Ubuntu
---

### Post by padser on 2020-12-15
[B]Total Ubuntu newbee,
[/B]
Ubuntu 20.04 won't boot from UEFI HHD, safe mode shows drive and exit starts Ubuntu?
Installed on new machine which came with windows 10 installed, installed Ubuntu from USD drive wiping all Microsoft/Windows stuff.
Got Ubuntu EFI partition on FAT32 formatted disk.
Power up but no startup of Ubuntu, force restart into safe mode and Ubuntu partition shows as no1 in boot screen, exit with no changes saved and Ubuntu starts up?
Any idea of what is going wrong?

---

### Post by oldfred on 2020-12-15
What brand/model system?
What video card/chip?

Have you updated UEFI from vendor. 
It may reset some settings to defaults so after an update check that settings are still correct.

Do you have UEFI set to boot in UEFI mode?
If set to BIOS/CSM/Legacy, it may try to boot in that mode, then switch to UEFI?

Just to confirm configuration is otherwise correct.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tea for one on 2020-12-15
> **padser said:**
> Power up but no startup of Ubuntu, force restart into safe mode and Ubuntu partition shows as no1 in boot screen, exit with no changes saved and Ubuntu starts up?


Can you clarify a couple of details:-

[COLOR="#0000FF"]force restart into safe mode[/COLOR] - Does this mean you enter your UEFI boot manager?
[COLOR="#0000FF"]Ubuntu starts up[/COLOR] - Starts without problems and you log in?

---

### Post by padser on 2020-12-16
hi tea for one,
Yes into safe mode, shows the ubuntu boot drive at top of list, exit without saving and everything is fine.

---

### Post by padser on 2020-12-16
Hi oldfred,

sys and hardware info:
Intel® Core&#8482; i9 14 Core Processor i9-10940X (3.3GHz) 19.25MB Cache
ASUS® ROG STRIX X299-E GAMING II
8GB NVIDIA GEFORCE RTX 3070

Not updated UEFI apart from disabling SecureBoot, was supplied with windows 10 installed, booted from Ubuntu USB, wiped that pesky microsoft with Ubuntu 20.04

Set to boot in UEFI mode, checked in terminal came back with "EFI boot on HDD" SecureBoot disabled as needed to sort out nvidia driver probs, latest nvidia drivers working perfectly.

now you lose me a bit ppa version with live installer Boot-info summary? but I installed 

installed grub-efi

Details of my system:
Device       Start        End   Sectors   Size Type
/dev/sdb1     2048    1050623   1048576   512M EFI System
/dev/sdb2  1050624 1000214527 999163904 476.4G Linux filesystem

There is a 2T drive also installed with id of sda and I think I read somewhere boot needs to be sda not sdb as mine is or that could just be snow blindness from all the sites I've been visiting looking for help.

Sorry for my inexperience an hope I've answered enough of your questions.

---

### Post by oldfred on 2020-12-16
If you have grub installed to ESP on sdb in UEFI boot mode and UEFI set for UEFI boot, it should work.
My older Z97 Asus only wanted to work in UEFI only mode, not UEFI or Legacy mode.

I did have to change a variety of settings in UEFI on Z97. Some were optional, others required.
Asus z97 screenshots probably similar since Asus & UEFI:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)

Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubunt](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubunt),

Ubuntu's Ubiquity installer only wants to install to first drive, either sda or first NVMe drive's ESP.
But grub can install to any drive & boot in UEFI mode.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by tea for one on 2020-12-16
> **padser said:**
> 

Details of my system:
Device       Start        End   Sectors   Size Type
/dev/sdb1     2048    1050623   1048576   512M EFI System
/dev/sdb2  1050624 1000214527 999163904 476.4G Linux filesystem

There is a 2T drive also installed with id of sda and I think I read somewhere boot needs to be sda not sdb as mine is or that could just be snow blindness from all the sites I've been visiting looking for help.

You did not mention in your original post that you had two drives on the PC.

Anyway, you can re-install (or redirect) grub while running Ubuntu with this command in the terminal:-

```
sudo grub-install --efi-directory=/boot/efi /dev/sdb

```

You have already indicated that sdb is the location of Ubuntu.

---

### Post by padser on 2020-12-18
Hi tea for one and oldfred,
I've run through all your suggestions, done all the UEFI boot stuff as suggested and all the grub stuff and everything is the way it should be, so here where I am:
Generally if the system is up and running through bios override in safe mode start up (ubuntu drive always shows and boots without problem this way) I can shut down and restart mostly okay but every now and then it gets cofused again and I'm back in safe mode which again via boot override option gets me going again. So sometimes it will boot okay and then sometimes it wont, keep checking ids on disks and the isn't any swapping on startup going on, sda is always sda and sdb is always sdb, all a bit crazy now.
I'm thinking, can I swap the IDs of sdb to sda and vice versa or implement some sort of persistent block device naming just in case there is a problem with my system disk not being sda or at least change the current media disk sda to sdc so the UEFI stuff is getting hung up on the sda disk with no bootable system on it?
Or am I showing my complete newbee ignorance. 
Thanks again for all your help so far:)

---

### Post by tea for one on 2020-12-18
> **padser said:**
>  So sometimes it will boot okay and then sometimes it wont, keep checking ids on disks and the isn't any swapping on startup going on, sda is always sda and sdb is always sdb, all a bit crazy now.


You could try a little experiment.

Isolate, de-activate (via UEFI set up) or physically remove your 2TB drive, boot into Ubuntu and see if the drive has changed id.

Is the 2TB drive used for data storage or do you intend to add other operating systems?

---

### Post by padser on 2020-12-18
Hi tea for one,
Inexperience showing now - how do I de-activate (via UEFI set up) and yes it is only going to be used for data storage no other operating systems.
Would prefer to de-activate if poss rather than physically remove as I don't have anti-static gear for going into the beast!!!

---

### Post by oldfred on 2020-12-18
Most new UEFI have a setting on drives perhaps the same as AHCI/Intel RST where disabled is a setting. Or drive is not seen.

UEFI/BIOS enumerates drives. And then port order usually determines which drive is sda, sdb etc. But  drive speed ( or how quickly seen by UEFI/BIOS) or even plugging in a flash drive can change drive's device setting/order. 

I always try to use SATA0 port for drive that will be boot drive. But on my NVMe system I had to check as some ports are disabled if NVMe is used. And on all my current & older systems, when I plugged in a flash drive as sdc, then on reboot flash drive was sda & every other drive changed up a letter.

---

### Post by tea for one on 2020-12-18
> **padser said:**
> Hi tea for one,
Inexperience showing now - how do I de-activate (via UEFI set up) and yes it is only going to be used for data storage no other operating systems.
Would prefer to de-activate if poss rather than physically remove as I don't have anti-static gear for going into the beast!!!

When you power on the PC, there is a dedicated key to access UEFI set up - do you know the keystroke for this?

Often it appears during power on such as:-

F10 - Boot Menu
F2  -  UEFI Set Up
F7  -  Update Visual BIOS (UEFI)

Once I have entered the set up pages and navigated to Devices, I can de-activate all sorts of Hardware, such as SD card reader, SATA ports, USB ports, Bluetooth etc.

Your UEFI will be different from mine because there is no consistent standard and each vendor has different ways of displaying the information.
Luckily, all the options in my UEFI set up are available without additional supervisor passwords.

You'll undoubtedly be able to find all the info on your vendor's internet pages.

---

### Post by padser on 2020-12-18
Hi Peeps,
Have just gone feral and dived in to the beast disconnected the 2TB drive and rebooted, got straight into Ubuntu, shut down, started up again and again straight into Ubuntu..............................10 times later I'm still booting with no problems and boot drive has changed to sda no longer sdb, so sata drive is confusing something somewhere?, another possible spanner in the works may be that Ubuntu system is on my Solid State Drive 512GB PCS 2.5" SSD, SATA 6 Gb (520MB/R, 450MB/W) I don't know if that causes any problems when the other is installed as well?

---

### Post by tea for one on 2020-12-18
Gone feral..........nice metaphor.

My next suggestion:-

Shut down Ubuntu and power off
Re-activate (or re-attach) the 2TB drive
Boot up Ubuntu and see if you are happy with drive id (some UEFI will nominate identities depending on when they are attached to the MB)

If your 2TB drive is now [COLOR="#0000FF"]sdb[/COLOR], you could use Disks (gnome-disk-utility) to create a permanent mount point for the future.

Time to go feral again...........

---

### Post by oldfred on 2020-12-18
When you reconnect drive note which SATA port you use.
You want to use a higher numbered port that current installed drive.
You may have to look at manual for your system as my motherboard had two in the middle as SATA0 & SATA1 and then 3 & 4 on one side and 5 & 6 on other side. Very confusing. And fine print, and manual's drawing was not totally clear on which was which.

---

### Post by padser on 2021-01-01
Hi Peeps,
Hope you all had a safe festive season:)
Tried all your suggestions/approaches but to no avail?
Kept trawling around and found some stuff on the ASUS motherboard forum relating to non booting windows systems where discussions as to the use of XMP on motherboards, is it more of a problem e.t.c and when next in my bios I found this ram speed thingy enabled. Only other options were "auto" or "manual" so I plumped for "auto" and lo and behold the computer has been booting up perfectly for 5 days now.
I have no explanation as I'm in no way talented enough to even try to understand:) but thank you both for your help as it moved my understanding of ubuntu in an upward direction.
All the best for 2012.

---

