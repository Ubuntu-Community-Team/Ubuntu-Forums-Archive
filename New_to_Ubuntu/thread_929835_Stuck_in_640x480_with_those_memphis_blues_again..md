---
title: "Stuck in 640x480 with those memphis blues again."
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Grrruff on 2008-09-25
I'm using Ubuntu 7.04
I was testing a new monitor and ended up playing around in the video setup section.  It looks like it has become stuck in 640 x 480 mode no matter what I choose.  I used the detect button as well. 

I moved back to the old monitor and the problem persists.:confused:

I'm using a have a 19 inch 1280 x 1024 LCD monitor in both cases.

Anyway I can get back to my higher res?

Thanks,
~Tom

---

### Post by shifty_powers on 2008-09-25
any particular reason you are using 7.04?

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

might help btw

---

### Post by Grrruff on 2008-09-25
I was not comfortable upgrading when I could only see a tiny corner of my desktop.  My plan was to upgrade before this happened.

Later on....

I upgraded anyway hoping it would fix the problem.
The Video options seem to have disappeared from the 
System Administration menu.  Wonder how one is suppose to choose a video driver without the menu option.?


I found the "detect displays" button on the screen resolution dialog under System Preferences. Pushed that and rebooted.

I think it is fixed. At least with the original monitor.  It is an SVA VR-178 which I could find no driver information on except that it was plug and play.

---

### Post by roger_1960 on 2008-09-25
Hi

Try in terminal

sudo displayconfig-gtk

Then change the model to something suitable (LCD) and select the resolution.

---

