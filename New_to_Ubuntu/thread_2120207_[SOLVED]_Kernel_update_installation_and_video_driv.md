---
title: "[SOLVED] Kernel update installation and video drivers"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by Garrigus Carraig on 2013-02-25
[Relevant specifications: Ubuntu 12.04 Precise Pangolin, Acer Aspire 5520, Nvidia GeForce 7000M/nForce 610M, Nvidia driver 302.07]

When I first started running Ubuntu a month ago, the video was screwed up (low resolution, console mode illegible). I eventually attempted to remedy this by installing the Nvidia drivers, and was successful. About ten days ago, I followed the Software Update recommendations to install the kernel updates, and the video broke (low resolution, Unity mode illegible). I was able to reinstall the Nvidia drivers (with some difficulty this time), and now the video is good again.

I am being offered another kernel update, and of course I am reluctant to install it. I only recently found out about the Nouveau drivers that apparently come with Ubuntu.

So my question is: Is there a reliable way to update the kernel as recommended without screwing up the video?

---

### Post by carl4926 on 2013-02-26
If you install the nvidia driver manually you will need to do so each time there is a kernel update.
But for me, using the nvidia-current from the sources, it all seems fine and they update in sync

---

### Post by Garrigus Carraig on 2013-02-27
Thanks, Carl. I downloaded the drivers, reviewed the installation procedure, held my breath, and updated the kernel. And my video was unaffected. So I didn't need to do it. 

> **carl4926 said:**
> But for me, using the nvidia-current from the sources, it all seems fine and they update in sync
I guess I don't know what you mean by "using the nvidia-current from the sources". Care to expand on that?

---

### Post by Lisiano on 2013-02-27
Open up Software Sources and in the last tab you will find Additional Drivers, there you can mark that you want to use the nvidia-current drivers. Turning on proprietary drivers this way, ensures your system will make sure you have the latest available drivers (As in, the latest nvidia-current) as well as making sure it is preserved between kernel updates.
You may also do this by issuing the following
```
sudo apt-get install nvidia-current
```
OR by [clicking here]("apt://nvidia-current")

EDIT: **WARNING**
Make sure you have also installed [linux-headers-generic]("apt://linux-headers-generic")!!! If you don't the driver might fail to install. There has been a bug once 12.10 was released that prevented it from being automatically installed (Older Ubuntu versions are not affected). Not sure if it was fixed.

---

### Post by Garrigus Carraig on 2013-02-27
Got it. Thanks, Lisiano!

---

### Post by Garrigus Carraig on 2013-03-03
[COLOR=#696969][FONT=garamond]*Umm... how do you mark a thread [SOLVED]? I can't find it under Thread Tools. Maybe it was moved in the redesign?*[/FONT][/COLOR] :-k

---

