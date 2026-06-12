---
title: "Dual boot, lost my hdd from windows"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by mark192 on 2015-01-31
Attempting my first ubuntu/linux install and wasn't given the option of installing alongside win 7 , so I chose (stupidly) the something else option and followd a post I read instructions to use ext 4 and | options .after that a warning popup notified me that I not chosen a location for swap files , In my eagerness to have a look at ubuntu , I continued on without selecting one for it as I didn't have any other partitions on the drive only the three 465GB win 7 ,15GB unallocated (ubuntu intended location) and the small however many meg system file partition. after several hours of the install it finally completely froze , stupid as I am , I knew this was bad , I immediately attempted to boot into win 7 to see if it would still work and it didn't , attempted startup repair using install disc and it stated it couldn't repair it. I tried chkdsk from cmd prmpt at boot but it could not see the drive , I plugged in my Win 8 drive alongside and loaded disc management and I could see it ,but it was 0 bytes and had no drive letter . 
I rebooted into the ubuntu disc and I can see it again, can anyone help me undo my stupidity and get me back my windows install and guide me through installing ubuntu alongside?.

---

### Post by mikewhatever on 2015-01-31
What exactly do you mean by "I rebooted into the ubuntu disc and I can see it again"? What do you see? If you can't describe it in words, post a screenshot.

---

### Post by mark192 on 2015-01-31
I mean that with the ubuntu iso I burned to a disc , I loaded the ubuntu install disc at boot  and instead of choosing to install I chose the option to Look around ubuntu or whatever it is.  I then went to look for the missing drive ,that I cant locate in windows ,which contains my win 7 os , and it is listed alongside all the other drives I have plugged in , plain as day . I opened it up and the folder structure of win 7 looks intact , but the partition where I attempted to install ubuntu is empty.

---

### Post by mark192 on 2015-01-31
From windows looking at the drive , I get the impression that its gone and I have to attempt some kind of format to even get the drive back let alone any data , but from ubuntu it looks fine.

---

### Post by ajgreeny on 2015-01-31
From the ubuntu DVD (or USB) live ubuntu system please post back here the output of the terminal command ```
sudo parted -l
```
This will show all the partitions on your hard disk and give us a start to figure out what has gone wrong.

I assume you removed the DVD or USB when rebooting the computer, otherwise the system will just boot again to the same live system that you used for installing rather than to the new installed Ubuntu OS.

For now until we know what has happened, you should avoid booting to any OS on the hard disk, if it were possible, and use just the live system as you could do more harm if you start using the hard disk itself.

---

### Post by mark192 on 2015-01-31
thanks for the advice , i will follow that and boot to the live cd , ill get back with the disk partition info

---

### Post by mark192 on 2015-01-31
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD6400AAKS-7 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  65.8MB  65.8MB  primary  fat16        diag
 2      65.8MB  16.2GB  16.1GB  primary  ext4
 3      16.2GB  640GB   624GB   primary  ntfs         boot
 4      640GB   640GB   1401kB  primary


Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model: Seagate Expansion Desk (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      8389kB  2000GB  2000GB  primary               boot


Model: SanDisk Cruzer Edge (scsi)
Disk /dev/sdd: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32


Model: HTC Android Phone (scsi)
Disk /dev/sde: 1978MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1978MB  1977MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$

---

### Post by mark192 on 2015-01-31
sorry I have no idea how to post the terminal text in the box as you all do.also I saved a screenshot in windows 8 of the disk management sysem tool,  showing my win 7 drive as invalid and with no drive letter however I can't see it in the folder I saved it in , it was a .png , I have no idea if its because I am using the live cd or something or If I have to install something but its not showing up. And I got mixed up about the drive size in my initial post it is 640GB not 500GB , got my win 7 and win 8 drives mixed up.

---

### Post by mark192 on 2015-01-31
I found that screenshot of windows disk management tool

---

### Post by oldfred on 2015-01-31
It looks like you have used all 4 primary partitions on sda. 
But since you have several drives, it often is better to have Windows exclusively on one drive and Ubuntu only on another drive. With each system having its boot loader/MBR on the same drive. Many disconnect other drives to be sure system is only installed to the one drive. 

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by mark192 on 2015-02-01
Thankyou Oldfred ,Aj... and Mike.. for your replies,
oldfred your post put me on the right track and after sifting through one of the links I realised I had destroyed the partition structure and software was the only way I'd 
get anywhere , I tried one partition recovery software. but it was it little too good , came up with 150 odd partition records, couldn't figure out what to do with them , I then gave diskgenius/partition guru a try and after doing a partition search three partitions showed up , I then saved the partitions which gave me back my drive letter, two actually , and neither was the one with windows on it. close enough. 
I tried to run chkdsk in win 8 on the drive but no luck so I rebooted with the win 7 live cd and tried to do a startup repair,  previously there was no record of windows or the disk but this time prior to starting the repair it did recognise that there was a win 7 install on the disk, so as the repair passed the previous fail point off 2 seconds and notifying it could not repair windowsi, I thought  I was in luck , ten min later it failed , same message ,startup repair cannot repair ... do you want to send...
I thougt stuff it , and attempted a restart and it booted straight into windows.All my files seem intact. I'll finish sorting this out and have a another crack , but I'll actually follow advice and make a recovery disc this time. thanks

---

### Post by oldfred on 2015-02-01
Glad you got it working. :)

---

