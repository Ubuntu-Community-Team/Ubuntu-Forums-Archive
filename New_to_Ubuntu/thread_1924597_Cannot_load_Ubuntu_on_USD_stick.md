---
title: "Cannot load Ubuntu on USD stick"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by ca1123 on 2012-02-13
The USB stick works fine on other computer.
but on this one it does not work.
I guess it is about hardware.
here is my detail config:
Phenom II X4 955
AMD 980FX chipest
16GB RAM
GTX580*2
Intel 320 40GB SSD + Segate 500G HDD

---

### Post by mastablasta on 2012-02-13
problem is the graphics card
 
also are those two cards? try to take one card out.
 
use boot options to boot if it still doens't work): [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ca1123 on 2012-02-13
> **mastablasta said:**
> problem is the graphics card
 
also are those two cards? try to take one card out.
 
use boot options to boot if it still doens't work): [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thanks for your contribution.
But the whole point for these two new graphic cards is for CUDA.
Thus it is not very good for me if I can only use one card when Ubuntu is finally installed.

Is it possible for me to install the system with only one card and run the system with both cards?

Also could u explain more about wat to do with boot options, I have checked the document but haven't found something helpful.

---

### Post by mastablasta on 2012-02-13
> **ca1123 said:**
> 

Is it possible for me to install the system with only one card and run the system with both cards?

Yes if this option is supported by linux driver that i show you would do it. first install the OS with one card and then install proprietary drivers. now if those drivers support this 2 card configuration it should all work. another option could be to use alternate install or mini iso and during that install do an install of the graphics drivers via command line.

> 
Also could u explain more about wat to do with boot options, I have checked the document but haven't found something helpful.boot options can make it boot into basic vesa graphics mode (for example) . sometimes this helps as you can later install propper drivers (form manufacturer). thoguh i am not sure if this is the case with dual GPU.

not sure how this is done in windows 7, but in XP for example when you first install it only uses vesa drivers or it uses some basic generic (proprietary) drivers.

Ubuntu uses/loads opensource drivers that are often reverse engineered. sometimes (or should i say often) they work ok, but usually to get full support for the new cards or card configuraitons you need proprietary drivers. now again Linux proprietary drivers do not always support all functions as windows drivers. or if they do they do not have full support. an example that affects a lot of people with laptops is optimus or hybrid graphics switching tecology, which simply does not work well in linux or not at all. the thanks goes to card manufacturers who do not want to provide drivers for it. however (fingers crossed) there is a hint of change at one manufacturer...


edit also check related nvidia info on your setup it might help to see if and how it is supported in linux: [http://forums.nvidia.com/index.php?showforum=68](http://forums.nvidia.com/index.php?showforum=68)

---

