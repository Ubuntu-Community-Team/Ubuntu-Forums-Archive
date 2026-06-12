---
title: "CAnt get my laptop to boot from cd."
date: 2008-08-17
forum: New to Ubuntu
---

### Post by zamadatix on 2008-08-17
i just inherited a 3rd generation laptop.it has xp on it but i, obviously, want to put ubuntu on it. the problem is the cd drive doesnt work (acer aspire 3000). so i cant boot it from a cd. is there any other way i can install ubuntu, like usb or something.

---

### Post by nicedude on 2008-08-17
Here is a link to how to do it form USB stick

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Or I would say if you know anyone that has a portable USB CD drive that might work as well.

Goodluck, and I hope you get it up and going :-)

---

### Post by Doommaster1994 on 2008-08-17
I tried it on my laptop too. It did the same thing. Is your laptop brand new? Mine is very old and its a Toshiba. And if it uses Intel Inside then it will not work.

---

### Post by jualin on 2008-08-17
Also check out [this link]("https://help.ubuntu.com/community/Installation") or install Ubuntu using the [Wubi installer]("http://wubi-installer.org/")

---

### Post by zamadatix on 2008-08-17
in my post i stated 3rd generation laptop so not new lol. i also said acer 3000. also i use puppy linux and could test a few others on it. so i googled around on ways to "burn" an iso to a usb in a cdfs format and some said they had it working but it was read only (fine with what im using) but i could never figure out how thy got it to cdfs.

thanks for hte link nicedude

---

### Post by Transcend on 2008-08-17
just trying to troubleshoot why you wouldnt be able to boot. did you set the bios to boot from the cd?

---

### Post by jualin on 2008-08-18
> **zamadatix said:**
> i just inherited a 3rd generation laptop.it has xp on it but i, obviously, want to put ubuntu on it. the problem is the cd drive doesnt work (acer aspire 3000). so i cant boot it from a cd. is there any other way i can install ubuntu, like usb or something.

The CD drive is not working.

---

### Post by Helios1276 on 2008-08-18
What about using Poweriso or something similar to mount the cd image on a virtual drive  and then install via Wubi?

---

### Post by jualin on 2008-08-18
> **Helios1276 said:**
> What about using Poweriso or something similar to mount the cd image on a virtual drive  and then install via Wubi?

If you go to [the Wubi website]("http://wubi-installer.org/") and download Wubi I think it automatically download the image to your hard drive and then it boots from it, so mounting the image manually is not necessary.

---

### Post by nicedude on 2008-08-18
This is kinda an older laptop so I would recommend not using Wubi if at all possible. Do you have any friends who might have a portable USB CD-ROM drive? You would only have to use it once to install. I haven't done a USB install so I don't know %100 but I think this is definitely possible assuming your laptop has a boot from USB stick option in the BIOS. It would be in the boot device selection menu. Maybe someone else here has done this before and can give more specific help.

---

