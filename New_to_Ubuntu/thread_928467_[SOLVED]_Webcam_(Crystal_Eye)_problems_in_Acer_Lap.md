---
title: "[SOLVED] Webcam (Crystal Eye) problems in Acer Laptop"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-09-24
Hi, I am not able to get my web cam (Acer CrystalEye) to work in Ubuntu 8.04 LTS. 

Running luvcview gives me the output:

```

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 22.
 Init v4L2 failed !! exit fatal 
```

Camorama says:

```
Could not connect to video device (/sda/video0). Please check connection
```

So I run dmesg to get:

```
dmesg | grep Crystal

[   33.588358] **uvcvideo**: Found **UVC** 1.00 device Acer CrystalEye webcam (064e:a101)
```

And lsusb gives me:

```
**Bus 005 Device 003: ID 064e:a101 Suyin Corp. **
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
```

I found out that Linux UVC ([http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")) drivers are for my webcam.

Should I install this driver? Or is it something else perhaps, that's keeping the webcam from working?

Thanks.****

---

### Post by Korijn on 2008-09-24
I have the same webcam (& laptop?) as you do. Mine is on an Acer Aspire 5930G. It doesn't work for me either, but that's probably because the hardware is all so new. Most recent hardware isn't fully supported yet. I couldn't get the Intel 5100 WiFi Link to work either. I have been told to wait till the linux kernels are released in Octobre. So I'm trying to remain patient. :)

---

### Post by Eto_Demerzel on 2008-09-24
My laptop is older (Aspire 4710), so I'm sure there's a way to get the web cam working.

I did install the Linux-UVC driver, but it still didn't help. :(

Any ideas, please?

---

### Post by Eto_Demerzel on 2008-09-26
Funny, I finally got it working, at least in luvcview.

```
luvcview -f yuv
```

So, I know my webcam is working. But its still not working in camorama etc. I'll mess around with the settings to see if I can get it to work.

---

### Post by Eto_Demerzel on 2008-10-08
I'm posting this because I finally solved the problem. Phew! I got it to work perfectly.

[http://ubuntuforums.org/showthread.php?t=941332](http://ubuntuforums.org/showthread.php?t=941332)

---

