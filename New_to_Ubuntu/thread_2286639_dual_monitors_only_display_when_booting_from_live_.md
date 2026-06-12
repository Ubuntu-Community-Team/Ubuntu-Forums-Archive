---
title: "dual monitors only display when booting from live cd"
date: 2015-07-13
forum: New to Ubuntu
---

### Post by jdlaustin on 2015-07-13
Ubuntu 14.04 updates froze. Now when I boot up, my dual monitors aren't configured and Detect Display doesn't work. However, when I boot to a live CD, both of my Dell monitors display correctly.

What can I do to fix this problem?

---

### Post by QIII on 2015-07-13
Hello!

Can you tell us the manufacturer and model of your graphics adapter and whether you are using a proprietary driver (if so, how did you install it?)

Thanks!

---

### Post by jdlaustin on 2015-07-13
Also it can't detect the usb drive. How to I fix a broken ubuntu 14.04?

---

### Post by QIII on 2015-07-13
One subject per thread will keep things from becoming confusing for you and those who would like to help.

Let's stick to the display issue here.

---

### Post by jdlaustin on 2015-07-13
> Can you tell us the manufacturer and model of your graphics adapter and  whether you are using a proprietary driver (if so, how did you install  it?)

they're Dell monitors. 

lspci | grep VGA says AMD...

What I really want to do at this point is to find a way to fix the broken update.

---

### Post by QIII on 2015-07-13
Perhaps not, which is why I ask.  It may be that the update broke in a manner that borked the graphics.  If we address that, you may be able to log in and continue the update.  An update can cause problems with graphics, depending on what was updated.  If that doesn't work, we can see if we can continue the update from rescue mode.

What model of AMD GPU and were you using and did you have a proprietary driver installed?

---

