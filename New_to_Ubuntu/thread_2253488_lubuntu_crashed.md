---
title: "lubuntu crashed"
date: 2014-11-20
forum: New to Ubuntu
---

### Post by panosss on 2014-11-20
I just installed lubuntu.
Rebooted 3-4 times and mainly used Firefox.
I reboot once more and click on the Web browser button and...lubuntu crashes!!!:shock:
I had to press reset button!
(now iI 'm writing this post from lubuntu)

Why did this happen?
Maybe it has something to with my graphics card? (nVidia GeForce 6150 SE).
I haven't installed any drivers for the graphics card.

---

### Post by DarkSapphire on 2014-11-22
Oldfred is right

---

### Post by oldfred on 2014-11-22
That is an older nVidia card, but I think the System settings should show the legacy driver for that card as an install option.

Confirm you are installing the correct legacy driver. Best to only install from repository. If you install from nVidia you have to in effect reinstall with every kernel update. Proprietary driver has to be integrated into kernel and if from Ubuntu repository that is done automatically.
       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

