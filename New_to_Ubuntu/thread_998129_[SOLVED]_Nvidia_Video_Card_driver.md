---
title: "[SOLVED] Nvidia Video Card driver"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Tom11235 on 2008-11-30
Hi,

I downloaded the driver for the Nvidia GeForce 8800 Ultra from Nvidia's site, and tried using tty to install it by using the following commands:

sudo /etc/init.d/gdm stop
ls
(found nvidia driver)
sudo .NVIDIA-Linux-x86-177.82-pkg1.run (sudo .*file name*)

Then I was to exit after the setup finished. However, once I entered ls and tried the 3rd step, it would say that the command is unrecognized. Could someone tell me how to properly install the driver, or what mistake I am making? Thanks in advance. 

P.S. Should I do this if I have already enabled proprietary drivers? Would it be the same thing?

---

### Post by overdrank on 2008-11-30
> **Tom11235 said:**
> Hi,

I downloaded the driver for the Nvidia GeForce 8800 Ultra from Nvidia's site, and tried using tty to install it by using the following commands:

sudo /etc/init.d/gdm stop
ls
(found nvidia driver)
sudo .NVIDIA-Linux-x86-177.82-pkg1.run (sudo .*file name*)

Then I was to exit after the setup finished. However, once I entered ls and tried the 3rd step, it would say that the command is unrecognized. Could someone tell me how to properly install the driver, or what mistake I am making? Thanks in advance. 

P.S. Should I do this if I have already enabled proprietary drivers? Would it be the same thing?

Hi and please correct me if I am wrong but the command to run the file would be ```
sudo sh NVIDIA-Linux-x86-177.82-pkg1.run
```

---

### Post by Tom11235 on 2008-11-30
Thank you, it does work now.

---

