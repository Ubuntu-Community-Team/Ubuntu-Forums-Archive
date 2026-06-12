---
title: "Safe shut-down when nothing else works"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by chrissie-c-l on 2013-11-22
Because of other issues I'm still trying to figure out and may go into on another forum post, On a restart I just have a screen with "ubuntu" and the "I'm thinking" dots. Ctrl-alt-f1 does not bring me into a console, and alt- prt sc reisub also doesn't do anything. Are there any other ways to safely shutdown, or am I stuck with the power button at this point? 

At at least it's a fresh re-install that still doesn't have functioning internet or ability to mount USBs, so I don't think I can make it that much worse at this point.

---

### Post by electrohandyman501 on 2013-11-22
A little more information would help. What hardware are you working with, and what version/release software are you trying to use. 
Did you boot with a LiveCD or USB, to test your hardware and such before the actual install.

---

### Post by chrissie-c-l on 2013-11-22
I was looking for generalities, especially for if I ever get in this situation again, but here are the specifics,

I had the base 13.04 Raring Ringtail running, but no updates since I don't have functioning wireless or ethernet connectivity.  Since lspci -v was still detecting my wireless card, I was thinking the issue must be in the driver.  I had my entire directory / backed up on an external hard drive before things started going down hill, so I copied /lib/modules from my external hard drive to /lib/modules on my computer and restarted it. The backed up operating system had been updated to 13.10.  

Once I manage to get it properly shut down, I'm thinking of trying to start with an installation of 13.10 and then somehow try to sync it back up with the external hard drive.  Hopefully that will fix the wireless and ethernet problems, mounting usb problems (I was unable to even manualy mount two similiar FAT usbs), and restore my system settings and program installations.

---

### Post by DuckHook on 2013-11-23
Hi chrissie-c-l

I'm afraid you can't go mixing drivers between two different releases without really bad things happening. It doesn't work like that. Each release builds the drivers specifically for the kernel it has. If you mix 13.04 drivers with 13.10 kernels, your system will either freeze or go into kernel panic. In your case, the computer's behaviour is only to be expected and you have no choice but to do a hard powerdown.

At this point, you must reinstall from a pristine state. Given that you copied over the entire /lib/modules/ directory (don't DO that), things are too gummed up to try straightening out in bits and pieces. However, as mentioned in a previous thread, you really should be looking at something more stable for your HW and your current expertise and install 12.04.

If you continue to run into network problems, then post on these forums about those issues specifically. Attack each problem individually and you will have a well-behaved system before you know it--take a chainsaw to problems requiring a scalpel and be prepared for a bloody mess. Under no circumstances should you go mixing modules or apps between different distros or releases. It's guaranteed to lead to nothing but heartache and misery.

A good start would be to let us know what your HW specs are, especially CPU, amount of RAM, video card, video RAM, make/model of network cards and anything else you can think of. The more info the better.

---

### Post by chrissie-c-l on 2013-11-23
Would it have worked if it had been a 13.10? Is there a way to go about copying over program files and drivers to the same OS without screwing everything up?

I was fine with my operating system until a week ago when I started poking at it, from now on I'll do my poking in a virtual OS until I'm absolutely sure I won't screw it up.

---

### Post by DuckHook on 2013-11-23
Don't take this the wrong way because it is not meant as a reproach--just a statement of fact--but your question is indicative of a Windows mindset. In Windows, users go to sites that they know nothing about to download apps and drivers that they know nothing about, and then wonder why viruses are such a problem in the Windows-sphere. But I digress. The point is that even when it works, this creates a mindset where drivers and apps are roughly interchangeable, like different drill bits that can be attached to an electric drill. In the Linux-sphere, the metaphor is much different. Drivers are either already compiled into the kernel or else are loaded as modules that act as extensions to the kernel. However, this latter technique is possible only if the kernel is informed that the module is waiting for its attention and has system hooks prepared exactly where the kernel expects to find them (and that also behave exactly as the kernel expects). For lack of a better word, Linux is much more "organic" than Windows. Therefore, you cannot just "plug in" a driver or an app and expect it to work. In fact, most drivers need to be compiled for the intricacies of the specific kernel version. Example: two systems may run 13.10, but if one system is on 13.10.9 and the other differs by just one maintenance upgrade, say, 13.10.8, then the one driver may work or it may not on the other system. Even if it works, it may give subtly wonky results that you won't be able to pin down until you remember that you assembled your system out of mismatched parts like some kind of Frankenstein's monster.

The proper way to install drivers in Linux is to:

1. download it from the repository for that specific distro, flavour and version, and
2. let the system *build it* into its module library using the module build tools that come with each distro.

It is possible to substitute another repository or even source code for step (1) above (at the risk of introducing Trojans/rootkits/keyloggers into your system), but you cannot skip step (2). Even if step (2) consists of nothing more than configuring some files for a pre-built binary, it still needs to be done.

This will ensure that the module is built/compiled with all of the system's quirks and eccentricities properly accounted for. The counterintuitive thing is that, once modules are built in this painstaking way, the resulting system tends to be so robust that if you take out your HDD and boot it up on a totally different machine (within limits), the kernel will instantly sense and switch in the proper modules for the new hardware and the system boots up just like it would on your old machine. Don't take this too far. Different video cards don't mix, you can't boot an x86 kernel in an ARM machine, etc, but by and large, a decent system can be installed on a USB stick and it will boot up on most standard computers. I use this trick to carry my own computing environment with me when visiting friends or relatives. I sometimes even manage to pique their interest in Linux.

I really encourage you to install a VM and poke that OS until it breaks. This is the best way to do crazy experiments with Linux. Don't do these things on your production box.

---

### Post by ian-weisser on 2013-11-24
> **chrissie-c-l said:**
> Would it have worked if it had been a 13.10? Is there a way to go about copying over program files and drivers to the same OS without screwing everything up?

Duckhook is right.

Program files are not the same as drivers. And neither are the same as your data.

Data is copyable. Program files (like stuff you wrote yourself) *may* be copyable. It depends. Compiled language applications *must* be recompiled to work with updated libraries and kernels. Kernel modules (drivers) are compiled, and must be recompiled with each new version of the kernel. Generally, you let the package manager handle all that for you.

If you have custom scripts, custom applications, custom kernel modules, custom kernels, etc., then document how you installed/uninstalled each one. You *will* need to refer to it. You can use links and makefiles and lots of other tools to simplify install/uninstall...but you still need to track and administer the customizations on your system.

And backups. Backups. Backups. Regular, reliable backups. Backups are *easy*.

---

