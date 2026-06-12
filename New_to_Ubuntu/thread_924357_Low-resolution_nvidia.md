---
title: "Low-resolution nvidia"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Vadi on 2008-09-19
I used envy to install the 173 nvidia drivers, but then Compiz was acting weirdly, so I decided to revert back to the normal ubuntu drivers. I uninstalled envy via synaptic, and used hardware drivers to enable the normal driver.

But now I'm stuck in low resolution ubuntu, on the "vesa" driver. Hardware drivers is lying to me that nvidia driver is enable and in use (it's not - nvidia settings says it isn't), using envy to install the 9x series drivers did not help either.

I'm out of ideas on what to do now... can anyone help?

---

### Post by northern lights on 2008-09-19
Try running 'nvidia-xconfig'

```
sudo apt-get update && sudo apt-get install nvidia-xconfig && nvidia-xconfig
```

Should that fail, please post the output of```
sudo lshw -C display
```

---

### Post by Vadi on 2008-09-19
It did fail unfortunately.

> vadi@ubuntu-laptop:~$ sudo lshw -C display
[sudo] password for vadi: 
  *-display               
       description: VGA compatible controller
       product: GeForce 8600M GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
vadi@ubuntu-laptop:~$ 


(when I go to nvidia x server settings, it says I'm not using the nvidia driver and I should run "sudo nvidia-settings")

---

### Post by philinux on 2008-09-19
I would uninstall the driver using envy. Then reboot and use xfix. Then use the nvidia-glx-new-envy driver from synaptic.

---

### Post by northern lights on 2008-09-19
> **Vadi said:**
> It did fail unfortunately.

```
vadi@ubuntu-laptop:~$ sudo lshw -C display
[sudo] password for vadi:
*-display
description: VGA compatible controller
product: GeForce 8600M GT
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vga_controller bus_master cap_list
configuration: [COLOR="Red"]driver=nvidia[/COLOR] latency=0 module=nvidia
vadi@ubuntu-laptop:~$ 
```

(when I go to nvidia x server settings, it says I'm not using the nvidia driver and I should run "sudo nvidia-settings")

This is very wicked, as not only the "Hardware Drivers" applet says it's in use, but also the above output.

Honestly, I'm trifled.

What exactly is reported as an error when running ```
gksu nvidia-settings
```Have you tried running 'nvidia-xconfig' as root also? I.e. ```
gksu nvidia-xconfig
```

What happens if you reconfigure X?
For that, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```This will most likely restore resolution, but revert back to vesa. Since your current nvidia driver is somehow screwed anyways, the latter is not so bad though, after all.

[EDIT]
Seen the above post.
Since Phil seems to have experience with envy leftovers, I'd say go that route.
[/EDIT]

---

### Post by Vadi on 2008-09-19
Okay, going phil's way. What is "xfix"?

---

### Post by Vadi on 2008-09-19
I uninstalled the driver with envy, installed nvidia-glx-new-envy, rebooted, and now have the normal resolution. However hardware drivers says the driver is not in use and I cannot launch any opengl games either.

> vadi@ubuntu-laptop:~$ sudo lshw -C display
[sudo] password for vadi: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 8600M GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
vadi@ubuntu-laptop:~$ 


---

### Post by nowshining on 2008-09-19
> **Vadi said:**
> I uninstalled the driver with envy, installed nvidia-glx-new-envy, rebooted, and now have the normal resolution. However hardware drivers says the driver is not in use and I cannot launch any opengl games either.

u need the regular nvidia drivers for those games I believe....as when u remove the nvidia driver from nvidia you also remove the needed files, etc..for those games to run, ie: opengl nvidia drivers only the nvidia driver from the nvidia site has...

---

### Post by gjoellee on 2008-09-19
this should work: [http://www.kshoster.net/index.php?c=tipsandtricks&h=xfix](http://www.kshoster.net/index.php?c=tipsandtricks&h=xfix)

---

### Post by Vadi on 2008-09-19
Above link didn't help, but a bit of googling turned up [this thread]("http://ubuntuforums.org/showthread.php?t=786737") - turns out I needed to boot into the recovery mode. Then the xfix option was available.

---

### Post by gjoellee on 2008-09-19
> **Vadi said:**
> Above link didn't help, but a bit of googling turned up [this thread]("http://ubuntuforums.org/showthread.php?t=786737") - turns out I needed to boot into the recovery mode. Then the xfix option was available.

Ooops, sorry I didn't notice that tha last change had not been uploaded to the internet. It is however now:)

---

### Post by Vadi on 2008-09-19
Nothing is helping. Max I got was a normal resolution, but without desktop effects or games.

---

