---
title: "Optimizing Nvidia 3D driver"
date: 2005-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by kuleali on 2005-06-07
Before you start open a terminal a type glxgears. Write down your fps.
    
*  Open a Terminal.
    * Check the status of the nvidia driver. Type: cat /proc/driver/nvidia/agp/status
    * Sample Output: 

 Status:            Enabled
 Driver:             AGPGART
 AGP Rate:        4x
 Fast Writes:     Disabled
 SBA:                Disabled

    * To enable 'Fast Writes' and 'SBA' you can try this.
    * Open a Run Button.
    * Type: sudo gedit /etc/modutils/nvidia-kernel-nkc
    * Add this to the end of the file and save: options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=8
    * Modify the above settings for your system.
    * Open a Terminal.
    * Type: sudo update-modules
    * Reboot or unload/load the Nvidia driver and restart X.
    * Sometimes you have to add 'agpgart' and 'via-agp' at the end of /etc/hotplug/blacklist

Check youre fps now, any improvments ?

---

### Post by meldroc on 2005-06-08
[QUOTE=kuleali]Before you start open a terminal a type glxgears. Write down your fps.
    
*  Open a Terminal.
    * Check the status of the nvidia driver. Type: cat /proc/driver/nvidia/agp/status
    * Sample Output: 

 Status:            Enabled
 Driver:             AGPGART
 AGP Rate:        4x
 Fast Writes:     Disabled
 SBA:                Disabled

    * To enable 'Fast Writes' and 'SBA' you can try this.
    * Open a Run Button.
    * Type: sudo gedit /etc/modutils/nvidia-kernel-nkc
    * Add this to the end of the file and save: options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=8
    * Modify the above settings for your system.
    * Open a Terminal.
    * Type: sudo update-modules
    * Reboot or unload/load the Nvidia driver and restart X.
    * Sometimes you have to add 'agpgart' and 'via-agp' at the end of /etc/hotplug/blacklist

Check youre fps now, any improvments ?[/QUOTE]
 Enabling fast writes gave me a small performance boost (SBA was already enabled when I checked.)  Switching from the default 386-compiled kernel to one that's compiled for your specific processor (K7 in my case) also gave me a little more speed.

---

### Post by skoal on 2005-06-08
It's always nice to have information, so thanks...

However, Side Band Addressing and Fast Writes are pretty unstable - always have been since these options were introduced waaaaay back in the 2.x driver versions.  You get a modest 1-2% gain in performance, but at the cost of stability - soft lock ups, random GL hangs, you name it.  Your mileage will vary with these options...

But that's half the fun on Linux, isn't it?

\\//_

---

### Post by jzke on 2005-06-09
How do i

Reboot or unload/load the Nvidia driver and restart X.???

---

### Post by gmc on 2005-06-09
Now this is weird. When I "cat /proc/driver/nvidia/agp/status", I get the following message:

Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

So I tried, "dmesg | grep agp" and get the following:

agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xd0000000

"lsmod agp" shows:

nvidia_agp              7452  1
agpgart                31784  2 nvidia_agp,nvidia

"lsmod nvidia" shows:

nvidia_agp              7452  1
nvidia               3923388  14
agpgart                31784  2 nvidia_agp,nvidia

Now I know the nvidia drivers are being loaded and used, because when 
xorg starts, I see the Nvidia logo screen, so the question is how come I get a status: disabled message from /proc/driver/nvidia/agp/status ?

G.

---

### Post by dtessier on 2005-06-09
[QUOTE=gmc]Now this is weird. When I "cat /proc/driver/nvidia/agp/status", I get the following message:

Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.
[/QUOTE]

I'm guessing that the NvAGP setting in your xorg.conf is set to 1. You want the following line in the "Device" section for your card
```
Option "NvAGP" "3"
```

---

### Post by gmc on 2005-06-10
Hi dtessier,

[QUOTE=dtessier]I'm guessing that the NvAGP setting in your xorg.conf is set to 1. You want the following line in the "Device" section for your card
```
Option "NvAGP" "3"
```[/QUOTE]

Good guess. After a quick review of the Nvidia driver readme file, I noticed that option. Unfortunately there was no NvAGP option in my xorg.conf file. After playing with the option it's there now as you advertised. Very bizaar, with out setting NvAGP it appears to default to option 1. I suspect it's this video card as it's prone to do other weird things.

Thanks for the tip just the same.

G.

---

