---
title: "can't completely fill the screen when within VirtualBox OSE with WindowsXP"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by mitchelljj on 2008-05-18
Hi,

I can't completely fill the screen when within VirtualBox OSE when running Windows XP as a virtual machine.

I have been able to get more of my screen filled by doing the following:
a.) Change to full screen mode via ctrl + f
b.) Change the screen resolution within XP to the highest that is listed which is 1024 by 768 pixels

But I still have some unused screen even after doing the above 2 steps

Any other suggestions?

Thanks,

John

---

### Post by jbrown96 on 2008-05-18
I believe you need to install the guest additions, which should allow higher resolutions. When you are in Windows XP, try the Virtualbox menus and one of them should give instructions on getting it. Download and mount as an iso (I believe it does this automatically). then install in Windows. Try to change resolution in Windows and there should be more options. If you want true fullscreen, set it to be the same resolution as your monitor.

---

### Post by HotShotDJ on 2008-05-18
> **jbrown96 said:**
>  Try to change resolution in Windows and there should be more options. If you want true fullscreen, set it to be the same resolution as your monitor.Once the guest additions are installed, full screen should happen automagically by hitting the Right Ctrl+F key

---

### Post by MyR on 2008-05-28
> **HotShotDJ said:**
> Once the guest additions are installed, full screen should happen automagically by hitting the Right Ctrl+F key

Also, make sure you increase the guest video memory in the virtualbox general settings.  For instance, 1920x1200 will require at least 10MB.

peace

---

