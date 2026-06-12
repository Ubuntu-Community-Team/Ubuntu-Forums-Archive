---
title: "SDDM not starting on Raspi 4B"
date: 2020-10-07
forum: New to Ubuntu
---

### Post by themmcmanus on 2020-10-07
I have searched all over and see plenty of people have the same problem but can't find a solution.

I have a Raspberry Pi 4B 4GB that I installed Ubuntu Server 20.04 on and would like to install the lubuntu-Desktop (gdm3 / ubuntu-desktop loads fine but is waaay heavy).  Everything installs fine but the graphical interface won't start after boot, you can switch to tty2 and startx to get the desktop rolling but it won't automatically start, everything I see seems to point to SDDM not working right on Raspi 4, has anyone run into this and found a solution?  Thanks for any insight in advance.

---

### Post by guiverc on 2020-10-07
`sddm` having issues on raspberry pi 4 is a known issue I believe (Kubuntu use it too).  I've heard mention, and discussion of it many times, but as I don't have a pi 4, I've not taken much notice.

I believe the solution is to just use another `dm`, but I can't advise on the best one.  (*I don't have a pi 4 to play or test with*)

I'm aware of many discussions on the topic, however whilst I remember two that were I thought useful, I've found neither one. I'll provide a link to [https://github.com/wimpysworld/desktopify/issues/19](https://github.com/wimpysworld/desktopify/issues/19)

---

### Post by themmcmanus on 2020-10-08
Thank you for the link, it really looks like I just have to wait until a dev works it out, no big deal.  I switched it to boot to multiuser instead of graphical and I just log in and use startx, works fine.  Having to load up gdm3 just to get a graphical lockscreen kind of defeats the purpose of loading lubuntu in the first place.

---

### Post by ActionParsnip on 2020-10-08
Could add a command in /etc/rc.local to run startx as your user (hacky but should work)

---

