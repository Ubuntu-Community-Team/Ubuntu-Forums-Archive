---
title: "cloning ssd with dd command"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by hugh4 on 2014-10-24
Hi,
I need to update the firmware of my SSD in the next week or so when Samsung release the fix for the 840 evo ssd.
I want to clone the disk to a USB hard disk just in case. I assume I need to run the dd command from a bootable usb and not from the bootable ssd I'm cloning. Is that right?
Cheers

---

### Post by JazzPotato on 2014-10-24
The easiest way to do this would be to use the clonezilla live disk.
[http://clonezilla.org/](http://clonezilla.org/)
Bear in mind that the partition you are cloning to should be equal in size or larger than the one you cloned from.

Cheers, and good luck :-)

---

### Post by oldfred on 2014-10-24
If you use dd you erase all data on hard drive as it copies over MBR. 
If you just dd partition you may not have full backup, but should just have to reinstall grub & perhaps partition table which then you may need to separately backup.

Often better to use one of the other image tools.
But I prefer to just backup my data, configuration and list of installed apps. Then I can easily reinstall if need be.

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by hugh4 on 2014-10-25
Thanks for the replies. I'll try the clonezilla live download.
Hugh

---

