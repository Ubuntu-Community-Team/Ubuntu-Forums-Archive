---
title: "How can I change the screen resolution?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by lonners on 2008-08-24
I've just installed Ubuntu to my laptop after getting a virus using Windows XP. The screen resolution options offer a maximum of 800x600 when I have previously been using 1280x800 on XP. How can I increase the resolution on Ubuntu? I have already searched around the web for solutions but I'm not too great with Linux.

---

### Post by zamadatix on 2008-08-24
are you sure you have the right driver? is the drive enabled (do you see a icon that looks like a chip in your taskbar)?

---

### Post by tuxxy on 2008-08-24
Firstly did you install the video drivers for your card at system > admin > hardware drivers ?

Next you could try and edit the res at system > prefs > screen resolution , what video card are you using? if its nvidia you could try and also edit it using the nvidia-settings package

---

### Post by nickgaydos on 2008-08-24
If you have an ATI or NvIDIA card, you can install drivers using EnvyNG
> Sudo apt-get install envyng-gtk

---

### Post by lonners on 2008-08-24
Thank you zamadatix... and also tuxxy.

It said the driver was not in use, I checked the box, rebooted and now I'm able to use the 1280x800 resolution.

This forum is really great. I've solved the problem in just a couple of minutes. :)

---

### Post by zamadatix on 2008-08-24
thats what its for glad to help :)

---

