---
title: "nVidia X Server Settings blank on 20.04.1 LTS fresh install"
date: 2020-08-08
forum: New to Ubuntu
---

### Post by jhemp on 2020-08-08
Hi i just did a fresh install of 20.04.1 LTS standard Ubuntu
on X Server Settings there's just a blank screen.

Nvidia-smi shows:
```
j@greenmachine:~$ nvidia-smi
Sat Aug  8 18:51:17 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.100      Driver Version: 440.100      CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1050    Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   44C    P0    N/A /  N/A |      0MiB /  3020MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```
The about page on settings only shows my onboard graphics and not the GTX 1050.

I have selected the recommended driver, restarted, confirmed i'm on legacy boot etc.

Not sure what steps to take from here.

---

### Post by jhemp on 2020-08-08
Okay so i went into bios settings and turned legacy boot off and also made sure to select secure boot as off, and rebooted.

"About" section now shows the GTX 1050 in there - but still nothing on X Server Settings.

---

### Post by deadflowr on 2020-08-08
My guess is that it's simply defaulting to the on board.
Check if you can toggle gpus in the BIOS.
The Nvidia card would probably be listed as pci-e, which is what most dedicated cards likely show as in the vga/gpu BIOS graphic settings.

---

### Post by Bucky Ball on 2020-08-10
Yea, I have the Ryzen 5 4600H with the Nvidia 1650 ti GPU. Very new hardware, but same combo as you have in this respect; AMD Ryzen ****H CPU/Nvidia GPU. And 20.04.1. I've been trying on and off to get the Nvidia card to work since I got the computer about three weeks ago and installed Xubuntu-core 20.04.

Anyhow, I [installed a newer kernel]("https://ubuntuforums.org/showthread.php?t=2447592&p=13974462&viewfull=1#post13974462") to start with and that got me some of the way. (You may not need, or want, to do this as your processor is a little older than mine, but might help.) Then I [installed a newer GPU driver,]("https://ubuntuforums.org/showthread.php?t=2447592&page=2&p=13974595&viewfull=1#post13974595") nvidia-driver-450, and here we are. A little further on than your good self.

My Nvidia GPU is there, it's seen, but it's not working and I can't seem to get it to. 'Usage' shows 0%. But all else is normal. The results of my nvidia-smi looks pretty much the same as yours, but I DO have Nvidia X Server Settings. When I was using the 440 driver, I was getting a small, blank window when I tried to open Nvidia X Server Settings, possibly similar to what you're getting.

In Nvidia X Server Settings there is an option to set Application Profiles and currently trying to figure out how to do that. Might be the key. I've also seen an option for Prime Profiles on other screen shots, but I don't have that in my Server Settings and not sure why. When I check, Prime seems to be installed on the system. Curious to know the outcome you get after trying the 450 driver, if you choose to.

Hope those links help you get a bit further and let us know how you go. Good luck.

(P.S. The advice to check the BIOS for the card is worth a try and I've read it before, but for me, there is no sign of the GPU in the BIOS anywhere! Strange. Stranger is that the GPU works fine in Windows 10 and is seen there and in Ubuntu 20.04.1.)

---

