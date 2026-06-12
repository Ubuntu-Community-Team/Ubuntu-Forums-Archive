---
title: "Questions about Usplash and Startup Manager on 1280x800 monitor"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by the8thstar on 2008-06-01
Hello all,

I have installed Startup Manager with a bunch of .so files to customize my usplash.

My laptop screen is 1280x800, which isn't listed in the options of SUM. Therefore, whenever I change the usplash (even the default Ubuntu one), my screen is all extended or worse, the splash is not centered.

So my questions are:

1. Is there a way to set a 1280x800 resolution? I tried setting usplash.conf, but it didn't change anything

2. Do I need to edit Grub? If so, what is the VGA code for this 1280x800 resolution?

3. Is there anything else I could do?

---

### Post by philinux on 2008-06-01
I think you'll find a lot of the .so files only work at 1024x768.

Which is where mine is set. However my display when logged on is higher.

---

### Post by sayakb on 2008-06-01
Try VGA=864 or 872

---

### Post by the8thstar on 2008-06-02
Thank you for these values **LinuxIsInnovation**. Now the Usplash displays at 1280x800 like it was meant to.

---

