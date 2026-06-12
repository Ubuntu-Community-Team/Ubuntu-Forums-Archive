---
title: "[SOLVED] Xubuntu Hardy FAT Mounting/Sharing"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by DFlame on 2008-09-06
Hey all, hope you can offer some help.

I've installed & fully updated Xubuntu 8.04 on a low-mid spec computer. Currently, there are two hard disks. The first (sda) contains a Windows installation (1), Linux installation (2) and the swap partition (3). The second drive (sdb) has one FAT32 partition which I use to store all of my media, documents etc.

I can easily mount the Windows NTFS partition via command line with read/write abilities. The problem stems from sdb1, the FAT32 drive. I can mount it via command line but can not change the ownership of files and folders to myself, so write access is restricted. Attempting to sudo chown the files has also failed with "Operation not permitted".

Ideally, I would like both sda1 and sdb1 to be mounted on startup, both with read/write access. Another desirable but non-essential ability would be sharing these drives on the local network via samba/smb.

Thanks for your time,

Gareth

---

### Post by wolfen69 on 2008-09-06
to have the FAT drive automount you need to add it to fstab. ```
gksudo gedit /etc/fstab
```then add a line at the bottom such as: ```
/dev/sdb1   media/whatever_the _drive_is_called   vfat  defaults 0 0
``` check your /media directory first to see if sdb1 is in there. if not, ```
sudo mkdir /media/what_you_want_to_call_it
```OK, back to fstab. after you make that line, click at the end of it as if you were going to add to it. hit enter.(you need a new line that's empty) save. reboot to see if anything has changed.

---

### Post by DFlame on 2008-09-06
Cheers, will attempt this now.

Gareth

---

### Post by DFlame on 2008-09-06
Well we're off to a good start. The fstab edit has auto-mounted the drive. I'm assuming how to get rw access comes next? :)

Gareth

---

### Post by wolfen69 on 2008-09-06
```
sudo chown -R username:username /media/storage
```replace storage with name you have ```
sudo chmod -R 755 /media/storage
```

---

### Post by wolfen69 on 2008-09-06
for read/write: ```
chmod -R ug+w /media/storage
``` again, replace storage for your drives name.

---

### Post by DFlame on 2008-09-06
First chown command throws up Operation not permitted errors

The next chmod command appears to work without fault

The chmod command providing rw access gives repeated Operation not permitted

Gareth

---

### Post by wolfen69 on 2008-09-06
try ```
sudo chown -R username:username /dev/sdb1
``` then try the last chmod command i gave again. if this does not work, i'm stumped, as it works for me.

---

### Post by DFlame on 2008-09-06
"sudo chown -R username:username /dev/sdb1" appears to work correctly, but the chmod still spews out Operation not permitted.

I'll continue to look for a solution for now. Any other tips are welcome and thanks for trying :)

Gareth

---

### Post by DFlame on 2008-09-06
Some more investigation has solved the problem!

I added umask, UID and GID parameters to the fstab line as according to [this thread](http://www.fedoraforum.org/forum/archive/index.php/t-1229.html) on the Fedora forum. i used the given umask, my uid of 1000 and the gid of gmac (same as my username). Upon restart, sdb1 was mounted with full access rights.

Networking has also gone smoothly. Using the menu given in Applications > System > Shared Folders, I have been able to install the networking components needed to share folders. Following that, I added the mount point of sdb1 to the shared folders. On restarting, the share was successful.

I found a program called pyNeighborhood which greatly helped in browsing to my share via another computer, though I did have to manually add the computer with the shared files manually, by IP address.

Thanks again for the initial fstab tips, those paved the way and now everything is working as it should. Issue resolved,

Gareth

---

