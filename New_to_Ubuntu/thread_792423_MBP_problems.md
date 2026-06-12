---
title: "MBP problems"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by kadinshino on 2008-05-12
Hey i was just wondering if anyone could point me out to were i might find how to enable my wireless card in my MBP

im running windows as a partition on my computer then installed ubuntu 8.04 inside the windows partition from the ubuntu CD,

Everything installed fine and it runs like it should but when i go to network admin to choose a network my wireless card wont show up. so i tried looking for the .inf file in windows to install the drivers but it did not work.

then i looked on Wiki to find the activation stuff but it did not show anything to do with apple

thanks for advice :)

---

### Post by lemming465 on 2008-05-19
There is some advice [here]("https://help.ubuntu.com/community/MacBookPro") which might help.  I was able to get Atheros-based wireless working on a Toshiba Satellite using ndiswrapper and a Vista driver.  Atheros is finally starting to help out with driver work, and the 2.6.25 kernel (Hardy Heron has 2.6.24) merged a newer driver.  So there is some hope that 8.10 "intrepid ibex" this fall might be less hassle to get going.

---

