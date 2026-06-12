---
title: "Failed to load nvidia module"
date: 2011-07-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-07-14
For a few days my desktop environment (LXDE) doesn't start anymore. I tried GDM as login manager instead of LXDM but this hasn't helped. The Xorg.0.log says the following:

```
[    25.199] (II) LoadModule: "nvidia"
[    25.199] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    25.399] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.427] 	compiled for 4.0.2, module version = 1.0.0
[    25.427] 	Module class: X.Org Video Driver
[    25.517] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    25.518] (EE) NVIDIA:     system's kernel log for additional error messages.
[    25.518] (II) UnloadModule: "nvidia"
[    25.518] (II) Unloading nvidia
[    25.518] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    25.518] (EE) No drivers available.
```

Maybe it has something to do with the updates in the last days. Has somebody else this problem too? Does anyone know how to fix this? The xorg.conf exists because of nvidia-xconfig --no-logo and the nouveau drivers are working. I tried reinstalling nvidia-current but this hasn't helped.

---

### Post by cariboo on 2011-07-14
Does /var/log/kern.log tell you anything, like the output asks?

---

### Post by Sworddragon on 2011-07-14
I have before this all deleted the content of /var/log and made a reboot to exclude unnecessary information. I got only this error and a kern.log don't exist. There is a lxdm.log but it shows only some information from Xorg.0.log.

---

### Post by Bowmore on 2011-07-14
Have you tried to reinstall (remove+install+reboot) the nvidia driver?

---

### Post by Sworddragon on 2011-07-14
Yes I have tried this too. I purged even all dependencies and created a new xorg.conf with nvidia-xconfig --no-logo but this hasn't helped.

---

### Post by cariboo on 2011-07-14
> **Sworddragon said:**
> I have before this all deleted the content of /var/log and made a reboot to exclude unnecessary information. I got only this error and a kern.log don't exist. There is a lxdm.log but it shows only some information from Xorg.0.log.

I seems that you have a broken system, without all the log files, it's pretty hard to help, if you can't show us the output of a log file. If you recreate the kern.log file does the system write to it?

```
sudo touch /var/log/kern.log
```

---

### Post by PhantmKllr on 2011-07-14
> **Sworddragon said:**
> For a few days my desktop environment (LXDE) doesn't start anymore. I tried GDM as login manager instead of LXDM but this hasn't helped. The Xorg.0.log says the following:

```
[    25.199] (II) LoadModule: "nvidia"
[    25.199] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    25.399] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.427] 	compiled for 4.0.2, module version = 1.0.0
[    25.427] 	Module class: X.Org Video Driver
[    25.517] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    25.518] (EE) NVIDIA:     system's kernel log for additional error messages.
[    25.518] (II) UnloadModule: "nvidia"
[    25.518] (II) Unloading nvidia
[    25.518] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    25.518] (EE) No drivers available.
```

Maybe it has something to do with the updates in the last days. Has somebody else this problem too? Does anyone know how to fix this? The xorg.conf exists because of nvidia-xconfig --no-logo and the nouveau drivers are working. I tried reinstalling nvidia-current but this hasn't helped.

I'm having a similar problem.

A few hours ago, I just finished upgrading to 11.10 from 11.04.

When I reach the (LightDM) login prompt, clicking on my name causes the screen to clear, after which the only thing visible on screen is the desktop background. The only way to login is to click on "Other" at the login prompt, and manually type in my user name and password.

After login, I am re-directed to Unity 2D, and a dialog box appears that reads "The program 'unity-compatibility-checker' has quit unexpectedly" (or something like that).

At this point, I uninstall the Nvidia drivers (using Jockey GTK), and restart my computer. LightDM still doesn't work correctly, and after login, I am offered the fully accelerated Unity interface. The weird thing is that I'm still getting the same performance that I would be getting with the proprietary drivers. This lead me to believe that the Nvidia driver was still loaded in the kernel, but according to 'lsmod', it wasn't.

Right now, I think that I'm using the Nouveau driver, but I don't remember Unity running under it. Has it improved that much?

Computer specs are in the sig.

---

### Post by cariboo on 2011-07-14
For me the nvidia drivers do load, but I have the same problem as PhantmKllr, starting in recovery mode and logging in at the prompt, then typing:

```
startx
```

gets me to a running gnome-shell

> lsmod | grep nvidia
nvidia              11989567  40 

---

### Post by vhaarr on 2011-07-14
I am having the same problem after my last reboot; when I try to manually modprobe the nvidia driver, this is what I get:

> $ sudo modprobe nvidia-current
[sudo] password for XXXX: 
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-5-generic/updates/dkms/nvidia-current.ko): No such device

So apparently now after the udev upgrades and /run etc, perhaps the nvidia module can't find the device, and it falls back to nouveau then?

---

### Post by PhantmKllr on 2011-07-14
Plus, another possibly related thing.

After the Nvidia drivers are uninstalled, and I login to unity, I get this message: "The program 'lightdm-example-greeter-gtk' has crashed unexpectedly".

