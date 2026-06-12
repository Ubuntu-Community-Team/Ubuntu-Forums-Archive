---
title: "[SOLVED] How to install again the restricted drivers?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by FotiX on 2008-09-12
Hi, I have an NVIDIA gfx card and I had the restricted drivers installed. I installed recently the newer drivers with EnvyNG, but there are some problems with compiz. How can I go back to the restricted drivers? Thanks a lot.

---

### Post by neurostu on 2008-09-12
You can try removing envy and then install the restricted drivers, but I've never been able to de-envy a computer. In the end I always end up re-installing Ubuntu.
Envy is great if you can get it to work but I've never been able to roll back successfully from envy.

---

### Post by FotiX on 2008-09-12
Thanks, but how can I install them again? From the repos? Which package is it?

---

### Post by Bucky Ball on 2008-09-12
ubuntu-restricted-extras

---

### Post by ntbutler on 2008-09-12
> **FotiX said:**
> Thanks, but how can I install them again? From the repos? Which package is it?

Hi. I am not sure if this helps, (i can't check at the moment because my computer is crashing, similar problem with nvidia...)
I noticed when i installed the restricted drivers a package like nvidia-glx-new. I am sorry i can't be of much help at the moment, but i do remember that there was a package with glx-new in it as one of the main ones, so you could try hunting through synaptic for something like that.

(for more information, you could try running ubuntu off the liveCD quickly and have a look at what the restricted driver was wanting through there, no issues to your current installation...)

---

### Post by perlluver on 2008-09-12
The package is called nvidia-glx-new, or you can go to System>Administration>Hardware Drivers.  As for Envy, there is an option to un install via Envy, just open it up, and click un install Nvidia Driver.

---

### Post by FotiX on 2008-09-12
Yes, it was nvidia-glx-new. I uninstalled the drivers through the envy menu and I downloaded them from synaptic. Thanks for your replies. Problem solved.:)

---

