---
title: "x server does not start automatically"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by arnav803 on 2013-02-19
hi. I have ubuntu 12.04 installed on my system yesterday i downloaded driver for nvidia ge force 210 from nvidia's website the file  NVIDIA-Linux-x86-310.32.run i opened it command line interface via 'sh' there first i stopped the x server by sudo service stop lightdm and and installation went smoothly but after rebooting the screen would go black(displaying could not write bytes:broken pipe) at log in screen after 2-5 seconds and i have to enter command line interface(by alt+ctrl+f1) and then start the x server sometimes it also says that x server is already running then i have to first stop and then start the x server.I am confused please help.
:confused::KS

---

### Post by Paqman on 2013-02-19
Hi,

On Ubuntu you generally don't install software the same way you would on Windows (by going to the manufacturer's site and downloading an installer).

On Ubuntu the system can install any software you want automatically. Normally you'd go straight to Software Centre and install from there, but graphics drivers are a bit different. Open up Software Sources and go to the drivers tab. Select one of the Nvidia drivers from there (I suggest picking the stable one) and have the system install it.

If you're not able to get into a graphical desktop at all we can tell you how to use the same tool from the command line, but from what you wrote it sounds like you are able to get into the GUI desktop eventually?

---

### Post by arnav803 on 2013-02-19
hi. thanks for your quick reply the problem that i am facing right now is that i dont have a internet connection at present and probably i'll get it in 10-15 days i download the driver in a cyber cafe (from nvidia's website) and brought it home through pendrive and then installed it from there so please tell me how to make this very driver work in ubuntu 12.04.:p

---