Is this all just a side effect of the keyboard issue fix?

---

### Post by Sworddragon on 2011-07-14
> **cariboo907 said:**
> I seems that you have a broken system, without all the log files, it's pretty hard to help, if you can't show us the output of a log file. If you recreate the kern.log file does the system write to it?

```
sudo touch /var/log/kern.log
```

No it doesn't. Maybe there is no application that wants to write to this file (it is not the same as dmesg or?).


> **vhaarr said:**
> I am having the same problem after my last reboot; when I try to manually modprobe the nvidia driver, this is what I get:

> $ sudo modprobe nvidia-current
[sudo] password for XXXX:
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-5-generic/updates/dkms/nvidia-current.ko): No such device

So apparently now after the udev upgrades and /run etc, perhaps the nvidia module can't find the device, and it falls back to nouveau then?

I tried this some hours ago before and got the same error.

---

### Post by cariboo on 2011-07-14
The log files are part of every Linux distribution.

Does the nvidia module get built, when you install it? Open a terminal and try:

```
sudo apt-get --reinstall nvidia-current
```

and watch the output to see if dkms is actually building the module.

To manually install the module:

```
sudo modprobe nvidia
```

nvidia-current is just the name of the package.

---

### Post by vhaarr on 2011-07-14
I really don't understand what's going on here.
Before this I completely reinstalled the nvidia module and DKMS gives no errors. The log file in /var/lib/dkms/nvidia-current/275.09.07/3.0.0-5-generic/x86_64/log is "clean", no compiler errors and ends with

>   ld -r -m elf_x86_64 -T /usr/src/linux-headers-3.0.0-5-generic/scripts/module-common.lds --build-id  -o /var/lib/dkms/nvidia-current/275.09.07/build/nvidia.ko /var/lib/dkms/nvidia-current/275.09.07/build/nvidia.o /var/lib/dkms/nvidia-current/275.09.07/build/nvidia.mod.o
NVIDIA: left KBUILD
So 'ld' worked fine and the module is built, right?

> $ sudo modprobe nvidia
FATAL: Module nvidia not found.

