---
title: "Thinkpad no PAE on 12.04"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2013-01-14
Hi
I'm trying to put 12.04 32 bit on a thinkpad.

While booting the CD it stops saying wrong CPU type, please use a CPU with PAE.

I remember reading that non-PAE support was being dropped from 12.10 but I thought it was still in 12.04

Any ideas

---

### Post by steeldriver on 2013-01-14
I may be wrong but iirc Xubuntu and Lubuntu both kept a non-PAE kernel option in 12.04 but not Ubuntu itself

---

### Post by NikTh on 2013-01-14
> **steeldriver said:**
> I may be wrong but iirc Xubuntu and Lubuntu both kept a non-PAE kernel option in 12.04 but not Ubuntu itself

Correct. 

So if OP wants Ubuntu 12.04 LTS (Unity) he/she must install one of 2 flavors of Ubuntu first (Lubuntu or Xubuntu) and then install ubuntu-desktop package (unity environment) 
OR 
can follow this tutorial 
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

Thanks

---

### Post by d4m1r on 2013-01-14
1) Yes, non-PAE support was dropped from Ubuntu 12.04 LTS but it was kept in other variants.

2) You can use the special ISO provided in that tutorial but as a warning, you need to be connected to the internet to proceed with the install. I tried it as I was not warned about this in the article...

3) Instead, I installed Ubuntu 11.10 will not connected to the internet, connected to the internet after the install, and simply upgraded to 12.04. It correctly and automatically upgraded me from 11.10 to 12.04 (non-PAE).

---

### Post by OrangeCrate on 2013-01-14
> **bigmonmulgrew said:**
> Hi
I'm trying to put 12.04 **32 bit** on a **thinkpad**.

While booting the CD it stops saying wrong CPU type, please use a CPU with PAE.

I remember reading that non-PAE support was being dropped from 12.10 but I thought it was still in 12.04

Any ideas


Though my T43 will take a PAE kernel, I'm using Xubuntu 12.04 (as suggested by others). Works great.

---

