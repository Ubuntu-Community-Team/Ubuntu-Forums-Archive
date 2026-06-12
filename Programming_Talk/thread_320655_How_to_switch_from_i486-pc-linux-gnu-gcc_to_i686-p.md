---
title: "How to switch from i486-pc-linux-gnu-gcc to i686-pc-linux-gnu-gcc"
date: 2006-12-17
forum: Programming Talk
---

### Post by bigpebble on 2006-12-17
Hi,

I am using Ubuntu 6.10 at home as Linux development environment. At work I use Gentoo and I have set my CHOST environment variable to i686-pc-linux-gnu. I would like to use distcc to offload some of my build time from my Gentoo workstation at work to my PC at home. However as I understand it I would need the same major and minor version of gcc available on Gentoo and Ubuntu. I have 4.1.1 on Gentoo and 4.1.2 on Ubuntu, however the "cross-compiler" names for them are different. On Gentoo it is i686-pc-linux-gnu-gcc and on Ubuntu it is i486-pc-linux-gnu-gcc. 

Is there a way to install the i686-* version on Ubuntu? Does it really matter, or could I just create hard links from the i486 versions to the i686 versions? 

Lastly, my Ubuntu install is not your average install. It is running in VMWare Player, and started out as the 5.10 VMWare Appliance that was on the VMWare website. It was upgraded to 6.06 and recently to 6.10. Could that be why I have i486 versions of the compiler instead of i686?

I would appreciate any advice or information. 

Thanks.

---

### Post by ashrack on 2008-04-13
I am in a simillar boat with Hardy. 
Can I set it to use I686?

---

### Post by ashrack on 2008-04-16
I recomoiled the GCC library to be i686 with version 4.1.1 which is what my Gentoo is using.

---