> $ locate nvidia | grep lib
/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so
/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1
/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1_lib32
/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so_lib32
/lib/nvidia-current
/lib/modules/3.0-3-generic/kernel/drivers/video/nvidia
/lib/modules/3.0-3-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.0-3-generic/updates/dkms/nvidia-current.ko
/lib/modules/3.0.0-4-generic/kernel/drivers/video/nvidia
/lib/modules/3.0.0-4-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.0.0-4-generic/updates/dkms/nvidia-current.ko
/lib/modules/3.0.0-5-generic/kernel/drivers/video/nvidia
/lib/modules/3.0.0-5-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.0.0-5-generic/updates/dkms/nvidia-current.ko
/lib/nvidia-current/modprobe.conf
/usr/lib/libvdpau_nvidia.so
/usr/lib/nvidia
/usr/lib/nvidia-current
/usr/lib/directfb-1.2-9/gfxdrivers/libdirectfb_nvidia.so
/usr/lib/nvidia-current/XvMCConfig
/usr/lib/nvidia-current/alt_ld.so.conf
/usr/lib/nvidia-current/bin
/usr/lib/nvidia-current/ld.so.conf
/usr/lib/nvidia-current/libGL.so
/usr/lib/nvidia-current/libGL.so.1
/usr/lib/nvidia-current/libGL.so.275.09.07
/usr/lib/nvidia-current/libOpenCL.so
/usr/lib/nvidia-current/libOpenCL.so.1
/usr/lib/nvidia-current/libOpenCL.so.1.0
/usr/lib/nvidia-current/libOpenCL.so.1.0.0
/usr/lib/nvidia-current/libXvMCNVIDIA.a
/usr/lib/nvidia-current/libXvMCNVIDIA.so
/usr/lib/nvidia-current/libXvMCNVIDIA.so.1
/usr/lib/nvidia-current/libXvMCNVIDIA.so.275.09.07
/usr/lib/nvidia-current/libXvMCNVIDIA_dynamic.so.1
/usr/lib/nvidia-current/libcuda.so
/usr/lib/nvidia-current/libcuda.so.1
/usr/lib/nvidia-current/libcuda.so.275.09.07
/usr/lib/nvidia-current/libnvcuvid.so
/usr/lib/nvidia-current/libnvcuvid.so.1
/usr/lib/nvidia-current/libnvcuvid.so.275.09.07
/usr/lib/nvidia-current/libnvidia-cfg.so
/usr/lib/nvidia-current/libnvidia-cfg.so.1
/usr/lib/nvidia-current/libnvidia-cfg.so.275.09.07
/usr/lib/nvidia-current/libnvidia-compiler.so
/usr/lib/nvidia-current/libnvidia-compiler.so.1
/usr/lib/nvidia-current/libnvidia-compiler.so.275.09.07
/usr/lib/nvidia-current/libnvidia-glcore.so.275.09.07
/usr/lib/nvidia-current/libnvidia-ml.so
/usr/lib/nvidia-current/libnvidia-ml.so.1
/usr/lib/nvidia-current/libnvidia-ml.so.275.09.07
/usr/lib/nvidia-current/libnvidia-tls.so.275.09.07
/usr/lib/nvidia-current/libnvidia-wfb.so.1
/usr/lib/nvidia-current/libnvidia-wfb.so.275.09.07
/usr/lib/nvidia-current/modprobe.conf
/usr/lib/nvidia-current/tls
/usr/lib/nvidia-current/vdpau
/usr/lib/nvidia-current/xorg
/usr/lib/nvidia-current/bin/nvidia-bug-report.sh
/usr/lib/nvidia-current/bin/nvidia-smi
/usr/lib/nvidia-current/bin/nvidia-xconfig
/usr/lib/nvidia-current/tls/libnvidia-tls.so.275.09.07
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.1
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.275.09.07
/usr/lib/nvidia-current/xorg/libglx.so
/usr/lib/nvidia-current/xorg/libglx.so.275.09.07
/usr/lib/nvidia-current/xorg/nvidia_drv.so
/usr/lib/vdpau/libvdpau_nvidia.so.1
/usr/lib/xorg/modules/drivers/nvidia_drv.so
/usr/lib32/libvdpau_nvidia.so
/usr/lib32/nvidia-current
/usr/lib32/directfb-1.2-9/gfxdrivers/libdirectfb_nvidia.so
/usr/lib32/nvidia-current/libGL.la
/usr/lib32/nvidia-current/libGL.so
/usr/lib32/nvidia-current/libGL.so.1
/usr/lib32/nvidia-current/libGL.so.275.09.07
/usr/lib32/nvidia-current/libOpenCL.so
/usr/lib32/nvidia-current/libOpenCL.so.1
/usr/lib32/nvidia-current/libOpenCL.so.1.0
/usr/lib32/nvidia-current/libOpenCL.so.1.0.0
/usr/lib32/nvidia-current/libXvMCNVIDIA.so
/usr/lib32/nvidia-current/libXvMCNVIDIA.so.1
/usr/lib32/nvidia-current/libXvMCNVIDIA.so.275.09.07
/usr/lib32/nvidia-current/libXvMCNVIDIA_dynamic.so.1
/usr/lib32/nvidia-current/libcuda.so
/usr/lib32/nvidia-current/libcuda.so.1
/usr/lib32/nvidia-current/libcuda.so.275.09.07
/usr/lib32/nvidia-current/libnvcuvid.so
/usr/lib32/nvidia-current/libnvcuvid.so.1
/usr/lib32/nvidia-current/libnvcuvid.so.275.09.07
/usr/lib32/nvidia-current/libnvidia-cfg.so
/usr/lib32/nvidia-current/libnvidia-cfg.so.1
/usr/lib32/nvidia-current/libnvidia-cfg.so.275.09.07
/usr/lib32/nvidia-current/libnvidia-compiler.so
/usr/lib32/nvidia-current/libnvidia-compiler.so.1
/usr/lib32/nvidia-current/libnvidia-compiler.so.275.09.07
/usr/lib32/nvidia-current/libnvidia-glcore.so.275.09.07
/usr/lib32/nvidia-current/libnvidia-ml.so
/usr/lib32/nvidia-current/libnvidia-ml.so.1
/usr/lib32/nvidia-current/libnvidia-ml.so.275.09.07
/usr/lib32/nvidia-current/libnvidia-tls.so.275.09.07
/usr/lib32/nvidia-current/libnvidia-wfb.so.1
/usr/lib32/nvidia-current/libnvidia-wfb.so.275.09.07
/usr/lib32/nvidia-current/tls
/usr/lib32/nvidia-current/vdpau
/usr/lib32/nvidia-current/tls/libnvidia-tls.so.275.09.07
/usr/lib32/nvidia-current/vdpau/libvdpau.so.275.09.07
/usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so
/usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1
/usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.275.09.07
/usr/lib32/nvidia-current/vdpau/libvdpau_trace.so.275.09.07
/usr/lib32/vdpau/libvdpau_nvidia.so.1
/var/lib/dkms/nvidia-current
/var/lib/dkms/nvidia-current/275.09.07
/var/lib/dkms/nvidia-current/kernel-3.0-3-generic-x86_64
/var/lib/dkms/nvidia-current/kernel-3.0.0-4-generic-x86_64
/var/lib/dkms/nvidia-current/kernel-3.0.0-5-generic-x86_64
/var/lib/dkms/nvidia-current/275.09.07/3.0-3-generic
/var/lib/dkms/nvidia-current/275.09.07/3.0.0-4-generic
/var/lib/dkms/nvidia-current/275.09.07/3.0.0-5-generic
/var/lib/dkms/nvidia-current/275.09.07/build
/var/lib/dkms/nvidia-current/275.09.07/source
/var/lib/dkms/nvidia-current/275.09.07/3.0.0-5-generic/x86_64
/var/lib/dkms/nvidia-current/275.09.07/3.0.0-5-generic/x86_64/log
/var/lib/dkms/nvidia-current/275.09.07/3.0.0-5-generic/x86_64/module
/var/lib/dkms/nvidia-current/275.09.07/3.0.0-5-generic/x86_64/log/make.log
/var/lib/dkms/nvidia-current/275.09.07/3.0.0-5-generic/x86_64/module/nvidia-current.ko
/var/lib/dkms/nvidia-current/275.09.07/build/.nv-chrdev.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv-cray.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv-i2c.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv-mlock.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv-procfs.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv-usermap.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv-vm.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nv_gvi.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nvacpi.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nvidia.mod.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.nvidia.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.os-agp.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.os-interface.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.os-registry.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.os-smp.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/.os-usermap.o.cmd
/var/lib/dkms/nvidia-current/275.09.07/build/Makefile.kbuild
/var/lib/dkms/nvidia-current/275.09.07/build/Makefile.nvidia
/var/lib/dkms/nvidia-current/275.09.07/build/Module.symvers
/var/lib/dkms/nvidia-current/275.09.07/build/README.template
/var/lib/dkms/nvidia-current/275.09.07/build/conftest.sh
/var/lib/dkms/nvidia-current/275.09.07/build/cpuopsys.h
/var/lib/dkms/nvidia-current/275.09.07/build/dkms.conf
/var/lib/dkms/nvidia-current/275.09.07/build/g_nvreadme.h
/var/lib/dkms/nvidia-current/275.09.07/build/gcc-version-check.c
/var/lib/dkms/nvidia-current/275.09.07/build/makefile
/var/lib/dkms/nvidia-current/275.09.07/build/modules.order
/var/lib/dkms/nvidia-current/275.09.07/build/nv-chrdev.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv-cray.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv-i2c.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv-kernel.o
/var/lib/dkms/nvidia-current/275.09.07/build/nv-linux.h
/var/lib/dkms/nvidia-current/275.09.07/build/nv-memdbg.h
/var/lib/dkms/nvidia-current/275.09.07/build/nv-misc.h
/var/lib/dkms/nvidia-current/275.09.07/build/nv-mlock.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv-procfs.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv-reg.h
/var/lib/dkms/nvidia-current/275.09.07/build/nv-usermap.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv-vm.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv-vm.h
/var/lib/dkms/nvidia-current/275.09.07/build/nv.c
/var/lib/dkms/nvidia-current/275.09.07/build/nv.h
/var/lib/dkms/nvidia-current/275.09.07/build/nv_gvi.c
/var/lib/dkms/nvidia-current/275.09.07/build/nvacpi.c
/var/lib/dkms/nvidia-current/275.09.07/build/nverror.h
/var/lib/dkms/nvidia-current/275.09.07/build/nvidia.ko
/var/lib/dkms/nvidia-current/275.09.07/build/nvidia.mod.c
/var/lib/dkms/nvidia-current/275.09.07/build/nvidia.o
/var/lib/dkms/nvidia-current/275.09.07/build/nvtypes.h
/var/lib/dkms/nvidia-current/275.09.07/build/os-agp.c
/var/lib/dkms/nvidia-current/275.09.07/build/os-agp.h
/var/lib/dkms/nvidia-current/275.09.07/build/os-interface.c
/var/lib/dkms/nvidia-current/275.09.07/build/os-interface.h
/var/lib/dkms/nvidia-current/275.09.07/build/os-registry.c
/var/lib/dkms/nvidia-current/275.09.07/build/os-smp.c
/var/lib/dkms/nvidia-current/275.09.07/build/os-usermap.c
/var/lib/dkms/nvidia-current/275.09.07/build/patches
/var/lib/dkms/nvidia-current/275.09.07/build/rmil.h
/var/lib/dkms/nvidia-current/275.09.07/build/rmretval.h
/var/lib/dkms/nvidia-current/275.09.07/build/xapi-sdk.h
/var/lib/dkms/nvidia-current/275.09.07/build/patches/buildfix_kernel_3.0.patch
/var/lib/dpkg/info/nvidia-current-dev.list
/var/lib/dpkg/info/nvidia-current-dev.md5sums
/var/lib/dpkg/info/nvidia-current-dev.preinst
/var/lib/dpkg/info/nvidia-current.conffiles
/var/lib/dpkg/info/nvidia-current.list
/var/lib/dpkg/info/nvidia-current.md5sums
/var/lib/dpkg/info/nvidia-current.postinst
/var/lib/dpkg/info/nvidia-current.postrm
/var/lib/dpkg/info/nvidia-current.preinst
/var/lib/dpkg/info/nvidia-current.prerm
/var/lib/dpkg/info/nvidia-current.shlibs
/var/lib/dpkg/info/nvidia-settings.list
/var/lib/dpkg/info/nvidia-settings.md5sums
/var/lib/update-rc.d/nvidia-kernel

