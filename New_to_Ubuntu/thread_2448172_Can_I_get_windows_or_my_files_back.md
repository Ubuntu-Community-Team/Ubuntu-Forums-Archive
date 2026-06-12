---
title: "Can I get windows or my files back?"
date: 2020-08-03
forum: New to Ubuntu
---

### Post by harvster on 2020-08-03
I installed Ubuntu 20.04 on a laptop that had Windows 10 on it.  During installation I chose LVM because I thought that would just create a partition with unused space and not overwrite everything. Is there anyway to get windows to boot again or recover any of my files from the HD?

Thank you

---

### Post by mrdc76 on 2020-08-03
That you chose the LVM option means that the installer encrypted the harddrive. This means that you can't recover the files.

---

### Post by pbear42 on 2020-08-03
LVM doesn't necessarily entail encryption, but selecting an installation option which says "Erase disk and install Ubuntu" necessarily entails erasing the disk.

So, harvster, you're looking at reinstalling Windows.  Data files you'll have to restore from backup.  If you don't have backups ... no comment.

---

### Post by ActionParsnip on 2020-08-03
Use your backups. Did you make backups before making such a drastic chnage to the system?

---

### Post by oldfred on 2020-08-03
A Linux install is relatively small and files are scattered over the entire partition.
I believe encryption is only encrypting the data, not the unallocated space.
You may then have some files that were not overwritten and can use tools that scan drive for anything that looks like a file.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

But those that use Windows have said Windows tools typically work better for NTFS partitions.
Some are not free, like photorec.

You can download Windows from Microsoft. And if you install in UEFI boot mode, your product key is in the UEFI. But Windows does not include all the drivers you may need, so you have to go out to your vendor's support page & download any extra drivers or support files you need.

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-exFAT-Progs-1.0.4](https://www.phoronix.com/scan.php?page=news_item&px=Linux-exFAT-Progs-1.0.4)
Windows free recovery software - new 2020 Supports NTFS, FAT, exFAT and ReFS file systems
[https://www.microsoft.com/en-us/p/windows-file-recovery/9n26s50ln705?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/windows-file-recovery/9n26s50ln705?activetab=pivot:overviewtab)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)


Older info, not sure if still better or not.
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by harvster on 2020-08-03
I did not choose to erase the disk or to encrypt the drive.  And no, I don't have backups but, there is nothing of great value on the disk so I wasn't too concerned.  I'm swapping out the old HD for an ssd so I thought I would just put it back to it's original windows configuration if possible.  Thank you for the suggestions and advice.

---

### Post by pbear42 on 2020-08-03
> **harvster said:**
> I did not choose to erase the disk ...
Sorry, but you did.  Before you reinstall Windows, run the Ubuntu installer again.  (Nothing to lose at this point.)  LVM is a sub-choice of Erase & Install.

Edit: Forgot to mention. LVM generally isn't recommended for newbies.  If you try Ubuntu again, use a conventional partition scheme.  Can be dual boot with Windows if you like.

---

### Post by uninvolved on 2020-08-03
**Note:** Never click 'yes', 'continue', 'submit', press the 'enter button' in a terminal window, etc. without knowing *exactly* how the computer is going to interpret the input. Always keep current backups, with a good backup strategy that includes off-site storage.

Following those two rules will make your computing experience much better. It may seem laborious and time-consuming, but it's a lot less effort and time consuming than recreating data, reinstalling operating systems, or the likes.

It's a little late for that now - but that doesn't mean you can't start doing this going forward.

---

