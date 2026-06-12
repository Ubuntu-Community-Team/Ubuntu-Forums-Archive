---
title: "Manual Gnome 2.14"
date: 2006-03-12
forum: Programming Talk
---

### Post by SpEcIeS on 2006-03-12
Since I am interested in using the latest greatest Gnome, but not wanting to use the dapper, I am manually compiling the it. Yes, I have time to burn right now. ;) 

So far everything is working out really well, and the speed differences are noticable since I am compiling for my processor, athlon.

One issue I am coming across is gnome-vfs. It does not seem to want to recognize HAL during the configuring process. Does anyone have any insight on this? If more info is required I would be happy to supply it.

---

### Post by Klejs on 2006-03-12
I've had that problem with Dapper too, when Gnome loaded it couldnt start HAL...:(

---

### Post by SpEcIeS on 2006-03-12
Well I have not got so far as to compile gnome-vfs, but the configuration seems to indicate that HAL, even if the devs and bins are installed, does not find it. Perhaps there is a version difference, however it is not indicated in the README or INSTALL files that come with the tarball.

According to the HAL site if a higher version of HAL is used then the kernel needs to be 2.6.13 or higher. I was hoping to not implement a newer kernel, but I have compiled, installed, an alternative kernel, 2.6.15.6. 

Playing around with HAL will require a lot of extra work, so I was hoping to keep my kernel and current HAL that comes with Breezy. There must be a way. :confused:

---

