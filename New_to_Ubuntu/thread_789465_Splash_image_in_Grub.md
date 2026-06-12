---
title: "Splash image in Grub"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-05-10
Hi,

I'm just playing around with my Grub boot loader and trying to add a splash image.
I followed the Howto in the Ubuntu forum and have successfully added the image, however the menu box background (where I can select the OS) is black and appears on top of my splash image (obscuring most of it).
Is there any way to make the background of the Grub menu transparent so that I can see my splash image beneath it?

Cheers.

---

### Post by Biggy on 2008-05-10
Install Startup-Manager and manage grub settings

view Startup-Manager [Home]("http://web.telia.com/~u88005282/sum/index.html") for more info.

---

### Post by Jim_in_Germany on 2008-05-11
Hi,

Thanks for the tip.
I installed startup manager as suggested and managed to fix the problem (problem was that I had been trying to apply a splash image and different colours to the Grub bootloader at the same time).

Now I have a slightly different problem. I have managed to change the resolution of the Ubuntu image displayed once I select Ubuntu from the list of operating systems (the one with the Ubuntu logo and an orange progress bar).

I did this by changing the resolution in Startup manager to 1600 x 1200 and rebooting. After selecting Ubuntu from the list, it told me that the image resolution is not supported.

Using Startup Manager I managed to change it back to 1280x1024, which is ok, but I'd like the 1600 x 1200 back (which is what I had in the first place).

Does anyone know in which file Startup manager changes the resolution of the Ubuntu logo and progress bar?

Any help gratefully appreciated.

---

### Post by Jim_in_Germany on 2008-05-12
Alright,

Solved my own problem again.
I overlooked it the first time, but upon second inspection I noticed that Startupmagaer had added "vga=798" to the kernel's boot parameter.
I deleted that and now everything is back to how it was.

---