---

### Post by Sworddragon on 2011-07-14
> **cariboo907 said:**
> Does the nvidia module get built, when you install it? Open a terminal and try:

```
sudo apt-get --reinstall nvidia-current
```

and watch the output to see if dkms is actually building the module.

To manually install the module:

```
sudo modprobe nvidia
```

nvidia-current is just the name of the package.

This is the output for both commands:

```
sworddragon@ubuntu:~$ sudo apt-get install nvidia-current --reinstall
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
0 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 51,9 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Hole:1 http://de.archive.ubuntu.com/ubuntu/ oneiric/restricted nvidia-current amd64 275.09.07-0ubuntu4 [51,9 MB]
Es wurden 51,9 MB in 40 s geholt (1.271 kB/s)                                                                                                                                          
debconf: delaying package configuration, since apt-utils is not installed
(Lese Datenbank ... 85984 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von nvidia-current 275.09.07-0ubuntu4 (durch .../nvidia-current_275.09.07-0ubuntu4_amd64.deb) ...
Removing all DKMS Modules
Done.
Ersatz für nvidia-current wird entpackt ...
Trigger für man-db werden verarbeitet ...
nvidia-current (275.09.07-0ubuntu4) wird eingerichtet ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-275.09.07 DKMS files...
Building only for 3.0.0-5-generic
Building for architecture x86_64
Building initial module for 3.0.0-5-generic
Done.

nvidia-current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-5-generic/updates/dkms/

depmod....

DKMS: install Completed.
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.0.0-5-generic
W: Possible missing firmware /lib/firmware/nouveau/fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409c for module nouveau
sworddragon@ubuntu:~$ sudo modprobe nvidia
FATAL: Module nvidia not found.
```

