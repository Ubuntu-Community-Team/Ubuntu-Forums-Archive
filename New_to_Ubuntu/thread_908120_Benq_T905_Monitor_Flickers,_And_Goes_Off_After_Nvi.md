---
title: "Benq T905 Monitor Flickers, And Goes Off After Nvidia Install"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by nikki93 on 2008-09-02
I have an NVidia GeForce FX 5600 graphics card (old, I know). I tried out Ubuntu on my laptop when I was on vacation, and I liked it, and now I've returned home and so want to install it on my desktop.

The desktop has a BenQ T905 19" monitor.

After during and after installation, there were no problems at all. After the installation, it told me about some updates, mostly to the kernel and the headers. It also asked me whether it could get the 'restricted Nvidia drivers', and I chose 'yes'.

It installed fine, and asked me to reboot.

After rebooting, the monitor worked fine for a while, and shortly, started flickering and trying to adjust the screen position and size. I tampered around with the monitor controls, but it didn't help. After a while, the monitor went on, off, on, and off, permanently. I couldn't see anything. I rebooted the computer, but its fine till the splash screen and again goes off after that.

I tried the dpkg-reconfigure for xserver-xorg, but it didn't help. I also removed the words 'splash' from my grub menu.lst as was suggested in some other post, but that didn't help either.

Any ideas? Thanks for your help! :)

BTW: Check out my computer game at: [http://www.grall.uni.cc](http://www.grall.uni.cc)! :)

---

### Post by alienexplorers on 2008-09-08
What driver are you using, the nvidia-glx-new one?  Try using envy, found in the repositories.  Remove the old driver.  Do not reboot.  Now load the 96.xx.xx driver.  When the install completes reboot and see what happens.

---

