---
title: "Desktop fails to load, after adding 2nd gpu."
date: 2019-09-25
forum: New to Ubuntu
---

### Post by ender1618 on 2019-09-25
So I am building a multi-gpu ubuntu machine for use in my personal deep learning research. 

Its made up of:
-Deepcool 120mm fan 0.23A RF 120M x5
-Lian Li 120mm fan x2 
-Redux 80 Noctua  NF-R8 redux 1800 PWM
-Asus WS Z390 PRO motherboard 
-Lian Li PC-011 Air case
-EVGA SuperNOVA T2 1600 PSU
-Intel I9-9900K CPU (LGA1151)
-Corsair Vengence RGB Pro 16MB x 4 RAM
-ASUS GeForce RTX 2080 Ti Turbo x2 GPU
-Samsung 970 EVO M.2 1 TB SSD
-HP EX950 M.2 1 TB SSD
-Masterliquid ML360R RGB CPU cooler

The second GPU came in late, so i had setup one of the drives with Ubuntu 18.04, using only one GPU.
Got it booting, setup the nvidia driver, cuda, and tensorflow (with gpu) working.

The second GPU came in and i installed it, and tried to boot Ubuntu (i have the second drive with windows 10 on it), i get the login prompt for the desktop, enter my password, but then the system just hangs withe a purple background and my cursor (not able to move it any more). 

I can boot Ubuntu in safe mode, no GUI, and can run comands there.

Running nvidia-smi on the machine shows both of the GPUs.

Btw, I am an Ubuntu newbie.

Anyone have a clue as to what the issue might be?

If i boot to win 10, everything is fine, i can see the second gpu fine.

Thanks,
-Ryan

---

### Post by oldrocker99 on 2019-09-26
It sounds like installing with a single GPU and then adding a second one is your problem, because the UI is confused. Simply reinstall. You **certainly** are not the first Linux user to reinstall the system.:)

---

