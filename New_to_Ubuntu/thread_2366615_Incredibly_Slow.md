---
title: "Incredibly Slow"
date: 2017-07-19
forum: New to Ubuntu
---

### Post by spiritsavage on 2017-07-19
I have a Lenovo w520 with Intel i7 3.1 GHz (after turbo boost) quad-core multi-thread (8 total) laptop.  I have 10 GB total Ram and just under that as usable.  I have 64-bit Windows 10 Creators Update.  I am running the latest Oracle VM and have allocated a 2048 MgB Ram limit on the latest long-term supported 32-bit version of ubuntu.  I installed all updates while installing ubuntu.  When powering on ubuntu, it takes about ten minutes for the desktop to come up.  It also runs with about a 3-4 second delay when moving the mouse and freezing when I try to bring up applications.  I tried running 3D input, and I've discovered I can only use one thread on 32-bit version.  The Oracle VM would not let me install the 64-bit version.  I later discovered this may be due to visualization.  However, with my specs, I think the 32-bit version should work.  I am new to Linux and relatively new to programming, with minor experience in hardware, just to let you know where I'm at.  Could anyone help?  Thank you!

---

### Post by BenginM on 2017-07-19
Salutations! and welcome to the forums.

that's high end specs indeed .. maybe it's the hosts fault.. i mean are you running other applications and services in the background beside the Oracle VM ?

---

### Post by QIII on 2017-07-19
If you are running Ubuntu, the Unity DE is graphics hungry.  The virtual graphics adapter offered by VirtualBox is weak.  How much video memory did you assign to the VM?

---

### Post by vocx on 2017-07-19
> **spiritsavage said:**
> I have a Lenovo w520 with Intel i7 3.1 GHz (after turbo boost) quad-core multi-thread (8 total) laptop.  I have 10 GB total Ram and just under that as usable.  I have 64-bit Windows 10 Creators Update.  I am running the latest** Oracle VM and have allocated a 2048 MgB Ram limit on the latest long-term supported 32-bit version of ubuntu**.  I installed all updates while installing ubuntu.  When powering on ubuntu, it takes about ten minutes for the desktop to come up.  It also runs with about a 3-4 second delay when moving the mouse and freezing when I try to bring up applications.  I tried running 3D input, and I've discovered I can only use one thread on 32-bit version.**  The Oracle VM would not let me install the 64-bit version**.  I later discovered this may be due to visualization.  However, with my specs, I think the 32-bit version should work.  I am new to Linux and relatively new to programming, with minor experience in hardware, just to let you know where I'm at.  Could anyone help?  Thank you!

Please realize that performance of an operating system cannot be reliably measured inside a virtual machine because the operating system is not actually using the hardware components of your real machine, such as processor, cache, memory, graphics card, and data buses. This is a reason why when developing and testing a new version of the Linux kernel, or Ubuntu as a whole, it is not ideal to test it inside a virtualized environment. For actual testing, the operating system should be installed on the hard drive itself, and should have access to the motherboard directly.

In other words, you have several points where the problem may be, not including Ubuntu.
[LIST]
[*]First, some BIOS include a switch to toggle on and off the virtualization capabilities of the processor. The BIOS is that blue screen that you can get by pressing the keys «Del», or «F2», or «F11», or other, when the systems boots. Maybe you need to check that virtualization is activated.
[*]Second, Windows is the host operating system. It may have a problem of not running appropriately VirtualBox, or not virtualizing Ubuntu correctly.
[*]Third, the VirtualBox program may be at fault. Did you try the various options in the settings? Did you try another virtual machine software, such as VMWare?
[*]Once installed VirtualBox may actually have bugs. They release incremental versions continuously. So, maybe now they are at version 5.1.3, and you have some issues. Then, perhaps in a couple of weeks, you get a notification that a newer version 5.1.4 is available. So perhaps upgrading your version of VirtualBox also improves the behavior of your installed guest operating system.
[*]Fourth, last time I tried, VirtualBox had what they call "Guest additions", which is a collection of drivers that make the guest operating system, Ubuntu in this case, interact better with the host operating system, that is, Windows. In particular, these guest additions improve the graphics performance of the virtualized machine, so that the mouse transitions better between the host and the guest. It also provides better screen resolution, window auto resizing, and smoother animations, kind of like adding the proprietary Nvidia drivers to a real Ubuntu installation. I don't know what exactly the guest additions are, but they kind of add a virtualized high end graphics card, and the corresponding drivers to the virtualized operating system.
[*]Also, whenever you upgrade the VirtualBox program, usually you need to reinstall the guest additions to keep the graphics performance as described in the previous point.
[/LIST]

