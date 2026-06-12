---
title: "hp scanner 4400c doesn't work"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by allp on 2008-05-08
Unfortunately I seem to have one of the few scanners which do not work properly with Ubuntu. I've been searching the forums and found nothing. However, in Google I have found the following instructions:

[http://packages.ubuntu.com/feisty/libs/libsane-extras](http://packages.ubuntu.com/feisty/libs/libsane-extras)

where apparently the library libsane-extras (1.0.18.5) has a backend with hp_rts88xx which may be useful for my scanner.

I've downloaded that library from:

[http://packages.ubuntu.com/feisty/i386/libsane-extras/download](http://packages.ubuntu.com/feisty/i386/libsane-extras/download)

and it seems to have been installed correctly. In fact a new update for libsane-extras has been downloaded and installed as well. Now, when I start Xsane two different devices appear:

- Noname Z-star Vimicro z  dispositivo virtual [v4l:/dev/video0]

- Hewlett-Pac Scanjet 4400C escáner flatbed [hp_rts88xx:libusb:002:003]

but although I select the last one, the following error still appears:

Falló al abrir el dispositivo hp_rts88xx:libusb:002:003 Error durante E/S de dispositivo  (Unable to open device hp_rts88xx:libusb:002:003 Error while device I/O)

Please help me, since my scanner is the only thing which keeps me tied to Windows.

---

### Post by allp on 2008-05-10
Please, help me make scanjet 4400c work with Ubuntu. Otherwise I have to go back to Windows to be able to use it!

---

### Post by Malta paul on 2008-05-10
Hi, The reason you scanner will not work very well with Linux is that HP don't make a driver for Linux. You can use Xsane with Ubuntu but the quality may not be as good as the HP driver made for MS Windows.

I would use your scanner with Windows then reboot to Ubuntu to save or process your files.

Hope this helps :)

---

### Post by allp on 2008-05-10
Thanks but the problem is it does not work at all. This is the mesage I get:
[COLOR="Red"]Unable to open device hp_rts88xx:libusb:002:003 Error while device I/O[/COLOR]

---

### Post by Malta paul on 2008-05-11
Hi, Do you mean that your scanner fails to work also in Windows?

Here is a link to the latest MS HP drivers for your scanner:
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=61902&lang=en&#](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=61902&lang=en&#)

Hope this helps :)

---

### Post by ramjet_1953 on 2008-05-11
This link may be useful:

[http://reapoff.sourceforge.net/hpscanner/Default.htm](http://reapoff.sourceforge.net/hpscanner/Default.htm)

Regards,
Roger :cool:

---

### Post by rburkartjo on 2008-05-11
allp, try this is worked great on my hp deskjet f4140 all-in-one. go to applications/add-remove/make sure the show all avail applications is selected on the left hand top. in search box type in xsane. check box and hit apply changes in lower right hand corner. it will be installed under applications/graphics.right click on icon and select add launcher to desktop.it should work with no problem. /cheesemaker

---

### Post by allp on 2008-05-11
It does work properly with Windows but it doesn't with Ubuntu

---

### Post by rburkartjo on 2008-05-11
allp, just to check did you do this. open xsame it should scan for devices. if it recongizes a device there should be an option to check that device. then you have to use xsane not your hp scanner to do a scan. let me know cause it worked for me no problem/cheesemaker

---

### Post by Ingenium on 2008-05-26
I am having the same issue. It used to work perfectly out of the box in 7.10, but I get the I/O error in Hardy.

---

### Post by mathnuked on 2008-05-28
I know this does not help but I have the exact same problem. So a solution would be great.

allp, let me ask a question is your connect with a USB?

---

### Post by redcountess on 2009-08-07
I'm having this problem with a HP 4400c, same error message, in Jaunty with xsane and libsane extras installed, does anyone know of anything else I can try?

---

### Post by majdi on 2009-11-10
Running Ubuntu 8.04.3, I have a HP Photosmart C4483 all in one. It prints OK but I cant scan, Xsane will not detect it. Its connected via USB.

I have libsane-extras installed but cant get it to work. 

Any ideas?

---

