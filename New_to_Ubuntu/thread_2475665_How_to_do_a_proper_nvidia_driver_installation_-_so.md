---
title: "How to do a proper nvidia driver installation - so that it consumes low resources whe"
date: 2022-06-03
forum: New to Ubuntu
---

### Post by matadrox on 2022-06-03
Hello! Using the built-in driver installation applet, the system correctly installs driver 390 for my card (nvidia 540M). However, the problem is that the driver seems to run all the time, leading to significant power consumption and increased temperatures.   I can install Bumblebee but only for the nouveau driver, however its performance is quite poor. Generally I don't play much, but I would like everything to be as it should be. So is there any way to make sure that the closed driver is not used while resting? Any information requested - if anything is needed - I will complete. System is Ubuntu 22.04 witch Gnome.

---

### Post by #&amp;thj^% on 2022-06-03
Doesn't prime select work?
When the extra performance is not needed switch them out IE:
```
sudo prime-select intel
```

---

### Post by matadrox on 2022-06-05
After installing the driver, I get a minor resolution, making everything very large and system responsiveness very poor. I went back to using bumblebee with nouveau. It seems to me that my card is simply very old and not suitable

---

### Post by #&amp;thj^% on 2022-06-05
That version driver from Ubuntu is badly supported, >>with 390 driver from Nvidia I think will help you.
That's up to you though. :)

---

### Post by poorguy on 2022-06-05
I believe the last kernel to support Nvidia propriety graphics card drivers for older Nvidia graphics cards is the 5.4 kernel and that may be hit and miss by distro.

I need the 340.108 Nvidia driver although the only distros I seem to be able to successfully install and use the 340.108 Nvidia driver is Linux Lite 5.x and Linux Mint 20.x  which both still use the 5.4 kernel and not the HWE Stack Kernel.

I've kicked Nvidia to the curb and I'll stay with AMD / ATI and Intel which always work OOTB or do for me.

---

### Post by matadrox on 2022-06-07
Indeed on Kernel 5.4 the driver achieves the highest performance. 5.4 LTS is provided by two more distributions based on Arch. Anyway, I reinstalled the system and quite cleanly installed the 390 driver and now prime-select works fine. It's a shame that it's not possible to install a proper driver for bumblebee in Ubuntu, because this one is the most efficient in my case. Thank you all for speaking up.

---

### Post by #&amp;thj^% on 2022-06-07
Good Job! Thanks for including your fix.

---

