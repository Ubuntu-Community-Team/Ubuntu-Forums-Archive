---
title: "The relationship between drivers and the kernel"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Senator82 on 2008-11-30
I recently switched to Ubuntu 8.04 for everything except gaming and .NET development. I like it so far. I learned Windows by tinkering so I am doing the same for Linux. 

I am trying to understand what the kernel is. It sounds like it is Linux and the rest is just a pretty shell. I have run into some troubles after a recent kernel upgrade (.21 to .22). I have a Geforce 9800gtx+ which the stock kernel does not have drivers for. I followed some instructions I found here and installed the latest Nvidia drivers. It worked great and I had no issues until the kernel upgrade. Now it boots at 800x600 and my understanding, correct me if I am wrong, is that I will need to install the drivers again under the new kernel? Will I need to do this for every kernel upgrade? What does "installing" a driver do? Patch it into the current kernel?

I appreciate any insight/help that anyone can give me. Thanks!

---

### Post by sdennie on 2008-11-30
You can probably find very good guides on what the kernel is by searching google however, there is a fix to your immediate problem: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573").  Basically, drivers are tied to the kernel and so to make a kernel upgrade be seamless, some mechanism has to be in place to install any externally installed kernel modules (drivers) for the new kernel.  The link above should make future kernel upgrades install the nvidia driver you are using without any intervention on your part.

---

### Post by sdennie on 2008-11-30
I forgot to mention that the guide I posted won't fix your immediate problem but will only prevent it from happening on future kernel upgrades.  You'll still have to re-install the drivers in your current kernel.

---

### Post by Senator82 on 2008-11-30
Cool. I will do that. Thanks for the help.

---

### Post by SunnyRabbiera on 2008-11-30
Linux is a kernel, but it is also acts as a OS too.
We refer to Linux as both as when linux is on its own without a fancy GUI or anything it still behaves like a traditional OS.
Linux sort of redefines the border of OS and kernel, in the windows world you have Dos/NT as a kernel and its operating system is windows.
Windows provides the graphic frontends and core operations while Dos/NT provides the backbone.
In the OSX world, BSD is the kernel (technically) while OSX is its graphic frontend.
But linux is a different case, you can use linux on its own without a GUI and without needing to worry about adding extra nonsense you dont need.
This is why Linux is ideal for servers as well as BSD though BSD acts more like an OS then a kernel.
But this also makes both very flexible and able to use different interfaces and such, and you are not locked in like windows/ OSX

---

### Post by Senator82 on 2008-11-30
Do people typically remove old kernel versions or just stockpile them?

---

### Post by SunnyRabbiera on 2008-11-30
> **Senator82 said:**
> Do people typically remove old kernel versions or just stockpile them?

Usually the kernels are merged into one, the only reason you may see so many kernels during boot is that the other kernels are mainly for backup so if kernel a doesnt work kernel b is there to help

---

### Post by oldos2er on 2008-11-30
> **Senator82 said:**
> 
I am trying to understand what the kernel is. It sounds like it is Linux and the rest is just a pretty shell. I have run into some troubles after a recent kernel upgrade (.21 to .22). I have a Geforce 9800gtx+ which the stock kernel does not have drivers for. I followed some instructions I found here and installed the latest Nvidia drivers. It worked great and I had no issues until the kernel upgrade. Now it boots at 800x600 and my understanding, correct me if I am wrong, is that I will need to install the drivers again under the new kernel? Will I need to do this for every kernel upgrade? What does "installing" a driver do? Patch it into the current kernel?

I appreciate any insight/help that anyone can give me. Thanks!

 Did the instructions you followed tell you to go to System, Administration, Hardware Drivers to install your Nvidia drivers? Because if you install them this way, they should be automatically reconfigured for any new kernels you get through package updates.

 On Linux, drivers are compiled into the kernel as modules.

---

### Post by markbuntu on 2008-11-30
The kernel needs some proprietary modules for it to work properly with the nvidia driver. The kernel automated build got confused about which nvidia kernel modules it was supposed to load and so it left them out for you to add manually later. 

This a actually not a bad thing thing because if it had loaded the wrong ones.....

Anyway, the newer kernels are able to use dkms which is a dynamic kenel module something or other which allows the kernel to load dkms modules without needing to be rebuilt which is another good thing since the nvidia drivers use dkms kernel modules. If you had just the nvidia dkms kernel modules you could run dpkg with them and that would be all you need to do. I did this once with an ati driver that lost its kernel modules in an update.

---

