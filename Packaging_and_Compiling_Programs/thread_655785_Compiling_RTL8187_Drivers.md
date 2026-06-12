---
title: "Compiling RTL8187 Drivers"
date: 2008-01-01
forum: Packaging and Compiling Programs
---

### Post by FlyingIsFun1217 on 2008-01-01
Hey!

I'm attempting to compile and use RTL8187 drivers, since one's included with the kernel seem to never work right. I've also tried using ndiswrapper, but that has not worked correctly either (although a little better).

Basically, I'm attempting to compile the new ones as described [here]("http://rtl-wifi.sourceforge.net/wiki/Installing"). The only problem is that I have no connection (especially after I unload the module) since for some reason my ethernet is not working. So basically, I'm shooting to do all of this without internet.

I've gotten all of the needed packages and files through windows, and copied them over to my linux install to use. Everything was going fine, until I went to compile the new modules. When I open the terminal in the driver's main directory, and type in make (doing so as the root user, using 'su'), I just get:

> make[1]...
make[2]...
...
make[7534]...

The stuff after make is always the same, and it just cycles through until it hit's about 7500, where the whole desktop starts to freeze, and the system becomes unresponsive (as in I have to physically pull the laptops battery out).

What am I doing wrong here? Is this a known issue? Is there an easier way to install the driver explained in the link?

Thanks so much!
FlyingIsFun1217

---

### Post by Vadi on 2008-01-03
I think you run out of RAM.

And good luck. I tried compiling the 8185 ones, no luck. Thankfully ndiswrapper (although with degrading support in every new release) is still working.

---

### Post by FlyingIsFun1217 on 2008-01-04
I gig, and I run out? Why can I not compile kernel modules, yet I can compile new kernels? Funny...

Well, I'll try using NDISWrapper again...

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-04
Wait...

How do I re-add the ieee80211 stack, removed as the tutorial instructs:

> 
 sudo rm -r /lib/modules/`uname -r`/kernel/net/ieee80211
sudo modprobe -r ieee80211


Thanks again!
FlyingIsFun1217

---

