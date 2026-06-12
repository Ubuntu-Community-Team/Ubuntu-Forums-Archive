---
title: "Suspend works but screen stays blank which nvidia driver works best"
date: 2014-10-07
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-10-07
I have u14.04.1 running on my hp z400 ws. Suspend works but screen remains dark when I press key to recover. I can use reisub sequence to reboot the computer. I suspect nvidia driver problem. I clicked on dash and typed in hardware partitions and used arrow keys to highlight the file and then pressed enter. Every time I'm taken to the wickipedia page for nvidia. How do I open the nvidia driver file? I have a similar problem attempting to other other programs that are installed. What am I doing wrong?

---

### Post by Vladlenin5000 on 2014-10-07
Assuming you a have a standard Ubuntu, then at System Settings > Software&Updates, Additional Drivers tab, what do you see there? What driver version, if any, is selected?

Also, HP Z400 has many different hardware configurations with different graphics cards (at least one ATI/AMD). Which graphics card do you have?

---

### Post by nu2u904 on 2014-10-08
> **Vladlenin5000 said:**
> Assuming you a have a standard Ubuntu, then at System Settings > Software&Updates, Additional Drivers tab, what do you see there? What driver version, if any, is selected?

Also, HP Z400 has many different hardware configurations with different graphics cards (at least one ATI/AMD). Which graphics card do you have?

Thank you. I did this and then selecteded proprietory tested. This not only doesn't work and won't allow my screen to be  unblocked at all. I know u14.04 boots as I can use the reisub sequence to reboot but again with a black screen. Here are my options: From system settings>software updates > aditional drivers.
```

NVIDIA Corporation NV43 [Quadro NVS 440]
This device is using an alternative driver.
X  Using NVIDIA legacy binary driver - version 304.117 from media-304 (proprietory, tested}
O Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
O Using NVIDIA LEGACY BINARY DRIVER - VERSION 304.117 FROM.NVIDIA-304-UPDATES (PROPRIETARY)
O Using NVIDIA legacy binary- version 173.14.39 from nvidia-173 (proprietary)


```

I just down loaded from NVIDIA driver  NVIDIA  - Linux x86 -319.76 28.5 MB dated 11/27/13. I will install it and see if resolves the problem. I'm doing this using live u14.04

---

### Post by nu2u904 on 2014-10-08
> **nu2u904 said:**
> Thank you. I did this and then selecteded proprietory tested. This not only doesn't work and won't allow my screen to be  unblocked at all. I know u14.04 boots as I can use the reisub sequence to reboot but again with a black screen. Here are my options: From system settings>software updates > aditional drivers.
```

NVIDIA Corporation NV43 [Quadro NVS 440]
This device is using an alternative driver.
X  Using NVIDIA legacy binary driver - version 304.117 from media-304 (proprietory, tested}
O Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
O Using NVIDIA LEGACY BINARY DRIVER - VERSION 304.117 FROM.NVIDIA-304-UPDATES (PROPRIETARY)
O Using NVIDIA legacy binary- version 173.14.39 from nvidia-173 (proprietary)


```

I just down loaded from NVIDIA driver  NVIDIA  - Linux x86 -319.76 28.5 MB dated 11/27/13. I will install it and see if resolves the problem. I'm doing this using live u14.04

Does not match GNU, installation failed. I next tried all the  above installs. None could handle any blanking of the screen, i.e. lock screen screensavers or suspend. Only the x.Org x Server would unblank the screen after a reisub reboot or a normal boot. Any suggestions?

---