---

### Post by vhaarr on 2011-07-14
> $ sudo dkms install -m nvidia-current -v 275.09.07 -k 3.0.0-5-generic 
Module nvidia-current/275.09.07 already installed on kernel 3.0.0-5-generic/x86_64
But modprobe says it's not? :(

---

### Post by PhantmKllr on 2011-07-14
> **cariboo907 said:**
> 
Does the nvidia module get built, when you install it? Open a terminal and try:

```

sudo apt-get --reinstall nvidia-current

```

I went ahead and ran this, and all appears well. Here's the output:
```

Selecting previously deselected package nvidia-current.
(Reading database ... 143001 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_275.09.07-0ubuntu4_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_275.09.07-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (275.09.07-0ubuntu4) ...
Loading new nvidia-current-275.09.07 DKMS files...
Building only for 3.0.0-5-generic
Building for architecture x86_64
Building initial module for 3.0.0-5-generic
Done.

nvidia-current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-5-generic/updates/dkms/

depmod....

DKMS: install Completed.
Setting up nvidia-settings (275.09.07-0ubuntu1) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...

```

Gonna restart the computer now...

---

### Post by vhaarr on 2011-07-14
> [    8.547549] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[    8.547551] NVRM: This can occur when a driver such as nouveau, rivafb,
[    8.547552] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
[    8.547553] NVRM: the NVIDIA device(s).
[    8.547554] NVRM: Try unloading the conflicting kernel module (and/or
[    8.547555] NVRM: reconfigure your kernel without the conflicting
[    8.547556] NVRM: driver(s)), then try loading the NVIDIA kernel module
[    8.547557] NVRM: again.
[    8.547558] NVRM: No NVIDIA graphics adapter probed!

That's from syslog.

---

### Post by PhantmKllr on 2011-07-14
> **vhaarr said:**
> That's from syslog.

Alright, this is weird.

The Nvidia driver appeared to install successfully, however, I think I'm still using Nouveau.

Running "nvidia-settings" brings up a dialog box that states: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Running "sudo modprobe nvidia" gets the same result as Sworddragon: "FATAL: Module nvidia not found."

---

### Post by jamlam on 2011-07-15
I had this exact same issue yesterday. The reason you see the no such device messages from the Nvidia driver is that Nouveau has already loaded and taken over the Nvidia card, so the binary driver can't get at it. The Nouveau driver is blacklisted by the file /etc/modprobe.d/nvidia-graphics-driver.conf but a recent update seems to have stopped it working. 

To fix it I added the line 

```
blacklist nouveau
```

to the file /etc/modprobe.d/blacklist.conf

This has stopped the nouveau module loading and lets the Nvidia driver work properly on boot again.

---

### Post by vhaarr on 2011-07-15
> **jamlam said:**
> To fix it I added the line 
```
blacklist nouveau
```
to the file /etc/modprobe.d/blacklist.conf

No dice here, still the same problem.
With that change, however, the syslog no longer mentions the stuff I posted above.

Everything else remains the same.

---

### Post by jbicha on 2011-07-15
> **jamlam said:**
> 
```
blacklist nouveau
```to the file /etc/modprobe.d/blacklist.conf

This has stopped the nouveau module loading and lets the Nvidia driver work properly on boot again.

Your problem is different than the one I have. I went so far as to uninstall xserver-xorg-video-nouveau but I still get the "module-specific error, 0" message.

---

