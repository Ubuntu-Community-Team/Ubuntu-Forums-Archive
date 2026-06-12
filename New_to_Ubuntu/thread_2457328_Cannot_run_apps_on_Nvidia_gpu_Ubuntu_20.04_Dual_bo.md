---
title: "Cannot run apps on Nvidia gpu Ubuntu 20.04 Dual boot"
date: 2021-01-30
forum: New to Ubuntu
---

### Post by terrarium01 on 2021-01-30
I am running Ubuntu 20.04 on my Asus ROG GL503GE. I have secure boot disabled. I tried running `DRI_PRIME=1 glmark2` but I got the following error:<br>


 ```
   libGL error: failed to create dri screen
    libGL error: failed to load driver: nouveau
    =======================================================
        glmark2 2014.03+git20150611.fa71af2d
    =======================================================
        OpenGL Information
        GL_VENDOR:     Intel
        GL_RENDERER:   Mesa Intel(R) UHD Graphics 630 (CFL GT2)
        GL_VERSION:    4.6 (Compatibility Profile) Mesa 20.2.6
``` 
I had Performance Mode enabled by default on Nvidia X server settings -> PRIME Profiles. But that mode caused `gnome-shell` to run on my dgpu and was consuming too much battery, so I opted for Nvidia On Demand option. I rebooted my computer, and after that, I could not run any application with my dgpu. Here's the output of `nvidia-smi`


```
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 460.32.03    Driver Version: 460.32.03    CUDA Version: 11.2     |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |                               |                      |               MIG M. |
    |===============================+======================+======================|
    |   0  GeForce GTX 105...  Off  | 00000000:01:00.0 Off |                  N/A |
    | N/A   48C    P8    N/A /  N/A |      9MiB /  4042MiB |      0%      Default |
    |                               |                      |                  N/A |
    +-------------------------------+----------------------+----------------------+
                                                                                   
    +-----------------------------------------------------------------------------+
    | Processes:                                                                  |
    |  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
    |        ID   ID                                                   Usage      |
    |=============================================================================|
    |    0   N/A  N/A      1288      G   /usr/lib/xorg/Xorg                  4MiB |
    |    0   N/A  N/A      1864      G   /usr/lib/xorg/Xorg                  4MiB |
    +-----------------------------------------------------------------------------+

```

Here only `9MiB/4042MiB` has been consumed on Nvidia On Demand mode, but switching to performance mode consumes around `450MiB`.
What should I do to run an app on my dgpu, say for example `glmark2`? I would not want to switch back to Performance Mode, although it would fix my issue, it would cause `gnome-shell` to run on the dgpu and drain battery a lot faster.

---

### Post by CelticWarrior on 2021-01-30
Welcome.

You really only have two options, Intel or Nvidia.
The "on demand" mode is unusable at the moment.

---

### Post by terrarium01 on 2021-01-31
Thanks for making it clear. I guess I'll stick with it. By the way, do you know any other methods by which I can switch between Intel and Nvidia GPU for running a specific app?

---

