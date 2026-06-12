---
title: "I purged nvidia drivers and reinstalled them but my Nvidia drivers are not loaded"
date: 2018-11-21
forum: New to Ubuntu
---

### Post by ardahamamcioglu on 2018-11-21
Hi,
I've been having this problem for a few days. I was getting messages about starting and stopping Nvidia daemon for a while and i wanted to fix it by purging and reinstalling Nvidia drivers.  So i did, I purged nvidia and reinstalled it but no matter what i try i cant get nvidia to load. Here is where i am so far.


```

arda@arda-TULPAR-T7-V3:~$ nvidia-settings
ERROR: NVIDIA driver is not loaded
ERROR: Unable to load info from any available system

lsmod | grep nvidia and lsmod | grep nouveau
comes up with nothing

arda@arda-TULPAR-T7-V3:~$ lspci -v | grep -A 14 NVIDIA
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)
    Subsystem: CLEVO/KAPOK Computer GM204M [GeForce GTX 970M]
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [disabled] [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia


03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
    Subsystem: CLEVO/KAPOK Computer RTL8411B PCI Express Card Reader
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f7915000 (32-bit, non-prefetchable) [size=4K]
arda@arda-TULPAR-T7-V3:~$ apt-cache search nvidia-39
xserver-xorg-video-nvidia-390 - NVIDIA binary Xorg driver
nvidia-390-dev - Transitional package for nvidia-driver-390
nvidia-390 - Transitional package for nvidia-driver-390
xserver-xorg-video-nvidia-396 - NVIDIA binary Xorg driver
arda@arda-TULPAR-T7-V3:~$ lspci -k -s 01:00.00
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)
    Subsystem: CLEVO/KAPOK Computer GM204M [GeForce GTX 970M]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia


```

---

### Post by Autodave on 2018-11-21
Did it ever work properly?  Did you just upgrade your system?  I am assuming that you used the repositories and not Nvidia's site to obtain the driver?  That card appears to be for a laptop, correct?  If so, what model laptop?

---

### Post by Bashing-om on 2018-11-21
ardahamamcioglu; Hello - Welcome to the forum .

Let's have a look at what is installed, and what the gpu manager has to relate:
```

sudo lshw -C display
dpkg -l | grep -i nvidia
lsmod | grep nvidia
cat /var/log/gpu-manager.log

```

See where go go from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ardahamamcioglu on 2018-11-22
Hi, yeah the driver was working fine before the purge. I have done a clean install of 18.10. I did everything normally before purging gaming, rendering etc.. I just wanted to fix nvidia persistence daemon.

---

### Post by ardahamamcioglu on 2018-11-22
Hi, here is what that input came up with:
```
arda@arda-TULPAR-T7-V3:~$ sudo lshw -C display[sudo] password for arda: 
  *-display UNCLAIMED       
       description: 3D controller
       product: GM204M [GeForce GTX 970M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
arda@arda-TULPAR-T7-V3:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-415:amd64                    415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                        390.87-0ubuntu1                            all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-415                        415.13-0ubuntu0~gpu18.10.1                 all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                 390.87-0ubuntu1                            amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                  390.87-0ubuntu1                            i386         NVIDIA libcompute package
rc  libnvidia-compute-396:amd64                 396.54-0ubuntu0~gpu18.10.1                 amd64        NVIDIA libcompute package
rc  libnvidia-compute-396:i386                  396.54-0ubuntu0~gpu18.10.1                 i386         NVIDIA libcompute package
rc  libnvidia-compute-410:amd64                 410.73-0ubuntu0~gpu18.10.1                 amd64        NVIDIA libcompute package
rc  libnvidia-compute-410:i386                  410.73-0ubuntu0~gpu18.10.1                 i386         NVIDIA libcompute package
ii  libnvidia-compute-415:amd64                 415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA libcompute package
ii  libnvidia-compute-415:i386                  415.13-0ubuntu0~gpu18.10.1                 i386         NVIDIA libcompute package
ii  libnvidia-decode-415:amd64                  415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-415:i386                   415.13-0ubuntu0~gpu18.10.1                 i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-415:amd64                  415.13-0ubuntu0~gpu18.10.1                 amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-415:i386                   415.13-0ubuntu0~gpu18.10.1                 i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-415:amd64                    415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-415:i386                     415.13-0ubuntu0~gpu18.10.1                 i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-415:amd64                      415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-415:i386                       415.13-0ubuntu0~gpu18.10.1                 i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-415:amd64                    415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-415:i386                     415.13-0ubuntu0~gpu18.10.1                 i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-compute-utils-390                    390.87-0ubuntu1                            amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-415                    415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA compute utilities
rc  nvidia-dkms-390                             390.87-0ubuntu1                            amd64        NVIDIA DKMS package
ii  nvidia-dkms-415                             415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA DKMS package
ii  nvidia-driver-415                           415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-390                    390.87-0ubuntu1                            amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-415                    415.13-0ubuntu0~gpu18.10.1                 amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-415                    415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA kernel source package
ii  nvidia-prime                                0.8.10                                     all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                             415.13-0ubuntu0~gpu18.10.1                 amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-415                            415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-415               415.13-0ubuntu0~gpu18.10.1                 amd64        NVIDIA binary Xorg driver
arda@arda-TULPAR-T7-V3:~$ lsmod | grep nvidia
arda@arda-TULPAR-T7-V3:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.18.0-11-generic/updates/dkms
Found nvidia module: nvidia-drm.ko
Looking for amdgpu modules in /lib/modules/4.18.0-11-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? yes
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:416
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:13d8
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
	card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Intel hybrid system
Creating /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
Setting power control to "on" in /sys/bus/pci/devices/0000:01:00.0/power/control
Loading nvidia with "no" parameters



```

---

### Post by mc4man on 2018-11-22
What do these show?
```
sudo prime-select nvidia
```
```
ls /lib/modprobe.d |grep nvidia
```

---

### Post by ardahamamcioglu on 2018-11-22
The prime-select is working, i dont know the other one.
```

arda@arda-TULPAR-T7-V3:~$ sudo prime-select nvidia[sudo] password for arda: 
Info: the nvidia profile is already set
arda@arda-TULPAR-T7-V3:~$ ls /lib/modprobe.d |grep nvidia
blacklist-nvidia.conf
nvidia-graphics-drivers.conf
nvidia-kms.conf



```

---

### Post by mc4man on 2018-11-22
> **ardahamamcioglu said:**
> The prime-select is working, i dont know the other one.
```

arda@arda-TULPAR-T7-V3:~$ sudo prime-select nvidia[sudo] password for arda: 
Info: the nvidia profile is already set
arda@arda-TULPAR-T7-V3:~$ ls /lib/modprobe.d |grep nvidia
blacklist-nvidia.conf
nvidia-graphics-drivers.conf
nvidia-kms.conf



```
It's probable that when you  last switched from Intel to nvidia that the process wasn't completed. So you have nvidia loaded & blacklisted. You could try either - 
switch to intel, reboot, switch to nvidia, reboot, i.e
sudo prime-select intel
reboot
sudo prime-select nvidia
reboot

Or just try removing the blacklist & rebooting
```
sudo rm /lib/modprobe.d/blacklist-nvidia.conf && reboot
```

---

### Post by ardahamamcioglu on 2018-11-22
I cannot belive the solution was so simple. Oh my god you saved me a lot of time. Thank you soo much. selecting intel, rebooting and selecting nvidia then rebooting worked.

---

### Post by Bashing-om on 2018-11-22
ardahamamcioglu;  :)

As I live and learn too - a'int mc4man wonderful !

As this matter is now concluded - to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT]

---

