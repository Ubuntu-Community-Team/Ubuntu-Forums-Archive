---
title: "[SOLVED]windows lost during Ubuntu installation"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by anees2 on 2014-05-10
I was using windows 8 and Ubuntu 12.04(dual boot). I wanted to replace Ubuntu 12.04 with 14.04. During installation, I chose the option 'replace Ubuntu 12.04' and lvm installation. My old Ubuntu 12.04 was not lvm

Then some error messages came. So I quit installation. Then I rebooted the system again to see all data were gone. I also live booted Ubuntu 14.04 live CD and checked. The whole hard risk has turned into an lvm partition.

I lost my whole data. Anyone please suggest solution to recover my data.

---

### Post by oldfred on 2014-05-10
The LVM install always has been a full drive erase and install as LVM. The new installer's description does not make that totally clear. You may install manually using Something Else.

Not sure if you can recover anything or not. That is why we suggest really good backups for any major partition change or install.

First try testdisk. But with LVM it often cannot search inside that to find the old partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And then photorec has similar issues:

 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Not even sure if you can use LVM tools to remove LVM and then maybe testdisk will work. But LVM can not be edited with standard partition tools only LVM tools.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

 LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by nivek2 on 2014-05-10
I had the same problema few days ago installing the new LTS.
I also got an error during install, and when I rebooted you guessed it, I also got a black desktop.
Weird thing is, I was not using LVM, as I never had.
It might not be an issue with LVM (although I am kind of a newb ;)

---

### Post by anees2 on 2014-05-12
> **oldfred said:**
> The LVM install always has been a full drive erase and install as LVM. The new installer's description does not make that totally clear. You may install manually using Something Else.

Not sure if you can recover anything or not. That is why we suggest really good backups for any major partition change or install.

First try testdisk. But with LVM it often cannot search inside that to find the old partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And then photorec has similar issues:

 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Not even sure if you can use LVM tools to remove LVM and then maybe testdisk will work. But LVM can not be edited with standard partition tools only LVM tools.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

 LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

Thanks a million. Testdisk is working. I just checked it now. Almost all drives are listed. I copy small files and it is working. Now I need to connnect an external hard disk and copy all files to it. Athough some files are damaged and non-recoverable, allmost all files are there and hope it can be copied successfully. I will let you know once the backup procedure is completed.

---