### Post by vhaarr on 2011-07-15
Okay so I tried updating the initramfs after changing /etc/modprobe.d/blacklist.conf, and here's the output with unrelevant information snipped out (..):

> $ sudo update-initramfs -u -v
[sudo] password for XXX: 
Available versions:  3.0.0-5-generic 2.6.35-23-generic
Keeping /boot/initrd.img-3.0.0-5-generic.dpkg-bak
update-initramfs: Generating /boot/initrd.img-3.0.0-5-generic
..
Copying module directory kernel/drivers/net
(excluding appletalk arcnet bonding can hamradio irda pcmcia tokenring usb wan wimax wireless)
..
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/x86_64-linux-gnu/libext2fs.so.2
Adding library /lib/x86_64-linux-gnu/libcom_err.so.2
Adding library /lib/x86_64-linux-gnu/libe2p.so.2
Calling hook framebuffer
Copying module directory kernel/drivers/char/agp
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/char/agp/sis-agp.ko
Copying module directory kernel/drivers/gpu
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/drm.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/i810/i810.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/savage/savage.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/drm_kms_helper.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/i2c/ch7006.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/i2c/sil164.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/tdfx/tdfx.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/r128/r128.ko
Adding binary /lib/firmware/3.0.0-5-generic/r128/r128_cce.bin
Adding firmware r128/r128_cce.bin
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/ttm/ttm.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/video/sis/sisfb.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/sis/sis.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/acpi/video.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/platform/x86/mxm-wmi.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
W: Possible missing firmware /lib/firmware/nouveau/fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409c for module nouveau
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/via/via.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/i915/i915.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
..
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/gpu/stub/poulsbo.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/video/vesafb.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/video/vgastate.ko
Adding module /lib/modules/3.0.0-5-generic/kernel/drivers/video/vga16fb.ko
Calling hook fuse_utils
Adding binary /sbin/mount.fuse
Calling hook klibc
Calling hook thermal
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.8.so
Adding binary /sbin/udevd
Adding library /lib/x86_64-linux-gnu/libselinux.so.1
Adding library /lib/x86_64-linux-gnu/libdl.so.2
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/usb_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Calling hook plymouth
..
Adding library /usr/lib/nvidia-current/libGL.so.1
..
Adding library /usr/lib/nvidia-current/tls/libnvidia-tls.so.275.09.07
Adding library /usr/lib/nvidia-current/libnvidia-glcore.so.275.09.07
..
Adding library /usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.1
Adding library /usr/lib/libpciaccess.so.0
Adding binary /lib/plymouth/renderers/vga16fb.so
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook busybox
Adding binary /usr/lib/initramfs-tools/bin/busybox
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
Building cpio /boot/initrd.img-3.0.0-5-generic.new initramfs
$ 


As you can see even with nouveau blacklisted it adds it to the initramfs.

And the only nvidia libraries it adds are

/usr/lib/nvidia-current/libGL.so.1
/usr/lib/nvidia-current/tls/libnvidia-tls.so.275.09.07
/usr/lib/nvidia-current/libnvidia-glcore.so.275.09.07

Is that enough? Why isn't it adding /var/lib/dkms/nvidia-current/275.09.07/build/nvidia.ko there? I thought that was the kernel module.

Can I try to blacklist all the regular drivers like [mentioned here]("http://wiki.debian.org/NvidiaGraphicsDrivers#X_.28or_the_complete_machine_when_running_X.29_is_unstable"), and include uvesafb as well? Or will that render the machine completely unusable in case the nvidia driver doesn't work?

---

### Post by jbicha on 2011-07-15
Ok, by re-installing nvidia-current and rebooting, things are working now. I'm not sure about re-installing nouveau but I don't need it this week.

---

### Post by vhaarr on 2011-07-15
I think this has been filed in launchpad already as [bug 810647]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/810647").

---

### Post by vhaarr on 2011-07-15
[This initramfs update]("https://lists.ubuntu.com/archives/oneiric-changes/2011-July/004965.html") might fix it, I think - seems plausible from the changelog at least! :D

---

### Post by drodiger on 2011-07-15
I have just upgraded to Ubuntu 11.10 with nvidia graphic card and I didn't get gdm or lightdm login. What I have done is the following:
Alt-F1 and login as root. I have fix IP address (not dhcp) and I only had to add dns server ip address into resolv.conf.
After that I was able to install the packages.

So when I installed nvidia-current, it was complaining that nouveau firmware is missing, so I installed (just in case): firmware-tools firmware-extract and nouveau-firmware.

I blacklisted nouveau as suggested and done nvidia-xconfig.

After reboot, lightdm started, but click on my login didn't do anything.

So, I changed lightdm to gdm as root.
dpkgk-reconfigure gdm
service lightdm stop
service gdm start

I was upgrading, so I had gdm installed. If you don't have install it apt-get install gdm

I am logged in in graphic mode now :-)

---

### Post by vhaarr on 2011-07-15
You might be in graphic mode, but are you using the nvidia proprietary driver, or a fallback driver?

---

