---
title: "Clean install of Ubuntu Mate 18.04 need to move grub"
date: 2018-05-02
forum: New to Ubuntu
---

### Post by dave1956 on 2018-05-02
I am downloading and about to do a clean install of Ubuntu Mate, I did do a n upgrade of Ubuntu 12 to 16 and a lot of things went wrong.

First thing I need to do is move grub, took a long time to sort this out, some how grub is on an IDE drive when it should have been on the SATA drive.. I am going to replace the IDE drive with a larger IDE drive or maybe put both in and change the DVD drive to sata ?..

I know when I boot of the disc I have to "Try or do some thing different option" then some thing with fdisk ? maybe, had it wrote down but some one has done a runner with my paper note book.

Think I have every thing backed up, book marks and passwords ? 

I will also need to get an older version of google earth running and put back in all the POI's that I have saved up over the years, towns, hotels train stations etc.

First things first.  help moving grub please, 

Dave

---

### Post by oldfred on 2018-05-02
You normally do not move grub.
You can from inside an install, just reinstall it to any drive's MBR.
Or you can do a full uninstall/reinstall of grub.
Or use Boot-Repair to reinstall grub.

I like running Boot-Repair just to document system.Firefox & Thunderbird are normally in hidden files in /home, so if you have a full backup of /home then you have them. Often with new install you have to start Firefox or Thunderbird then copy yiour entire profile over and edit profile.ini to use old profile not new one.
 Also good to export list of installed apps. It is just a text based list. Best to remove kernels or anything you know you do not want, but it includes all the lower level dependencies, so long list.

         discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery

[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997) 

[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

### Post by dave1956 on 2018-05-02
> **oldfred said:**
> You normally do not move grub.
You can from inside an install, just reinstall it to any drive's MBR.
Or you can do a full uninstall/reinstall of grub.
Or use Boot-Repair to reinstall grub.

I like running Boot-Repair just to document system.Firefox & Thunderbird are normally in hidden files in /home, so if you have a full backup of /home then you have them. Often with new install you have to start Firefox or Thunderbird then copy yiour entire profile over and edit profile.ini to use old profile not new one.
 Also good to export list of installed apps. It is just a text based list. Best to remove kernels or anything you know you do not want, but it includes all the lower level dependencies, so long list.

         discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery

[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997) 

[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

Thanks fred, most of what you have given me, most of which I don't understand, but I do know that the computer will not, or did not reboot to the DVD drive when I had the IDE drive plug pulled out.
Hence the question on moving grub, I would like to point out, that I do not like computers, but I really hate windows.
Ubuntu Mate is what my old version of Ubuntu 12 looked like, which I like to use.


I will pull the plug on the IDE drive and see what happens, as the saying goes.. Stay tuned for the next song ?

Dave

---

### Post by oldfred on 2018-05-02
You boot DVD from BIOS or if newer computer UEFI.
Often f10 or f12, check your manual, and choose what drive, DVD, flash drive or any internal drive to boot from. Assumes valid boot loader or boot files are on that device.

---

### Post by dave1956 on 2018-05-03
> **oldfred said:**
> You boot DVD from BIOS or if newer computer UEFI.
Often f10 or f12, check your manual, and choose what drive, DVD, flash drive or any internal drive to boot from. Assumes valid boot loader or boot files are on that device.

Hi fred, maybe I should say oldfred, but I like the sound of young fred
It is F2 on this unit, but when the IDE drive is un-pluged the OS fires up from the DVD and goes as far as the second dot on the Ubuntu install from the DVD, and hangs there for hours, until I hit the reset... strange?

I am going to hold back a few days on the clean install, got a bill to pay which has to be done with on-line banking..... from P to D to S then C, long gone are the days when you could walk into a bank and pay the bills, now we have to wait days for this to work and that to work..
If you are from the UK, you will know about the TSB bank on-line banking failure, 2 million customers effected.

Dave

---

### Post by oldfred on 2018-05-03
Ancestry only says I am 49% from England. I thought it would be 100% since both maternal grandparents were directly from Northhampton area. And Dad was from Canada,but probably English.

I like to know what is installed where for booting. So I run this, before & after any major changes. And good backups.

What brand/model system?
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

