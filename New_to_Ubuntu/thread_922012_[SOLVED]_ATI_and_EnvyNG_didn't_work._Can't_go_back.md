---
title: "[SOLVED] ATI and EnvyNG didn't work. Can't go back to original settings."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by ejv on 2008-09-16
Hello

I was trying to repair some video problems, like intermitent images instead of fluid videos on some online movies.  I installed EnvyNG and then the ATI Drivers but it all got worse, with sudden shutdowns or closing of windows (although the video was apparently a bit better).  I then tryed uninstalling the ATI and NVIDIA Drivers from EnvyNG, but they just reinstalled themselves. Now everything on the monitor moves slower than ever.

I'v also got two new icons on my **Applications**
 
ATI Catalyst Control Center
ATI Catalyst Control Center (super user)

What I really want now is to uninstall all this stuff.

Thanks for any help

ejv

---

### Post by tuxxy on 2008-09-16
Open synaptic and search for **fglrx** remove any you have installed, also what model card are you running

---

### Post by Tatty on 2008-09-16
can you post the output of:

```
lsmod | grep fglrx
```

---

### Post by ejv on 2008-09-17
I think I've got no fglrx installed.  They weren't marked in synaptic.


```
edna@edna-desktop:~$ lsmod | grep fglrx
edna@edna-desktop:~$ 
edna@edna-desktop:~$ lsmod | grep fglrx
edna@edna-desktop:~$ 
```

How do I see which Video card I have?

ejv

---

### Post by ejv on 2008-09-17
I reinstalled the drivers from envyNG and uninstalled them once more from synaptic.  I suppose i'm now only with the restricted drivers from linux.  I deactivated the visual effects and now everything is moving smoothly once again.  but i'm once more on the beggining. Videos, especially on full screen, are not yet satisfactory...

 my card is an ATI Radeon 9250

---

