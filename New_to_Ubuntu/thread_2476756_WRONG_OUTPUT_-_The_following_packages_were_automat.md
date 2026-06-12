---
title: "WRONG OUTPUT - The following packages were automatically installed and are no longer"
date: 2022-07-05
forum: New to Ubuntu
---

### Post by darthvader-reali on 2022-07-05
HI Team.
 I'm getting the following message on a recently installed system:

```

r4@r4-ThinkPad-T440p:~$ sudo apt-get upgrade
[sudo] password for r4: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi libatomic1:i386 libbsd0:i386
  libdrm-amdgpu1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386
  libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386 libglvnd0:i386
  libgstreamer-plugins-bad1.0-0 libicu70:i386 libllvm13:i386 libmd0:i386
  libnvidia-cfg1-470 libnvidia-common-470 libnvidia-compute-470:i386
  libnvidia-decode-470 libnvidia-decode-470:i386 libnvidia-egl-wayland1
  libnvidia-encode-470 libnvidia-encode-470:i386 libnvidia-extra-470
  libnvidia-fbc1-470 libnvidia-gl-470 libnvidia-gl-470:i386 libnvidia-ifr1-470
  libsensors5:i386 libstdc++6:i386 libvulkan1:i386 libwayland-client0:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386
  libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0
  libxshmfence1:i386 libxxf86vm1:i386 mesa-vulkan-drivers:i386
  nvidia-compute-utils-470 nvidia-kernel-source-470 nvidia-settings
  nvidia-utils-470 pkg-config screen-resolution-extra
  xserver-xorg-video-nvidia-470
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Problem I see is that it says nvidia drivers, mesa vulkan and a lot of  gstreamer things. How can I make sure that future updates will ignore  this?

---

### Post by guiverc on 2022-07-06
You haven't provided any release details; which are useful to look up the *package dependency rules* involved; as they can vary between releases.

Most of the packages in your listing are not default packages; thus were installed by a user of your system, or as a consequence of a user command*, *for example you can view the manifest for *jammy* (22.04) [here]("https://cdimage.ubuntu.com/ubuntu-mate/releases/22.04/release/ubuntu-mate-22.04-desktop-amd64.manifest") which tells you what you'd expect to find for that release. But if you provide your release details, we can limit what we look up to a specified release & thus provide more detailed answers.

You can mark packages to be *held* (so they're not upgraded/removed), but anything a user holds, can be overruled by a subsequent command anyway, so it cannot prevent careless mistakes anyway esp. when users just copy/paste commands from the internet & don't think thru the effects of commands before using them.

I've not answered your question as I don't know your release; and for me to be specific; a single package would be chosen as example & I'd use commands to look up why it was installed, what can cause it's removal etc (*which requires a specified release first*).

---

### Post by Impavidus on 2022-07-06
A lot of these are 32-bit packages, which you only need if you want to run 32-bit software. There's no more 32-bit software in the official repositories. I think some 32-bit libraries may be pulled in by wine. Then there are some nvidia packages, which may be needed on particular hardware, codecs and pkg-config, which is a tool for some compilation work. Do you use nvidia graphics or have you got other nvidia drivers installed? 

If you think you still need these packages, you can mark them as manually installed, so they won't be autoremoved. Use the GUI tool synaptic or the apt-mark command line tool. Don't put them on hold; that will not only block autoremoving, but also upgrading the packages. That may later cause version conflicts and block upgrading of other packages.

---

### Post by guiverc on 2022-07-07
Also asked at [https://ubuntu-mate.community/t/wrong-output-the-following-packages-were-automatically-installed-and-are-no-longer-required/25632/2](https://ubuntu-mate.community/t/wrong-output-the-following-packages-were-automatically-installed-and-are-no-longer-required/25632/2)

---

