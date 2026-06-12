---
title: "Which distro for Nvidia GeForce 8500 GT?"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by antoelca on 2013-10-02
[SIZE=3][FONT=century gothic]Hi,

i'm a new user of linux and I need some help for choosing a distro.

My computer has this hardware:
> Intel Core 2 Quad CPU
Q6600 @ 2.40GHz
1,98 GB de RAM
graphic card: NVIDIA GeForce 8500 GT

I wish to use it for simple office and internet tasks, I also do some little python code.
Trying ubuntu from a wubi installation I felt that my system [/FONT]was not working so fast and reliable, and I want some advice before choosing the distro, i don't know if a gnome desktop is better than unity for my hardware.[/SIZE]

thank you in advance,

---

### Post by Vakman on 2013-10-02
Your machine should run Ubuntu perfectly fine. 
Wubi itself may have been the issue or perhaps you didn't realize it but it could have been your graphics drivers.

---

### Post by DuckHook on 2013-10-02
Hi antoelca and welcome!

Yours is a very good system, more than capable of running Ubuntu. WUBI should not slow it down, but most of us have never installed that way, so when it comes to issues that touch upon file structures, it may be out of our depth.

Like *Vakman* my first suspicion is that you are using the standard open-source video drivers, and this may be the issue. To help us pin things down further, please expand on what you mean by "...my system was not working so fast and reliable"? Please provide every detail you can think of. Also, post back to this thread the results of:```
lspci -vk | grep -iA13 vga
```

With respect to choosing distros, your computer is good enough to run any distro you want. However, the choice of distro is a difficult matter to advise you on because it is mainly a matter of personal preference. Since you have sufficiently robust hardware to run any distro, why don't you try them out as LiveDVD/USB before installing the one you like? In the Ubuntu universe there are already four flavours that you can try: Ubuntu, Kubuntu, Xubuntu and Lubuntu. It's a simple matter to try them all out, for the cost of four DVDs.

---

### Post by antoelca on 2014-06-03
[B]

[SIZE=3]Hi Vakman and DuckHook. Thanks for your advice. Sorry about writing so late.[/SIZE][/B][SIZE=3]
I did what you said to try the Live versions, a friend helped me building the bootable USB. And we had some creative discussion.
I choose lubuntu. My parents have to use this computer now that XP is an undead danger ( xD ) and the Unity way of life is not in their mood.[/SIZE]

About the "performance" and lazy description i gave to you: first time I used ubuntu with the unity desktop I saw that swapping between web browser and the spreadsheet I was working had some lag and the fan noise in the CPU was more often loud than I could remember it had to be.

Thanks to both of you ^^

however the output you asked for:

> 01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8500 GT] (rev a1) (prog-if 00 [VGA controller])	Subsystem: ASUSTeK Computer Inc. Device 8245
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 92000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb


03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface




---

### Post by Vladlenin5000 on 2014-06-03
```
Kernel driver in use: nouveau
```
means you're using the open-source drivers.

---

### Post by antoelca on 2014-06-03
So may I make any changes? Vladlenin5000

---

### Post by Vladlenin5000 on 2014-06-03
Sure. You can try nvidia's proprietary drivers. A GeForce 8500 GT should work better with those instead of the open-source nouveau.

System Settings > Software & Updates > Additional Drivers (last tab). Select the recommended (tested) driver version; it'll will automatically download and install. Reboot & test.

---

### Post by antoelca on 2014-06-03
Thank you Vladlenin5000

---

