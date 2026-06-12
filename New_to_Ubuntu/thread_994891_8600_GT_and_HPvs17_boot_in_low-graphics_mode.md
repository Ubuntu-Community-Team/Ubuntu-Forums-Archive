---
title: "8600 GT and HPvs17 boot in low-graphics mode"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by nbeerbower on 2008-11-27
Hey Guys,

I recently updated to 8.10 from 8.04, and I'm having some trouble. I'm using a Geforce 8600 GT on an HP vs17 monitor and everytime I boot I get an error saying that Ubuntu needs to run in low-graphics mode. I've tried various different things like nvidia-xconfig, manually editing xorg, and even using the configuration tool the error message provides. Currently, my monitor is set at 800x600 and has a refresh rate of 73. When it really should be at 1280x1024, 60hz. 

Please be as n00b friendly, I'm only 13. :P

Thanks a lot,
-nbeerbower

---

### Post by Bölvaður on 2008-11-27
Try set up the driver again with your chosen way.

nvidia website
envy
restricted-hardware


you just need the driver to be run under the kernel, as the kernel controls the hardware, the driver must become part of it.

---

### Post by nbeerbower on 2008-11-27
What the...?

That was surprisingly easy. I just used Envy and everything was good, which is strange because the restricted drivers didn't work.

Well thank you. :)

-nbeerbower

---

### Post by philinux on 2008-11-27
Under system>admin>hardware drivers does it say the driver is in use?

---

