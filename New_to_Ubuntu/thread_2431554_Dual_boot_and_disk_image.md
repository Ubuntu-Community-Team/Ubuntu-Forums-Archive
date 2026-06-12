---
title: "Dual boot and disk image"
date: 2019-11-18
forum: New to Ubuntu
---

### Post by matusa15 on 2019-11-18
Hello, Im fairly new to ubuntu, i had been using it form a few months now (since I tried to use W10 actually ) and Im really happy, 

I keep W10 in a different partition, because sometimes I like to play games, but I want to get rid of W10 and come back to W7, I have to format my hard drive in order to do this, but since I alredy did some configurations in ubuntu I dont want to start with ubuntu form scratch, so I would like to create an image of the ubuntu partition, format the hard drive with W7 requeriments and use the ubuntu image to restore the system, so my concerns are

- Is this goint go work?, is a goos approach to the problem?
- What ubuntu partitions do I need to backup
- How do I get back GRUB?


thnaks in advance

Cesar

---

### Post by yancek on 2019-11-18
A default install of windows 10 uses UEFI so if you are successfully booting both sysem, Ubuntu is also UEFI.  It is possible to install windows 7 UEFI but you will need to do some research on how that is done.  Both systems should be either UEFI or Legacy in order to boot both without going into the BIOS firmware.  You can verify that your system is UEFI with the command below which should show an EFI partition if you are using it.

```
sudo parted -l
```

That's a lower case Letter L in the command.

Installing windows 7 UEFI would eliminate the need to reinstall Ubuntu.  The microsoft site below explains installing windows 7 uefi. 

[https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/](https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/)

---

### Post by oldfred on 2019-11-18
Be sure to backup your Windows 10, you really should reinstall it next January as Windows 7 is then EOL.

Windows 7 End of Life - January 2020

---

### Post by crip720 on 2019-11-18
If you have enough ram, more 4GBs, might be better to have Win 7 as a VM.  In two months Win 7 will lose security updates and any other updates.  For two months does not make much sense to maybe mess up a working system.

---

### Post by matusa15 on 2019-11-19
[COLOR=#000000]Thanks, Im sure thay my system is UEFI... that should do the trick, anyway just in order to gather some knowledge, using partition images as "disaster recovery" procedure, as i used to do with windows, works in the same way with ubuntu?[/COLOR]

[COLOR=#000000]Regards[/COLOR]

[COLOR=#000000]Cesar[/COLOR]

---

### Post by oldfred on 2019-11-19
Some like to do the image backup.
discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/](https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

But with Ubuntu you can quickly reinstall. I have it down to about 10 minutes from RAM copy of ISO to SSD. Another 20 Min to reinstall all software from exported backup list & all user configuration is in /home. I have all data in a separate data partition (did that with Windows where possible also).  So you do not have to back up Ubuntu, just your data and configuration. About impossible to do that with Windows, so full image is the norm with Windows.

---

