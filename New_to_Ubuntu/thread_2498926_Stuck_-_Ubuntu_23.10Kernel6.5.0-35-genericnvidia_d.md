---
title: "Stuck - Ubuntu 23.10/Kernel:6.5.0-35-generic/nvidia driver 535 (proprietary, tested)"
date: 2024-07-04
forum: New to Ubuntu
---

### Post by comoema on 2024-07-04
I had a working configuration where my NVIDIA graphics card was working correctly (same 23.10, kernel 6.5.0-35, same driver 535 tested).
I messed up with some stuff while updating the kernel and more confusion was generated right after.

Im just stuck, I followed multiple posts online and went through multiple approach but non of these worked successfully. 

Im a new to Ubuntu so not sure really how to fix the issue since I tried multiple time.
I wanted to start with fresh installation of the OS but I setup other software already and Im not keen to take this way (I try to keep it as last chance).

Im asking if anyone is keen to guide me step by step and see if can make it working again, help is much appreciated (Right now using driver 535 but cant communicate with the graphics card anymore and not visible in nvidia control panel- please refer to screenshot - issue : [FONT=monospace][COLOR=#000000]VIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running[/COLOR][/FONT]).

Thank you!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293940&stc=1[/IMG]

---

### Post by TheFu on 2024-07-04
Before going too much farther, realize that support for 23.10 ends this month.  You need to move to 24.04 ASAP.

If that surprises you, read up about the different types of releases and why those exists and the support periods for them.  In short, only use LTS releases like 24.04 and 22.04.

A few years ago, to aid my sanity, I removed nVidia hardware from my systems and switched to AMD GPUs.  AMD GPU drivers are built into the kernel, so there's no hunting for the correct driver.

---

