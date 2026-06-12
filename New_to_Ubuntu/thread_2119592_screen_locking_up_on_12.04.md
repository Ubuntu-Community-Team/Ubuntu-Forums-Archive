---
title: "screen locking up on 12.04"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by stm146 on 2013-02-24
The screen keeps locking up up on my Dell 9150. The mouse still moves but nothing else works. All I can do is reboot using alt+ctrl+sysreq reisub. This problem can happen after a few minutes or a few hours.

After rebooting Syslog shows this error message was logged 475 times at the time the problem happened: 
Feb 24 12:13:14 ubuntu kernel: [ 1582.381640] [drm] nouveau 0000:01:00.0: PFIFO_CACHE_ERROR - Ch 1/1 Mthd 0x187c Data 0x00000000.

This error message was logged 4 times: 
Feb 24 12:13:14 ubuntu kernel: [ 1582.390297] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 1 Get 0x00022000 Put 0x0001e338 State 0x80022054 (err: INVALID_CMD) Push 0x00000000. 

This pair of error messages was logged 20 times: 
Feb 24 12:13:14 ubuntu kernel: [ 1582.391587] [drm] nouveau 0000:01:00.0: PGRAPH - ERROR nsource: METHOD_CNT nstatus: INVALID_STATE
Feb 24 12:13:14 ubuntu kernel: [ 1582.391621] [drm] nouveau 0000:01:00.0: PGRAPH - ch 1 (0x000ed000) subc 6 class 0x008a mthd 0x1e64 data 0x00000044

Finally this error was logged 10 times :
Feb 24 12:13:14 ubuntu kernel: [ 1582.393584] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 1 Get 0x00022000 Put 0x0001e4d8 State 0x80022054 (err: INVALID_CMD) Push 0x00000000

Does this information identify the problem or is any other information needed?

What do I need to do to find a solution?

---

### Post by deadflowr on 2013-02-24
The problem seems to be with the graphics driver.
Your nvidia card is using the open source driver (nouveau),
You are probably better off trying out the closed source driver from nvidia.

Look here on how to install the nvidia drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by stm146 on 2013-02-24
Thanks deadflowr. The Ubuntiu nvidia HowTo says that nouveau "may not work with the very latest video cards or technologies from NVIDIA". My nvidea card is around 5 years old so it's unlikely that this is the problem. Think I'll see if I get any other suggestions before I try changing drivers.

---

### Post by stm146 on 2013-03-17
I've had no other suggestions, so I'm trying to follow deadflowr's advice. I went to [https://help.ubuntu.com/community/Bi...erHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") then selected option 1 [nvidia-current]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers") and downloaded [295.40-0ubuntu1.3]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1.3") but I get no notification about availability of restricted drivers even after rebooting. According to the installation instructions I should go to System -> Administration -> Additional Drivers to install the driver, but I don't know what this means or how to do it (I really am an absolute beginner!), Could someone tell me what I need to do?

---

### Post by stm146 on 2013-03-17
Think I've figured out how to do this - went to Dash Home and entered "drivers" in the search box & an additional drivers icon came up. Clicking this took me to a list of proprietary drivers. I selected the recommended driver, rebooted and system details now shows video driver as "unknown". Hopefully this will resolve the problem - I'll know in a few days.

---

### Post by deadflowr on 2013-03-17
After installing the nvidia driver, you'll need to configure it.
Run
```
sudo nvidia-xconfig
```

in a terminal, which will, or should produce an xorg file, from which the system will later on read.
Good luck, and after hopefully it works.
after reboot, if all is well, look at the syslog you post from earlier to see if any strange errors show up like the last time.

---

### Post by stm146 on 2013-03-26
Driver installed & configured & problem resolved.
Thanks deadflowr!

---

