---
title: "USB video grabber &quot;softwear&quot;"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2013-01-14
I have a usb video grabber but no linux softwear to run it. Does anyone know of some suitable software to run on 12.04?

Thanks.

---

### Post by squakie on 2013-01-14
First, with the adapter plugged in, do the following:

lsusb

and copy/paste the output back here.

There are a couple of ways to try this - ffmpeg, VLC, etc., but it depends on the information the above provides.

---

### Post by dougcumiskey123 on 2013-01-14
The device is.......

Bus 002 Device 003: ID 1d19:6109 Dexatek Technology Ltd. 

I have VLC and would be happy to use it but in my ignorance I can find no way to capture from the USB port and I found this....  

[http://www.linuxtv.org/wiki/index.php?title=SilverCrest_USB_2.0_Video_Grabber_VG_2000&oldid=31274](http://www.linuxtv.org/wiki/index.php?title=SilverCrest_USB_2.0_Video_Grabber_VG_2000&oldid=31274)  which says that the new chip set (as of late 2012) is not supported by linux.



lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 002 Device 003: ID 1d19:6109 Dexatek Technology Ltd. 
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 006 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse

Thanks.

---

### Post by squakie on 2013-01-14
I would hook everything up, start playing a tape, then open vlc and selecting an input device of /dev/video0 and see if it shows anything.  I have a completely different device from Roxio, but if I select /dev/video0 the picture is there.  May also need to change the audio device to get sound.  If you can get it to play through VLC, then you can also capture it with VLC.

Let us know if that works or not.  I've seen several posts on this usb manufacturer id and product id - one of which did say it's not support at this time.  There are others that appear to be in German, or at least a language I don't know (I'm native U.S., and I have a hard enough time just doing English ;) ).  It's also possible, depending on the kernel version you are running, that we might be able to find something else.

---

### Post by dougcumiskey123 on 2013-01-14
So far: the only device that VLC can see is the USB camera, with the camera removed it finds nothing.

---

### Post by squakie on 2013-01-14
I'll look around some more later tonight.

---

