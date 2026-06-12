---
title: "I can't boot Windows after installing Gparted on hardisk"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by tlerdrden on 2013-04-06
Hello,
I am new at Ubuntu. Today I've had a problem and, after looking posts, I haven't found any solution. 
I've installed Gparted in my Windows7 in my hardisk, where Windows7 is located. Now, when I try to boot Windows, the only thing appears on my screen is:
"SYSLINUX 4.06 EDD 4.6-pre 7 Copyright (C) 1994-2012 H.Peter Anvin et al".
I don't know how to fix the problem...Any suggestions?
I don't want to format the system...
Thanks,
A.

---

### Post by tlerdrden on 2013-04-06
For additional info, I don't have any partition...:(

---

### Post by oldfred on 2013-04-06
Most of the USB type installers highlight that you overwrite the entire USB drive when installing. It sound like you installed with a flash drive installer, but to your internal drive? IF so you erased the entire drive.

You may be able to recover some or most of data, but since some system files were overwritten, you cannot restore to a boot able system. Stop using anything on hard drive as you may be further overwriting your data.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


 As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Bresser on 2013-04-06
If you installed on your HDD, that is not good. This means the HardDrive could have been formatted or overwritten. You can try to recover some files, but it is unlikely for you to get everything back. I'm sorry. Let me know how it goes

Thanks,
Bresser.

---

### Post by Bresser on 2013-04-06
Also if you find that you are not capable to recover windows 7 (I also managed to delete windows 7 from my computer). If your files are still there as mine were you can boot Ubuntu from Live CD and put them on an external HDD. 

Put a enter after each line:
```

sudo -s
mkdir /mnt/Windows
mount -t /dev/sda2 /mnt/Windows -o "umask=022"

```
All your windows content should be in your mnt folder inside your user on the LiveCD. Just Copy Paste to your external HDD.

---

### Post by Mark Phelps on 2013-04-06
Most likely, your files will NOT be there if you overwrote Win7 with Linux. The more you use it, the more files you will destroy.

If you really want to get your Win7 data files back, you will need to be able to remove the overwritten drive, connect it to a working Win7 PC, and be prepared to spend some money ... read on

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

