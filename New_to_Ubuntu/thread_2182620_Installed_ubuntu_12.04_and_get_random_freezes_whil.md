---
title: "Installed ubuntu 12.04 and get random freezes while using ubuntu"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by brainox on 2013-10-21
Hello ubuntu forum,
I am a total linux noob and wanted to use ubuntu for my laptop. The installation worked fine and I updated it after finishing the installation.
But my laptop freezes randomly now. I still can u se ctrl+alt+f1 and get back to the desktop from there but then it freezes again randomly.
I use a Samsung 300V3A-S02:
CPU: Intel Core i5 2410M
VRAM: Nvidia GT520M
Memory: 4GB

Does it have to do with the vram because I read about optimus having problems with linux etc.?

---

### Post by BBQdave on 2013-10-21
> **brainox said:**
> ...my laptop freezes randomly...
I use a Samsung 300V3A-S02:
CPU: Intel Core i5 2410M
VRAM: Nvidia GT520M
Memory: 4GB

Does it have to do with the vram because I read about optimus having problems with linux etc.?

Running Ubuntu Unity 12.04LTS - **64bit**, on a Toshiba Satellite c655-s5503, with out trouble. Hardware is an i3 with intel graphics and 4GB of ram.

Maybe hybrid graphics is giving you trouble? If you did a regular install with **Ubuntu Unity 12.04LTS AMD 64** - *64 bit version*, then updated, you should be running the stock video driver that comes with the Kernel Linux.

Usually this trouble happens, trying to run Nvidia driver.

---

### Post by brainox on 2013-10-21
> **BBQdave said:**
> Running Ubuntu Unity 12.04LTS - **64bit**, on a Toshiba Satellite c655-s5503, with out trouble. Hardware is an i3 with intel graphics and 4GB of ram.

Maybe hybrid graphics is giving you trouble? If you did a regular install with **Ubuntu Unity 12.04LTS AMD 64** - *64 bit version*, then updated, you should be running the stock video driver that comes with the Kernel Linux.

Usually this trouble happens, trying to run Nvidia driver.
i installed the 64bit version and just i think i use the stock video driver. I thought about using bumblebee or so if it has to do with the hybrid graphic but since its my first time using linux i want to ask first^^.

---

### Post by BBQdave on 2013-10-21
> **brainox said:**
> i installed the 64bit version and just i think i use the stock video driver. I thought about using bumblebee or so if it has to do with the hybrid graphic but since its my first time using linux i want to ask first^^.

That's curious. You have the right install for your hardware and good solid hardware for performance - so this is odd with the random freezes.

I think you are on the right track with video drivers - might be worth checking out Nvidia driver.

---

