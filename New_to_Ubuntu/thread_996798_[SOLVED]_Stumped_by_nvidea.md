---
title: "[SOLVED] Stumped by nvidea"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-29
Hi, can anyone help me?

Have installed a new graphics card, but Nvidea settings doesnt seem to give me the option to set monitor res correctly?

---

### Post by MasterSander on 2008-11-29
Try installing restricted drivers, envy is for nvidia I believe.

---

### Post by nnjond on 2008-11-29
Thanks for your interest. I believe i have installed restricted drivers.

---

### Post by overdrank on 2008-11-29
> **nnjond said:**
> Thanks for your interest. I believe i have installed restricted drivers.


Ok could you give some more info. What version of ubuntu, graphics card model, what do you mean nvidia settings does not offer the screen resolution you are trying to achieve?

---

### Post by nnjond on 2008-11-29
My os is Ibex. I used to run my pc with an onboard grapics thingy  1600x1200 @ 75hz.
today I installed a GeForce FX 5500 and i was prompted to dl the restricted drivers wich i think idid. NVidia X server settings has appeared in my menu but the option to change the monitor settings isn't functioning. Now my present sit is 640x480@ 60hz

I've tried Apps> Other> scrn @ graphics which promts me for my pw but then dissapears with no consequences? Thanks for your interest.

---

### Post by overdrank on 2008-11-29
> **nnjond said:**
> My os is Ibex. I used to run my pc with an onboard grapics thingy  1600x1200 @ 75hz.
today I installed a GeForce FX 5500 and i was prompted to dl the restricted drivers wich i think idid. NVidia X server settings has appeared in my menu but the option to change the monitor settings isn't functioning. Now my present sit is 640x480@ 60hz

I've tried Apps> Other> scrn @ graphics which promts me for my pw but then dissapears with no consequences? Thanks for your interest.

You may try and use the command ```
gksu nvidia-settings
```
Also try and reboot into recovery mode and use the xfix option.

---

### Post by w4ett on 2008-11-29
I have a 5500 card in one of my machines and I had a similar experience.  This particular card IDs to use the Nvidia-glx-new driver, but I found the card runs better with the legacy driver which I installed manually...you can use the helper program[COLOR="Blue"] Envyng[/COLOR] available via the Synaptic Package Manager..use this to remove your old driver and manually install the new one...I recommend using the 96.43.09 driver.

Also, be aware that there is currently a bug report for the 71 and 96 (legacy) divers [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107)
Nvidia has released a new  driver which is compatible with the new kernel 2.6.27 in Intrepid and hopefully these older cards will play a little nicer in 8.10 and 9.04.

---

### Post by thadacto on 2008-11-29
Having upgraded from 7.10 to 8.04, I have spent the last 30 hours trying to get my screen res over 640x480. (Ge Force 6100)
The upgrade didn't recognise my monitor and had set the res to 640x480.
I have been mucking around with Ge Force drivers, install - uninstall - reinstall etc. none of which worked.
Try the Screen & Graphics program which for some reason does't appear in the Applications menu but I had to go 
Places/Computer/file system/usr/share/application/screen and graphics.

I now have 800x600 and God only knows what driver is being used!
But I'll put a new post about that soon.

---

