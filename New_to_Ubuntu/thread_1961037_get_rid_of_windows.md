---
title: "get rid of windows"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by rima on 2012-04-18
Just generally, I want to get rid of my Windows.

I want to start with LiveUSB for 12.04. I'll manage to set it up and boot properly from USB stick. Now, a couple of questions:

a) If the LiveUSB tells you can "uninstall Windows and install Ubuntu as the only OS" will it get rid of ALL my partitions, or just the Windows ones? Because I have one Windows recovery partition somewhere, and I don't know how to get rid of it

b) Will the LiveUSB set up Ubuntu partitions for me automatically ?

c) Am I sure that I'll definitely be able to boot up system properly after the successful install?



Just a couple of questions.

I tested out all my hardware-specific stuff with Wubi, everything's gone nice and smooth and everything works great (except for the webcam, I don't know about that one, I heard it doesn't work but I NEVER use webcam, so I don't really mind)

---

### Post by raja.genupula on 2012-04-18
> **rima said:**
> Just generally, I want to get rid of my Windows.

I want to start with LiveUSB for 12.04. I'll mangaNow, a couple of questions:

a) If the LiveUSB tells you can "uninstall Windows and install Ubuntu as the only OS" will it get rid of ALL my partitions, or just the Windows ones? Because I have one Windows recovery partition somewhere, and I don't know how to get rid of it

b) Will the LiveUSB set up Ubuntu partitions for me automatically ?

c) Am I sure that I'll definitely be able to boot up system properly after the successful install?



Just a couple of questions.

I tested out all my hardware-specific stuff with Wubi, everything's gone nice and smooth and everything works great (except for the webcam, I don't know about that once, I heard it doesn't work but I NEVER use webcam, so I don't really mind)

1 Ans: it will give you options such as Remove all partitions and install side by side and manual something like that .
so if you wanna get rid off from windows then while doing partition step selection you can clear the windows partition and you can install ubuntu in that .

2 . If you choose install along side option then partition will done automatically .

3 .yes 100% , but 12.04 is not released officially . but as you said its fine with hardware of yours , maximum 99% it will be fine . so you can happily go on with installation in your PC .

---

### Post by cottfcfan on 2012-04-18
If you are happy to wipe your computer totally and install Ubuntu, you could just use gparted from the live usb, and wipe the whole disk.
I suggest you then create 3 partitions, 1 for / the 2nd for /home, and the 3rd for swap.
I don't know how big your disk is, but on mine its 500 gig.
20 for /, 475 for /home, & 5 for swap.
Then install to those partitions.

---

### Post by rima on 2012-04-18
Thank you so much! *grabs a cup of coffee and waits for 12.04* I just wanted to confirm, that's all.

---

### Post by raja.genupula on 2012-04-18
ok now please mark the thread as solved from thread tools .

---

