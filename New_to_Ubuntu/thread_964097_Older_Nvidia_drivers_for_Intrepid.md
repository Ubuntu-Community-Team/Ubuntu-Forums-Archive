---
title: "Older Nvidia drivers for Intrepid?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by desperado665 on 2008-10-30
Does anyone know if there are any plans in the works to include older Nvidia drivers for the new "bulletproof" X? 

I have already upgraded to Intrepid and the only thing I have issue with is the lack of support for older video cards. Unfortunately, I have an older ti4600 card and I'm unable to use any desktop effects.

---

### Post by jbrown96 on 2008-10-30
I believe that bulletproof X is only meant to be a failsafe. It almost certainly uses the vesa graphics driver because that will work on practically anything all the time. You could try getting drivers from nvidia's website, but your card may not support the effects

---

### Post by markharding557 on 2008-10-30
there is a package called nvidia-glx-71 in the intrepid repository which lists your card as supported

---

### Post by desperado665 on 2008-10-31
Upon trying all the available drivers (71.xx and 96.xx) all I get is low graphics mode and DKMS fails to load on startup. After a little research, I found out that Nvidia doesn't yet have drivers to support the older cards with the new X. Hopefully this will be resolved soon. For the time being, I've had to drop back to Hardy (sigh...).

---

