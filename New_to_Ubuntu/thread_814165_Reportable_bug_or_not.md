---
title: "Reportable bug or not?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by awang on 2008-05-31
When I upgraded to Hardy 8.04, my wireless connection was broken.
Then I noticed in my GRUB list that there were older versions(-17, -16, -14) of the kernal.
I booted on the oldest kernal(-14), and voila, the wireless works.

Is this something I can/should report as a bug?

---

### Post by shifty_powers on 2008-05-31
nope, this happens with kernel upgrades. the wireless modules is integrated into the kernel...

---

### Post by FuturePilot on 2008-05-31
What wireless card do you have? Intel?

> **shifty_powers said:**
> nope, this happens with kernel upgrades. the wireless modules is integrated into the kernel...
Stuff like this should not break with new kernels.

---

### Post by awang on 2008-05-31
It's a BCM94311MCG wlan mini-PCI.

---

### Post by FuturePilot on 2008-05-31
Did you have to do anything special before to get it working? If you did you might just have to redo those steps while running the new kernel.

---

### Post by awang on 2008-05-31
Nothing special.  Even tried to log in with newer kernel(2.6.22-17) after getting it to work with 2.6.22-14.  Did not work.

---

