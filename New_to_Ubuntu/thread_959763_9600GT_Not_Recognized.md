---
title: "9600GT Not Recognized"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by davidwoo15 on 2008-10-26
I've recently installed Ubuntu 8.04.1 LTS on my pc but my graphics card is not being registered in the "Update hardware drivers" option.  I tried going on the NVidia website and finding the correct drivers, but as i am new to this i have had some problems. If anyone would point me in the right direction that'd be great.


Specs incase needed : Intel Q6600
                      NVidia 9600GT
                      4GB RAM
                      ASUS Mobo


Thanks.

---

### Post by Riffer on 2008-10-26
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

This is the FAQ page for EnvyHG.  It tells you how to download/install and use.  Many have found this program the best way to install the necessary driver for your nVidia card.

---

### Post by igknighted on 2008-10-26
You have 4 choices, none are entirely ideal.  Nvidia hadn't released drivers for your card when Hardy was released, so they weren't included.

1) Install Ubuntu 8.10 (RC, or Final will be out within a week).

2) Change your repositories from hardy to intrepid, install the latest nvidia-glx-new (it will bring in a new kernel and other stuff, that's normal... just don't do a general system update).

3) Download the drivers from Nvidia.  Every time a kernel upgrade comes through, you will have to reinstall these drivers, as they are built specifically for each kernel version

4) Wait for the driver to get backported to Ubuntu 8.04 (will likely happen some time, and actually might be in hardy-proposed, can someone check?)

---

### Post by davidwoo15 on 2008-10-30
Ok thanks. I'm just gonna download 8.10 now!

---

