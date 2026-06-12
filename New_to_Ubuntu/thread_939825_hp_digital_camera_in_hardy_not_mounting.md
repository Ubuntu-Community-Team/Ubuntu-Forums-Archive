---
title: "hp digital camera in hardy not mounting"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by lapubell on 2008-10-06
I just got a free digital camera from work and after a little tinkering I can't get it to mount in ubuntu.  Wondering if HP has any special software for this camera?  After a quick google all I got was product reviews and a virus scan (that told me my windows install had 22 infected .dll files.  *sigh)

anyway,

ubuntu 8.04, fully upgraded
output of lsusb

lapubell@lapubell-desktop:~$ lsusb
Bus 002 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:7702 Hewlett-Packard PhotoSmart R817 (PTP mode)
Bus 001 Device 001: ID 0000:0000


EDIT -->
I opened the menu on the camera and switched the mode from camera to disk drive.  This took it out of PTP mode and it mounted correctly in linux.

---

### Post by phidia on 2008-10-06
There is a [reported bug]("https://lists.ubuntu.com/archives/ubuntu-mono/2008-March/011185.html") in hardy about PTP mode but it may not be related.

---

### Post by ianhaycox on 2008-10-06
gphoto2 says it supports your camera, so try installing gphoto2 and see if you see files on the camera. Once installed via Synaptic plug in the camera and try,

$ gphoto2 --list-files --recurse

If you can see your photos then we are half-way there.

---

### Post by timcredible on 2008-10-06
i see you changed the usb mode on your camera, that works 99.9% of the time.

also, try digikam as your photo manager/editor program.  it's in synaptic.  also install kipi-plugins to get 30+ plugins for digikam.

---

