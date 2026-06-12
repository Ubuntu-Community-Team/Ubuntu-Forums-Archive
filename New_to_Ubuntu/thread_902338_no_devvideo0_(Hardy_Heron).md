---
title: "no dev/video0 (Hardy Heron)"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Jengajam2 on 2008-08-27
note: I have looked at other similar topics, but none seem to help.

I am trying to run my webcam using gspca and spcaviewer, but whenever i try to run spcaviewer, i always get this message: 
```
 Spcaview version: 1.1.7 date: 06:11:2006 (C) mxhaard@magic.fr 
video /dev/video0 
ERROR opening V4L interface
```
I've used the module assistant to get/update the spca5xx and gspca modules, but with no luck.
Help would be aprecciated.

---

### Post by Zwalther on 2008-08-27
Could you give a little more information?

Can you type the following in a terminal: 
  ```
grep gspca /var/log/messages
```
When I do this one of the lines I see on my pc is:
  ```
Aug 23 07:23:33 gpc kernel: [   58.567547] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX)
```

Does /dev/video0 exist and do you have the correct permissions?
  ```
ls -l /dev/video0
```

---

### Post by Jengajam2 on 2008-08-27
> **Zwalther said:**
> Could you give a little more information?

Can you type the following in a terminal: 
  ```
grep gspca /var/log/messages
```
When I do this one of the lines I see on my pc is:
  ```
Aug 23 07:23:33 gpc kernel: [   58.567547] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX)
```

Does /dev/video0 exist and do you have the correct permissions?
  ```
ls -l /dev/video0
```
when i did grep gspca /var/log/messages i got this ```
Aug 25 20:21:45 jengajam2-desktop kernel: [ 8417.884378] usbcore: registered new interface driver gspca
Aug 25 20:21:45 jengajam2-desktop kernel: [ 8417.884385] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Aug 25 20:57:54 jengajam2-desktop kernel: [10584.254828] usbcore: deregistering interface driver gspca
Aug 25 20:57:54 jengajam2-desktop kernel: [10584.254866] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: driver gspca deregistered
Aug 25 20:58:11 jengajam2-desktop kernel: [10600.976052] usbcore: registered new interface driver gspca
Aug 25 20:58:11 jengajam2-desktop kernel: [10600.976057] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Aug 25 21:03:09 jengajam2-desktop kernel: [10898.899718] usbcore: deregistering interface driver gspca
Aug 25 21:03:09 jengajam2-desktop kernel: [10898.899755] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: driver gspca deregistered
Aug 25 21:03:18 jengajam2-desktop kernel: [10908.223664] usbcore: registered new interface driver gspca
Aug 25 21:03:18 jengajam2-desktop kernel: [10908.223672] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered

```
and i also used ls -l /dev/video0, did a search, and found a file called video0, but still no luck.

---

### Post by Zwalther on 2008-08-27
I get those messages in /var/log/messages too, but I also get the "USB GSPCA camera found.(ZC3XX)"
It looks like the driver didn't recognize your camera. 
What is the exact type of webcam you have and are you sure it is supported by gspca?

---

### Post by Jengajam2 on 2008-08-27
> **Zwalther said:**
> I get those messages in /var/log/messages too, but I also get the "USB GSPCA camera found.(ZC3XX)"
It looks like the driver didn't recognize your camera. 
What is the exact type of webcam you have and are you sure it is supported by gspca?

oh, now that you think of it it may not be: [http://www.qbik.ch/usb/devices/showdev.php?id=3347](http://www.qbik.ch/usb/devices/showdev.php?id=3347)
(I got the windows driver, if that helps any)

---

### Post by Zwalther on 2008-08-28
I don't think there is a way to use the Windows driver. Unfortunately I can only think of two things to do: complain to the manufacturer that he is not supporting linux and/or buy a different webcam.

---

