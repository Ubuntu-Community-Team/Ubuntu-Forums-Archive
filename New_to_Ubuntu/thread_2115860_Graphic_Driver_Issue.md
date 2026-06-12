---
title: "Graphic Driver Issue"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by LTVX on 2013-02-14
Hello all,

I installed Ubuntu 12.10 yesterday and I´ve been fooling around with it to get it up and running. I noticed that my system didn´t recognize my graphic card (I have a ASUS EAH6670/DIS/1GD5) So I decided to install amd-driver-installer-catalyst-13.1-linux-x86.x86_64 everything went well however my system details displays ¨VESA: TURKS¨ Experience: ¨Standard¨ under graphics. I tried googling for a solution but no luck so far. What seems to be the issue? And how do I change it?

Thanks in advance,

LTVX

Edit: I should note that my motherboard has a on board VGA chip.

---

### Post by grahammechanical on 2013-02-14
"Experience standard" is the standard description of the Graphics page in the Details utility. I have seen it continually since 12.04, through 12.10 and it is still saying that in 13.04 which I am testing.

That Graphics page serves no useful purpose as far as I can tell. As you have installed a proprietary video driver you will find much more useful information in the proprietary video driver settings utility.

You will also notice that the Displays utility does not work either. It only works when you use the default open source video driver (Nouveau).

This is how things are.


Oh. I forgot. Welcome to the forums. Sorry for forgetting.

Regards.

---

