---
title: "Loading Ubuntu on a new build/no OS"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Solarbronco on 2012-02-02
Hi everyone! I am building a new PC for my wife and have decided to load 64 bit 11.10 on it after some great test results using live cd on her exsisting pc.

My First question is about drivers. Do I load them before loading unbuntu or after?
Not running wireless, will be Ethernet. So that's one less worry.

I am building the pc using the following:

Asus M4A88T-M motherboard
Amd phenom ll x6 1045T processor 
4 gig Patriot gamer2 memory- 1 stick.
Generic/cheap  lite on DVD reader/writer 
Will pick up a hdmi monitor to use.
Seagate 500gig sata 6g hard drive.

Any useful advice would be greatly appreciated! I am very new at Linux, but have been a Mac user for years.

---

### Post by arochester on 2012-02-02
In Microsoft Windows you have to load lots of drivers. In Linux you don't have to load lots of drivers - there are already some drivers in the kernel/installed. 

If you have already tried the LiveCD without problems it is a good bet that an install will work out-of-the-box. TRY IT! If you then have any problems feel free to come back here for more information.

---

### Post by Solarbronco on 2012-02-02
Thanks! I'm hoping that you are correct.

The live cd is running on an old PC that has Windows xp loaded on it.




> **arochester said:**
> In Microsoft Windows you have to load lots of drivers. In Linux you don't have to load lots of drivers - there are already some drivers in the kernel/installed. 

If you have already tried the LiveCD without problems it is a good bet that an install will work out-of-the-box. TRY IT! If you then have any problems feel free to come back here for more information.

---

### Post by mastablasta on 2012-02-02
graphics card? built in? 
 
you might need drivers for it. basic ones come in kernel but for better support you might need ot add them later via hardware driver utility.
 
sound card? some new sound chips are problematic. the driver for them is usually in kernel (maybe it could be later be upgraded to unstable version if there is no sound).

---

### Post by arochester on 2012-02-02
> The live cd is running on an old PC that has Windows xp loaded on it.
 Try the LiveCD in the new machine. It should work even when there is noting on your hard drive. (It will leave the hard drive completely untouched, as though it had never been there.) 

You might need to change the BIOS/Boot Order so that the computer will boot fron the CD first, before the hard Drive

---

