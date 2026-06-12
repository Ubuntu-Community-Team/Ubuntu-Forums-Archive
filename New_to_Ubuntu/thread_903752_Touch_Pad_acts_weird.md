---
title: "Touch Pad acts weird"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Edmin on 2008-08-28
Hi):P

I am quite a new bee to Ubuntu recently moved from windows to Ubuntu. I use a Dell XPS 1530 with Ubuntu 8.04 installed along with vista home edition. Everything has been good since the time i dual booted Ubuntu and Vista. I am facing few issues
1. Touch pad refuses to work :confused:, I am able to use a usb mouse without any problems. How do i enable it? I have tried to check out options under  
system - preferences - mouse but couldn't locate any touch pad tab. Would be great if any help could be offered.
2 The next issue i am facing is with my graphic card. I am not sure if 256MD Nvidia 8600M GT graphic card goes well with ubuntu!:rolleyes:
3 Looks like the web cam isn't working too!

---

### Post by ggaaron on 2008-08-28
For the touchpad part, run 'synclient -l' and then 'lshal | grep -i synaptics' in a terminal. First one should give quite much of output - if it does then your touchpad works (or should work/can be configured to work). Second should search your detected devices for synaptics (you can also try with alps).

---

### Post by plettpc on 2008-11-10
> **Edmin said:**
> Hi):P

I am quite a new bee to Ubuntu recently moved from windows to Ubuntu. I use a Dell XPS 1530 with Ubuntu 8.04 installed along with vista home edition. Everything has been good since the time i dual booted Ubuntu and Vista. I am facing few issues
1. Touch pad refuses to work :confused:, I am able to use a usb mouse without any problems. How do i enable it? I have tried to check out options under  
system - preferences - mouse but couldn't locate any touch pad tab. Would be great if any help could be offered.
2 The next issue i am facing is with my graphic card. I am not sure if 256MD Nvidia 8600M GT graphic card goes well with ubuntu!:rolleyes:
3 Looks like the web cam isn't working too!
Solved! Add i8042.nomux=1 to your kernel line in grub.

---

