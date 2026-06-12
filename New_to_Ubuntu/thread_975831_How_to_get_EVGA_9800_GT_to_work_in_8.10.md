---
title: "How to get EVGA 9800 GT to work in 8.10"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by ctothebizza on 2008-11-08
I just installed a new 9800GT in my computer and Ubuntu does not show it in the restricted drivers.  Is there a way that I can install the drivers manually?

---

### Post by Skripka on 2008-11-08
Dd you download the driver via Synaptic?  Ibex loaded at native resolution, and driver 177.80 installed through Synaptic and activated automagically.

---

### Post by ctothebizza on 2008-11-08
I'm not sure how to do that....how do I install the driver?

---

### Post by Haluci on 2008-11-08
> **ctothebizza said:**
> I'm not sure how to do that....how do I install the driver?

If you have no video card problems, chances are that it has already been installed.

---

### Post by Skripka on 2008-11-08
> **ctothebizza said:**
> I'm not sure how to do that....how do I install the driver?

Get thee to Add/Remove programs (or Synaptic for that matter)...you'll be wanting Nvidia-Settings, as well as the Nvidia driver.  Check "Hardware Drivers"-and see what is listed, in Ibex if a driver isn't listed these and "activated", odds are it isn't installed....

---

### Post by pgorillaman on 2008-11-08
I have the same card. Here is what I did to fix it.

```
sudo apt-get install nvidia-glx-177
```

```
sudo apt-get install nvidia-settings
```
This was already installed on my system.

Reboot.

Go to System->Administration->Hardware Drivers and select the nvidia driver (177).

Reboot.

Then run:
```
gksudo nvidia-settings
```
and remember to save the xorg.conf. 

If it doesn't save, manually move your xorg.conf to xorg.conf.bak and try to write it again.

---

