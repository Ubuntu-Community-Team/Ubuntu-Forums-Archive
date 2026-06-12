---
title: "32 or 64bit system"
date: 2012-05-06
forum: Recurring Discussions
---

### Post by Azyx on 2012-05-06
Hi.
What is the advantage of 64-bit Ubuntu 12.04 compared to 32bit with PAE? Are there any disadvantege with 64-bit? Have a dual core 1,6GHz AMD-processor on 64-bit, but I think the system have high load even if the processor don't work much...

---

### Post by 3Miro on 2012-05-06
64-bit uses more ram, but it is faster. That's about it.

My rule is, if you have at least 3GB of RAM, go for 64-bit and the speed boost. Otherwise, stay with 32-bit.

---

### Post by linuxmatt7 on 2012-05-06
If you are wondering what version to download than just download and install the 32bit version. If you know you have a 64bit processor than download and install 64bit version.

---

### Post by Azyx on 2012-05-06
> **linuxmatt7 said:**
> If you are wondering what version to download than just download and install the 32bit version. If you know you have a 64bit processor than download and install 64bit version.

I have a 64-bit version, but I think it slow, and wonder if the system being faster with a 32-bit OS instead. May some of the hardware-drivers being not so good in 64-bit system?

---

### Post by Azyx on 2012-05-06
> **3Miro said:**
> 64-bit uses more ram, but it is faster. That's about it.

My rule is, if you have at least 3GB of RAM, go for 64-bit and the speed boost. Otherwise, stay with 32-bit.

What is 'speed boost'?

---

### Post by 3Miro on 2012-05-06
> **Azyx said:**
> I have a 64-bit version, but I think it slow, and wonder if the system being faster with a 32-bit OS instead. May some of the hardware-drivers being not so good in 64-bit system?

There are some very old printer drivers that work on 32-bit only, but those are rare. Under Linux, the open 64-bit drivers are just as good as the 32-bit ones. Also, the major proprietary drivers like Nvidia, ATI and Broadcom are also good for both 32-bit and 64-bit.

64-bit applications use more registers on your processors, hence they are a bit faster. I was reading benchmarks a few years ago and they seem to indicate about 10% average increase in performance (also, things like video editing were much faster with 64-bit). However, 64-bit apps use more RAM and if you don't have enough RAM, you will lose speed due to more work on swap or generally HDD activity. I personally go for 64-bit on anything with at least 3GB of RAM, others might pick a bigger threshold. 

If your system feels slow, it is probably due to the low speed of your CPU. The boost from 64-bit might not be noticeable enough for you to feel comfortable, but it is worth the shot.

---

