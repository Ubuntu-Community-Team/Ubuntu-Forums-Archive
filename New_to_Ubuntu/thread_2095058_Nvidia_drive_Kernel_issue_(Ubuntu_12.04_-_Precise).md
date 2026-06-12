---
title: "Nvidia drive Kernel issue (Ubuntu 12.04 - Precise)"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by Danilo11 on 2012-12-15
I installed Ubuntu 12.04 Precise a couple of weeks ago
so far, I really like it, except that my computer keeps on freezing and/or crashing when I'm using either Firefox or Chrome.

I've been trying to fix this problem for at least 2 weeks already and I'm not gonna lie, I'm beginning to think that it's not worthy.

I installed "System load indicator" and I don't see anything "unusual" before the computer crashes.
I've noticed that a lot of times the computer crashes exactly when I'm typing something in Google and Google tries to show results before I'm finished typing.
I ran memtest 1 time and everything was fine. But I'm going to leave it running tonight to see what I get.
I'm using Gnome Classic and the computer seems to be a little better, but sometimes when I'm browsing "Applications" I can see the mouse cursor freeze for 1 second.

This is what I'm seeing in the terminal

> dopoco01@dopoco01-HP-Compaq-dc7700-Convertible-Minitower:~$ uname -a
Linux dopoco01-HP-Compaq-dc7700-Convertible-Minitower 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
> dopoco01@dopoco01-HP-Compaq-dc7700-Convertible-Minitower:~$ sudo lshw -c video
  *-**display UNCLAIMED **    
       description: VGA compatible controller
       product: NV44 [Quadro NVS 285]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f1000000-f1ffffff memory:e8000000-efffffff memory:f2000000-f2ffffff memory:f0000000-f001ffff> dopoco01@dopoco01-HP-Compaq-dc7700-Convertible-Minitower:~$ glxinfo | grep glx
Xlib:  extension "NV-GLX" missing on display ":0.0".
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
> dopoco01@dopoco01-HP-Compaq-dc7700-Convertible-Minitower:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  In  /var/log/Xorg.0.log
> [    25.424] (II) Loading extension GLX
[    25.424] (II) LoadModule: "dri"
[    25.424] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.425] (II) Module dri: vendor="X.Org Foundation"
[    25.425]    compiled for 1.11.3, module version = 1.0.0
[    25.425]    ABI class: X.Org Server Extension, version 6.0
[    25.425] (II) Loading extension XFree86-DRI
[    25.425] (II) LoadModule: "nvidia"
[    25.425] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    25.425] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.425]    compiled for 4.0.2, module version = 1.0.0
[    25.426]    Module class: X.Org Video Driver
[    25.428] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    25.428] (EE) NVIDIA:     system's kernel log for additional error messages.
[    25.428] (II) UnloadModule: "nvidia"
[    25.428] (II) Unloading nvidia
[    25.428] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    25.428] (==) Matched nvidia as autoconfigured driver 0
[    25.428] (==) Matched nouveau as autoconfigured driver 1
[    25.428] (==) Matched nv as autoconfigured driver 2
[    25.428] (==) Matched vesa as autoconfigured driver 3
[    25.428] (==) Matched fbdev as autoconfigured driver 4
[    25.428] (==) Assigned the driver to the xf86ConfigLayout
[    25.428] (II) LoadModule: "nvidia"
[    25.428] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    25.428] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.428]    compiled for 4.0.2, module version = 1.0.0
[    25.428]    Module class: X.Org Video Driver
[    25.428] (II) UnloadModule: "nvidia"
[    25.428] (II) Unloading nvidia
[    25.428] (II) Failed to load module "nvidia" (already loaded, -1217172965)
[    25.428] (II) LoadModule: "nouveau"
[    25.428] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    25.458] (II) Module nouveau: vendor="X.Org Foundation"
[    25.458]    compiled for 1.11.3, module version = 1.0.2
[    25.458]    Module class: X.Org Video Driver
[    25.458]    ABI class: X.Org Video Driver, version 11.0
[    25.458] (II) LoadModule: "nv"
[    25.459] (WW) Warning, couldn't open module nv
[    25.459] (II) UnloadModule: "nv"
[    25.459] (II) Unloading nv
[    25.459] (EE) Failed to load module "nv" (module does not exist, 0)
[    25.459] (II) LoadModule: "vesa"
[    25.459] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.459] (II) Module vesa: vendor="X.Org Foundation"
[    25.459]    compiled for 1.11.3, module version = 2.3.0
[    25.459]    Module class: X.Org Video Driver
[    25.459]    ABI class: X.Org Video Driver, version 11.0
[    25.459] (II) LoadModule: "fbdev"
[    25.459] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.460] (II) Module fbdev: vendor="X.Org Foundation"
[    25.460]    compiled for 1.11.3, module version = 0.4.2
[    25.460]    ABI class: X.Org Video Driver, version 11.0
[    25.460] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    25.460] (II) NOUVEAU driver for NVIDIA chipset families :
[    25.460]    RIVA TNT        (NV04)
[    25.460]    RIVA TNT2       (NV05)
[    25.460]    GeForce 256     (NV10)
[    25.460]    GeForce 2       (NV11, NV15)
[    25.460]    GeForce 4MX     (NV17, NV18)
[    25.460]    GeForce 3       (NV20)
[    25.460]    GeForce 4Ti     (NV25, NV28)
[    25.460]    GeForce FX      (NV3x)
[    25.460]    GeForce 6       (NV4x)
[    25.460]    GeForce 7       (G7x)
[    25.460]    GeForce 8       (G8x)
[    25.460]    GeForce GTX 200 (NVA0)
[    25.460]    GeForce GTX 400 (NVC0)
[    25.460] (II) VESA: driver for VESA chipsets: vesa
[    25.460] (II) FBDEV: driver for framebuffer: fbdev
[    25.460] (++) using VT number 7
In  /var/log/jockey.log

