---
title: "performance issue with new ubuntu dual boot installation"
date: 2021-08-02
forum: New to Ubuntu
---

### Post by lonchanick on 2021-08-02
Hello everyone.

I have installed ubuntu next to windows on my laptop, I followed all the steps and I took all preventions reagding to the installation but once instalation is completed its tuns out that the OS performance is really really bad (every action in the pc is terribly slow), it takes about 2 minutes just to start (from de beggining until de loggin screen). I atach more information about the PC and the OS versions I have tryed.

PC details:

MANUFACTURER: ASUS (ASUSTeK COMPUTER INC.)
MODEL: ASUS TUF Gaming F15 FX506LI_FX506LI ([https://www.asus.com/es/Laptops/For-Gaming/TUF-Gaming/ASUS-TUF-Gaming-F15/](https://www.asus.com/es/Laptops/For-Gaming/TUF-Gaming/ASUS-TUF-Gaming-F15/))
CPU: Intel(R) Core(TM) i5-10300H CPU @ 2.50GHz, 2496 Mhz
MAIN OS: WINDOWS 10 (Microsoft Windows 10 Home Single Language)
BIOS MODEL: UEFI
RAM MEMORY: 8GB
GPU: NVIDIA GeForce GTX 1650 ti

I have tried installing ubuntu 20.04 LTS and ubuntu 21.04 and I don't really know why the performance of the OS is too bad, I mean in relation with the hardware it should run really well.


I really thanks all you guys in advances for your help!

PD: Excuse my english :| 

Regards!

---

### Post by tea for one on 2021-08-02
> **lonchanick said:**
> 
GPU: NVIDIA GeForce GTX 1650 ti

Have you installed Nvidia drivers for your graphics card?

---

### Post by Impavidus on 2021-08-02
Ubuntu has a utility to find, download and install the drivers automatically, so don't look for them on some website to install them manually. It's just that they can't be installed out of the box for legal reasons.

Is secure boot still on? In that case you may have to set trust somewhere in UEFI to allow booting with the proprietary graphics drivers. I don't know where exactly. If secure boot is off, it should work directly.

---

