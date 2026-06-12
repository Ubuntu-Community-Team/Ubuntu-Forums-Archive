---
title: "Links to ntfs drive don't work after boot until I access drive  through file manager"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by mayoman on 2012-10-19
I am a long time windows user but Linux novice - however have turned my  old Xp family PC into a dual boot xububtu12.04/xp machine. As we still  need to boot into Xp (to use MS office) fairly regularly I have imported  Outlook data into Thunderbird on the Xp side & set it to operate  off the same profile in Xubuntu. This is where my problem cropped up.
Thunderbird  cannot find the the ntfs profile data after booting in Xubuntu, However  after I access the ntfs disk through file manager, Thunderbird works  fine. After spending considerable time tweaking & researching  Thunderbird setup I realized that this affects any link to a file or  folder on the ntfs partition (e.g. a shortcut to my old my documents  folder).  
I note that in Xubuntu file manager the ntfs drive has a  little eject button like it is a removable drive, I don't know if that's  normal or if its due to my setup. Either way I'm looking for the best  way to resolve the problem (without restarting from scratch!)
The  machine is an old (10yr+) Dell dimension 4400 & Xp & Xubuntu are  on two separate internal IDE hard drives. Oh, and (just to complicate  matters) the Xubuntu install is in Japanese.

---

### Post by Bashing-om on 2012-10-19
mayoman; Hi ! Welcome to the forum.

Off the top of my head, I would say your ntfs partition is not mounted in /etc/fstab. As usage and access is personal on ntfs, let me point you to some tutorials:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

HOWTO: Mount NTFS partitions with specific ownership/permissions
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[INDENT]hth ->any further questions -> ask <==BDQ

[/INDENT]

---

### Post by LewisTM on 2012-10-19
Yep, at the moment the NTFS drive gets mounted only when you try to access it for the first time in the file manager. Before that, it's just nowhere in the file tree so symlinks will not work.

You can use fstab to mount it at boot. More simply, you can trigger the automatic mounting at login just as if you had clicked the drive. First find the device corresponding to your NTFS partition.
```
sudo fdisk -l
```
The drive will begin with /dev/sd# and will be of type NTFS/HPFS.

Next add this command to your startup applications:
```
gvfs-mount -d /dev/<yourdrive>
```
That's it! 
One warning: this command will mount the drive in /media. If you upgrade to 12.10, it will be put in /media/<user> instead so you will have to recreate your symlinks.

Cheers!

---

### Post by audiomick on 2012-10-19
Sounds like the ntfs partition isn't automatically mounting at boot. Have you noticed if the little eject symbol is there imediately after boot up? The symbol, by the way, is quite normal, but I believe it indicates something that is not mounted at boot. If it is not there at boot, then this is surely the case.

Anyway, have a look at this

[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")
Note that when you see this command, you will most likely need to subsitute the xubuntu editor for gedit, and probably just "sudo" for "gksudo"
```
gksudo gedit /etc/fstab

```

I got that article from a link on this one, which is what my search in the ubuntu document turned up (and what I was looking for).

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

hope that helps.

---

### Post by Bashing-om on 2012-10-19
@ LewisTM; 
That is one of the reasons I am so avid for this forum - Learn something alla the time. 

[INDENT]still learning even after all these years ==> BDQ

[/INDENT]

---

### Post by mayoman on 2012-10-20
Thank you, it was a partition mount issue ok.
Put following command into startup applications & links all now working first time.
gvfs-mount -d /dev/sda1

---

