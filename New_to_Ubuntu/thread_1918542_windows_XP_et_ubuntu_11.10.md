---
title: "windows XP et ubuntu 11.10"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by pqku on 2012-02-01
hi guys,

I bought a computer with free OS.
I didn't have the cd for windows XP yet so I set up ubuntu 11.10.
Can I install now Windows XP but I wanna keep linux at the same time. Is ti possible ?
Thanks

---

### Post by arochester on 2012-02-01
"How to dual boot Linux and Windows XP (Linux installed first) -- the step-by-step guide with screenshots" - [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by pqku on 2012-02-01
I cannot open this link :/


Unfortunately APCMag.com is not currently available in your country for legal and commercial reasons.

Do you have an other one ? 

Thank you

---

### Post by varunendra on 2012-02-01
The easiest way would be to recreate partitions (removing Ubuntu), then install XP first and Ubuntu later. You can try [remastersys]("http://www.geekconnection.org/remastersys/") to create a live backup DVD of the currently installed Ubuntu, which, if successfully created, can be used to reinstall with all current apps and settings (within 5-10 min!).

However, if you want to go 'XP over Ubuntu' way, this should be all you need:

[LIST=1]
[*][COLOR=Red][B]Backup your data first (preferably on an external medium) since partition manipulation operations always have a potential risk of data loss!
[/B][/COLOR]
[*]Boot with Ubuntu live cd, and run gparted
[*]Resize or delete one of the existing partitions to create space for one primary NTFS partition for XP. [COLOR=DarkRed](If you are resizing, better empty the partition, or move as much data as possible from it beforehand, because otherwise it may take too long to finish the operation, and any attempt to interrupt once it started is almost a guarantee of unrecoverable data loss)[/COLOR]
[*]Create a new NTFS partition in this space, and assign it a suitable 'Label' for easy recognition, when installing XP.
[*]Right-click on this partition > click "Manage Flags" > check (tick) the "boot" checkbox to set it 'active'.
[*]Reboot with XP cd, and choose the newly created partition for installation
[*]When  the installation is finished, boot from hard disk to see if XP boots correctly.
[*]Reboot with Ubuntu live cd (same one from which you have installed it) and follow [this quick guide to restore grub]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2") on MBR to be able to boot already existing Ubuntu again.
[*]After correctly reinstalling grub, reboot into installed Ubuntu, and run **sudo update-grub** to let it recognize and add winXP to its boot menu. [COLOR=DarkRed](NOTE: the partition holding XP must have "ntldr" and maybe also "ntdetect.com" file to be recognized by grub. If these don't exist there, simply copy-paste them from the partition on which they have been installed)[/COLOR]
[/LIST]
If  you have any confusions or questions, please boot with live cd, run gparted and post  its screenshot while it is showing the target hard disk layout.

For a detailed howto: [https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by blackbird34 on 2012-02-01
And to get around the "legal reasons", perhaps you could use [Tor]("https://www.torproject.org/projects/torbrowser.html.en") or a [Proxy]("http://peacefire.org/") (though you may have already...)

---

### Post by pqku on 2012-02-02
Thank you.
Actually i can unistall linux and reinstall after on windows xp.

How can i install windows xp and delete linux ?

Thanks

---

### Post by mastablasta on 2012-02-02
boot from XP install cd, use fdisk do delete partitions, reformat the disk (probably to NTFS) and then install winXP.

---

### Post by varunendra on 2012-02-02
> **pqku said:**
> Thank you.
Actually i can unistall linux and reinstall after on windows xp.

How can i install windows xp and delete linux ?

Thanks
Simplest way:

**_Install XP First_:**

[LIST=1]
[*]Boot with XP cd
[*]on the partitioning stage, delete all existing partitions (assuming you have nothing to save, or have backed up externally whatever you had on it)
[*]recreate one partition, large enough to install XP+apps on it (typically 20-40GB). Leave the rest of space as 'unused'.
[*]install XP. Let it finish.
[*]Boot from hard drive to see if XP is working as expected (just a formality, can be skipped)
[/LIST]

**_Install Ubuntu next_:**

[LIST=1]
[*]reboot with Ubuntu live cd/usb. Select "Try without installing" mode.
[*]run Gparted and load the target drive on it.
[*]In the "Unsused space" you left above, now create partitions for Ubuntu and swap. [COLOR=DarkRed]*(please refer the Ubuntu partition plan below for further advice on this)*[/COLOR].
[*]Create at least one extra ntfs partition (primary or extended, as required) for sharing data between XP and Ubuntu.
[*]Proceed with installing Ubuntu on the ext4 partition you created for root.
[*]Make sure the grub boot loader is being installed on the MBR of the correct drive (it'll be selected automatically, you just have to confirm. It rarely needs correction). The correct place for grub2 is something like sda, sdb etc. (not sda**1**, sda**2** etc.)
[*]Finish the installation, and reboot. The grub menu should welcome you to choose between XP or Ubuntu! :)
[/LIST]


**_Suggested Partition Planning (may vary depending upon usage)_:**

[LIST]
[*]For Ubuntu, I usually suggest **one ext4** partition **for root (/)** (20GB or more)
[*]**one 2GB swap**. If you are going to use "Hibernation" feature, then make it equal to or slightly bigger than the amount of RAM. (but at least 2GB, in case the RAM is less than 2GB)
[*]I DO NOT RECOMMEND separate /boot, /home, etc., as it sometimes adds unnecessary complexity and limitations.
[*]The size for the root ext4 partition should be **at least 20GB**, assuming you will keep all your user data on the separate "Data" partition (the extra NTFS one). Make it at least 26GB if you are planning to do a lot of stuff with a lot of applications.
[*]All of this makes a typical layout like this:
[/LIST]
[INDENT]
[LIST=1]
[*]One 20-40GB partition for XP, (Primary- NTFS)
[*]One 20-40GB partition for Ubuntu (Primary- Ext4)
[*]One 2GB or more Swap partition (Primary)
[*]**One Extended Partition in the rest of the space** (This is important to have, since you can have no more than 4 primary partitions. So this facilitates more (logical) partitions for future requirements)
[*]One or more NTFS partitions for Data (Extended- NTFS)
[/LIST]
[/INDENT]

Hope it is not very confusing. I'd love to assist, if you have any doubts or questions.

---

### Post by 3rdalbum on 2012-02-02
Windows XP is ancient; it's so old that the installer disc will probably crash if it detects a SATA hard disk.

If you get the Blue Screen of Death while the installer boots up, you will need to go into the BIOS and change the "SATA mode" to "Compatibility" or "IDE". Once Windows XP is installed and you've got the drivers for the SATA controller, you can change it back to "Performance" or "AHCI" to get better speed from the hard disk.

---

### Post by pqku on 2012-02-02
Thank you , I have a question.
Once i install windows xp , there will be no driver at all ?
So i have to install them right ?
But how can i install them if i cannot plug a ethernet cable because no driver to read it ?
Wih my laptop they give me a dvd , maybe there are the driver inside ?
Thank you

---

### Post by varunendra on 2012-02-02
> **pqku said:**
> Thank you , I have a question.
Once i install windows xp , there will be no driver at all ?
So i have to install them right ?
XP has most of the drivers included for the generic type hardware that existed when that version of XP was released. So your basic hardware 'may' be picked up by default installation. But it is very unlikely since your laptop seems to be 'new'!

> **pqku said:**
> But how can i install them if i cannot plug a ethernet cable because no driver to read it ? In that case, you'll have to install them from a CD or USB. Alternatively, you can boot into Ubuntu live to download then, then install from within XP.
> **pqku said:**
> Wih my laptop they give me a dvd , maybe there are the driver inside ?Maybe, mabe not! If the laptop is indeed new, then most probably the DVD contains _only Win7 drivers_! It should be mentioned on the DVD. If so, then you may have to go to manufacturer's site to download drivers for XP. You can use another computer for downloading, or can use Ubuntu live to do it (it will almost certainly pick up the cable connection).

---

### Post by pqku on 2012-02-02
Thank you for you help.

---

