---
title: "Integrated Graphics + Screen Signal Resolution Problem"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Erinn on 2008-09-12
Hi

I've just built this pc and am using an ASrock ALiveNF7G-FullHD motherboard. I'm running Ubuntu 8.04 and everything's working great, except for the graphics. The resolution is 800x600, and it's huge, and there's no desktop effects. When I go System>Admin>Hardware Drivers, the driver's there, but once I enable it and restart, I get to the splash screen and login and the screen goes black with a 'Signal Out of Range' message. I have to restart and ```
sudo dpkg-reconfigure xserver-xorg
```to go back to the old settings, and the graphics no longer work, again. I've been at this for hours now and can't fix it, any help'd be greatly appreciated.

Thanks,
Erin

---

### Post by skippuff54 on 2008-09-12
maybe adjust ur refresh rate? are u usin monitor? crt, lcd?

---

### Post by Erinn on 2008-09-12
I'm using an LCD monitor.

I can't change the refresh rate, it's set at 61 Hz and I can't change it from that. 

??

---

### Post by skippuff54 on 2008-09-12
why can't u change it? will ur driver not let u change it? i had to change mine to output to the tv, i just went to system> preferences > screen resolution and changed it there.

---

### Post by skippuff54 on 2008-09-12
u might also try tweaking the settings of ur xorg.conf file

---

### Post by Erinn on 2008-09-12
I just can't, I go to System>Admin>Screen Resolution and there's no option to change it to.

---

### Post by Erinn on 2008-09-12
xorg.conf file? Where is this? I can't find it..

---

### Post by Erinn on 2008-09-12
Ahh, okay. It's all good, I fixed it myself. I had to change the monitor, or what Ubuntu had decided the monitor was, then changed the resolution, and then change the resolution in System>Admin>Screen Res. After restarting, I enabled the graphics driver in Hardware Drivers and restarted and for some reason it worked.

What I think happened.. this time when I enabled the driver it added drivers from Synaptic, previously I had disabled them all when it wouldn't work, and maybe it was two different drivers conflicting?

I don't know, but for some reason it worked this time.

*is happy*

Thanks for your help though.

---

### Post by skippuff54 on 2008-09-12
yeah almost def. a driver issue. sometimes when u first install ubuntu/linux it takes some tweaking to get ur hardware settings just right but 9/10 the correct drivers are in the repositories. then u just have to restart a couple-few times to make sure everything is enabled/disabled appropriately.

glad u got everything worked out

---

