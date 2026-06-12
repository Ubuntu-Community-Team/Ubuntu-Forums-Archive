---
title: "[SOLVED] canon Ixus850is not autodetected in Heron"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Piddell on 2008-06-29
Just upgraded from 6.06 to Heron, and I must say it's very impressive.
I had a slight issue with the NVIDIA driver in that I had to stop it and restart it to get a good screen resolution, but that was it!

However.....  My Canon camera (IXUS 850IS) is not being auto detected any more (it was ok in 6.06)

If I run lsusb I can see it ok, along with the Maxtor external drive (which works much better in Heron)
Bus 002 Device 006: ID 04a9:3136 Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0d49:7310 Maxtor 
Bus 001 Device 001: ID 0000:0000  

Just tested it with my other camera:
Bus 002 Device 007: ID 04a9:30f0 Canon, Inc. PowerShot S2 IS (PTP mode)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0d49:7310 Maxtor 
Bus 001 Device 001: ID 0000:0000  

Slightly more detail, but still not running the picture transfer software.

PC is an old IBM P4 (6790 - 11G)

Oh - I love the new audio support.

Thanks

Phill

---

### Post by Piddell on 2008-06-30
If I run Fspot manually I can download the pictures from the camera

---

### Post by Piddell on 2008-07-06
Any thoughts?

---

### Post by Piddell on 2008-08-08
a complete ubuntu re-install has fixed this

---

### Post by philinux on 2008-08-08
When you transfer files to the pc does it preserve the shooting date or do you get the system date?

[https://bugs.launchpad.net/ubuntu/+bug/242644](https://bugs.launchpad.net/ubuntu/+bug/242644)
[https://bugs.launchpad.net/ubuntu/+bug/242647](https://bugs.launchpad.net/ubuntu/+bug/242647)

---

### Post by Piddell on 2008-08-10
It gives the file the date/time you imported it, which is annoying.  it does keep the date and time taken as this is stored in the jpeg  information.
Phill

---

