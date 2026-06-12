---
title: "Nvidia GTX960M internal error."
date: 2018-06-29
forum: New to Ubuntu
---

### Post by br3ach89 on 2018-06-29
Hello there, I've installed xubuntu 16.04 on my MSI [https://es.msi.com/Laptop/GE72-6QD-Apache-Pro.html](https://es.msi.com/Laptop/GE72-6QD-Apache-Pro.html) with GPU Nvidia GTX960M. At least once a day it freezes for a while and sometimes my file system get corrupted, so i have to reboot and do a fsck manually. Every time this error message shows up [see attachment]. I guess the problem is the GPU, but i've already updated my drivers, i don't know what do. Help! :confused:

---

### Post by Bashing-om on 2018-06-29
Hello br3ach89; Welcome to the forum :)

Let's take a look at the status of the driver.
Post back the text outputs - Between Code Tags - of terminal commands:
```

sudo lshw -C display
cat /var/log/gpu-manager.log
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see if a 
[INDENT][INDENT]tale gets told
[/INDENT][/INDENT]

---

### Post by br3ach89 on 2018-07-06
Thanks for the reply! :D let's see the output:
```
*-display                 
       description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:134 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff

```[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]**[FONT=&amp]sudo lshw -C display[/FONT]**[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for fglrx modules in /lib/modules/4.13.0-45-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.13.0-45-generic/updates/dkms
Found nvidia module: nvidia_390.ko
Looking for amdgpu modules in /lib/modules/4.13.0-45-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:191b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:139b
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Found "/dev/dri/card1", driven by "i915"
output 0:
    card1-eDP-1
Number of connected outputs for /dev/dri/card1: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Intel IGP detected
Desktop system detected
or laptop with open drivers
Discrete NVIDIA card detected
System configuration has changed
Removing xorg.conf. Path: /etc/X11/xorg.conf
Moved /etc/X11/xorg.conf to /etc/X11/xorg.conf.07062018

```[COLOR=#000000][FONT=&amp]

[B]dpkg -l | grep -i nvidia
[/B][/FONT][/COLOR]```
ii  bbswitch-dkms                                               0.8-4ubuntu1                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-390                                                390.67-0ubuntu0~gpu17.10.1                  amd64        NVIDIA CUDA runtime library
ii  nvidia-390                                                  390.67-0ubuntu0~gpu17.10.1                  amd64        NVIDIA binary driver - version 390.67
ii  nvidia-opencl-icd-390                                       390.67-0ubuntu0~gpu17.10.1                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.8.5                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             396.24-0ubuntu0~gpu17.10.1                  amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by Bashing-om on 2018-07-06
br3ach89; Well - 

We have conflicts:
> 
configuration: driver=nvidia
bk
Is nouveau blacklisted? no
bk
396.24-0ubuntu0~gpu17.10.1


which raises the question of how you installed the nvidia proprietary driver.

Depending on what you did is what we now do.

And - what release are we working with as 17.10 is soon (19th) End-of-Life !

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by br3ach89 on 2018-07-13
I was installing ubuntu on an external hard disk (ssd to usb) but it kept freezing during the installation. It was because of the missing nvidia drivers, that each time provoked the fatal error. So I installed ubuntu through a virtual machine, installed the nvidia drivers as well, and then i started to boot linux from external hd. Does this may be the problem?

---

### Post by Autodave on 2018-07-13
Where did you get the driver from? (I believe that is what he is looking for.....)

---

### Post by br3ach89 on 2018-08-08
I installed the drivers from the nvidia website

---

### Post by br3ach89 on 2018-08-08
what should i do? install again the drivers?

---

### Post by Bashing-om on 2018-08-08
br3ach89; Ouch -

> 
I installed the drivers from the nvidia website


And nvidia says do not do this:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


So the question now is how to remove the OEM driver in order to install the driver from the repository.

show is the output of terminal commands:
```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia
lsmod | grep nvidia
sudo lshw -C display

```

see what we can do.

[INDENT][INDENT]there is a path that seems right, But .....
[/INDENT][/INDENT]

---

