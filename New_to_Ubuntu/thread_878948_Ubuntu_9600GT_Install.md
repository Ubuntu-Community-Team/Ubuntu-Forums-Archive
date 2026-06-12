---
title: "Ubuntu 9600GT Install?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by chris062689 on 2008-08-03
I'm trying to install the drivers from Nvidia's site for my 9600GT, I got it working before, using this: [http://www.adamspotton.com/node/1](http://www.adamspotton.com/node/1)
But the site is down.
I am using Ubuntu 8.04.1 (64bit)

Can anyone give me a guide?

---

### Post by CatKiller on 2008-08-03
If you go to System -> Administration -> Hardware Drivers, you should be able to install the drivers by putting a tick in a box.

---

### Post by ConMan318 on 2008-08-03
> **CatKiller said:**
> If you go to System -> Administration -> Hardware Drivers, you should be able to install the drivers by putting a tick in a box.

Nope, not for this card (I have one of the same series, they are too new for Ubuntu).  Don't bother with the drivers from Nvidia's site.  I also tried from Nvidia's site first, but it's quite a big hassle to get them working properly.  Go into Synaptic, search 'envy'.  Install "envyng-gtk", which should also install 'envyng-core'.  Or just do 'sudo apt-get install envyng-gtk'.

Go to Applications > System Tools > EnvyNG.  Select NVIDIA from the 2-selection box on the left.  Tick the 'Install the Nvidia driver (Manual selection of the driver)' button (the auto-detect won't work, but you can try it if you don't believe me :p).  The default driver at the bottom should be the correct one, the 173.14.09  one.

Then just hit apply.  I used this about a week ago on my new build with an Nvidia 9800GT and it works perfectly.

---

### Post by Ru$$i@N on 2008-08-04
bull **** :D it's really easy to install 9600 GT driver from NVidia! I have this card. The thing is, you have to reinstall the driver (at least my way) every time you have kernel update, because the program from Nvidia recompiles the kernel.
So here's how i do it...

first, download the driver
```
http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```
this is the latest one at the moment.

save this file in your home directory for simplisity.

switch to console mode
```
Control + Alt + F1
```

kill X-es, i assume you run GNOME
```
sudo killall gdm
```

in your home directory, or wherever you have the .run file saved type
```
sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```
where NVIDIA-Linux-x86_64-173.14.12-pkg2.run is the name of the file, if you find a newer one, just change the name

Then just follow the instructions. The program will probably tell you that there are no kernels found that are already precompiled, that's fine, tell it to recompile the kernel that you have. Enable OpenGL 32 if you're playing any games that require OpenGL, and all :)

---

### Post by chris062689 on 2008-08-04
EnvyNG worked great!  Thank you!

---

### Post by allensaucier on 2009-04-27
Thx for the posts guys.  I'm just now installing a 9600GT on ubuntu 9.0.4 and can't get the device drivers working @ all from nvidia - 173, 177, 180 or 185b.

I'll try envy!!:P

---