> 2012-12-15 14:49:45,341 DEBUG: nvidia.available: falling back to default
2012-12-15 14:49:45,385 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:49:45,385 DEBUG: KMH enabled: False
2012-12-15 14:49:45,365 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA a$
2012-12-15 14:49:45,385 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module':$
2012-12-15 14:49:45,401 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia$
2012-12-15 14:49:45,401 DEBUG: nvidia_173_updates is not the alternative in use
2012-12-15 14:49:45,385 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonf$
2012-12-15 14:49:45,405 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find mo$


---

### Post by Danilo11 on 2012-12-15
Before that post, I changed the kernel to what it is right now (shown in previous post) and I was able to use the computer for 1 hour without crashing.
Before, it would crash every 5-10 minutes.

I did notice that the "load" in "Indicator multiload" was high.
And the computer didn't freeze and crash like before, it was more like it would in Windows.

I went into  /var/log/jockey.log and this is what I got before I turned the computer off a few minutes later.

> 2012-12-15 14:52:22,476 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module$

2012-12-15 14:52:22,476 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-12-15 14:52:56,484 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:56,485 DEBUG: KMH enabled: False
2012-12-15 14:52:56,504 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:56,504 DEBUG: KMH enabled: False
2012-12-15 14:52:59,552 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current$
2012-12-15 14:52:59,552 DEBUG: nvidia_173 is not the alternative in use
2012-12-15 14:52:59,584 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia$
2012-12-15 14:52:59,584 DEBUG: nvidia_173_updates is not the alternative in use
2012-12-15 14:52:59,619 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:59,620 DEBUG: KMH enabled: False
2012-12-15 14:52:59,639 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:59,639 DEBUG: KMH enabled: False
2012-12-15 14:52:59,679 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nv$
2012-12-15 14:52:59,679 DEBUG: nvidia_current_updates is not the alternative in use
2012-12-15 14:52:59,715 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/n$
2012-12-15 14:52:59,715 DEBUG: nvidia_experimental_304 is not the alternative in use
2012-12-15 14:52:59,758 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:59,758 DEBUG: KMH enabled: False
2012-12-15 14:52:59,776 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:59,776 DEBUG: KMH enabled: False
2012-12-15 14:52:59,826 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current$
2012-12-15 14:52:59,826 DEBUG: nvidia_173 is not the alternative in use
2012-12-15 14:52:59,858 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia$
2012-12-15 14:52:59,859 DEBUG: nvidia_173_updates is not the alternative in use
2012-12-15 14:52:59,888 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:59,889 DEBUG: KMH enabled: False
2012-12-15 14:52:59,911 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf c$
2012-12-15 14:52:59,911 DEBUG: KMH enabled: False
2012-12-15 14:52:59,942 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nv$
2012-12-15 14:52:59,942 DEBUG: nvidia_current_updates is not the alternative in use
2012-12-15 14:52:59,973 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/n$
2012-12-15 14:52:59,973 DEBUG: nvidia_experimental_304 is not the alternative in use
2012-12-15 14:55:08,716 DEBUG: Shutting down

---

### Post by Danilo11 on 2012-12-16
Looks like I might have fixed the problems (I bet there's a 5% chance that I did)

But here's a few of the things I did.

Adjust "swappiness"
[http://scottlinux.com/2010/06/23/adjust-your-swappiness/](http://scottlinux.com/2010/06/23/adjust-your-swappiness/)

Downloaded NVIDIA drivers from advanced search
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

Blacklist other drivers
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Install NVIDIA recommended .run driver
[http://askubuntu.com/questions/18747/how-do-i-install-run-files](http://askubuntu.com/questions/18747/how-do-i-install-run-files)


Forgot to mention... I also changed my kernel to the latest version that I found for the version of my Ubuntu (Precise) that I found in this page
[http://www.unixmen.com/upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint/](http://www.unixmen.com/upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint/)

---

