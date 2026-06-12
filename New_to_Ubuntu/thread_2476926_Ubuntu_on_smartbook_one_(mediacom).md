---
title: "Ubuntu on smartbook one (mediacom)"
date: 2022-07-12
forum: New to Ubuntu
---

### Post by abbazzz on 2022-07-12
Hi I have recently purchased a smartbook one (mediacom) 



I decided to install Ubuntu 20.04.4 lts and keeping windows for dual boot

Once Linux is installed some components do not work like wifi, the sound card and  more

(Initially I had to reinstall windows and it couldn't find the drivers "automatically". Once I downloaded the proprietary drivers from the manufacturer everything was fine)


What procedure should be followed to install proprietary drivers in ubuntu?
Is it possible? 


 Software updates - additional driver does not show any


I tried even Ubuntu 22.04.4 lts but nothing changed

---

### Post by grahammechanical on 2022-07-12
The main component of a Linux distribution is the Linux kernel. Another component is the Linux firmware package which provides hardware drivers. If the hardware in your device is non-standard then it is unlikely that there will be drivers for that hardware unless the manufacturer of the device provides the drivers.

Proprietary software is software whose source code is not available for examination. The manufacturer needs to make available to the Linux developers examples of the hardware and copies of the source code of the Windows drivers and then perhaps the Linux developers can write Linux drivers for that hardware and include it in Linux firmware. Alternatively, the manufacturer can write proprietary Linux drivers and make them available to the developers of Linux distributions. And then Ubuntu Software and Updates>Additional drivers will be able to offer to install it.

Regards

---

### Post by abbazzz on 2022-07-12
Thx a lot for the reply @grahammechanical. 


Well I was hoping fore some workaround

For example in this Linux forum an expert was able to fix  WiFi card  on a Smartbook Mediacom with Linux mint os

[https://forums.linuxmint.com/viewtopic.php?f=65&t=368421&start=20](https://forums.linuxmint.com/viewtopic.php?f=65&t=368421&start=20)


Maybe my hardware is cheap but not so "odd standard", I hope


[https://www.mediacomeurope.it/pc-e-notebook/183/smartbook-one](https://www.mediacomeurope.it/pc-e-notebook/183/smartbook-one)

---