### Post by vhaarr on 2011-07-15
> **vhaarr said:**
> [This initramfs update]("https://lists.ubuntu.com/archives/oneiric-changes/2011-July/004965.html") might fix it, I think - seems plausible from the changelog at least! :D

Yes, that fixed it!

Download from here: [https://launchpad.net/ubuntu/+source/initramfs-tools/0.99ubuntu2](https://launchpad.net/ubuntu/+source/initramfs-tools/0.99ubuntu2)

---

### Post by drodiger on 2011-07-15
lsmod |grep nvidia gives me that nvidia driver is loaded
    nvidia 11989567 42
and /var/log/Xorg.0.log says:

LoadModule: "nvidia"
Loading /usr/lib/xorg/extra-modules/nvidia_drv.soNVIDIA dlloader X Driver 275.09.07
...
NVIDIA Unified Driver -...
Using VT number 7...
...
Loading extension NV-GLX
...
Loading extension NV-CONTROL
Loading extension XINERAMA
...

In Ubuntu Classic I have compiz efects (waiving windows), so I think I have nvidia drivers loaded ;)

---

### Post by Sworddragon on 2011-07-15
> **vhaarr said:**
> [This initramfs update]("https://lists.ubuntu.com/archives/oneiric-changes/2011-July/004965.html") might fix it, I think - seems plausible from the changelog at least! :D

I made a dist-upgrade (because the version is now in the repository) but this hasn't helped. Even reinstalling nvidia-current after this hasn't changed anything.

I made a look at /etc/modprobe.d/nvidia-graphics-drivers.conf and the content is:

```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
```

I tried the solution of jamlam and blacklisted nouveau in /etc/modprobe.d/blacklist.conf too and this worked. But I'm wondering why this step must be done because on my tests xserver-xorg-video-nouveau was not installed.

---

### Post by Sworddragon on 2011-07-21
*deleted*

---

### Post by psytrox on 2011-07-27
> **drodiger said:**
> I have just upgraded to Ubuntu 11.10 with nvidia graphic card and I didn't get gdm or lightdm login. What I have done is the following:
Alt-F1 and login as root. I have fix IP address (not dhcp) and I only had to add dns server ip address into resolv.conf.
After that I was able to install the packages.

So when I installed nvidia-current, it was complaining that nouveau firmware is missing, so I installed (just in case): firmware-tools firmware-extract and nouveau-firmware.

I blacklisted nouveau as suggested and done nvidia-xconfig.

After reboot, lightdm started, but click on my login didn't do anything.

So, I changed lightdm to gdm as root.
dpkgk-reconfigure gdm
service lightdm stop
service gdm start

I was upgrading, so I had gdm installed. If you don't have install it apt-get install gdm

I am logged in in graphic mode now :-)
Worked great. Thanks!

---

### Post by 23dornot23d on 2011-07-27
> 
So when I installed nvidia-current, it was complaining that nouveau  firmware is missing, so I installed (just in case): firmware-tools  firmware-extract and nouveau-firmware.

I blacklisted nouveau as suggested and done nvidia-xconfig.

Blacklisting the nouveau probably did the trick ..... but added the firmware-tools too as above  ..... so who knows ......

I also installed gdm but did not use it - as  kdm is my desktop manager of choice and it runs with that alright ...... on my system


So good news .... the same thing worked for me too ....... thank you .... :D

Latest [COLOR=Blue]_*[**Screenshot**]("http://img195.imageshack.us/img195/1590/screenshotat20110728034.jpg")*_[/COLOR] .... and transparency in Conky too ....

---

### Post by Harry33 on 2011-07-28
> **23dornot23d said:**
> Blacklisting the nouveau probably did the trick ..... but added the firmware-tools too as above  ..... so who knows ......
...


Nvidia-current should blacklist nouveau automatically upon installation.
The file /etc/modprobe.d/nvidia-graphics-drivers.conf is created with the following lines:

```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```

---

### Post by 23dornot23d on 2011-07-28
Well if that is not the case then the blacklisting that is .....


Then its either the **firmware tools** or adding the new gdm ( even though I boot up using kdm ?)  

...... that solved the problem ..... then .... 

So its most probably the firmware tools .....

as the problem is the Nvidia module is not being built correctly or at all ....

or ...... just remembered one more thing I did ..... could be this ....


 [B]sudo update-initramfs -u -v
[/B] 
As all is well now ...... as I said .....[[COLOR=Red]_***SCREENSHOT***_[/COLOR]]("http://img29.imageshack.us/img29/5071/screenshotat20110728140.jpg")

---

### Post by jbicha on 2011-07-28
dkms has been having issues. One fix for some of these nvidia problems may be as simple as:

sudo apt-get install --reinstall nvidia-current

You might have to do that after every kernel upgrade until it gets fixed. Personally, I just switched that laptop to nouveau as I think it'll be good enough.

---

### Post by 23dornot23d on 2011-07-28
Could be right as I know Quackers and Cecil ..... solved theirs this way with just re-installing the Nvidia-Current and Nvidia-settings ....

