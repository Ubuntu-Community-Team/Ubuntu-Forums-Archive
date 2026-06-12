---
title: "Can't use nouveau"
date: 2024-07-31
forum: New to Ubuntu
---

### Post by maketopsite on 2024-07-31
```
root@maketopsite:~# init 3
root@maketopsite:~# modprobe -rv nvidia_uvm
...
root@maketopsite:~# modprobe -rv nvidia
...
root@maketopsite:~# modprobe -rv nvidia_drm
...

root@maketopsite:~# lsmod | grep nvid
root@maketopsite:~# 
root@maketopsite:~# 

root@maketopsite:~# modprobe -v nouveau
modprobe: ERROR: ../libkmod/libkmod-module.c:838 kmod_module_insert_module() could not find module by name='off'
modprobe: ERROR: could not insert 'off': Unknown symbol in module, or unknown parameter (see dmesg)
root@maketopsite:~#
```

after reboot:
nvidia kernel modules were loaded after booting with
```
ro splash=verbose modprobe.blacklist=nvidia modprobe.blacklist=nvidiafb
```
kernel boot parameters.

Ubuntu 20.04 LTS, Optimus laptop. Do I please need to remove nvidia drivers (as suggested here [https://askubuntu.com/questions/1268765/modprobe-error-libkmod-libkmod-module-c838-kmod-module-insert-module-cou](https://askubuntu.com/questions/1268765/modprobe-error-libkmod-libkmod-module-c838-kmod-module-insert-module-cou)) ?

---

### Post by grahammechanical on 2024-07-31
It is my understanding that if we have installed proprietary video drivers then Ubuntu will load using those proprietary video drivers. If we remove the proprietary video driver then Ubuntu will load using an open source video driver. This will be Nouveau if the video adapter is Nvidia.

Software & Updates>Additional Drivers tab is where we can disable a proprietary video driver. Then a reboot will load with the open source video driver.

When installing Ubuntu if we tick to install third party software then a proprietary video driver is also installed. If we do not tick to install third party software we will not have a proprietary video driver installed. But we can install a proprietary video driver through Software & Updates>Additional Drivers tab. We need to be connected to the internet to allow the utility to search for a selection of proprietary video drivers.

You mention Nvidia Optimus. This has long caused problems with users being unable to switch between the Nvidia video adapter and the Intel video adapter. I am unaware of the latest solutions.

[https://askubuntu.com/questions/1232211/nvidia-optimus-on-20-04-switching-to-intel-gpu-works-on-ubuntu-mate-but-not-on](https://askubuntu.com/questions/1232211/nvidia-optimus-on-20-04-switching-to-intel-gpu-works-on-ubuntu-mate-but-not-on)

Regards

---

### Post by maketopsite on 2024-08-27
> **grahammechanical said:**
> It is my understanding that if we have installed proprietary video drivers then Ubuntu will load using those proprietary video drivers. If we remove the proprietary video driver then Ubuntu will load using an open source video driver. This will be Nouveau if the video adapter is Nvidia.

Software & Updates>Additional Drivers tab is where we can disable a proprietary video driver. Then a reboot will load with the open source video driver.

When installing Ubuntu if we tick to install third party software then a proprietary video driver is also installed. If we do not tick to install third party software we will not have a proprietary video driver installed. But we can install a proprietary video driver through Software & Updates>Additional Drivers tab. We need to be connected to the internet to allow the utility to search for a selection of proprietary video drivers.

You mention Nvidia Optimus. This has long caused problems with users being unable to switch between the Nvidia video adapter and the Intel video adapter. I am unaware of the latest solutions.

[https://askubuntu.com/questions/1232211/nvidia-optimus-on-20-04-switching-to-intel-gpu-works-on-ubuntu-mate-but-not-on](https://askubuntu.com/questions/1232211/nvidia-optimus-on-20-04-switching-to-intel-gpu-works-on-ubuntu-mate-but-not-on)

Regards

Thank you.

---

