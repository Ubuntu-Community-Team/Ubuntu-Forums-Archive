---
title: "Ubuntu doesn't see my GeForce GTX 1050 Ti Mobile"
date: 2017-12-20
forum: New to Ubuntu
---

### Post by guilhermefalcao on 2017-12-20
hey, guys,
I just installed Ubuntu 17.10 and for some reason, it can't see my GeForce GTX 1050 Ti Mobile. 
when I open the "About" it shows my Intel® HD Graphics 630 (Kaby Lake GT2)
(Sorry, I tried to post an image but it didn't work)
[https://ibb.co/nH7aH6](https://ibb.co/nH7aH6)[IMG]https://ibb.co/nH7aH6[/IMG]

[IMG]https://ibb.co/nH7aH6[/IMG]
[IMG]https://ibb.co/nH7aH6[/IMG][IMG]http://ibb.co/nH7aH6[/IMG]but when I type 
```
sudo ubuntu-drivers devices
```
It shows the gforce (the one that I want to use)
[https://ibb.co/mekjAR](https://ibb.co/mekjAR)

Which one is the Ubuntu really using? How can I use the GTX instead of the Intel HD Graphics?

I also have other questions:
How can I make sure that my Ubuntu is well set up in a way that I will get the best performance that my hardware allows?
Does it make any difference if I install the Ubuntu on the SSD?

[COLOR=#000000]specifications: 2.8GHz Intel Core i7-7700HQ quad-core processor and 16GB of RAM, 1TB hard drive, 128GB solid-state drive, NVIDIA GeForce GTX 1050 Ti.
[/COLOR]Thank you, guys! 

[COLOR=#000000]
[/COLOR]

---

### Post by mastablasta on 2017-12-20
> **guilhermefalcao said:**
> 
Which one is the Ubuntu really using? How can I use the GTX instead of the Intel HD Graphics?


Look into project bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[https://bumblebee-project.org/](https://bumblebee-project.org/)

> 
I also have other questions:
How can I make sure that my Ubuntu is well set up in a way that I will get the best performance that my hardware allows?

use a test software. Phoronix test suite for example. then compare with others.

> 
Does it make any difference if I install the Ubuntu on the SSD?

of course. time to access & read & write files is much lower on SSD than on standard HDD. if you can most cost effective seems to be  is SSD for OS, HDD for data at the moment.

---

### Post by SeijiSensei on 2017-12-20
See if you can disable the Intel adapter in the BIOS if you don't intend to use it. Then reboot and run the Driver Manager.

---

### Post by guilhermefalcao on 2017-12-21
Ok, I'll do all these things on the weekend. I'll keep you guys updated. 

Thank you!

---

