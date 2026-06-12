---
title: "Mount NTFS Partitions permanently"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by greendragons on 2011-11-13
It's really bugging me to every time click on NTFS partitions so tht they can be mounted....
I want to mount them permanently... i don't know how to edit fstab entry.....

---

### Post by Cyclane on 2011-11-13
Well if you want us to tell you what to put in fstab your gonna need to give us some information.

Would you please mount the NTFS partition as you normally do and after that go to the terminal and give it the command 'mount'. Please give me the output of that.

---

### Post by papibe on 2011-11-13
> **Cyclane said:**
> ...give us some information....

+1

Could you post the results of these two commands?
```
sudo fdisk -l

sudo blkid
```
Regards.

---

### Post by greendragons on 2011-11-13
```

kodedozer@KodeWagen:~$ sudo fdisk -l
[sudo] password for kodedozer: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x39515d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11132    89414772    7  HPFS/NTFS
/dev/sda2           11132       22250    89298945    f  W95 Ext'd (LBA)
/dev/sda3           22250       38914   133853180    7  HPFS/NTFS
/dev/sda5           11132       20177    72652800    7  HPFS/NTFS
/dev/sda6           20177       21858    13501440   83  Linux
/dev/sda7           21858       22250     3142656   82  Linux swap / Solaris


kodedozer@KodeWagen:~$ sudo blkid
/dev/sda1: UUID="C27EFA347EFA2139" TYPE="ntfs" 
/dev/sda3: LABEL="MULTIMEDIA" UUID="9C743BA4743B8056" TYPE="ntfs" 
/dev/sda5: LABEL="CRUCIAL_CLUTCHES" UUID="BE5A8D685A8D1E71" TYPE="ntfs" 
/dev/sda6: UUID="69add51d-c5e9-4168-922f-aff9dbfd3644" TYPE="ext4" 
/dev/sda7: UUID="11643475-99dd-4247-b806-b93d4095dd0d" TYPE="swap" 


```

---

### Post by Morbius1 on 2011-11-13
Use the following as a template:

[a] Run the following command to get the right UUID number for your partition:
```
sudo blkid -c /dev/null 
```[b] Unmount the partition from Nautilus if you currently have it mounted

[c] Create a permanent mount point:
```
sudo mkdir /media/DriveD 
```[d] Add the following line to /etc/fstab:
```
UUID=DA9056C19056A3B3 /media/DriveD ntfs    defaults,nls=utf8,umask=000,uid=1000,windows_names 0       0 
```[COLOR=Blue]*Substitute the UUID number you got from step [a] in the above line*[/COLOR]

[e] Run the following command which will test for errors and if there are none mount the partition without a reboot:
```
  sudo mount -a
```We can play with the different options ( umask, uid, ... ) to modify permissions and ownership if you would like. See the following for a further discussion: [http://ubuntuforums.org/showthread.php?t=1880238](http://ubuntuforums.org/showthread.php?t=1880238)

---

### Post by greendragons on 2011-11-13
> **Cyclane said:**
> Well if you want us to tell you what to put in fstab your gonna need to give us some information.

Would you please mount the NTFS partition as you normally do and after that go to the terminal and give it the command 'mount'. Please give me the output of that.

I know mount command to mount, but rather than mounting manually i want it is done automatically as i login..

---

### Post by Morbius1 on 2011-11-13
I really should read the intervening posts before I post.

The "mount" command would tell us what you have already mounted and how they are mounted. It's one piece of the puzzle. Some folks like to create fstab entries from that output. I do not.

---

### Post by beew on 2011-11-13
> **greendragons said:**
> I know mount command to mount, but rather than mounting manually i want it is done automatically as i login..

Just open a folder, go to the left panel and mount from File Systems. Since  even if a partition is pre mounted you would still need to open it with Nautilus to access its contents anyway this is not really an extra step. I don't think you need to do anything special with the command line or fstab.

---

### Post by Jacobonbuntu on 2011-11-13
Hi green one :)

you do need to add a line in your fstab file to make the partition automount
what you should do is:

