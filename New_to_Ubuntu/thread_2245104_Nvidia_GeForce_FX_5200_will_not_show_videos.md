---
title: "Nvidia GeForce FX 5200 will not show videos"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by impartit on 2014-09-21
My Ubuntu 14.04 install shows two graphics card drivers are present and the active one is:

X.org X Server - Nouveau display driver from xserver-org-video-nouveau(open source)

lspci | grep  VGA confirms that I have installed a VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)graphics card (configured in BIOS as AGP)

However if I choose the other driver NVIDIA legacy binary driver - version 173.14.39 from nvidia-173(propriety,tested) it screws my display on boot where after login the screen remains blank with a cursor and the terminal screen is unreadable garbage.

The X.org X Server refuses to show play videos (youtube etc. using Firefox with Adobe Flash Player installed).

About this computer shows
Memory 2 Gb
Processor AMD Athlon(tm) XP 2600 + (yes OK it is a bit of a dinosaur)
Graphics Gallium 0.4 on NV34
OS type 32 bit
Disk 76.5 Gb

Because Terminal gives an unreadable display I cannot change the driver if I select the wrong one.

Can anyone advise please?

---

### Post by mörgæs on 2014-09-21
An Athlon XP does not have SSE2 which Flash requires. 

For an FX 5200 I would drop Ubuntu and begin with a fresh install of Lubuntu 14.04.1. More advice in the thread in my signature.

---

### Post by Vladlenin5000 on 2014-09-21
Hi, welcome.

The legacy 173 is the nvidia's recommend driver version for your hardware. You can also try 173 (updates) that should be offered at additional drivers. Check whether or not it makes a difference.

---

