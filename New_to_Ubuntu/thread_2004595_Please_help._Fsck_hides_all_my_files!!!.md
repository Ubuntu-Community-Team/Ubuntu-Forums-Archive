---
title: "Please help. Fsck hides all my files!!!"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by cinlung on 2012-06-16
Dear All ubuntu Guys,

I have a huge problem that really needs your helps. I have one server under ubuntu 10.4 LTS Server 64Bit worked great for few months.

Yesterday, I decided to run fsck via Putty and it just blew the MBR off. My server started to boot only to grub> prompt.

I read few searches that grub reinstall would fix it. So, this is what I did:
1. I load ubuntu 10.4 LTS Desktop 64 Bit and run fsck /dev/sda2. A bunch of stuff said to be fixed and I kept pressing y button to continue.
2. After that I did grun-install command and reinstall the grub.
3. After that I reboot the computer and the partition was recognized and I was able to mount the missing partition. But, all I got was just boot and lost&found directories.
4. I tried to search the lost&found for my MySQL dump files (i named it with db<yyyy><mm><dd><hh><mm><ss>.sql, but none was found. All I find in lost&found directory are some old files I deleted.

Tried to use testdisk, got confused on how to use it. Still trying scalpel, and understanding how it works.

Is there any user friendly way to rescue my file? I just need to rescue one MySQL dump file. The location of my dump file is in /Files/Backup/DB

I tried to check total space used in the drive and it is said that my drive was used about 12GB. Then I check the lost&found directory and it is 5GB. Then I tried to restore an old image of the same drive to another HDD using Clonezilla. After restoring, I check the restored drive size is 7GB.

So, there are 7GB hidden in the problem disk. Is there a ways to recover that missing 7GB?

Please help. I am totally exhausted searching for this. I am a newbie and starting to learn Linux. I wonder if there is a simple tool like in Windows to do file search.

All helps are appreciated.

Thank You
Rendra

---

### Post by black veils on 2012-06-16
ther only file search app i know of is **Catfish**.


i dont know anything about servers, but surely it would be possible to boot a ubuntu live cd/usb normal desktop GUI environment, using the **Try** option, *not*  install, open the file manager, and locate your files, to then copy-paste to another usb flash drive?

---

### Post by cinlung on 2012-06-16
> **black veils said:**
> ther only file search app i know of is **Catfish**.


i dont know anything about servers, but surely it would be possible to boot a ubuntu live cd/usb normal desktop GUI environment, using the **Try** option, *not*  install, open the file manager, and locate your files, to then copy-paste to another usb flash drive?

Nope, Doing live CD did not work. In fact the live cd thinks that the server partition is ext2, not ext4 and thus this was how my files got hidden. When I ran FSCK from live CD, the live CD recognize the SDA2 (boot) as ext3 and tried to change it to ext2.

On catfish, I checked it and it seems to be a regular file search. I need some application that can read original file structure that has been messed by the fsck.

---

### Post by Zill on 2012-06-16
> **cinlung said:**
> ...I just need to rescue one MySQL dump file. The location of my dump file is in /Files/Backup/DB...
Unfortunately, I can't help you with fixing your damaged file system.

However, your problem has highlighted the importance of keeping regular backups of important data files.  Your reference to "/Files/Backup/DB" apparently indicates that you recognise this.  Regrettably, keeping backups on the *same* hard-drive as the original data does not give much additional security as HDDs can and do fail.  As you have discovered, HDD filesystems can also be corrupted and, if your sole backup is on the same HDD, it is very difficult to recover the data.

So, when you do manage to restore your system I respectfully suggest that you regularly save data backups to an external location - such as a different HDD, a different system, optical media or "the cloud".

HTH.

---

### Post by CharlesA on 2012-06-16
Did you run the fsck with the file system mounted? It should have given you a warning if it was.

In any case, it is likely the drive is hosed since only lost&found and boot exist, so you'd have to do a reinstall.

Backups are a good idea. ;)