[LIST]
[*]create a mount point (directory)
[*]open a terminal, type sudo gedit /etc/fstab
[*]add a line in your fstab file that looks like: dev/sda3 /your_mountpoint ntfs auto
[/LIST]
sda3 is the partition you want to automount I guess
this is how my entry looks:
dev/sda4 /media/intern_1 ntfs auto

---

### Post by greendragons on 2011-11-13
> **beew said:**
> Just open a folder, go to the left panel and mount from File Systems. Since  even if a partition is pre mounted you would still need to open it with Nautilus to access its contents anyway this is not really an extra step. I don't think you need to do anything special with the command line or fstab.

Auto mount is essential as i download and save data to that ntfs drive...so whenever i reboot and starts torrent it jes stuck as it does not get drive mounted...so everytime i need to make sure that i have my drives mounted after reboot...even if i don't need to  access them....

---

### Post by Jacobonbuntu on 2011-11-13
> **greendragons said:**
> Auto mount is essential as i download and save data to that ntfs drive...so whenever i reboot and starts torrent it jes stuck as it does not get drive mounted...so everytime i need to make sure that i have my drives mounted after reboot...even if i don't need to  access them....

I agree, I make automatic backups from my NAS to my (internal) ntfs partition. annoying if you have to mount manually..... :)

---

### Post by greendragons on 2011-11-13
```
UUID=DA9056C19056A3B3 /media/DriveD ntfs    defaults,nls=utf8,umask=000,uid=1000,windows_names 0       0 
```[I]

[/I][LEFT][I]What i need to write as windows_names values....label for drive?
and what is da difference it i write auto.....
[/I]** [/LEFT]

---

### Post by Jacobonbuntu on 2011-11-13
> **greendragons said:**
> ```
UUID=DA9056C19056A3B3 /media/DriveD ntfs    defaults,nls=utf8,umask=000,uid=1000,windows_names 0       0 
```[LEFT][I]What i need to write as windows_names values....label for drive?
and what is da difference it i write auto.....
[/I] [/LEFT]


just dev/sda3 is enough really (+the options ntfs and auto like my example)

---

### Post by Cyclane on 2011-11-13
TBH Morbius1 posted everything you need to do. (maybe you need to add the option auto)

---

### Post by Jacobonbuntu on 2011-11-13
> **Cyclane said:**
> TBH Morbius1 posted everything you need to do. (maybe you need to add the option auto)
possibly, but really unnecessarily complicated IMO :)

and NTFS does not support Linux rights/ownership

---

### Post by Morbius1 on 2011-11-13
> **greendragons said:**
> ```
UUID=DA9056C19056A3B3 /media/DriveD ntfs    defaults,nls=utf8,umask=000,uid=1000,windows_names 0       0 
```[LEFT][I]What i need to write as windows_names values....label for drive?
and what is da difference it i write auto.....
[/I] [/LEFT]

"windows-names" is the actual name of the option and should be added just like I posted. It prevents you from creating files with names that Windows cannot recognize.

The auto option is not necessary it's in the defaults.

---

### Post by greendragons on 2011-11-13
Thnx all :) :)

---

### Post by Morbius1 on 2011-11-13
> **Jacobonbuntu said:**
> Hi green one :)

you do need to add a line in your fstab file to make the partition automount
what you should do is:

[LIST]
[*]create a mount point (directory)
[*]open a terminal, type sudo gedit /etc/fstab
[*]add a line in your fstab file that looks like: dev/sda3 /your_mountpoint ntfs auto
[/LIST]
sda3 is the partition you want to automount I guess
this is how my entry looks:
dev/sda4 /media/intern_1 ntfs auto

* Never use sudo with a gui application use gksu instead or else you will eventually corrupt your system.

* Your line in fstab is incorrect since you left off the beginning "/" and you didn't end it with a "0 0" - although as far as the "0 0" - I'm a stickler for exact syntax.

> and NTFS does not support Linux rights/ownership Quite correct but the mounting of an NTFS partition in Linux is a "view" that permits one to mount with with ownership and permissions Linux will understand.

---

### Post by greendragons on 2011-11-13
All working fine after reboot..... :D

---

### Post by Jacobonbuntu on 2011-11-13
> **greendragons said:**
> All working fine after reboot..... :D

that's all that matters :)

to morbius; you are quite right about the /before dev (of course, I copied too quick)

---

