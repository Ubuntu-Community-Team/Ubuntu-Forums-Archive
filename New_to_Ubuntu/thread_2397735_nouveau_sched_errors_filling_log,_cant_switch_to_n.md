---
title: "nouveau sched errors filling log, cant switch to nvidia drivers"
date: 2018-08-02
forum: New to Ubuntu
---

### Post by Prawesome on 2018-08-02
I am having trouble with Nouveau. As soon as I suspend and resume my laptop, my log fills up with these errors and these files take up GBs within minutes, I then have to restart my laptop to fix this. I installed Nvidia drivers and the problem was fixed, but had then changed it to my integrated Intel card for better battery. Now I can't open Nvidia settings after running `ubuntu-drivers devices` and it gives me an `No Nvidia drivers loaded` error. 
I blacklisted Nouveau hoping to fix the error but that has not had any effect.

    ```
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
        Subsystem: ASUSTeK Computer Inc. Skylake GT2 [HD Graphics 520]
        Kernel driver in use: i915
        Kernel modules: i915
    01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 950M] (rev a2)
        Subsystem: ASUSTeK Computer Inc. GM107M [GeForce GTX 950M]
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```


lsmod | grep "nvidia" does not return anything. I am not an expert with Ubuntu and I would really appreciate some help over here
I am using Ubuntu 18.04 and I have an integrated Intel GFX card along with a Nvidia GTX 950M

```
     sudo modprobe nvidia
```
returns the following:

        ```
modprobe: ERROR: ../libkmod/libkmod-module.c:832 kmod_module_insert_module() could not find module by name='off'
    modprobe: ERROR: could not insert 'off': Unknown symbol in module, or unknown parameter (see dmesg)
```

---

### Post by Yellow Pasque on 2018-08-03
Try booting with:
```
nouveau.modeset=0
```

If it works, you can make it permanent in /etc/default/grub.

---

### Post by Prawesome on 2018-08-06
That fixed the errors, thanks, but my battery life is still really bad. How can i convert back to Nvidia drivers?

---

