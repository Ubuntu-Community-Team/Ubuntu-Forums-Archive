---
title: "External Hard Drive - Cannot Mount Drive"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by zilinskas.andrew on 2008-08-09
I recently switched from Vista to Ubuntu.  Obviously I wanted to back up my files, so I saved them on an external hard drive.  Now I am unable to open the drive.  Some one please help.  Oh yeah - I am SO new at Linux and Ubuntu, so please treat me like a complete moron!  Thanks - I appreciate the help

---

### Post by NewDisciple on 2008-08-09
See this post: [http://ubuntuforums.org/showthread.php?t=874729&highlight=%2Fdev%2Fsdb+won%27t+show]("http://ubuntuforums.org/showthread.php?t=874729&highlight=%2Fdev%2Fsdb+won%27t+show")

---

### Post by bpowell2005 on 2008-08-09
> **zilinskas.andrew said:**
> I recently switched from Vista to Ubuntu.  Obviously I wanted to back up my files, so I saved them on an external hard drive.  Now I am unable to open the drive.  Some one please help.  Oh yeah - I am SO new at Linux and Ubuntu, so please treat me like a complete moron!  Thanks - I appreciate the help


What do you mean "Unable to open the drive"? Does Ubuntu give you an error (like "drive not properly shut down...must use "force"") or some other kind of error...or is the drive simply not appearing on your desktop? If you go to "Places" and "Home" can you see the drive in the left column?

---

### Post by st33med on 2008-08-09
```
cd /media
sudo mkdir ./ex_hdd
sudo mount -t fat32 /dev/usb/<tab> /media/ex_hdd
```

This is assuming that your external HDD is formatted as fat32 and is attached to your usb. Make any changes you need.

---

### Post by zilinskas.andrew on 2008-08-10
I appreciate all of the help.  Here is a little more info:

When I try to access my usb external hard drive, I receive the message "Cannot Mount Drive"  and here are the details
"$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked for to be in use. Choose one action; Choice 1; If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type the command line: mount  -t ntfs-33g/dev/sdb1/media/disk -o force   Or add the option to the relevant row in the /etc/fstab file:   /dev/sdb1/media/disk ntfs-3g force 0 0"


I did try this:

"andrew@andrew-laptop:~$ cd /media
andrew@andrew-laptop:/media$ sudo mkdir ./ex_hdd
[sudo] password for andrew: 
andrew@andrew-laptop:/media$ sudo mount -t fat32 /dev/usb/hiddev0 /media/ex_hdd
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?
andrew@andrew-laptop:/media$ 
andrew@andrew-laptop:/media$ 
andrew@andrew-laptop:/media$



I should also make note that I definitely do not want to loose any information on the hard drive.

Thanks again for all the help

---

