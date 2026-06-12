---
title: "Ubuntu keeps randomly rebooting my PC"
date: 2021-05-28
forum: New to Ubuntu
---

### Post by aamilm23 on 2021-05-28
Hello Everyone.

Whenever I boot into Ubuntu, after I login my screen will randomly go black and my PC will reboot. I have dual booted Windows 10 and Ubuntu (Separate Harddrive). Sometimes it takes a while to happen but mostly happens immediately after logging in. My hardware is fine because Windows runs perfectly with zero crashes/reboots/BSODs/bad performance/etc...Can somebody please assist me?

Thank you in advance.

---

### Post by grahammechanical on 2021-05-28
We do need further information. Please tell us the specification of your machine. Make of machine?; CPU? Amount of RAM? Video card? The version of Ubuntu? Is Ubuntu Running on a proprietary video driver or an open source video driver? How long has Ubuntu been installed? Did this begin to happen after there was an update to Ubuntu? Have you modified Ubuntu in any way? Added a different Desktop Environment and User Interface? Information like this can help us identify possible causes.

There is something you can do for yourself. At the Grub boot menu select Advanced Options for Ubuntu. And then select another kernel in the list to boot from. Does that make any difference?

Also, if you select a kernel with recovery mode Linux will load to a recovery menu. If you select Resume Ubuntu will load to a desktop will a low resolution open source video driver. Is the desktop stable? Opening Software & Updates>Additional Drivers tab will allow you to either disable or activate a proprietary video driver. Doing one or the other and rebooting may solve the problem. It may not but at least we will have eliminated one possible cause. We need to be connected to the internet to activate a proprietary video driver.

Regards

---

### Post by Impavidus on 2021-05-28
If Windows runs perfectly, it's plausible there's no hardware problem, but it's not guaranteed. For example, it may be that the crash is triggered by accessing a particular bad memory sector that's just never accessed on Windows. At the grub menu you should find an option to run a memory check.

---

### Post by aamilm23 on 2021-05-28
My PC specs are; Ryzen 5 3500, 16GB DDR4 2666, Radeon R9 390. Ubuntu is 20.04 LTS. No proprietary video drivers so I guess open source. I'd say I've had it installed for about 5 minutes until the problem started. I've made no changes to Ubuntu.

I will try those suggestions, thank you so much for your help.

---

### Post by aamilm23 on 2021-05-28
I will try the memory check and report back. Thanks so much!

---

### Post by mastablasta on 2021-05-31
> **aamilm23 said:**
> My PC specs are; Ryzen 5 3500, 16GB DDR4 2666, Radeon R9 390. Ubuntu is 20.04 LTS. No proprietary video drivers so I guess open source. I'd say I've had it installed for about 5 minutes until the problem started. I've made no changes to Ubuntu.

I will try those suggestions, thank you so much for your help.

you should be good with opensource drivers. if you wish to upgrade them, you need to upgrade the kernel. here is how you do it on LTS: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

back to rebooting - the reboot occurs when there is an issue with PSU, or if there is an overheating issue. if it works fine on windows we could probably excludethe PSU. so this leaves us with drivers for motherboard, CPU and GPU.

What motherbroard do you have?

CPU drivers are available with 20.04, however if you have the 3500X version it came later in the 2019, so you might want to make sure you have later kernel. 

also make sure the cooler and fan are attached well. i had this issue on intel GPU. one of the screws was kind of loose and it would overheat the CPU on occasion and reboot the PC. to check temperatures you can use psensor; [https://wpitchoune.net/psensor/](https://wpitchoune.net/psensor/)

GPU drivers - these will be opensource and apparently the older kernels would load the old radeon driver instead of amdgpu. see here for a possible solution usign kernel parameters (first answer):
[https://www.reddit.com/r/linuxhardware/comments/dd1fja/amdgpu_r9_390_hawaii_should_work_but_doesnt/](https://www.reddit.com/r/linuxhardware/comments/dd1fja/amdgpu_r9_390_hawaii_should_work_but_doesnt/)

from arch wiki:
> **R9 390 series poor performance and/or instability**

[COLOR=#202122][FONT=sans-serif]If you experience issues [[5]]("https://gitlab.freedesktop.org/mesa/mesa/-/issues/1222") with a AMD R9 390 series graphics card, set radeon.cik_support=0 radeon.si_support=0 amdgpu.cik_support=1 amdgpu.si_support=1 amdgpu.dc=1 as [kernel parameters]("https://wiki.archlinux.org/title/Kernel_parameters") to force the use of amdgpu driver instead of radeon.[/FONT][/COLOR]
[COLOR=#202122][FONT=sans-serif]If it still does not work, try disabling DPM, by setting the [/FONT][/COLOR][kernel parameters]("https://wiki.archlinux.org/title/Kernel_parameters")[COLOR=#202122][FONT=sans-serif] to: [/FONT][/COLOR]radeon.cik_support=0 radeon.si_support=0 amdgpu.cik_support=1 amdgpu.si_support=1

use temporary parameters first. if these parameters work we can help you make them permanent.
About kernel parameters: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

another option would be to load newer kernel. you can check current kernel with command

```
uname -a
```

20.04 has version 5.4 loaded by default. and oyu can load the HWE kernel as i indicated in link above.

---

