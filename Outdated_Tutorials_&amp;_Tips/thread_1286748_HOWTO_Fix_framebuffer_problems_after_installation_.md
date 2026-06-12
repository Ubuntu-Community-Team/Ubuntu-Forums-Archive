---
title: "HOWTO: Fix framebuffer problems after installation of new kernel in Acer Aspire 4520"
date: 2009-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by mo0nykit on 2009-10-09
[LEFT]by Kristofer Monisit

[SIZE=3]**_ Author's Message_**[/SIZE][INDENT]This is my first HOWTO in my whole experience with Linux. Many of the statements here are my personal opinions. I just want to give back to the community who also helped me form these opinions. I hope this would be of help. I welcome corrections and confirmations :)
[/INDENT][SIZE=3]**_Statement of the Problem_**[/SIZE][INDENT]I had just installed my new custom kernel. Now the framebuffer does not work! Here are the symptoms of framebuffer problems:

[LIST]
[*]The boot-up process has been successful, without any glitches. The GUI looks fine with the correct resolution (after having installed Nvidia proprietary drivers). BUT when I switch to a virtual console, everything is garbled, nothing is comprehensible.
[*]Upon shutting down, the screen is also garbled. I couldn't see the shutdown splash (Although I could see the bootup splash).
[/LIST]
 [/INDENT][SIZE=3]**_Hypothesis of the Cause of the Problem_**[/SIZE][INDENT]
[LIST]
[*]The **initrd** corresponding to the new kernel does not load the needed modules for framebuffer rendering
[*]The kernel boot options lack the **vga** option
[/LIST]
[/INDENT][SIZE=3]**_Objective_**[/SIZE][INDENT]Get the framebuffer to work so that I could use the virtual console.
[/INDENT][SIZE=3]**_Overview of the Solution_**[/SIZE][INDENT]This HOWTO will be presented in four parts:

[LIST]
[*]PART 1. Compiling and customizing the kernel
[*]PART 2. Installing the kernel
[*]PART 3. Installing the Nvidia proprietary drivers
[*]PART 4. Fixing the framebuffer problem
[/LIST]
_PART 1_ illustrates my preferred method of compiling and installing the kernel. In this HOWTO, we will be using the **2.6.28 kernel with Ubuntu patch 15.52** It needs to be presented in order to provide a background pertaining to the important framebuffer modules.

_PART 2_ contains a critical step before installing the kernel, which when followed correctly, you no longer need to proceed to PART 4.

_PART 3_ provides instructions for uninstalling the Nvidia drivers (for the **current** kernel) and then installing them (for the **new** kernel) downloaded from the official [Nvidia site]("http://www.nvidia.com/object/linux_display_ia32_185.18.36.html").

_PART 4_ provides step-by-step instructions for fixing the framebuffer problem AFTER your kernel image has been built and installed. You might just want to get the framebuffer to work, and your virtual console to be usable. You can jump directly to this part. If something confuses you, try reading up on the preceeding parts.
[/INDENT][SIZE=3]**_Revision Notes_**[/SIZE]

[LIST]
[*]October 11, 2009 -- First Edition
[*]October 13, 2009 -- Rearranged some initial sections, placed "Statement of the Problem" closer to the beginning.
[/LIST]
[SIZE=3]**_Author's Computer Specs (Test Platform)_**[/SIZE]