They actually removed them completely and put them back in again .... but this did not work for my situation - so as you say it may be different for different systems and setups ....

But we do have all the information here now for people having the same or similar problems .....

DKMS was not showing in my last logs as a problem though as the loading up again of Nvidia-Current was 
setting it up ok ....

What was not happening ...... was the module being picked up when the kernel was being compiled.

It does now though .... and thats why I put everything in this [[COLOR=Red]_***LINK***_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11092619&postcount=13") as I kept re-installing the Nvidia-current to no avail .....

I spent roughly 6 hours yesterday going through it ..... and the only thing that helped was when someone reposted this thread at 1:00 in the morning .... and I followed it through and it did finally get the Nvidia
to work

---

### Post by cecilpierce on 2011-07-28
Geezzzz! I know what you mean Keith, I've sent about 2+ days with 3 installs, I left one alone because it still working the way I want it to.
The other 2 are a mess but working, sometime it gets stuck at 'checking battery' and I have to go to tty1 and startx and most of all I have no auto login on those 2 that are updated, the auto login is grayed out, I unlock it, change it, when I go back and look its off and grayed out again, I hate loging in a million times a day  :(

---

### Post by 23dornot23d on 2011-07-28
Yep you went through it with me yesterday and when we are checking everything thoroughly and making sure every step of the way what is happening .... as us old folks do ....

Then the problems start to become more isolated ......

1 ...... replace Nvidia Current ..... definately was not the answer for me ...replaced it numerous times
         ( to the point in the thread where I was sarcastic asking exactly how many time the Nvidia-current needed installing before it worked )

2 ...... it was constantly reporting that the module was not being picked up ...... ( clue maybe )

3 ..... it was also only using the nouveau driver ( another possible clue )

4 ..... after re-booting ..... it was reporting other errors that I have on my camera ..... and hanging at the
splash screen ....

5 ..... startx was the only way to get the screen running ..... but it was not using the Nvidia driver ....

So to simply say just re-install Nvidia-Current ....... and then find people are still reporting problems
after doing this ...... is not the full solution ..... 

But a few of us are working ok with it ...... would like to know how many others are not though ....
as a lot may read these threads and wait for the solutions to arise ......

By the way Cecil .... 
I am getting some panel errors now and then but no lock ups ...... and nothing related to
battery as I am running off mains on the laptop .....  and only [[COLOR=Red]_***4 extensions are loaded up on mine***_[/COLOR]]("http://img705.imageshack.us/img705/3964/screenshotat20110728151.jpg").

---

### Post by cecilpierce on 2011-07-28
Ive been getting pop up errors to and I just close them, I think someone said to remove 'apport' and they would stop but not sure.
Im on ubuntu-unity right now but was going to switch to gnome shell, where did you get the 'Dock' extension and what does it do ?

Good Luck on the book, Im saving the money  :P

---

### Post by 23dornot23d on 2011-07-28
For the Dock

Have a look here [[COLOR=Red]_***LINK ***_[/COLOR]]("http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html")

(but I did not update the .json file for the dock) ..... so its not one that I run ..... 
its actually worked out as a good way of only activating the ones I want nowadays ..... 

The book is coming on and you will definitely get the first copy - signed too .... ;)

---

### Post by cecilpierce on 2011-07-28
> **23dornot23d said:**
> For the Dock

Have a look here [[COLOR=Red]_***LINK ***_[/COLOR]]("http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html")

(but I did not update the .json file for the dock) ..... so its not one that I run ..... 
its actually worked out as a good way of only activating the ones I want nowadays ..... 

The book is coming on and you will definitely get the first copy - signed too .... ;)

Boy! I sure need that book, I cant figure out how to even get the Dock thing from your link.
Have you DL the 'lightdm-greeter' I can get it to run in a terminal but not when I log in or out, I guess it needs to be stuck in a conf file somewhere ???
I need a vacation from this junk, im loosing it, ha! maybe never had it :confused:

---

### Post by 23dornot23d on 2011-07-28
The dock you refer to is it this one ? [COLOR=Blue]_***[LINK]("http://www.google.com/imgres?q=meego+cairo+dock&um=1&hl=en&client=ubuntu&channel=fs&biw=939&bih=541&tbm=isch&tbnid=vC0Rs04vmHl6yM:&imgrefurl=http://www.unixmen.com/software/1470-glx-dock-23-beta-is-released-ex-cairo-dock&docid=n9dM2wLAJWv1pM&w=1280&h=960&ei=wa0xTvmqCIuq-ga8iLGhDQ&zoom=1&iact=hc&vpx=145&vpy=89&dur=744&hovh=194&hovw=259&tx=122&ty=86&page=1&tbnh=129&tbnw=181&start=0&ndsp=12&ved=1t:429,r:0,s:0")***_[/COLOR]

Because that is the Cairo Dock one themed  ..... using the Meego theme .....

I have yet to try out Lightdm ..... 

I keep reading what others are putting about it ..... once I am sure its reasonably stable I will install it too .....

---

