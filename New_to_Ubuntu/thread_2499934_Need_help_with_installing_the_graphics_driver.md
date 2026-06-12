---
title: "Need help with installing the graphics driver"
date: 2024-08-15
forum: New to Ubuntu
---

### Post by markcodes on 2024-08-15
Hi, I'm new to Linux and recently installed Ubuntu on my Asus laptop. I've been struggling to install the driver for my Nvidia GT 520M. I used the command "sudo apt install nvidia-driver-390" (390 being the latest supported version for my GPU), the installation resulted in an error (log: [https://pastebin.com/TzZNUFRu](https://pastebin.com/TzZNUFRu)). What could be the issue and how do I fix it? Thanks for your help.

---

### Post by deadflowr on 2024-08-15
Does the driver even work with the 6.8 linux kernel?

---

### Post by markcodes on 2024-08-15
I don't know, how can I check that?

---

### Post by #&amp;thj^% on 2024-08-15
> **deadflowr said:**
> Does the driver even work with the 6.8 linux kernel?
Not without extra help.
EDIT: [https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp](https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp)
> **markcodes said:**
> I don't know, how can I check that?

```
apt policy nvidia-dkms-390
```
or 
```
nvidia-smi
```

---

### Post by markcodes on 2024-08-15
Thanks a lot, is this alternative version usable for the current Ubuntu version though? When I added the PPA and tried to install the driver, it said "Unable to locate package nvidia-driver-390". Is it because it's built for an older version?

---

### Post by #&amp;thj^% on 2024-08-15
It supports kernels up to 6.8.
Show me this:
```
sudo apt update
```

EDIT I see you are a newer user, Enter that code in the terminal, and copy and paste back here please. (With Code Tags if you how)

BTW This driver is not going to help you on Gnome and in particular Wayland..
> Note that you probably want to use XServer instead of Wayland with a driver this old.

---

### Post by markcodes on 2024-08-15
I get this:

```
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://archive.ubuntu.com/ubuntu noble-updates InRelease                 
Hit:3 http://archive.ubuntu.com/ubuntu noble-backports InRelease               
Hit:4 http://security.ubuntu.com/ubuntu noble-security InRelease               
Hit:5 https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu noble InRelease 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```

---

### Post by #&amp;thj^% on 2024-08-15
> **markcodes said:**
> I get this:

```
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://archive.ubuntu.com/ubuntu noble-updates InRelease                 
Hit:3 http://archive.ubuntu.com/ubuntu noble-backports InRelease               
Hit:4 http://security.ubuntu.com/ubuntu noble-security InRelease               
Hit:5 https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu noble InRelease 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```
Cool it works on Noble:
Now before we continue, you did remove and purge all nvidia right? If not do that now please.
please show this now:
```
apt policy nvidia-dkms-390
```

---

### Post by markcodes on 2024-08-15
Yup, Nvidia should be removed

```
N: Unable to locate package nvidia-dkms-390


```

---

### Post by #&amp;thj^% on 2024-08-15
It better be there, from the site:
```
Built packages

    libcuda1-384 Transitional package for nvidia-headless-390

    libnvidia-cfg1-390 NVIDIA binary OpenGL/GLX configuration library

    libnvidia-common-390 Shared files used by the NVIDIA libraries

    libnvidia-compute-390 NVIDIA libcompute package

    libnvidia-decode-390 NVIDIA Video Decoding runtime libraries

    libnvidia-encode-390 NVENC Video Encoding runtime library

    libnvidia-fbc1-390 NVIDIA OpenGL-based Framebuffer Capture runtime library

    libnvidia-gl-390 NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD

    libnvidia-ifr1-390 NVIDIA OpenGL-based Inband Frame Readback runtime library

    nvidia-384 Transitional package for nvidia-driver-390

    nvidia-384-dev Transitional package for nvidia-driver-390

    nvidia-compute-utils-390 NVIDIA compute utilities

  [COLOR="#FF0000"]  nvidia-dkms-390 NVIDIA DKMS package
[/COLOR]
    nvidia-driver-390 NVIDIA driver metapackage

    nvidia-headless-390 NVIDIA headless metapackage

    nvidia-headless-no-dkms-390 NVIDIA headless metapackage - no DKMS

    nvidia-kernel-common-390 Shared files used with the kernel module

    nvidia-kernel-source-390 NVIDIA kernel source package

    nvidia-libopencl1-384 Transitional package for nvidia-headless-390

    nvidia-opencl-icd-384 Transitional package for nvidia-headless-390

    nvidia-utils-390 NVIDIA driver support binaries

    xserver-xorg-video-nvidia-390 NVIDIA binary Xorg driver


```

One more:
```
apt search nvidia-dkms-390
```

---

### Post by markcodes on 2024-08-15
```
Sorting... Done
Full Text Search... Done


```

---

### Post by #&amp;thj^% on 2024-08-15
Your source is there, but wont show what we need to see???
Let me see this please:
```
apt list --upgradable
```

---

### Post by markcodes on 2024-08-15
```
Listing... Done
gnome-text-editor/noble-updates 46.3-0ubuntu1 amd64 [upgradable from: 46.1-1]
N: There is 1 additional version. Please use the '-a' switch to see it

```

---

### Post by #&amp;thj^% on 2024-08-15
I'll bet your using wayland now, show this please:
```
inxi -G|grep Display
```

---

### Post by markcodes on 2024-08-15
```
 Display: wayland server: X.Org v: 23.2.6 with: Xwayland v: 23.2.6


```

---

### Post by #&amp;thj^% on 2024-08-15
Can you log out and back in again with Ubuntu on X11.

---

### Post by markcodes on 2024-08-15
Did that, now the command outputs this:

```
Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.6 driver: X:


```

---

### Post by #&amp;thj^% on 2024-08-15
Nice, Now show me any errors from:
```
sudo apt install nvidia-driver-390 nvidia-dkms-390
```

---

### Post by markcodes on 2024-08-15
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package nvidia-driver-390
E: Unable to locate package nvidia-dkms-390

```

---

### Post by #&amp;thj^% on 2024-08-15
He may have named it different
```
apt search nvidia-graphics-drivers-390
```

---

### Post by #&amp;thj^% on 2024-08-15
No he did not use different naming....I've sent Daniel a email, letting him know about this:
But for now I've kind of cheated here, so please now run:
```
sudoedit '/etc/apt/sources.list.d/dtl131-ubuntu-nvidiaexp-noble.sources' 
```
And change the line "Suites: noble" to "Suites: jammy' ie:
```
URIs: https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu/
[COLOR="#FF0000"]Suites: jammy[/COLOR]
Components: main
Signed-By: 
```

Now run 
```
sudo apt update && sudo apt install nvidia-driver-390 nvidia-dkms-390
```
```
apt policy nvidia-dkms-390 nvidia-driver-390
nvidia-dkms-390:
  Installed: (none)
  Candidate: 390.157-0ubuntu9~nvidiaexp4
  Version table:
     390.157-0ubuntu9~nvidiaexp4 500
        500 https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu jammy/main amd64 Packages
nvidia-driver-390:
  Installed: (none)
  Candidate: 390.157-0ubuntu9~nvidiaexp4
  Version table:
     390.157-0ubuntu9~nvidiaexp4 500
        500 https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu jammy/main amd64 Packages

```

---

### Post by markcodes on 2024-08-16
Okay, so I've made the change and it installed. This is the command output now:

```
nvidia-dkms-390:
  Installed: 390.157-0ubuntu9~nvidiaexp4
  Candidate: 390.157-0ubuntu9~nvidiaexp4
  Version table:
 *** 390.157-0ubuntu9~nvidiaexp4 500
        500 https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-driver-390:
  Installed: 390.157-0ubuntu9~nvidiaexp4
  Candidate: 390.157-0ubuntu9~nvidiaexp4
  Version table:
 *** 390.157-0ubuntu9~nvidiaexp4 500
        500 https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

EDIT: After a reboot I only see a black screen.

---

### Post by #&amp;thj^% on 2024-08-16
I'm afraid to say that driver might only work on 22.04 and not 24.04.

At boot select Advanced Option and drop to root shell and remove the driver.
```
sudo apt autoremove --purge nvidia*
```
And reboot.

You may need to look at Kubuntu, Xubuntu, Lubuntu, for a lighter DE.

---

### Post by markcodes on 2024-08-16
Oh ok, so if I install Xubuntu, will the driver work?

---

### Post by #&amp;thj^% on 2024-08-16
> **markcodes said:**
> Oh ok, so if I install Xubuntu, will the driver work?

I'm doing that now, just to save us both time. (and frustration)

Will reply when I'm finished.

Right now I'm always on an unsupported system and using newer kernels and drivers:
```
nvidia-smi
Fri Aug 16 13:47:18 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 560.31.02              Driver Version: 560.31.02      CUDA Version: 12.6     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0 Off |                  N/A |
| N/A   40C    P0              9W /   60W |      23MiB /   4096MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      1018      G   /usr/lib/Xorg                                   4MiB |
+-----------------------------------------------------------------------------------------+

```

---

### Post by #&amp;thj^% on 2024-08-17
@markcodes, Yes it dose work on jammy and kernel 6.8
```
 nvidia-smi && uname -r
Sat Aug 17 09:42:02 2024       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.157                Driver Version: 390.157                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 730M     Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   47C    P0    N/A /  N/A |    115MiB /   983MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+
6.8.0-40-generic

```

---

### Post by deadflowr on 2024-08-17
Is that with the PPA?
I'd assume jammy could run fine if you use the GA kernel instead of the HWE kernel.
Since the GA kernel is 5.15.

---

### Post by #&amp;thj^% on 2024-08-17
> **deadflowr said:**
> Is that with the PPA?
I'd assume jammy could run fine if you use the GA kernel instead of the HWE kernel.
Since the GA kernel is 5.15.

Yes with the PPA, and Xubuntu 22.04.
I found it worked on all kernels 6.26 thru 6.8.0-40-generic.
```
apt policy nvidia-driver-390
nvidia-driver-390:
  Installed: 390.157-0ubuntu9~nvidiaexp4
  Candidate: 390.157-0ubuntu9~nvidiaexp4
  Version table:
 *** 390.157-0ubuntu9~nvidiaexp4 500
        500 https://ppa.launchpadcontent.net/dtl131/nvidiaexp/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     390.157-0ubuntu0.22.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
     390.147-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/restricted amd64 Packag
```

I was tied up with him for few hours yesterday, and is working on kernel 6.10, I was the only sucker using kernel 6.10 currently.
PLEASE DON'T USE>>>kernel 6.10 yet, it will fail.

BTW: I forgot to mention the "ppa:graphics-drivers/ppa" 390 will only work on kernel 6.2

---

