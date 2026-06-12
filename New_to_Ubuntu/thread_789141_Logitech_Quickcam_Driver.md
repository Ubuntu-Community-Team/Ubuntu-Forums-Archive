---
title: "Logitech Quickcam Driver"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-10
Hi guys,

Can anone tell me how to install my logitech webcam? Again, im very new to linux so instruction must be grandpa noobie :)

---

### Post by barbedsaber on 2008-05-10
You may not need to install anything, (then again, you might)

plug it in, and open up cheese, (alt+f2 cheese)

can you see yourself?

---

### Post by appoloin on 2008-05-10
tried that.. and no i cant see my self.

---

### Post by barbedsaber on 2008-05-10
ok, so you are seeing static?

if so, I don't have a clue, sorry mate.

---

### Post by appoloin on 2008-05-10
Yeah im seing static

---

### Post by aswinms on 2008-05-10
> **appoloin said:**
> Yeah im seing static

Did you check if your webcam is supported ? if not check it []("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras").
Also, try removing and installing "Cheese", in fact try this before anything else.. Cheese supports almost any cam without any issue.Do you use the packae manager to install packages or do you use the command line? Not that it would make much of a difference but it is a good practice to use the command line as the dependencies are also taken care of(at least it tells you if you need an extra package).

---

### Post by appoloin on 2008-05-10
Just update on this. I was trying my skype and on test i see my self on about an inch of the top screen but the rest its static. Can anyone helpme?

---

### Post by barbedsaber on 2008-05-10
what the other guy is saying is, click applications, accessories, terminal.

don't be scared

type ```
sudo apt-remove cheese
```

then enter your password

then ```
sudo apt-get cheese
```

---

### Post by SunnyRabbiera on 2008-05-10
well I know that this model has had some success working in linux, but how to get it working is beyond me...
but be patient and dont give up, just some words of encouragement.

---

### Post by aswinms on 2008-05-10
> **appoloin said:**
> Just update on this. I was trying my skype and on test i see my self on about an inch of the top screen but the rest its static. Can anyone helpme?

Does your webcam figure [here]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")?

---

### Post by TeoBigusGeekus on 2008-05-10
Check this out as well
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by appoloin on 2008-05-10
YES!! :)  Logitech
	

QuickCam Pro5000
	

uvcvideo
	

Yes
	

Requires updated uvcvideo driver, easy to get from [WWW] [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)). uvc makefile: Change INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo.
	

v7.04 (Feisty)
	

USB ID 046d:08ce
	

now how do i install it?

---

### Post by SunnyRabbiera on 2008-05-10
they link a guide:
[here]("http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC")

I never done it myself so I cannot provide you with support.

---

### Post by vaibshah on 2008-06-18
Hi!
I get this error, during the driver installation, after I get everything into the directory qc-usb-0.6.6

$ make all
awk: cannot open /lib/modules/2.6.15-magma/build/include/linux/version.h (No such file or directory)
/bin/sh: line 0: [: -ge: unary operator expected
/bin/sh: line 0: [: -ge: unary operator expected
cc -I/lib/modules/2.6.15-magma/build/include -nostdinc -iwithprefix include -DMODULE -D__KERNEL__ -DNOKERNEL -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -Wall -Wstrict-prototypes -Wno-trigraphs -DHAVE_UTSRELEASE_H= -pipe -c qc-driver.c
make: cc: Command not found
make: *** [qc-driver.o] Error 127

Thanks!


> **appoloin said:**
> YES!! :)  Logitech
	

QuickCam Pro5000
	

uvcvideo
	

Yes
	

Requires updated uvcvideo driver, easy to get from [WWW] [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)). uvc makefile: Change INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo.
	

v7.04 (Feisty)
	

USB ID 046d:08ce
	

now how do i install it?

---

### Post by vaibshah on 2008-06-18
Hi!

I cannot get cheese by "sudo apt-get cheese"

How do I install cheese on my Ubuntu 6.06?

Thanks!


> **aswinms said:**
> Did you check if your webcam is supported ? if not check it []("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras").
Also, try removing and installing "Cheese", in fact try this before anything else.. Cheese supports almost any cam without any issue.Do you use the packae manager to install packages or do you use the command line? Not that it would make much of a difference but it is a good practice to use the command line as the dependencies are also taken care of(at least it tells you if you need an extra package).

---

### Post by vaibshah on 2008-06-18
Hi!
Could you install Skype 2.0

I am getting an error of libasound2 while installing the .deb package i downloaded from skype.


Thanks ahead!

> **appoloin said:**
> YES!! :)  Logitech
	

QuickCam Pro5000
	

uvcvideo
	

Yes
	

Requires updated uvcvideo driver, easy to get from [WWW] [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)). uvc makefile: Change INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo.
	

v7.04 (Feisty)
	

USB ID 046d:08ce
	

now how do i install it?

---

### Post by pneaveill on 2009-03-05
Read above there and discovered this link [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech) and found this:  Anyone know of any plans on getting this one fixed?[INDENT] Logitech QuickCam Express quickcam 046d:0870 No None available yet [/INDENT]      Or why this happened?[INDENT]       Used to work in Breezy 4 years ago...       2009-Mar-01 [/INDENT]

---

