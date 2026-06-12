---
title: "Not loading on ASUS Eee PC 1101ha"
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mrdoob on 2011-09-01
Both "Try Ubuntu without installing" and "Install Ubuntu" hang with the screen saying "* Checking battery state... [ OK ]"

Any way I can give more information?

---

### Post by mrdoob on 2011-09-03
*bump*

---

### Post by lucazade on 2011-09-03
your netbook comes with an Intel gma500 gfx card, 
give it a shot to these threads:

[http://ubuntuforums.org/showthread.php?t=1792777](http://ubuntuforums.org/showthread.php?t=1792777)

[http://ubuntuforums.org/showthread.php?t=1818866](http://ubuntuforums.org/showthread.php?t=1818866)

and the megathread you can find in my signature.

---

### Post by mrdoob on 2011-09-03
Yeah, I've been following these threads. My problem is that I put the usbstick in, the laptop starts to boot the installer/live but it gets stuck, so at no point I can have access to a terminal to try thing.

---

### Post by lucazade on 2011-09-03
it is a known issue.
oneric kernel comes with the psb_gfx driver installed by default but it is an old version and it breaks livecd from starting up


> To make the livecd startup we have to unload a couple of drivers adding some parameters to kernel, otherwise it ends up in a white screen (or stuck at battery checking)

add 'poulsbo.dummy=1 psb_gfx.dummy=1' to kernel params at grub time (hit F6 when livecd starts and append params at the end of string)
this way the 2 kernel modules are not loaded, because of wrong options enabled, and livecd could use vesa as X driver.

when you hit f6 you'll get a screen like this:
[http://shiba89.files.wordpress.com/2010/07/02.png](http://shiba89.files.wordpress.com/2010/07/02.png)

---

### Post by mrdoob on 2011-09-03
Yay! That did the trick. Thanks lucazade!

Good to see the thing booting again, hopefully the driver issue will get fixed in time. Otherwise it'll be 6 months more of wait.

---

### Post by lucazade on 2011-09-03
> **mrdoob said:**
> Yay! That did the trick. Thanks lucazade!

Good to see the thing booting again, hopefully the driver issue will get fixed in time. Otherwise it'll be 6 months more of wait.

glad it worked for you... we're trying to get emgd in a good state for oneiric, especially with the great support of thopiekar in the mega thread.
with the kernel 3.1 psb_gfx will likely work out of the box but oneiric won't use it, so for the lts i'm confident things will be better :)

---

### Post by jbernardo on 2011-09-04
What ubuntu image version did you try? I am getting hangs even when passing the parameters to grub, on a 1101ha, with alpha3 and nightly 0830.
I'll download beta1 now to see if it makes any difference.

---

### Post by mrdoob on 2011-09-05
It was beta1 32-bit.

---

### Post by jbernardo on 2011-09-05
Thanks, I'll try that.

---

