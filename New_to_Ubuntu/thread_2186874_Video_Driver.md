---
title: "Video Driver"
date: 2013-11-09
forum: New to Ubuntu
---

### Post by frigioiustefan on 2013-11-09
Hi! I've just started using ubuntu 13.04 alongside my old windows 7. The thing that bothers me is that when I check Graphics in System Settings->Details, it says "Gallium 0.4 on llvmpipe(LLVM 3.2, 256 bits)", and the system feels a bit laggy in some cases. I have a Lenovo y510p with Intel Core i7 Haswell 4700MQ, 8GB RAM , Integrated Graphics Processor Intel HD 4600 and the GPU is NVIDIA Geforce GT750M 2GB. In the section Additional Drivers there is nothing listed and though I tried to install Intel Graphics Driver nothing changed. Moreover, when I play HD videos in Fullscreen mode, I experience a massive lag-small framerate(on VLC I had to set video output to X11 to solve it).
Honestly I don't know what to do anymore, as I already tried installing the driver from nvidia(331.20) and it said it is not compatible with my video card. I can't set another resolution than 1920*1080 and also cannot set brightness.
Do you guys have any idea what to do, as I searched on many forums and didn't find a clear solution to my case?

---

### Post by sandyd on 2013-11-09
> **frigioiustefan said:**
> Hi! I've just started using ubuntu 13.04 alongside my old windows 7. The thing that bothers me is that when I check Graphics in System Settings->Details, it says "Gallium 0.4 on llvmpipe(LLVM 3.2, 256 bits)", and the system feels a bit laggy in some cases. I have a Lenovo y510p with Intel Core i7 Haswell 4700MQ, 8GB RAM , Integrated Graphics Processor Intel HD 4600 and the GPU is NVIDIA Geforce GT750M 2GB. In the section Additional Drivers there is nothing listed and though I tried to install Intel Graphics Driver nothing changed. Moreover, when I play HD videos in Fullscreen mode, I experience a massive lag-small framerate(on VLC I had to set video output to X11 to solve it).
Honestly I don't know what to do anymore, as I already tried installing the driver from nvidia(331.20) and it said it is not compatible with my video card. I can't set another resolution than 1920*1080 and also cannot set brightness.
Do you guys have any idea what to do, as I searched on many forums and didn't find a clear solution to my case?

Do you have switchable graphics?

If so, 
Have you tried installing the bumblebee drivers?
See [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

There is also a bumblebee gui configuration tool (after you install the drivers) that can be installed using the instructions at [http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

Welcome to Ubuntu :)

---

### Post by frigioiustefan on 2013-11-09
I installed bumblebee, but nothing changed. Yet, I couldn't install the bumblebee configuration tool, as i got these errors:
> sudo apt-get updateW: GPG error: [https://download.01.org](https://download.01.org) Ubuntu Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D8847D52F4AAA66


sudo apt-get install bumblebee-config-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bumblebee-config-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  bumblebee-config-gui


E: Package 'bumblebee-config-gtk' has no installation candidate. Gallium is still there.

---

### Post by grahammechanical on 2013-11-09
Gallium is the code name for the Nouveau open source video driver and llvmpipe is a subset of Nouveau for use on graphic cards without video acceleration. It is used as a fallback mode in Ubuntu from 13.04 onwards. So, for some reason you are running on llvmpipe and not full Nouveau or a proprietary video drvier.  And yes the experience is laggy. You need to install either Nouveau or a proprietary video driver. We do that through System Settings>Software and Updates>Additional Drivers tab. The machine needs to be connected to the internet as the driver has to be downloaded.

Regarding Intel Haswell you might find this link interesting.

[http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html](http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html)

Regards

---

### Post by frigioiustefan on 2013-11-09
I have ubuntu and windows on the same computer. I earlier tried to install Intel Graphics Installer but unfortunately it didn't work. Moreover, in the Additional Drivers tab there is absoloutely nothing. So what can I do to install the proprietary driver or at least Nouveau? Thank you.

---

