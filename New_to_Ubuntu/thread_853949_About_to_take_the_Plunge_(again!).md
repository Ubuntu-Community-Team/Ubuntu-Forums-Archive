---
title: "About to take the Plunge (again!)"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by chris062689 on 2008-07-09
I have a 9600 GT Nvidia card, and last time I tried installing Ubuntu, worked great OOTB, when I installed the nvidia driver, that's when it started giving me tons of problems.  Mostly starting up in safe graphics mode.

Does this latest driver fix these issues?
[http://www.nvidia.com/object/linux_display_amd64_173.14.09.html](http://www.nvidia.com/object/linux_display_amd64_173.14.09.html)

Is it SAFE to use that Xorg Configuration Utility?

---

### Post by ChameleonDave on 2008-07-09
Yes, I believe the latest driver works.

Do a advanced title search for "nvidia 9600" on these fora.  There are several threads on it.

---

### Post by bumanie on 2008-07-09
This may help. [http://adamspotton.com/node/1](http://adamspotton.com/node/1)

---

### Post by WonderStivi on 2008-07-09
You could install the drivers by using EnvyGT. This is a utility that will install drivers that I believe are newer than the ones in repos.

Envy is available in Synaptic.

---

### Post by ChameleonDave on 2008-07-09
> **WonderStivi said:**
> You could install the drivers by using EnvyGT. This is a utility that will install drivers that I believe are newer than the ones in repos.

Envy is available in Synaptic.

You mean EnvyNG.

It is not as new as the drivers downloaded directly from NVidia.com, which I believe he needs.

---

### Post by pedro_orange on 2008-07-09
Nvidia driver installation using restricted drivers should do the trick tbh.

---

### Post by WonderStivi on 2008-07-09
Yes, of course. Thank you for correcting me.

Downloading directly from Nvidia will give the newest drivers, but I'd rather use Envy than just enabling restricted drivers.

---

### Post by chris062689 on 2008-07-09
2) Install the packages for some of the more common development tools if they aren't already: gcc, linux-headers, pkg-config, and xserver-xorg-dev

I can't install linux-headers, it gives me a bunch of listings, which one do I install?  (Ubuntu 8.04.1)
[EDIT Just went ahead and installed the generic one ;)

---

### Post by stchman on 2008-07-09
> **pedro_orange said:**
> Nvidia driver installation using restricted drivers should do the trick tbh.

No nvidia-glx-new for Hardy is 169.12 and that driver does not support the 9xxx series of nvidia cards.

He will have to manually install the drivers gotten from nvidia website.

I am not familiar as to which driver EnvyNG installs.

---

### Post by pedro_orange on 2008-07-10
> **stchman said:**
> No nvidia-glx-new for Hardy is 169.12 and that driver does not support the 9xxx series of nvidia cards.



Ah. My mistake!
Thanks for pointing this out.

---

