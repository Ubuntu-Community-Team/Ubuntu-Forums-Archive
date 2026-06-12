---
title: "My cpu is always at 95%, is it because of the graphic drivers?"
date: 2017-10-17
forum: New to Ubuntu
---

### Post by mult1ple on 2017-10-17
I just installed Ubuntu, dual boot.
I am really new to the interface but my CPU is always at 95%. I have not installed the graphic drivers, my notebook has a NVIDIA 970m, 16gb RAM and i7 6700.
[ATTACH=CONFIG]277158[/ATTACH]

---

### Post by wildmanne39 on 2017-10-17
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by HermanAB on 2017-10-17
That could be.  Run top or htop and have a look.

---

### Post by Autodave on 2017-10-18
Go to Settings -> Additional Drivers and let Ubuntu tell you which Nvidia driver you need and install it from there.  384.90 looks to be like the one you need according to Nvidia's website.

Do NOT install the driver from Nvidia's site!!!  You can do what I suggested above or you can install from the Software Center or Synaptic.

---

### Post by mult1ple on 2017-10-18
After running top, the information I get is PID 368 root using 95% of the CPU and it is  kworker/0:2. By the fact that I have no idea what is going on, it is really hard for me to try tracking the problem so I am trying to do the maximum research I can.

---

### Post by mastablasta on 2017-10-19
install the binary driver. you are using nouveau which is opensource reverse engineered driver and it might be using CPU instead of GPU to draw the desktop on screen.
your picture is showing that xorg (the graphical desktop interface) is on top.

---

