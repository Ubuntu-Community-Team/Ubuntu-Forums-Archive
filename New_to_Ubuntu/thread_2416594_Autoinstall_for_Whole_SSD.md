---
title: "Autoinstall for Whole SSD?"
date: 2019-04-11
forum: New to Ubuntu
---

### Post by emmysage on 2019-04-11
Hello all,

I've used ubuntu before but this is the first time dual booting with two separate SSDs, and I have a question about the installation process. If I select the option to wipe the entire disk and install the operating system on it, can I choose which SSD I would wish to use? I manually divided the /var /tmp /swap etc. and I didn't allot enough space for memory, which has made ubuntu not perform as well as I was hoping. I am looking to redo it, but the autoinstall (and subsequent wipe of the hard drive) option instead of manual mode. In essence, I just don't want it to overwrite my SSD that has Windows because I want to dual boot, and I also want it to use the entire space that I have on my second SSD. Is this possible? Can I choose my second hard drive and have it only wipe and install on that one instead of the one with windows on it?

Thank you, I hope I was clear enough
Emmy

---

### Post by oldfred on 2019-04-11
I only trust Something Else, so I have control. Auto install normally works but if Windows not seen or some other issue it may get overwritten.
You also should have current backups of all your data and configurations. 

Most desktops do not need separate partitions for system folders with the possible exception of /home.
Default install is now just / (root) as it now uses a swap file. And if UEFI, you will need an ESP - EFI system partition. But only one per drive, and if Windows seen as sda or first drive if NVMe, then it may add another folder into the existing ESP.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
      [/URL]
 Good advice on UEFI and two drive installs and links to UEFI explanations
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration) 
    [URL="https://help.ubuntu.com/community/UEFI"]
      [/URL]
 Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[http://ubuntuforums.org/showthread.php?t=2305876](http://ubuntuforums.org/showthread.php?t=2305876)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot](http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot)
[http://askubuntu.com/questions/720827/using-ubiquity-for-the-full-disk-encrypted-install-to-disk-on-dev-sdb-instead-o/722147#722147](http://askubuntu.com/questions/720827/using-ubiquity-for-the-full-disk-encrypted-install-to-disk-on-dev-sdb-instead-o/722147#722147)
hide sda so second drive seen as sda
[http://askubuntu.com/questions/797989/ubiquity-mounts-wrong-esp-during-install](http://askubuntu.com/questions/797989/ubiquity-mounts-wrong-esp-during-install)
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378) 
    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by TheFu on 2019-04-11
Unplug the SSD you don't want written, assuming it isn't m.2.
If you want easier control over storage, but separate management/limits, choose to use LVM. It is slightly more complex, but fixing the sizing issues you have listed above is relatively simple. Making ext4 logical volumes larger can happen while the OS is running, for example.

After the install finishes, you reboot and make certain stuff is good enough, then you can reconnect the Windows SSD, boot into Ubuntu and run **grub-install** and **update-grub** to place it into the other drive, if you like .... or not.  **update-grub** will search for all OSes on all disks and add them to the boot menu.

Also, do you know that an install and restore of a proper backup to the same computer should take less than 30 min total.  If it takes longer, I'd say you are doing it wrong. Backup settings, data, /home/ and anything you've placed in odd locations.  Also create and backup a list of all the manually installed packages - apt-mark will do that.  At restore, just install the same OS as before, using whatever storage layout you like - these sorts of backups don't care about that, then put the settings, data, /home/ and odd-location stuff back where it was originally.  Lastly, feed in that list of manuallly installed packages to apt-mark and run a dselect task to have them all installed.  Done and done.  On an SSD, it should be faster.

The only reason a restore should take over 45 min is if there is lots and lots of data.  Usually, this isn't critical to have back immediately, so get everything except the huge data areas restored, then install the manual packages before going back to load up the TB of media stuff.  When you are done, the machine should feel exactly like it did before.  No settings to tweak, no missing packages to vaguely remember and install.  It is the same system as before.

Don't know which areas to backup? The "Linux File System Hierarchy Standards" has a table to explain. Google it.

I've been doing backups in this way for 8+ yrs and have used the restore technique a few times a year, when different disks failed on different systems.  Just last week, I moved a HDD, Legacy boot install over to a UEFI + SSD install using these techniques. I had to be more careful about some of the OS settings in /etc/ since things changed, but it was "my machine" about 45 after I started.  So far, I haven't noticed anything missing. Of course, when I was new to Linux, I didn't have the skills to think up this method or the skills to know which 10 files in /etc/ should and shouldn't be restored post-fresh-install.  That comes with experience. Which happens by trying to accomplish a restore.  Plus, it isn't like you have anything to loose. Even with just /home/ and the list of manually installed packages, you are way, way, ahead of the curve.

It would be smart to have a bootable flash drive ready, so if anything goes wrong, you can fix it.  Same for having backups for Windows. I can't help with Windows backups. The licensing, proprietary software, each with different keys, gets in the way of my mellow. ;)

---

### Post by emmysage on 2019-04-11
Thanks for the comments! I am not super familiar with the partitioning lingo so a lot of it went over my head--but thank you for the information nonetheless and I will work on it.

TheFu, I tried to resize the ext4 volume in charge of the memory that I have on the OS (I can't recall if it was root or /home) but it wouldn't let me resize while the OS was running. It would only let me downsize it. I booted into the usb that I have with the ubuntu installer and it would let me increase the size but I would have to format it. Which is okay, but I wanted to see if I would be able to just have the "Erase Disk and Install Ubuntu" option available instead of having to manually create all of the options for the OS. I could unplug the drive that has the windows OS on it but I was also scared I would somehow mess with the motherboard. The paranoia to create an issue that would be costly or more difficult to repair is real here, haha. But I might honestly just unplug the windows cable from the motherboard, boot back into the flash drive, hit the erase all and install ubuntu option, and try to install it onto the other SSD that I have dedicated to ubuntu. I guess it would make the most sense. 

Do you think that's a viable option for me?

---

### Post by oldfred on 2019-04-12
A lot of new systems do not require you to physically unplug drive, but logically in UEFI unplug/turn off/de-activate a drive. 

You need to always use live installed to modify partitions as partitions must be unmounted.
Resizing should not require reformatting.

If drive not seen, then default install to SSD is a good option. Default install in UEFI mode will be just ESP and / (root). 
Only if you use Something Else, then you can add /home as another partition if desired.

If newer UEFI system, then how you boot install media, UEFI or BIOS is then how it installs. And you need to be sure to boot/install in same boot mode as Windows. Microsoft has required vendors to use UEFI since 2012 & release of Windows 8, but users sometimes install in the old BIOS boot mode.

---

### Post by TheFu on 2019-04-12
> **emmysage said:**
> Thanks for the comments! I am not super familiar with the partitioning lingo so a lot of it went over my head--but thank you for the information nonetheless and I will work on it.

TheFu, I tried to resize the ext4 volume in charge of the memory that I have on the OS (I can't recall if it was root or /home) but it wouldn't let me resize while the OS was running. It would only let me downsize it. I booted into the usb that I have with the ubuntu installer and it would let me increase the size but I would have to format it. Which is okay, but I wanted to see if I would be able to just have the "Erase Disk and Install Ubuntu" option available instead of having to manually create all of the options for the OS. I could unplug the drive that has the windows OS on it but I was also scared I would somehow mess with the motherboard. The paranoia to create an issue that would be costly or more difficult to repair is real here, haha. But I might honestly just unplug the windows cable from the motherboard, boot back into the flash drive, hit the erase all and install ubuntu option, and try to install it onto the other SSD that I have dedicated to ubuntu. I guess it would make the most sense. 

Do you think that's a viable option for me?

If you are really new to all this, listen to Oldfred.  The resizing methods I mentioned only work with LVM already installed and don't allow a partition manager to resize them. Only LVM tools can be used.

Until you nail down the HDD and partitioning terms, this will all seem really complex. It isn't, but getting used to them will be important to ensure you don't accidentally destroy data you want left alone.

If you have any concerns about accidentally harming your Windows install - physically unplug the device. The extra 5 minutes is worth it. People have and do totally destroy their Windows setups all the time.  There is almost ZERO chance you can physically harm any hardware unless you do something physical to it these days.

---

### Post by emmysage on 2019-04-13
Thank you oldfred and TheFu for the information! I'm going to work on ubuntu later tonight. I appreciate it :KS

---

