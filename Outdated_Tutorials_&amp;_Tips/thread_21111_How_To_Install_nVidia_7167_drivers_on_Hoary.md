---
title: "How To: Install nVidia 7167 drivers on Hoary"
date: 2005-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Zaphrod on 2005-03-20
Now  get 3d acceleration in Hoary  for the latest Nvidia cards , you only need to do 

$ sudo apt-get install nvidia-glx

then edit /etc/X11/ xorg.conf  Section "Device" to show  Driver  "nvidia"

And I personally add just below that 

Option "NoLogo" "on" 

to get rid of the nvidia splash screen.

------------ Below is obsolete but would still work ------------------------------------------

This How To is a modified version of [Tichondrius'](http://www.ubuntuforums.org/member.php?u=5630) [How To  for Warty ](http://http://www.ubuntuforums.org/showthread.php?t=12823&highlight=6600gt).  All credit should go to him for such a thorough guide.

The version of Nvidia's display driver in the Ubuntu repositores is 1.0-6111 which does not support some of the new video cards, like the ones based on 6600/GT GPUs. There is a newer version 1.0-6629 which supports all the new video cards, as well as providing performance improvements of up to 10% for existing GPUs, especially the 6800 series.

The new driver is available on nvidia's web site, but it comes with a proprietary built in installer, so the installation is not tracked by debian's package management system apt/dpkg. Also, if you already installed the 6111 driver from Ubuntu's repository using apt, then the nvidia installer will overwrite some of the driver and configuration files, which could mess up the 6111 driver and make it hard to restore it.

This howto explains how to get and install the new driver's debian packages, which are available from the debian unstable repository. The driver includes three parts -
(a) The X-Windows binary driver and libraries, which is contained in nvidia-glx package.
(b) The nvidia kernel module, contained in the nvidia-kernel-v.v.v.v package (which we need to create).
(c) Configuration files, contained in the nvidia-kernel-common package.

Note that (a) depends on (b) which depends on (c), so we install them in reverse order (c,b,a). The most difficult part is the nvidia kernel module (b), which must be compiled for your specific kernel version, so we will need to get the nvidia-kernel sources as well as linux kernel sources (although it's not required to compile a new kernel, it is in fact much safer and simpler, since we don't have to touch the existing kernel). We'll use the sources to create the nvidia-kernel package (which contains the nvidia kernel module) together with a matching kernel-image package (which contains the new kernel and the standard modules).

This has worked for me on a computer with a 6600GT PCI-E, and another computer with a 6800GT AGP card. Both had the standard Woody release with XFree86. In the latter case, I already had the older nvidia driver 6111 installed before installing the new version 6629, and I noticed a significant performance increase with the new driver (by running a doom 3 timedemo). So here goes the complete list of steps:

Installing the latest nVidia Drivers on Hoary

1. Download and install the 2.6.10 kernel source package and a few other packages required for compilation (or use synaptic if you prefer):

$ sudo apt-get install linux-source-2.6.10 build-essential fakeroot kernel-package libglade2-dev dpatch debhelper

2. Download and install the 7167 [nvidia-kernel-common](http://http://ftp.debian.org/debian/pool/contrib/n/nvidia-kernel-common/nvidia-kernel-common_1.0.7167-1_all.deb)  and [nvidia-kernel-source](http://ftp.egr.msu.edu/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-kernel-source_1.0.7167-1_i386.deb)  packages from debian unstable (click on the links to download, and use the following commands to install):

$ sudo dpkg -i nvidia-kernel-common_1.0.7167-1_all.deb
$ sudo dpkg -i nvidia-kernel-source_1.0.7167-1_i386.deb

3. Check that you are added to the src group, by typing "groups". If you are not, do the folowing (you will need to logout and login again for this to take effect):

$ sudo addgroup `whoami` src

4. Unpack the sources (make sure to move/rename any previous directories which conflict, like /usr/src/modules/nvidia-kernel and /usr/src/linux-source-2.6.8.1)

$ cd /usr/src
$ tar jxvf linux-source-2.6.10.tar.bz2
$ tar zxvf nvidia-kernel-source.tar.gz
$ ln -s linux-source-2.6.10 linux




5. If you want to use your current kernel's configuration (which you probably do) you can copy it from /boot like this (if your current kernel version is older, it will tell you about any new kernel configuration options. You can choose the defaults by pressing enter):

$ cd /usr/src/linux
$ cp /boot/config-`uname -r` .config
$ make oldconfig

6. Configure the kernel to not include the Nvidia Riva framebuffer driver (FB_RIVA under Device Drivers->Graphics Support->Support for frame buffer devices), because it might conflict with the new nvidia driver. You can also change any other kernel option you like, then save the kernel configuration and exit. Note that this step is recommended by Nvidia in their README file which accompanies their kernel module source package, but in most cases the module will work even without performing this step:

$ cd /usr/src/linux
$ make gconfig

7. Compile the kernel and nvidia module (note you can replace "custom1" with any string to append to the version. This guarantees that your new kernel version is unique, so there are no conflicts with existing kernels):

$ cd /usr/src/linux
$ sudo make-kpkg clean
$ sudo fakeroot make-kpkg --initrd --append-to-version custom1 kernel_image modules_image

8. Install the new kernel-image and nvidia-kernel packages

$ cd /usr/src
$ sudo dpkg -i kernel-image-2.6.10custom1*.deb
$ sudo dpkg -i nvidia-kernel-2.6.10custom1*.deb

9. Download the 7167 [nvidia-glx](http://ftp.debian.org/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-glx_1.0.7167-1_i386.deb)  package from debian unstable (the binary driver and libs for X windows) by clicking the link. (Note that if you are currently running an older nvidia driver, then it's safer to exit from X windows before installing this package, because the installation it will replace some files used by the old driver. To exit X windows, you can press ctrl-alt-F1 to get a console, login and then kill gdm using the command "sudo killall gdm"). Change directory to the package location. Now install the package:

$ sudo dpkg -i nvidia-glx_1.0.7167-1_i386.deb

10. Save a backup of the X server configuration file /etc/X11/xorg.conf. Now change the file t use the nvidia driver, by changing the argument string of the "Driver" line in the Section "Device" to "nvidia". Also, in the Section "Module", comment out "GLCore" and "dri" lines, and make sure there is a "glx" line there. Add the following line just below  the Driver "nvidia" line If you don't want the nVidia Splash logo to show at start up. 

Option "NoLogo" "on"

11. To make sure the nvidia module is loaded at boot time, add a line "nvidia" to the end of the file /etc/modules. You can do it like this (or just edit the files /etc/modules with your favorite editor):

$ sudo sh -c "echo nvidia >> /etc/modules"

12. Reboot into your new kernel.

If something goes wrong, for example if X doesn't start, then login with text console and check if the nvidia kernel module was loaded:

$ lsmod | grep nvidia

If it's not listed, it may be that modules dependencies were not updated (usually installing the nvidia-kernel package takes care of that automatically, but sometimes it doesn't...). So do it manually, and start X (next time it should boot without problem): (note: I have always had to do this step)

$ sudo depmod
$ sudo modprobe nvidia
$ startx

Also, if this doesn't work you can easily go back to your previous configuration by restoring your old xorg.conf file which you saved in step 10. If you were previously using the an older nvidia driver (e.g. 6111), and you want to go back to it, you also need to uninstall the nvidia-glx-1.0.6629 package, and re-install nvidia-gix-1.0.6111 package from Ubuntu's repositorues. Then boot your old kernel (the one your were using previously).

---

### Post by digby on 2005-03-20
Just wanted to say that it worked perfectly with my GF4 Ti4600. I also had to run 'depmod' before I could load the nVidia module.

Thanks!

---

### Post by mal on 2005-03-21
I managed to get my Nvidia 6600 based card working in Hoary with just the following commands described in the "Tweaking Ubuntu after your first installation" thread:

$ sudo apt-get install nvidia-glx
$ sudo nvidia-glx-config enable
$ sudo reboot

I don't know whether the same would apply to the 6600GT and I can't comment on the other Nvidia chips covered by this HowTo.

Mal

---

### Post by jdong on 2005-03-21
Simply 'apt-get' installing nvidia-glx will get you version 6629, which doesn't support a few chipsets.

---

### Post by agentworm on 2005-03-21
So I got to step 4:

$ tar jxvf linux-source-2.6.10.tar.bz2
$ tar zxvf nvidia-kernel-source.tar.gz
$ ln -s linux-source-2.6.10 linux

but then it told me that it couldn't open: no such file or directory for everything. So I take it I'm missing something......where can I get it?

Worm

---

### Post by digby on 2005-03-22
Make sure you are either using sudo with those commands or running as root.  I think it might have been a small omission from the instructions.

---

### Post by agentworm on 2005-03-22
[QUOTE=digby]Make sure you are either using sudo with those commands or running as root.  I think it might have been a small omission from the instructions.[/QUOTE]

Let me add that I'm a major n00b. But I made it to step 8 and this command line didn't want to work. I'm on my windows right now, when I log in with ubuntu I'll post the error it gave me. But that's where it stopped for me...again...I'll get it th ough... I'll get it... I hope :(

$ sudo make-kpkg clean

---

### Post by digby on 2005-03-22
There's nothing wrong with being a noob.  I'm still one too... I had to sit and think about that one for a sec when I was doing it myself.  Eventually I just got tired of forgeting to type sudo before everything and just switched to root.

---

### Post by mdb on 2005-03-23
I highly recommend you do not try this with linux-2.6.11. I have experienced a reduction of 3000 fps in glxgears with a 6800GT. Although it could be related to the Big Block Kernel Preempt I thought would be fun to try. Stability also seems to be in question since my kernel just freaked out and oopsed.

---

### Post by mconbere on 2005-03-23
I'm an Ubuntu Noob at the moment (had experience with other distros).  I have hoary installed, but the newest Nvidia drivers don't work with my card (old tnt2).  How do I get apt to install the older 6111?

I know this isn't exactly the purpose of this post, but the topic was mentioned and I can't find information elsewhere that I understand.

thanks
morgan

---

### Post by fibster on 2005-03-23
I have an old  mx440 card that I followed the instructions for 4.10,, apt-get installetc when I got to the 4th one that is nautilus I believe I control alt f1 that took me to a log in entered name password and startx and nvidia logo popped up and all is great easiest set up I ever didl

gl

tb aka fibster

---

### Post by sudonim on 2005-03-27
Thanks for the guide conversion man  8)  . So I'm also new to Ubuntu ,my friend gave me some Warty cd's that he ordered and I finally got around to trying them today, wasn't in the mood of downloading packages through w3m to get my 6600GT working so just dl'ed Hoary. I was reading the guide about things to do after installing and I did the one where I re-compiled my kernel with the specific 686 package. Is this now going to wipe out those optimizations? I did copy the config from that kernel when I was at step 7, where I gather I was creating a new kernel sources package.

EDIT: I can't type worth jack

---

### Post by jdodson on 2005-03-31
i do mean to cross post, but i think this is important. if you have a nvidia card, check out this thread: [http://www.ubuntuforums.org/showthread.php?t=23130](http://www.ubuntuforums.org/showthread.php?t=23130)

basically it looks like they are doing some last minute testing on the latest nvidia driver to possibly include in hoary. snag the debs, test it out and respond to the post i have cited.  if these drivers get included in hoary it will save you time from actually compiling things from source, etc(which is not bad, just not needed if the devs can include drivers).

---

### Post by jdodson on 2005-03-31
**UPDATE** the 7167 driver is now in hoary!

---

### Post by crane on 2005-04-03
very cool, I'm downloading the lastest release of hoary right now.
Isn't the official release like next week or something?

---

### Post by p!=f on 2005-04-03
[QUOTE=jdodson]**UPDATE** the 7167 driver is now in hoary![/QUOTE]
Partially. nvidia-kernel-common is still at 6629 version so my xserver refuses to start.  (sure, downloading the package from Debian makes things running) ;)

---

### Post by Skid on 2005-04-05
Hey folks,

I just followed the guide, had to depmod, + modprobe nvidia. 

As soon as I got into X, the syanptic update manager tells me that my driveres are out of date and wants to update them..

If I update the nvidia packages + other ones that are out of date (gaim, etc) will this conflict with what I have just done?

Thanks.

---

### Post by Spudgun on 2005-04-14
Excellent, worked perfect for my 6600GT PCI Express  :smile:

---

### Post by SillyHalfMexican on 2005-10-10
Hey all, I'm pretty much a total "noob" when it comes to Linux.  Just switched over and it hasn't been the most pleasant switch so far.  But any ways.

Nice tutorial, easy to follow and such.

However, I am getting problems when I go to edit /etc/X11/ xorg.conf

I'm assuming I type: edit /etc/X11/ xorg.conf
in the terminal correct?

If so, this is the error I get when doing that:

Warning: unknown mime-type for "/etc/X11/xorg.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

If I am supposed to do it a different way, please don't be harsh on a noob. :D
Also, when I try and just double click it, it won't let me edit it manually, but it does say it's read-only.

Thanks for anyones help in advance.  :D
But, please direct me torwards the proper way of doing it.

Hardware:
AMD 64 3500+
nVidia 6800GT AGP (BFG)
Asus A8V Mobo
1GB Corsair XMS Platinum
For linux only: 20GB Maxtor HD

---

### Post by tseliot on 2005-10-10
[QUOTE=SillyHalfMexican]I'm assuming I type: edit /etc/X11/ xorg.conf
in the terminal correct?[/QUOTE]

You should type sudo nano /etc/X11/ xorg.conf

CTRL+O to save the file
CTRL+X to exit

"nano" works also outside the graphical interface.

If you want something easier or more eyecandy you can use "gedit" (in GNOME) and "kate" (in KDE)

EDIT: BTW why are you trying to install 7176? It is not the latest version. Moreover you don't need to compile a new kernel in order to install the nvidia drivers (USE THE NVIDIA INSTALLER, it's easier, no offense to the author of this guide). You can try my guide (look at my signature)

---

### Post by SillyHalfMexican on 2005-10-10
[QUOTE=tseliot]
EDIT: BTW why are you trying to install 7176? It is not the latest version. Moreover you don't need to compile a new kernel in order to install the nvidia drivers (USE THE NVIDIA INSTALLER, it's easier, no offense to the author of this guide). You can try my guide (look at my signature)[/QUOTE]


I figured that it would work for any version of the driver.  It didn't specify to get a certain version of the driver.  Thanks for your help though, appreciated.

Will let you know how it turns out.

---