EDIT: Check [here]("https://help.ubuntu.com/community/DataRecovery") if you want to try to recover your data, but there are no guarantees if it has been overwritten.

---

### Post by cinlung on 2012-06-16
> **Zill said:**
> Unfortunately, I can't help you with fixing your damaged file system.

However, your problem has highlighted the importance of keeping regular backups of important data files.  Your reference to "/Files/Backup/DB" apparently indicates that you recognise this.  Regrettably, keeping backups on the *same* hard-drive as the original data does not give much additional security as HDDs can and do fail.  As you have discovered, HDD filesystems can also be corrupted and, if your sole backup is on the same HDD, it is very difficult to recover the data.

So, when you do manage to restore your system I respectfully suggest that you regularly save data backups to an external location - such as a different HDD, a different system, optical media or "the cloud".
 
HTH.
True that. My inner voice told me to atleast copy the last backup of mysql dump file. But my curiosity beats it. Although running fsck on system file gave me warning, i thought maybe it will run a scheduled fsck next time. 

Oh well.... I guess it is back to ground zero. Thanks guys. :KS

One more thing, if i partition the harddrive to two or add second harddrive, i would still have to mont the harddrive to a folder inside root directory. If in the middle of the process, the fsck somehow killed the system partition again, can i stil use the live cd to read the second partition or the second hdd?
For example:
Sda1 - swap
Sda2 - system file
Sda3 - data files
Sdb1 - backup

If the sda1 and 2 somehow went bad, can  still read sda3 and sdb1 with live cd?

---

### Post by Zill on 2012-06-17
> **cinlung said:**
> ...One more thing, if i partition the harddrive to two or add second harddrive, i would still have to mont the harddrive to a folder inside root directory. If in the middle of the process, the fsck somehow killed the system partition again, can i stil use the live cd to read the second partition or the second hdd?
For example:
Sda1 - swap
Sda2 - system file
Sda3 - data files
Sdb1 - backup

If the sda1 and 2 somehow went bad, can  still read sda3 and sdb1 with live cd?
I am certainly *not* an expert in the complexities of filesystems but my understanding is that fsck should *not* be run on a mounted system.  [fsck]("http://manpages.ubuntu.com/manpages/lucid/man8/fsck.8.html") has the option of specifying a device or a mount point to check.  However, if no option is specified then the default is to check all the filesystems in /etc/fstab serially.

So, by ensuring that you only run fsck on each (specified) unmounted filesystem as required, this should not affect any other filesystem.  IMHO, the best way to ensure this is to run the check only from the Live CD, making sure the HDD filesystem remains totally unmounted.

Taking your example then, with a bad check on sda1 or sda2, this should mean that data on sda3 or sdb1 should still be readable after mounting to the Live CD.

Of course, if the bad check on sda1 or sda2 is due to a "hard" fault within the HDD itself then this may well mean that data on sda3 is also corrupted or unavailable, even though this is on a different partition.  However, even in this case, data on sdb1 should remain readable by the Live CD as this data is on a totally separate drive.

---

### Post by Cheesehead on 2012-06-17
> **cinlung said:**
> if i partition the harddrive to two or add second harddrive, i would still have to mont the harddrive to a folder inside root directory. If in the middle of the process, the fsck somehow killed the system partition again, can i stil use the live cd to read the second partition or the second hdd?
For example:
Sda1 - swap
Sda2 - system file
Sda3 - data files
Sdb1 - backup

If the sda1 and 2 somehow went bad, can  still read sda3 and sdb1 with live cd?

Yes, the LiveCD can mount sdb. I think in terms of whole drives (sda, sdb) for backup. If a drive dies, all partitions on it are lost.

fsck 'somehow' killing a filesystem only happens when the user overrides the 'WARNING!!! SEVERE FILESYSTEM DAMAGE' at the beginning of the process. So just don't run it again on mounted partitions, and you can avoid that use case.

fsck will automatically check the root filesystem every 30 boots (before the root filesystem is mounted). If you want to change the frequency, or reboot and check it immediately, easy instructions are at [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