[LIST]
[*]Acer Aspire 4520 laptop
[*]AMD Turion64 X2 1.8Ghz (I'm only using the 32-Bit Ubuntu)
[*]160GB HDD (12GB ext3 for Ubuntu, 4GB swap, the rest is for Windows)
[*]2GB RAM
[*]Nvidia nForce 610m (motherboard chipset)
[*]Nvidia GeForce 7000m (integrated graphics card)
[*]Running Ubuntu 9.04 Jaunty Jackalope
[*]Kernel source 2.6.28 with Ubuntu patch 15.52
[*]Nvidia installer ([NVIDIA-Linux-x86-185.18.36-pkg1.run]("http://www.nvidia.com/object/linux_display_ia32_185.18.36.html"))
[/LIST]

[B][U][SIZE=3]External References[/SIZE]
[/U][/B]Ubuntu Community Wikis

[LIST]
[*][KernelCompile]("https://help.ubuntu.com/community/Kernel/Compile")
[*][BinaryDriverHowtoNvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
[*][NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
[/LIST]
Ubuntu Forums

[LIST]
[*][Framebuffer console during boot]("http://ubuntuforums.org/showthread.php?t=477080")
[*][Gutsy Framebuffer HOWTO]("http://ubuntuforums.org/showthread.php?t=652038")
[*][[ubuntu] Screen flicker on shutdown and reboot]("http://ubuntuforums.org/showthread.php?t=1268335")
[*][[SOLVED] ]("http://ubuntuforums.org/showthread.php?t=1282338")[Screen flicker on virtual console Acer Aspire 4520]("http://ubuntuforums.org/showthread.php?t=1282338")
[/LIST]
[SIZE=3]**_Step-by-Step Solution_**[/SIZE][INDENT]Now let's get our hands dirty

_ **Part 1. Compiling and customizing the kernel**_

[LIST=1]
[*]Install the necessary packages for building the kernel
```
$ sudo apt-get install build-essential kernel-wedge kernel-package ccache makedumpfile libncurses5-dev
$ sudo apt-get build-dep linux
```
[*]Create and **cd** into a directory at $HOME where you will store the kernel source tree
```
$ cd ~
$ mkdir linux
$ cd linux
```
[*]Get the kernel sources (DON'T use sudo here!). You have two methods. You can use either method.
[LIST]
[*]From the official apt repositories
```
$ apt-get source linux-source-2.6.28 --download-only
```
[*]From [http://archive.ubuntu.com](http://archive.ubuntu.com)
```
$ wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.28.orig.tar.gz
$ wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.28-15.52.diff.gz
```
[/LIST]
 
[*]Unpack the source tree and the diff patch
```
$ tar xvjf linux_2.6.28.orig.tar.gz
$ gunzip linux_2.6.28-15.52.diff.gz
```
[*]Patch the original source tree
```
$ cd linux-2.6.28
$ patch -p1 -i ../linux_2.6.28-15.52.diff
```
[*]Update the rules
```
$ chmod +x ~/linux/linux-2.6.28/debian/rules
$ chmod +x ~/linux/linux-2.6.28/debian.master/scripts/misc/*
$ debian/rules updateconfigs
```
[*]Copy your current kernel's config file. This config will tell the compiler how to build the kernel. If you want to customize it, at least you'll have a starting point.
```
$ cp /boot/config-$(uname -r) ~/linux/linux-2.6.28/.config
```
[*]Customize your kernel. Now this will present a LOT of options and a LOT of possibilities to screw up. Your kernel might not compile properly or you might not be able to boot into it. I assume you'll want to learn how to customize it. The only advice I could give in this HOWTO is this. Use / to search, and ? to learn about a specific option.
```
$ make menuconfig
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] Make sure you have the following options compiled as built-in
```
Device Drivers --> Graphics Support --> Support for framebuffer devices
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] Make sure you have the following options compiled as modules
```
Device Drivers --> Graphics Support --> /dev/agpgart (AGP Support) --> NVIDIA nForce/nForce2 chipset support
Device Drivers --> Graphics Support --> VGA 16-color graphics support
Device Drivers --> Graphics Support --> Userspace VESA VGA graphics support
Device Drivers --> Graphics Support --> VESA VGA graphics support
Device Drivers --> Graphics Support --> Console display driver support --> Framebuffer Console support
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] Completely disable the following options. If you have these options enabled, the Nvidia proprietary driver installer will complain about nvidiafb.
```
Device Drivers --> Graphics Support --> nVidia Framebuffer support
Device Drivers --> Graphics Support --> nVidia Riva support

```
[*]Save your kernel configuration and exit
```
Save an Alternate Configuration File --> .config
```
[*]Back in the terminal, compile your kernel. These commands, specifically because of **make-kpkg**, will create two .deb files in ~/linux which you will be able to install easily later. In **--append-to-version**, you can change **mycustomkernel** to string you want. Keep the small dash after the equals sign :)
```
$ fakeroot ccache make-kpkg --initrd --append-to-version=-mycustomkernel kernel-image kernel-headers
```
[*]The compile process takes about 2 1/2 hours on my laptop. Better go do something else worthwhile. But BEWARE! You might have done some settings in **make menuconfig** which might cause compile errors. Such problems are beyond the scope of this HOWTO. I have encountered such problems before. For example, the error is related to **lirc**, I'll just head over to **make menuconfig** again and disable **lirc**. (Dirty hack, I wouldn't recommend it)
[*]Then... Congratulations! You have just compiled your custom kernel! \\:D/
[/LIST]
[/INDENT][INDENT]**_PART 2. Installing the kernel_**
[/INDENT][INDENT]
[LIST=1]
[*]By this time you will already have two .deb files in ~/linux, for example
```
$ cd ~/linux
$ ls | grep deb
linux-headers-2.6.28-15.52-kit-superconfig-01_2.6.28-15.52-kit-superconfig-01-10.00.Custom_i386.deb
linux-image-2.6.28-15.52-kit-superconfig-01_2.6.28-15.52-kit-superconfig-01-10.00.Custom_i386.deb
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] If you follow this step, you no longer need PART 4 of this HOWTO. Before you install your new **.deb**s, edit */etc/initramfs-tools/modules* and add the following lines
```
fbcon
vesafb
```
[*][COLOR=Green]OPTIONAL:[/COLOR] If you want your splash screen to look good (not stretched or placed over to the side), edit */etc/usplash.conf* and make sure you have the following screen resolution settings, for example
```
xres=1024
yres=768
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] You will need to edit your */boot/grub/menu.lst*. As a best practice, back it up first
```
$ cd /boot/grub
$ sudo cp menu.lst menu.lst.bak
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] Now edit menu.lst using any text editor you want
```
$ sudo gedit menu.lst
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] Look for the **# defoptions=** line and add the **vga=792** option, for example (DO NOT UNCOMMENT it! Leave the # sign untouched)
```
## If my # defoptions line looked like this
# defoptions=quiet splash

## I can make it look like this
# defoptions=quiet splash vga=792
```
[*]You can now install your new kernel and its corresponding headers
```
$ cd ~/linux
$ sudo dpkg -i linux-headers-2.6.28-15.52-kit-superconfig-01_2.6.28-15.52-kit-superconfig-01-10.00.Custom_i386.deb
$ sudo dpkg -i linux-image-2.6.28-15.52-kit-superconfig-01_2.6.28-15.52-kit-superconfig-01-10.00.Custom_i386.deb
```
[*][COLOR=Red]VERY IMPORTANT:[/COLOR] When the linux-image installer asks about the */boot/grub/menu.lst*, let it "Install the package maintainer's version".
[*][COLOR=Red]PROBLEM CHECKPOINT:[/COLOR] If, when installing the linux-image, you encounter an error with nvidia-common, it helps to purge it and install it again
```
$ sudo apt-get purge nvidia-common
$ sudo apt-get install nvidia-common
```
[*][COLOR=Red]DON'T[/COLOR] restart yet! :)
[*]Congratulations! You have just installed a new kernel! \\:D/
[/LIST]
[COLOR=SeaGreen]_SOME LINUX THEORY:_[/COLOR]

[LIST]
[*]In steps 2 and 3, you edited configuration files related to the **initrd** (initial RAM disk). Upon installing **linux-image**, the **update-initramfs **tool will automatically run, creating a new **initrd** for your new kernel. The configuration files will help configure your new **initrd** upon building it. For example */etc/initramfs-tools/modules* will tell your new initrd to load **fbcon** and **vesafb** upon bootup.
[*]In steps 4 to 6, you edited a configuration file related to **grub** (GRand Unified Bootloader). Upon performing step 8, the **update-grub** tool will refer to the **# defoptions=** line and makes sure that every kernel listed in */boot/grub/menu.lst* will have those boot options.
[/LIST]
**_PART 3. Setting up the Nvidia proprietary drivers_**

[LIST=1]
[*]Now we will need to uninstall the Nvidia drivers for your current kernel. Just to make sure that your next kernel will be able to load the X GUI using default (no Nvidia) configurations. You will have two methods, depending on how you installed your drivers.
[LIST]
[*]If you installed them using System --> Administration --> Hardware Drivers, disable your current driver from there.
[*]If you installed your current driver using the installer from the official site, do the following
[LIST=1]
[*]Switch and login to a virtual console by pressing Ctrl-Alt-F1
[*]Stop the X server
```
$ sudo /etc/init.d/gdm stop
```
[*]Uninstall the Nvidia drivers. Make sure you still have the installer. For example
```
$ sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg1.run --uninstall
```
[*]Restart the X Server
```
$ sudo /etc/init.d/gdm start
```
[*]If it complains that the nvidia module does not exist, tell it to reconfigure itself using the default generic *xorg.conf*.
[*]Switch back to the virtual console (Ctrl-Alt-F1) and restart the X Server
```
$ sudo /etc/init.d/gdm stop
$ sudo /etc/init.d/gdm start
```
[*]Your GUI should now be in an ugly resolution. That should confirm that you Nvidia drivers have been uninstalled.
[/LIST]
 
[/LIST]
 
[*]Shutdown your computer and turn it back on. SHUTDOWN ensures that you will be able to access the GrUB menu.
```
$ sudo shutdown -P now
```
[*]In the GrUB menu, boot into your new kernel. It should take you to a GUI with an ugly resolution.
[*]After the bootup process, switch to a virtual console
[*]In the virtual console, stop the X Server
```
$ sudo /etc/init.d/gdm stop
```
[*]Install the Nvidia drivers
```
$ sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg1.run
```
[*]Inside the installer program, it will ask you if you want to download a precompiled kernel interface. DON'T download. Instead, let it compile a new kernel interface. This will depend on the linux-headers that you have installed previously.
[*]After installation, the program will also ask you if you want to automatically configure your *xorg.conf* so that the X Server will use the Nvidia drivers and render your GUI in a beautiful resolution. Let it configure automatically.
[*][COLOR=Red]PROBLEM CHECKPOINT:[/COLOR] In my experience, at this point of the installation, the problems start flying in. When I switch back to a virtual console after installing the Nvidia drivers, the screen becomes garbled. These problems should occur if you missed Steps 2-6 in PART 2.
[*]Test your installation now by pressing Ctrl-Alt-F1
[LIST]
[*]If it renders fine (text is readable). You're good to go!
[*]If it doesn't, switch back to the GUI by pressing Ctrl-Alt-F7. Then follow the instructions in Part 4.
[/LIST]
 
[*]Congratulations! You have just installed the Nvidia drivers! \\:D/
[/LIST]
**_PART 4. Fix the framebuffer AFTER installation of the new kernel_**
This portion of the HOWTO will be similar to a troubleshooting guide, so I will present first the solutions pertaining to the most common causes of the problem

[LIST]
[*]CAUSE 1: You probably do not have **vga=792** in the boot options in */boot/grub/menu.lst* for your current kernel
[LIST=1]
[*]You will need to edit your */boot/grub/menu.lst*. As a best practice, back it up first
```
$ cd /boot/grub
$ sudo cp menu.lst menu.lst.bak
```
[*]Now edit *menu.lst* using any text editor you want
```
$ sudo gedit menu.lst
```
[*]Look for the **# defoptions=** line and add the **vga=792** option, for example (DO NOT UNCOMMENT it! Leave the # sign untouched)
```
## If my # defoptions line looked like this
# defoptions=quiet splash

## I can make it look like this
# defoptions=quiet splash vga=792
```
[*]Then **update-grub**
```
$ sudo update-grub
```
[*]Tell it to "Install the package maintainer's version"
[*]Restart your computer. Then test your installation by switching to a virtual console.
[/LIST]
 
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]CAUSE 2: Your current kernel's **initrd** probably doesn't load the **fbcon** and **vesafb** modules. For this procedure, make sure you are running under your problematic kernel.
[LIST=1]
[*][COLOR=Red]VERY IMPORTANT:[/COLOR]Edit */etc/initramfs-tools/modules* and add the following lines
```
fbcon
vesafb
```
[*][COLOR=Green]OPTIONAL:[/COLOR] If you want your splash screen to look good (not stretched or placed over to the side), edit */etc/usplash.conf* and make sure you have the following screen resolution settings, for example
```
xres=1024
yres=768
```
[*]The two modifications above will only take effect after the following command
```
$ sudo update-initramfs -u
```
[*]Restart your computer. Then test your installation by switching to a virtual console.
[/LIST]
 
[/LIST]
[/INDENT]That wraps up this HOWTO. I hope this helps everyone. Post your questions and suggestions and I will update this HOWTO as I deem fit. You will be properly credited :popcorn:
  [/LEFT]

---

