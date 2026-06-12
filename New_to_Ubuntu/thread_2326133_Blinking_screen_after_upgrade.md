---
title: "Blinking screen after upgrade"
date: 2016-05-28
forum: New to Ubuntu
---

### Post by ccdavis77 on 2016-05-28
While trying to troubleshoot another problem, I upgraded to Ubuntu 16.04 and now my screen blinks every 2 seconds which is driving me crazy. I have an Intel i3 processor and Intel Ivybridge desktop graphics card. Please help!!

---

### Post by T.J. on 2016-05-28
Does it boot or not?  If it gets to the login and then blinks, have you tried adding "nomodeset vga=0x318" to your kernel parameters at the boot menu?

---

### Post by SageAbkatsor on 2016-05-28
Wahoo, that worked for me

---

### Post by T.J. on 2016-05-29
> **SageAbkatsor said:**
> Wahoo, that worked for me

Does your display work as expected after you log in?  Does everything look very large or normal sized? If everything looks good, do you need help making the change permanent?

---

### Post by SageAbkatsor on 2016-05-30
In my case I was not upgrading to 16.04. I had no OS installed on my machine and had just installed it for the first time. 

Everything got large for the login screen after the nomodeset was added, and there was a grid of very light dots over the background as well (maybe I just hadn't noticed it before, but I think it was new). At first it still didn't seem to work, as none of the apps or menu bar were displayed, but when I right clicked the drop down no longer was blinking but stayed on as it should. Then a menu popped up and took me through the installation of some drivers and such, ultimately leading to a reboot. 

Once I rebooted everything worked almost perfectly. Had to switch to the proprietary drivers for my gfx card but I think that's about it. Things are working well now. Might redo the whole process to partition out my ssd a bit. I am sure there is a better way to do it, but cloning my install to the hdd, or partitioning on a live disk, seems complicated:confused:.

EDIT: The one thing I will say is that it seems like nomodeset is still applied, as things seem larger than they were before I added nomodeset. I don't think it is applied, but it seems like it is. With that said, I have no idea what nomodeset actually does.

---

### Post by T.J. on 2016-05-31
> **SageAbkatsor said:**
> EDIT: The one thing I will say is that it seems like nomodeset is still applied, as things seem larger than they were before I added nomodeset. I don't think it is applied, but it seems like it is. With that said, I have no idea what nomodeset actually does.
You may need to adjust your display resolution.

the "nomodeset" option disables the kernel mode setting. If it is applied, you probably won't have a graphical logo screen on startup.  The login screen and everything after should be fine though.


 For some, this option prevents a lock up if their default video driver is less than optimal.  Unfortunately, because of the way some hardware companies do business, they won't give us all the information we need for a perfect Linux driver.   Normally, this is not a problem, but on some occasions - hopefully very rare - you might have to override a setting in order to get things to work as you expect.  The developers do the best they can, but the world is not a perfect place.

---

