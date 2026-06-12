---
title: "Really need help from some guru's after upgrade to 20.04"
date: 2021-05-03
forum: New to Ubuntu
---

### Post by magmp2 on 2021-05-03
Hi, I'm new on the forum nad trying to get some help as nothing have worked for me. Situation is : I have upgraded from 16.04 to 18.04 and straight to 20.04. I can start metacity but not gnome3. I got used to gnome3 and would like to go back to it. I think long before upgrade I made some mods and symlinks to nvidia libraries when using cuda (not using any more) and now after upgrade I cannot run gnome3 or some apps like gnome-control-center, here's one of errors:

gnome-control-center: error while loading shared libraries: libnvidia-tls.so.418.87.01: cannot open shared object file: No such file or directory

and ldd:

ldd /usr/bin/gnome-control-center | grep 'not found'

    libnvidia-tls.so.418.87.01 => not found
    libnvidia-glcore.so.418.87.01 => not found

I have tried remove libGL.so symlinks and libs also, reinstalled nvidia driver 460. Thing is this 418 version is no longer on my system (and wasn't for a while even on 16.04) and I have no idea how to remove this error as I'm thinking it's the problem to run gnome3 also.

Need some help guys
(&#8857;&#9602;&#8857;&#10006; )

---

### Post by jeremy31 on 2021-05-03
Moved to New to Ubuntu from ULOS chat

---

### Post by grahammechanical on 2021-05-03
I suggest that you open Software & Updates>Additional Drivers tab and select the open source Nouveau video driver and then reboot and see what happens. You may need to purge that 418 Nvidia driver. There is a command to do that. Additional Drivers will install (activate) the Nouveau driver. Get running with Nouveau first before purging Nvidia

[https://linuxconfig.org/how-to-uninstall-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-uninstall-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux)

Regards

---

### Post by magmp2 on 2021-05-03
Thanks for response. I have purge nvidia with:

sudo apt remove --purge '^nvidia-.*'
sudo apt autoremove
sudo apt autoclean

after switching to nouveau and rebooting. Checked the modules for nouveau with

lsmod | grep nouveau

but no result. Checked by running gnome-control-center and same thing:

gnome-control-center: error while loading shared libraries: libnvidia-tls.so.418.87.01: cannot open shared object file: No such file or directory

Checked also with

dpkg -l | grep nvidia

but no results there for 418.87.01 or nvidia

also checked

dpkg -l | grep nouveau
ii  libdrm-nouveau2:amd64                                       2.4.102-1ubuntu1~20.04.1                    amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  nouveau-firmware                                            20091212-0ubuntu1                           all          Firmware for nVidia graphics cards
ii  xserver-xorg-video-nouveau                                  1:1.0.16-1                                  amd64        X.Org X server -- Nouveau display driver

Any more ideas??

---

### Post by deadflowr on 2021-05-05
If you have inxi installed try
```
inxi -G
```
Which should show the current GPU stats.

(if you do not have inxi installed you can install it with 
```
sudo apt install inxi
```

---

### Post by magmp2 on 2021-05-05
Thanks for response. Installed inxi and that's the outpu:

inxi -G
Graphics:
  Device-1: NVIDIA GP104 [GeForce GTX 1070] driver: nvidia v: 460.73.01 
  Display: x11 server: X.Org 1.20.9 driver: nvidia tty: N/A 
  Message: No advanced graphics data found on this system.

---

### Post by deadflowr on 2021-05-05
You have the nvidia driver loaded (version 460.73.01.
But it still shows nothing in the dpkg output?
Did you perchance install the driver from nvidia's website?
(The .run file version?)

---

### Post by magmp2 on 2021-05-05
Dpkg out from previous post was after purging nvidia and installing nouevau . I had before driver from nvidia site .run but not anymore ( also tried install it now but fails with : kernel modules build errors), so I used : ubuntu-drivers autoinstall. Here's fresh output from dpkg:

dpkg -l | grep nvidia
ii  libnvidia-cfg1-460:amd64                                    460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-460                                        460.73.01-0ubuntu0.20.04.1                  all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-460:amd64                                 460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA libcompute package
ii  libnvidia-compute-460:i386                                  460.73.01-0ubuntu0.20.04.1                  i386         NVIDIA libcompute package
ii  libnvidia-decode-460:amd64                                  460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-460:i386                                   460.73.01-0ubuntu0.20.04.1                  i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-460:amd64                                  460.73.01-0ubuntu0.20.04.1                  amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-460:i386                                   460.73.01-0ubuntu0.20.04.1                  i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-460:amd64                                   460.73.01-0ubuntu0.20.04.1                  amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-460:amd64                                    460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-460:i386                                     460.73.01-0ubuntu0.20.04.1                  i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-460:amd64                                      460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-460:i386                                       460.73.01-0ubuntu0.20.04.1                  i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-460:amd64                                    460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-460:i386                                     460.73.01-0ubuntu0.20.04.1                  i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  linux-modules-nvidia-460-5.4.0-72-generic                   5.4.0-72.80+1                               amd64        Linux kernel nvidia modules for version 5.4.0-72
ii  linux-modules-nvidia-460-generic                            5.4.0-72.80+1                               amd64        Extra drivers for nvidia-460 for the generic flavour
ii  linux-objects-nvidia-460-5.4.0-72-generic                   5.4.0-72.80+1                               amd64        Linux kernel nvidia modules for version 5.4.0-72 (objects)
ii  linux-signatures-nvidia-5.4.0-72-generic                    5.4.0-72.80+1                               amd64        Linux kernel signatures for nvidia modules for version 5.4.0-72-generic
ii  nvidia-compute-utils-460                                    460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA compute utilities
ii  nvidia-driver-460                                           460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-460                                    460.73.01-0ubuntu0.20.04.1                  amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-460                                    460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA kernel source package
ii  nvidia-prime                                                0.8.16~0.20.04.1                            all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             460.39-0ubuntu0.20.04.1                     amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-460                                            460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                                     0.18build1                                  all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-460                               460.73.01-0ubuntu0.20.04.1                  amd64        NVIDIA binary Xorg driver

and nvidia-installer.log

[https://paste.ubuntu.com/p/sMZPWX2kmS/](https://paste.ubuntu.com/p/sMZPWX2kmS/)

---

### Post by magmp2 on 2021-05-05
Finally after searching by modification day manually removed libGL.so and symlinks from /usr/lib32 folder. Message from gnome-control-center already changed (missing libGL.so instead libnvidia-tls.418....) but still wouldn't run. so I run:

sudo apt install --reinstall libgl1 

and DONE. All working including Gnome 3 Xorg. No more errors. Thanks guys for your time. Left here my solution so someone can try as well.
:popcorn:

---

