---
title: "Kernel update ?"
date: 2017-07-13
forum: New to Ubuntu
---

### Post by mac187 on 2017-07-13
I have installed Ubuntu 16.04 LTS 64bit

Im new to Ubuntu so i have to ask this, i know im running this kernel -> 4.8.0-58-generic

Is it any newer kernel than 4.8.0-58-generic ? 

If is, should i update to the newer one, and how? 

Thanx

---

### Post by RobGoss on 2017-07-13
Hello and welcome, I'm sure we've all ask this question at one point but I was told when I ask this same question if your system is running as it should why even attempt to update the Kernel, in some cases if may even break some systems if there's something wrong with the new kernel if installed

you might find this page useful [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Just as a side note, I always Install Ubuntu and keep the kernel that's supplied with the new installation. I would only install a newer kernel if my system needs it at any given time which I haven't since I been using Ubuntu a few years now

I would have any system installation of a new Kernel is OK and should be safe, keep in mind not every system adapts well to system changes and may have issues

---

### Post by mac187 on 2017-07-13
SO if my system is running ok, then i dont need to update to new kernel? I was just hinking maybe there is some bugs that have been fixed and etc. but then i just leave it as it now :) thanx

---

### Post by RobGoss on 2017-07-13
Yeah sir that's correct if everything is running good I don't see and reason to install a newer kernel, I'm sure others may have a different opinion this is my experience with Linux

Hope this has help

---

### Post by vasa1 on 2017-07-13
> **mac187 said:**
> SO if my system is running ok, then i dont need to update to new kernel? ...
Kernel updates *which are suggested by the system* should be accepted in my opinion. They may include fixes to security issues.

---

### Post by ajgreeny on 2017-07-13
> **vasa1 said:**
> Kernel updates *which are suggested by the system* should be accepted in my opinion. They may include fixes to security issues.
+1 ^^^^^

As you are using 16.04 and now have kernel 4.8 series I assume either that you installed originally from the 16.04.2 point version or have manually updated to the **linux-image-generic-hwe-16.04**.

If so you should be updated further when necessary to the 4.10 series, which I think will be when the 4.8 series is no longer supported.
Normal updates will (or should) be all that is needed to keep your system fully supported and up to date.

---

### Post by mac187 on 2017-07-14
So how should i update to 4.10 series ? with safe and easy way ?

the newest series is 4.12 , should i update to 4.12 or 4.10 ?

---

### Post by vasa1 on 2017-07-14
> **mac187 said:**
> So how should i update to 4.10 series ? with safe and easy way ?

the newest series is 4.12 , should i update to 4.12 or 4.10 ?What is your problem? Has your system prompted you to upgrade your kernel?

---

### Post by mac187 on 2017-07-14
hehe no, i was just thinking maybe upgrading to new kernel may be do my system peformance better ? im new to ubuntu, im trying to learn so thats why im asking hehe

I only use linux, and going to use it all the way under education and later on work, never going back to windows :P

---

### Post by mastablasta on 2017-07-14
> **mac187 said:**
> hehe no, i was just thinking maybe upgrading to new kernel may be do my system peformance better ? 

with new hardware that is possible. as is with old if there is a fix/improvements of sorts. but be sure to check the kernel release notes and such to see if it actually brings any improvements to your system. otherwise security patches as well as some other patches do get to older versions as well.

---

### Post by ajgreeny on 2017-07-14
On 16.04 I am still using the 4.4.0-## series with no problems at all; my hardware is four years old, however, so certainly not new enough to require the latest and best(?) kernel series, but there is very often no need at all to bother using the most recent kernel version.

Just run normal updates and all should be fine for you as well.

---

### Post by mac187 on 2017-07-14
Ok, i bought my computer for 3 months ago, so the conclusion is just keep the kernel i have now? or update?

---

### Post by TheFu on 2017-07-14
> **mac187 said:**
> Ok, i bought my computer for 3 months ago, so the conclusion is just keep the kernel i have now? or update?

The simple answers have already been provided. 

In short, stay patched and stay on a supported Ubuntu release.  Kernels are patched from time to time. **sudo apt upgrade** will get those updates, but keep the same kernel with just the fixes.

16.04.2 support for the kernel you are on will end in August (less than a month).  At that time, you'll want to run **sudo apt dist-upgrade** to move to the 16.04.3 line. Then do the apt upgrade stuff. 9 months later, that kernel line will lose support. and 16.04.4 will be released.  dist-upgrade again to move to a supported line again. ... you get the idea.  You can safely run **apt dist-upgrade** all the time, if you prefer.

[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support) has a chart.

I will stay on 16.04.1 for 6 yrs on my 16.04 servers.  I have no need for newer kernels, just the security patches for the 4.4.x line. If I buy a new CPU/motherboard (like a Ryzen), then thee 4.4.x kernel won't work well. I **must** have a newer kernel since the ryzen CPU hardware requires it.

Most of my servers still run 14.04 with the 3.13.x kernel line. We will start migrating those to 16.04 next year. That will give us plenty of time to plan and test everything before impacting our users.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) explains the .2, .3, .4, .5, releases.  There is a chart which makes it clearer.  Be certain to scroll through the entire page to see all the different charts showing which kernels are supported for how long.

If you really, really, really, want to run the kernels provided by Linus, you can.  There is a how-to guide.  In the 1990s, I did that. It was a pain.  That just isn't needed any more for 99.999% of Linux users.

---

### Post by mac187 on 2017-07-14
Thanx for the answer :)

---

### Post by Dennis N on 2017-07-14
If the computer is fully functional, don't be concerned about the kernel. As suggested, just applying the kernel updates offered by the software updater is sufficient.

---

