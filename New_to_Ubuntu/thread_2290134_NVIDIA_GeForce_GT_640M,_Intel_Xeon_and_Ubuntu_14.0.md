---
title: "NVIDIA GeForce GT 640M, Intel Xeon and Ubuntu 14.04"
date: 2015-08-09
forum: New to Ubuntu
---

### Post by jgervais89 on 2015-08-09
[FONT=arial][COLOR=#000000]Hi there, [/COLOR]
[COLOR=#000000]
I have a Dell XPS 27 one, and I was thinking  installing Ubuntu (14.04LTS) on it. [/COLOR]


[COLOR=#000000]Of what I heard from other Linux users (you can see the thread, here: [http://ubuntuforums.org/showthread.php?t=2010298)]("http://ubuntuforums.org/showthread.php?t=2010298),this"), this computer should works well with Ubuntu, with one caveat, the NVIDIA graphic card; I think they are right. Indeed, I decided to try Ubuntu without installing it, using a USB, and I used the inxi-xG  command. The result was: 
[/COLOR]
[COLOR=#000000]Graphics:[/COLOR]
[COLOR=#000000]    Card-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controllerbus-ID: 00:02.0 [/COLOR]
[COLOR=#000000]    Card-2: **NVIDIAGK107M **[GeForce GT 640M] bus-ID: 01:00.0[/COLOR]
[COLOR=#000000]    DisplayServer: X.org 1.17.1 drivers: intel (unloaded: fbdev,vesa) **FAILED**: nouveau Resolution:  138x77 [/COLOR]

[COLOR=#000000]From there, I concluded that my NVIDIA graphic card won't work with Ubuntu, at least with the current configuration. So, I would have three questions: [/COLOR]

[COLOR=#000000]1-Theoretically[/COLOR][COLOR=#000000], is the N[/COLOR][COLOR=#000000]VIDIA [/COLOR][COLOR=#000000]GeForce GT 640M (GK107M) graphic card compatible with [/COLOR][COLOR=#000000]Ubuntu 14.04 LTS (in the thread shown above, one user seems to have been able to make it work with Ubuntu [/COLOR][COLOR=#000000]12.04. [/COLOR][COLOR=#000000]I can't try his/her codes with Ubuntu 14.04, however, because it requires rebooting)?[/COLOR]

[COLOR=#000000]2- If not (or if for some reasons I am not able to make it works), am I right by saying that my Intel Xeon graphic card should work properly?
[/COLOR]
[COLOR=#000000]3- I don't remember where (sadly), but in a blog related to the question of the installation of NVIDIA with Ubuntu, the administrator consistently suggested to those with dual cards to use the Intel integrated card rather than the Nvidia card, for different reasons. Is it a fair advice? I mean, would I lose a lot if I'm not able to make my Nvidia card working? Is the Intel Xeon good enough? [/COLOR]

[COLOR=#000000]Thank you in advance![/COLOR][/FONT]

---

### Post by NathanRodriguez on 2015-08-09
[FONT=arial][COLOR=#000000]GeForce GT 640M is listed as compatible with the Nvidia Linux driver, should work fine.

[http://www.nvidia.com/object/linux-display-ia32-295.59-driver](http://www.nvidia.com/object/linux-display-ia32-295.59-driver)
[/COLOR][/FONT]

---

### Post by Yellow Pasque on 2015-08-10
> From there, I concluded that my NVIDIA graphic card won't work with Ubuntu,
The output of inxi is confusing. When it says failed, it is referring to the generic vesa and fbdev drivers (which don't load by design when there are better drivers available).
As for the LiveUSB, it is using the open-source nouveau driver, which should work (detailed info: [http://nouveau.freedesktop.org/wiki/Optimus/](http://nouveau.freedesktop.org/wiki/Optimus/) )
A lot of folks opt for the proprietary nvidia driver, but ideally, it shouldn't be necessary unless you're a gamer or need maximum 3D power.

---

### Post by jgervais89 on 2015-08-10
Thank you for these answers!

---