In other words, this is not a problem of Ubuntu, but of the layers on which it sits, namely VirtualBox and Windows. Remember, Ubuntu is not actually touching your processor, RAM, and graphics card. It is touching a virtualized processor, a virtualized amount of RAM, a virtualized graphics card, etc. You should probably ask the support channels of VirtualBox and Windows about this problem, and whether they have tips about the configuration that would make Ubuntu install and run better for your specific version of CPU, Windows, and VirtualBox. For example, why doesn't VirtualBox allow you to install a 64-bit Ubuntu? Well, this is something you should ask the VirtualBox people, not the Ubuntu people. For anything else, regarding the actual use of Ubuntu, you may ask in this forum.

---

### Post by miqrojamie on 2017-07-20
A virtual machine is never going to provide the same performance as a real machine. Windows processes in the background, the amount of allocated resources, etc. will affect the VM's response and such. As previously stated, VirtualBox has a weak video processor.

If you really want to continue using virtual machine, make sure you install the VirtualBox guest additions. However, I'd recommend to get a taster of an operating system, you boot from a LiveCD and try it out.

---

### Post by vocx on 2017-07-20
> **miqrojamie said:**
> A virtual machine is never going to provide the same performance as a real machine. Windows processes in the background, the amount of allocated resources, etc. will affect the VM's response and such. As previously stated, VirtualBox has a weak video processor.

If you really want to continue using virtual machine, **make sure you install the VirtualBox guest additions**. However, I'd recommend to get a taster of an operating system, you boot from a LiveCD and try it out.
Despite what I wrote in the previous post, I have used Windows 7 and Ubuntu in a virtual machine with VirtualBox without problems. I just made sure to install the guest additions. I don't think it was slow, and I definitely recommend it.

My intension with the previous post was just to point out that in case of slowness the problem should be investigated first with the virtualization software (VirtualBox), and not the guest system (Ubuntu).

---

### Post by HermanAB on 2017-07-20
Regular Ubuntu will be slow even with VMWare Guest Additions.  You should use Xubuntu/Lubuntu - it will run smoothly.  

If you want to have real speed, then use Slackware.  Slack simply cuts out all the cruft and runs extremely fast compared to Ubuntu.

---

### Post by ajgreeny on 2017-07-20
I have been running Ubuntu 16.04 64bit as a VM in VBox 5.1.24 (just updated from 5.1.22 a few minutes ago) and it is running just as fast as any other of the *ubuntu family of OSs.

My host is Xubuntu 16.04 64bit on an i5-3570-K with 8GB ram but no separate video card, just the integrated Intel chip. The VM has 4GB ram and 128MB video memory allocated, so I am not in agreement with HermanAB when he says Ubuntu with unity will always run slowly.  I wonder if it is something more related to the settings you have for the Ubuntu VM?

Tell us all the settings you use for the VM and we may have more clues about how to help you.

---

### Post by miqrojamie on 2017-07-20
@ajgreeny: The speed of your VM could be because you are running Linux on Linux host, while this user is using a Windows host. Just keep that in mind. ;)

---

### Post by vocx on 2017-07-20
> **miqrojamie said:**
> @ajgreeny: The speed of your VM could be because you are running Linux on Linux host, while this user is using a Windows host. Just keep that in mind. ;)
But... I agree with ajgreeny, and don't agree with HermanAB. I can confirm I was running Ubuntu on Windows 7. After installing the guest additions, the Ubuntu guest worked pretty well. I was not running games or anything heavy, just browsing, opening IRC, and normal things like that, and the system was just as responsive as I was expecting.

The problem the OP describes could have many causes. I do not blame Ubuntu or Unity.

---

### Post by mastablasta on 2017-07-21
> **spiritsavage said:**
>  The Oracle VM would not let me install the 64-bit version. 

do oyu have virtualization feature of your CPU enabled in BIOS? if not, this could also explain slowness.

in any case Xubuntu is faster as it does't need GPU power to draw the desktop itself.

---

