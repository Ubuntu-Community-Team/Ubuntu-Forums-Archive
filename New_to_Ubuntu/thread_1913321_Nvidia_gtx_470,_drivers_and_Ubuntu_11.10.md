---
title: "Nvidia gtx 470, drivers and Ubuntu 11.10"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by Nick_Kats on 2012-01-22
Two days ago, I decided to install Ubuntu 11.10 on my desktop PC. Everything works fine until now,
but sometimes the screen freezes and I have to reset my PC.
I did some research on what might be the case but I did not figured out much, except that this screen freezing may be caused by the graphics driver.
My setup is:
```

nick@nick-ubuntu:~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation GF100 [GeForce GTX 470] (rev a3)
01:00.1 Audio device: nVidia Corporation GF100 High Definition Audio Controller (rev a1)
nick@nick-ubuntu:~$ lsmod | grep nvidia
nvidia              10390874  40 

```Anyone had a similar problem? If yes, how did he/she solve it?

Thank you in advance :D

---

### Post by TeoBigusGeekus on 2012-01-22
Did you install the nvidia proprietary drivers?
(from Additional Drivers)

---

### Post by Nick_Kats on 2012-01-22
Yes I did. But I installed the one marked as recommended.
From the additional Drivers window I see that the NVIDIA accelerated graphics driver (version current) [Recommended] is activated and currently in use.

---

### Post by TeoBigusGeekus on 2012-01-22
Try with an older driver and see how it goes.

---

### Post by Nick_Kats on 2012-01-22
I re - installed the driver and I hope that there will be no more freezes. If the problem continues to exist, I will install previous drivers. 
Thank you for the advice :D

---

