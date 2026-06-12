---
title: "Can't get into the system after NVIDIA driver install, Ubuntu 18.04"
date: 2018-07-18
forum: New to Ubuntu
---

### Post by Crisantha on 2018-07-18
Hey there.

I'm trying to install NVIDIA-driver. After try to do that I've got just black screen after rebooting the system. Installing driver nvidia-390. I did this way: 
```
ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
```

Tried it on Ubuntu 18.04 on Unity, Kubuntu 18.04, Xubuntu 18.04, I have used different versions of a driver.

After rebooting I see the black screen, my computer's speaker's doing PEEEEP, then my monitor is going to safe mode, that's all.

Sorry for my broken English, I just came here from russian Ubuntu forum and there no one who can help me with this problem.

Forgot, my videocard is PALIT GTX 1050 Ti. Now I'm using the system from recovery mode.

---

### Post by Bashing-om on 2018-07-18
Crisantha; Hello - Welcome to the forum .

"autoinstall" should just work . Let's see what we can do to find out why the install of the driver fails.
Post back - Between Code Tags - the outputs of terminal commands:
```

sudo lshw -C display
cat  /var/log/gpu-manager.log
dpkg -l | grep -i nvidia
lsmod | grep nvidia
lsmod | grep nouveau

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
See here if there are any hints on what is not taking place.

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by Crisantha on 2018-07-18
sudo lshw -C display
```
*-display                 
       description: VGA compatible controller
       product: GP107 [GeForce GTX 1050 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:30 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
```

cat  /var/log/gpu-manager.log\
```
cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-23-generic/updates/dkms
Found nvidia module: nvidia.ko
Looking for amdgpu modules in /lib/modules/4.15.0-23-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
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
Vendor/Device Id: 8086:412
BusID "PCI:0@0:2:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver. Skipping...
Vendor/Device Id: 10de:1c82
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

dpkg -l | grep -i nvidia

```
ii  libnvidia-cfg1-390:amd64                        390.48-0ubuntu3                             amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                            390.48-0ubuntu3                             all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                     390.48-0ubuntu3                             amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                      390.48-0ubuntu3                             i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                      390.48-0ubuntu3                             amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                       390.48-0ubuntu3                             i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                      390.48-0ubuntu3                             amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                       390.48-0ubuntu3                             i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                        390.48-0ubuntu3                             amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                         390.48-0ubuntu3                             i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                          390.48-0ubuntu3                             amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                           390.48-0ubuntu3                             i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                        390.48-0ubuntu3                             amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                         390.48-0ubuntu3                             i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390                        390.48-0ubuntu3                             amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                                 390.48-0ubuntu3                             amd64        NVIDIA DKMS package
ii  nvidia-driver-390                               390.48-0ubuntu3                             amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390                        390.48-0ubuntu3                             amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                        390.48-0ubuntu3                             amd64        NVIDIA kernel source package
ii  nvidia-prime                                    0.8.8                                       all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                 390.42-0ubuntu1                             amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                                390.48-0ubuntu3                             amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390                   390.48-0ubuntu3                             amd64        NVIDIA binary Xorg driver
```

lsmod | grep nvidia

```
nvidia_uvm            757760  0
nvidia_drm             40960  1
nvidia_modeset       1110016  6 nvidia_drm
nvidia              14340096  727 nvidia_modeset,nvidia_uvm
drm_kms_helper        167936  2 i915,nvidia_drm
drm                   401408  5 i915,nvidia_drm,drm_kms_helper
ipmi_msghandler        53248  2 nvidia,ipmi_devintf
```

lsmod | grep nouveau

```
Nothing happened
```

I'm doing this from recovery mode.

---

### Post by Bashing-om on 2018-07-18
Crisantha; Welp;

This :
> 
 *-display UNCLAIMED
       description: VGA compatible controller
<snip>
configuration: latency=0

says that the problem lies within the Intel chip set. Unfortunately, I am not too versed with Intel. 
At this point I need to determine the nature of the graphic systems. Are you "muxed" or "muxless" ?
> 
 MUX-less:  Optimus chipsets - that is, dual GPUs where the outputs are NOT switched between the GPUs using a multiplexer.
the Intel GPU would need to be active since MUX-less works by the nvidia doing the work but the Intel writing the framebuffer to the outputs, rather than with MUX systems where each GPU writes to its own framebuffers, and the outputs are switched between the 2 GPUs.


So, let us begin processes to determine what is up with the Intel chip set . Mind you will also be a learning process of my own . I do not know Intel !
In terminal run :
```

sudo /usr/bin/prime-supported

```
that generates a log file : /var/log/prime-supported.log, 
which may be useful in such cases.
Post back the contents of that log file:
```

cat /var/log/prime-supported.log

```

hybrid graphics require the config file " /etc/X11/xorg.conf "; does a sane one exist ?
post back:
```

cat /etc/X11/xorg.conf

```

That is enough to get us started .. we look at drivers at a later time.

[INDENT][INDENT]If I only knew
[/INDENT][/INDENT]

---

### Post by Crisantha on 2018-07-19
Started to read your msg about muxed and muxless and understood nothing. IDK why but I went to bios and disabled INTEL GRAPHICS (its graphic of my motherboard). And now, system is rebooting in normal state, Not sure the driver is working good (I can see some freezes) but at least my PC can reboot and I can get into the system.

---

### Post by Bashing-om on 2018-07-19
Crisantha; Uh Huh ...

Like I advised, is the Intel driver we are concerned with .
If you are not concerned with the battery life, then all is well with the Intel card disabled .

[INDENT][INDENT]ain't nothing but a thing[/INDENT][/INDENT]

---

### Post by Crisantha on 2018-07-19
Thanks for your help!

---

### Post by Bashing-om on 2018-07-19
Crisantha; Hey like -

> 
Thanks for your help! 


Help is what we do :)

If you are completely satisfied at this time - then->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Else:
enable the Intel chip set. provide the requested outputs - and we continue to prosecute a Intel driver issue .

[INDENT][INDENT]your call
[/INDENT][/INDENT]

---

### Post by mc4man on 2018-07-19
Wouldn't think Ubuntu (or maybe linux in general?) can automatically deal with a hardware mux video system when using the nvidia prop drivers. So you'd need to do as you did , i.e, enable one & disable the other.

---

### Post by Bashing-om on 2018-07-19
@Crisantha - well !

mc4man is writing the book on Nvidia interfacing - He knows !

@mc4man - thanks for providing the info - noted.

[INDENT][INDENT]all in this together
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2018-07-22
> Started to read your msg about muxed and muxless and understood nothing.

That's because you probably don't have a laptop with hybrid graphics and it's not applicable to your hardware. Bashing-om assumed you had a laptop for some reason. I'm not sure why. "Palit GTX 1050" is a desktop card.

---

