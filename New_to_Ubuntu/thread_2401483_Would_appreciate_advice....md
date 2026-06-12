---
title: "Would appreciate advice..."
date: 2018-09-18
forum: New to Ubuntu
---

### Post by n2k12 on 2018-09-18
hello all. new user to ubuntu here! i have learned some of the basics and commands and driver installation methods for ubuntu. and i am up an running! i just have questions on optimization for performance. i am using the NOOP shceduler, have my cpu at performance mode using cpufrequtils. i have tried tweaking my graphics settings using driconf, however it says "no direct rendering devices detected" i have dri3 enabled, and checked. hardware accleration is enabled. so whats the go there? the other thing is, i was wondering about sysctl.conf tweaks, grub tweaks, etc. its a gaming machine with 16gb ram and an 8 core amd ryzen 1400 cpu, paired with an rx560. the other issue is, i am trying to overclock my gpu, and i have read on how to do so using the file in /sys/class/card0 that controls the clock speed, however its always stuck on 0. i did chown the file to my user, and saved it, and its back on 0 again. same with memclock. 


running ubuntu 18 lts x64. using the ppa repo oibaf drivers for my amd gpu. have latest mesa, vulkan ,all that. games work well. would just like to make sure the machine is optimized for max performance. 

running the LXDE desktop as i prefer it over the default one.

thanks guys for any help :)

edit: forgot to mention  i am running the liquorix kernel also.

---

### Post by QIII on 2018-09-18
Hello!

Don't ever chown system files and take ownership yourself.  Not a good idea to chown then at all.  They are meant to be run by specific users -- in this case *probably* root but maybe not.  Not by you for sure.  Doing such things can cause serious problems with your system.

I would suggest On Demand for your CPU.  You don't press your foot on the throttle pedal when you are sitting at a stop light, do you?  Let your hardware step on the throttle when it needs to.

I recommend against PPAs for a driver for AMD GPUs these days.  Ubuntu and AMD have a long bromance going on.  Ubuntu installs the appropriate AMDGPU driver when it detects a supported GPU.  There is no need for anything else, unless you want Vulcan, in which case you can add the AMDGPU-PRO proprietary overlay on to AMDGPU.

---

### Post by n2k12 on 2018-09-19
hi thanks for your response. i tried what you said, and then tried the amd drivers from the AMD website, and lost massive amounts of performance. they are total trash. went back to my ppa added drivers and performance doubled. i chose performance mode for my cpu, because of gaming. i will try on demand and see how that goes. i got vulkan up and running through a PPA as well. and got directx 11 titles running perfectly to through lutris. i decided to research some things for myself. paid off. very happy

---

