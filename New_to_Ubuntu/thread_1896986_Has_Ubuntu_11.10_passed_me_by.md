---
title: "Has Ubuntu 11.10 passed me by?"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by carusoswi on 2011-12-18
I have run the same Shuttle XPC machine since purchasing it in 2004.  I've added storage and memory (2gb RAM), but, other than that, the machine is as it was way back then.

I have also run every version of Ubuntu since version 6.xx.

I would say that the 10.xx series is really the last version that could run flawlessly on my computer.  Versions later than that exhibit very choppy video, and, unless I run Classic Gnome, performance in general is degraded.  Boot up times are extended, program load times and web pages the same.

As long as I do not try to watch streaming video, the web experience is tolerable, but forget video.  It is unwatchable due to the choppiness of the video.

Other than the fact that my system is dual boot, I think the installation is rather mundanely routine.

Please advise.  For now, most of my work, by necessity, will be done in WinXP.

Advice happily/humbly received.

Thanks.

Caruso PS: I have tried Classic Gnome with and without effects to no avail.

---

### Post by mastablasta on 2011-12-18
Ubuntu gained a bit of weight (i.e. by default it uses hardware acceleration to redner menues) and the problem might also be unsupported graphics card or a bug. try to run Ubuntu with 2D unity.

Additionally you could try Xubuntu to see if it works better. it is lighter on resources and also doesn't have the special effects...

Lubuntu is even lighter on resoruces however i have a feelign oyu migth already do preety well with Xubuntu.

it will be hard to give any more help since you didn't post your system specificaitons (aside from RAM). 
while the choppines in performance is not dependant (only) on amount of ram but on CPU and graphics card.

---

### Post by coffeecat on 2011-12-18
If your graphics also dates from 2004, that could be the problem. Or rather the driver. Is it a separate graphics card or onboard video? Post the terminal output of:

```
lspci | grep VGA
```

---

