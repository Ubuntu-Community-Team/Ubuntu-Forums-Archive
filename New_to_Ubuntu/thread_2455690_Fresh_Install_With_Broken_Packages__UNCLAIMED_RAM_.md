---
title: "Fresh Install With Broken Packages / UNCLAIMED RAM memory"
date: 2020-12-25
forum: New to Ubuntu
---

### Post by dragonsway on 2020-12-25
I am on a:

Machine :  Acer Aspire 5 (A5 515-55g).
Processor: Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz
Memory  : 7923MB (5740MB used)
Resolution  : 1920x1080 pixels
OpenGL Renderer : GeForce MX350/PCIe/SSE2 (Nvidia driver 455 open-source)
Gnome-shell version: 3.36.8

I just a completely fresh install and ran all firmware / software updates. Then I ran `sudo lshw -c memory`, which showed

 ```
*-memory UNCLAIMED        
description: RAM memory        
product: Intel Corporation        
vendor: Intel Corporation        
physical id: 14.2        
bus info: pci@0000:00:14.2        
version: 30        
width: 64 bits        
clock: 33MHz (30.3ns)        
capabilities: pm bus_master cap_list        
configuration: latency=0        
resources: iomemory:600-5ff iomemory:600-5ff memory:6013108000-6013109fff memory:601310d000-601310dfff 
```

Then I ran `sudo ubuntu-drivers autoinstall` ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-driver-455 : Depends: nvidia-kernel-source-455 (= 455.38-0ubuntu0.20.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

so I ran `sudo apt install -f`  which could not fix the broken package, but told me to remove "libfprint-2-tod1", so I did.

Under "Software & Updates" I see an Nvidia 455 driver option: [https://postimg.cc/sBHr4BRs](https://postimg.cc/sBHr4BRs)

any suggestion on how to fix these issues before I restore my system?

thx

---

### Post by TheFu on 2020-12-25
```
sudo apt update
sudo apt full-upgrade
reboot
```
are the 1st steps necessary after any install.

Only then try driver updates.

---

### Post by dragonsway on 2020-12-25
I did exactly that and rebooted... I still have the above errors... That is why I posted in this forum...

---

### Post by TheFu on 2020-12-26
> **dragonsway said:**
> I did exactly that and rebooted... I still have the above errors... That is why I posted in this forum...

sorry. I didn't get that from the prior post. people claim to have run all updates when they actually didn't.  Sometimes they had selected 'install updates' as part of the install, but that isn't the same as running those commands.

---

