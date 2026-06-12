---
title: "GRUB, Vista and installation"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by PetruM on 2008-07-07
Hi :D

I bought an ASUS F5SL laptop two weeks ago and it currently runs Windows Vista Home Premium. I want to set up Kubuntu on it and I have a few questions:

1) will GRUB interfere in any way with the Vista boot loader? I know it's going to replace it, but will Vista boot without any problems? I still need vista for some applications. :)
2) I don't have any CD or DVD to burn the Kubuntu image to, but I have a 2GB USB flash drive. How could I use that to install Kubuntu? As far as I know, the notebook can boot from an USB device?
3) the notebook has an ATI Radeon HD3470 graphics card with 256MB dedicated memory. I'm interested in running Compiz, is it possible?

Any help is appreciated. ;)

---

### Post by rockerphil on 2008-07-07
first off GRUB shouldn't conflict with Vista booting up, all it really does is list the installed OSes. secondly you should have no troubles installing from a USB drive as long as the system supports booting from a USB device, but if not you can always order the free Kubuntu Live CD, and i don't see why you couldn't run Compiz on that card as long as it's supported, not too sure about the card being supported though. hope this info helps,


Phil

---

### Post by DezSP on 2008-07-07
Compiz and ATi cards don't tend to play nicely with each other, so I'm afraid you'll likely have to tinker to get them working together. You can boot from a USB stick, but you'll need to Google around for something to "burn" an ISO to a USB stick -- it'll wipe anything else on there, of course.

---

### Post by muteXe on 2008-07-07
Installed unbuntu to dual-boot with vista a few weeks back.  I didn't encounter a problem with vista not working.
I suspected that after intalling SP1 on vista that this might bugger up GRUB, but it worked as normal even after this :)

---

### Post by billgoldberg on 2008-07-07
> **DezSP said:**
> Compiz and ATi cards don't tend to play nicely with each other, so I'm afraid you'll likely have to tinker to get them working together. You can boot from a USB stick, but you'll need to Google around for something to "burn" an ISO to a USB stick -- it'll wipe anything else on there, of course.

ATI card on linux have come a long way.

I have no problem running my ati radeon card.

---

### Post by DezSP on 2008-07-07
Running it and running Compiz on it are different things. Your mileage may vary of course, and it is improving.

---

### Post by ET! on 2008-07-07
the grub menu will override the vistas boot.ini....so when the system starts it is not the boot.ini which is loading it is the grub...

---

### Post by PetruM on 2008-07-09
Thanks for the help ;)
Whatever happens, I know how to fix the Vista boot loader.
So I set up Kubuntu (finally got a CD to burn it to) with both video and wireless working (some Atheros chip that gave me a headache). However, the sound is still not working.

```
petru@mars:~$ sudo lspci | grep Audio
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
```

I also heard that it's SiS966 or something.

Any ideas? :-s

---

### Post by jamesrfla on 2008-07-09
If you want the GRUB boot loader install vista first then install Ubuntu. If you want the vista boot loader install Ubuntu then Vista. Not sure if it will work but just a guess.

---

### Post by PetruM on 2008-07-09
I doubt the Vista boot loader will do anything about Ubuntu :)
Anyway, booting is no longer a problem, sound is. :D

---

### Post by youthforlinux on 2008-07-09
I thought that it didn't use boot.ini to manage oses anymore?

---

### Post by redsun82 on 2008-09-03
> **PetruM said:**
> Any ideas? :-s
I also had problems with my brand new laptop some time ago. You could try to install the latest alsa drivers directly from source

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

though there is compiling to be done... but the version is more recent than the one in the repositories, so it could help. Maybe one has also to tinker (as I had to) with /etc/modprobe.d/alsa-base, but that is greatly dependant on the card (and I just don't know enough to help in that case). I'd try just the new version of alsa for now and see if that does the job.

---

