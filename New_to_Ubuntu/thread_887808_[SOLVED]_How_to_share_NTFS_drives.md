---
title: "[SOLVED] How to share NTFS drives?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by wonderbiscut on 2008-08-12
HI, I have searched the forum and web but have been unable to find the answer to my question.

How can I share both my NTFS drives.  I want to give full access to 3 users who are using windows.

I am a total noob at Ubuntu, but even after just a short while it has become my main OS, windows kept for playing games.

Here his a copy on my drive layout (fdisk -l)

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x236d236d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x359a04ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS


I need step by step instructions as it has taken the best part of a day to figure out how to have my orther hard drives automount on startup (I said I was a noob :P)

Thanks.

---

### Post by bumanie on 2008-08-12
In terminal > sudo apt-get install ntfs-3gthis gives read/write capability to ntfs, then > sudo apt-get install ntfs-configGo to Applications --> System Tools --> ntfsconfig and set up you drives via the config box. The drives will be automatically added to /etc/fstab and should automount at boot.

---

### Post by ajgreeny on 2008-08-12
It should either be possible by using ntfs-3g which is installed by default in Hardy but also needs ntfs-config to use it easily, I think, and puts a menu item in somewhere to configure your ntfs drives, or you could simply add this line

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

to your /etc/fstab file as root by using ```
gksudo gedit /etc/fstab
```

---

### Post by Cypher on 2008-08-12
I presume you want to share your NTFS drivers on a network? Use the suggestions above me to get those partitions mounted in your Linux environment. You'll then want to setup SAMBA to share the directories on the network and the Windows users can access it..

---

### Post by wonderbiscut on 2008-08-12
Thanks for the help.

But I still can't share them. I receive this message every time I try;

'net usershare' returned error 255: net usershare add: cannot share path /media/sdc1 as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

I don't know how to do what it is asking  "add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this"

I'm sure it is something to do with not being root, but other than that I'm lost

---

### Post by wonderbiscut on 2008-08-12
And yes it is to share the two drive over a local network.

---

### Post by HemiGTX on 2008-08-12
in terminal:

sudo gedit /etc/samba/smb.conf

you will see [global] in the file

at the end of the global section add

usershare owner only = False

save and exit, 

in terminal:
/etc/init.d/samba restart

---

### Post by Cypher on 2008-08-12
Nm

---

### Post by wonderbiscut on 2008-08-12
Thats it!

All sorted.  Thank you all for your help and assistance.

You have made a stressed man very happy. :D

---

