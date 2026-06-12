---
title: "Googleearth and Compiz"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by stchman on 2008-05-15
Hello all.

I recently upgraded to Hardy on my laptop (ATI Xpress 200M).  I can use Compiz OOB after enabling the restricted driver.

When I install googeearth it works but flickers very badly.

If I disable desktop effects GE works fine.  Is this normal?  On my 8800GT equipped desktop GE works fine with Compiz.  Is this a dramatic video card horsepower difference?

---

### Post by philinux on 2008-05-15
Quite smooth here even with compiz on. I had a popup on install in the notification area regarding nvidia driver and just ticked the box.

See sig for spec.

---

### Post by maphilli14 on 2008-05-15
> **stchman said:**
> Hello all.

I recently upgraded to Hardy on my laptop (ATI Xpress 200M).  I can use Compiz OOB after enabling the restricted driver.

When I install googeearth it works but flickers very badly.

If I disable desktop effects GE works fine.  Is this normal?  On my 8800GT equipped desktop GE works fine with Compiz.  Is this a dramatic video card horsepower difference?

Mine's 'flickery' too...  ATI 5250 on Lenovo Thinkpad T60p using proprietary fglrx drivers.

:(

Mike

---

### Post by stchman on 2008-05-15
> **maphilli14 said:**
> Mine's 'flickery' too...  ATI 5250 on Lenovo Thinkpad T60p using proprietary fglrx drivers.

:(

Mike

Maybe it is an ATI thing.  Oh well, the few times I use GE I just turn off desktop effects.

---

### Post by Thingymebob on 2008-05-15
Yeah, I get this with compiz on, not just in google earth, but in any 3d app/game/etc but if I  do
```
metacity --replace
``` runs a treat.

---

### Post by dizee on 2008-05-15
It's the ATI driver's fault, I have the same graphics card and have to disable Compiz for Google earth to be usable. The fusion-icon program is very handy, it sits in the system tray and allows you to switch from Compiz to other window managers very quickly.

---

### Post by yaknowwat on 2008-05-15
Theres a Little applications called Compiz Fusion Icon I use this as it allows easy access to change Window Managers.

---

### Post by catanzag on 2008-05-19
Did you try indirect rendering with ATI driver? I've a nvidia, but I found some time ago a solution for a similar problem in google.groups. From prompt

$ export LIBGL_ALWAYS_INDIRECT=true
$ googleearth

hope this can help you

regards

---

