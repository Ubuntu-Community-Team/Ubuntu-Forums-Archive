---
title: "Connecting to phone"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by andrew110 on 2014-05-13
Thanx been reading the manual and downloaded synaptc.My other problem is im trying to connect my phone via usb.I found a tutorial and tried using the terminal,this is what i got.
andrew@andrew-FQ569AA-ABA-a6755y:~$ sudo apt-get install mtpfs
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mtpfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
andrew@andrew-FQ569AA-ABA-a6755y:~$ sudo mkdir /media/MTPdevice
andrew@andrew-FQ569AA-ABA-a6755y:~$ sudo chmod 775 /media/MTPdevice
andrew@andrew-FQ569AA-ABA-a6755y:~$ sudo mtpfs -o allow_other /media/MTPdevice
Unable to open ~/.mtpz-data for reading, MTPZ disabled.Listing raw device(s)
   No raw devices found.
In lost lol.

---

### Post by mörgæs on 2014-05-13
Moved to a thread of its own.
Please mark the other thread 'solved'.

---

