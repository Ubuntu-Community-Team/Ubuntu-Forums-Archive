---
title: "[SOLVED] missing software sources/8.04 cd not recognised"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-15
i went into my software sources to add the 8.04 hardy cd,and got this error:
error scanning the cd,e:failedto mount the cd rom,but the dvd works fine.
as i was playing with this my sources disappeared(oops)universe,etc,
so can any one help with the dvd issue and how do i get my sources back?????
please help me!!:confused:
rick

---

### Post by PmDematagoda on 2008-07-15
To get the sources back you should be able to use Software Sources to get activate them again, did you try that?

About the CD issue, try doing:-
```
sudo mount /dev/scd0 /media/cdrom0 && sudo apt-cdrom add /media/cdrom0
```

---

### Post by rixtr66 on 2008-07-15
yes,but im missing multivers,universe,and abunch of others,the media im trying to mount is a hardy dvd not a cdrom,heres the output of the command you gave me:rick@rick-laptop:~$ sudo mount /dev/scd0 /media/cdrom0 && sudo apt-cdrom add /media/cdrom0
[sudo] password for rick: 
mount: block device /dev/scd0 is write-protected, mounting read-only
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.
rick@rick-laptop:~$ 
dont know what to make of that??
rick

---

