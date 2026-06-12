---
title: "More ATI driver garbage"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by jjstein on 2008-06-26
I was having absolutely no luck with the ATI drivers in gutsy so (for whatever reason) decided to upgrade to hardy.   Now, even less works than before and the things that were previously failing miserably are failing even harder.  The main problem would be the drivers.  

First thing's first, I have an ATI Radeon express 200m.  I used Envy to install the drivers.  It claimed that everything worked but obviously if it did I wouldn't be here.  Under Administration>hardware drivers, it says the ATI driver is in use and enabled but no videos work, any time I try to do ANYTHING involving any form of video (even the default games that come with Ubuntu) it lags like crazy and eventually closes.  I was better off not even installing the drivers because it worked better before.


Any help would be INCREDIBLY helpful. If more info is needed I will be willing to provide it.

---

### Post by iaculallad on 2008-06-26
Had you tried reading this [thread]("http://ubuntuforums.org/showthread.php?t=321766")? It talks about installing the video card you mentioned. You could try it too if this will work for you.

---

### Post by UbuntuNerd on 2008-06-26
try this 


Method 1: Install the Driver the Ubuntu Way

This will install the driver that is currently in the repositories. It may be older than the current version from AMD.

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

The second line of the above may not be necessary. If apt says it cannot find the "linux-restricted-modules" package, try line 3. If that fails, check your sources.list (see top of page)

If the system complains about dependencies, use your preferred package manager to download python2.4 and, if necessary, its dependencies.
[edit] Method 2: Install the Catalyst 8.4 Driver Manually

    This is just an alternative installation method for the section above. It might help if you still get 'DRI missing' errors. 

Download the ATI driver installer: ati-driver-installer-8-4-x86.x86_64.run (this installer is for 32bit and 64bit systems)

Change to the directory you downloaded the file. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

There is a detailed manual with screenshots at Ubuntu Wiki.

By default, Ubuntu did not enable the Universe and Multiverse repositories, but now in Gutsy, both Universe and Multiverse are activated by default.

Install necessary tools:

sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)

Uninstall previous fglrx: Using Synaptic, completely remove any packages containing "fglrx" in their name.

If using 64bit make sure to collect package "ia32-libs" before you continue!

Create .deb packages:

sudo sh ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/gutsy

note: if this step fails with a signal being caught, and you are running the script on an NFS-mounted directory, copy it to a local partition, and it will work. The same error may result from insufficient disk space.

As an alternative, you can just use

sudo sh ./ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu --autopkg

which will download all the needed packages by itself and also automatically detects the Ubuntu version used.

If this step fails on amd64/x86_64 with a No such file or directory message about missing files in X11R6/lib, follow these instructions and come back here. Also check that your download path does not contain spaces.

Blacklist old fglrx module from linux-restricted-modules:

As Ubuntu Gutsy's linux-restricted-modules package includes the fglrx module from an old driver version (8.37.6), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

Ubuntu/Gnome users type in:

gksu gedit /etc/default/linux-restricted-modules-common

Kubuntu/KDE users type in:

kdesu kate /etc/default/linux-restricted-modules-common

Add "fglrx" to the line "DISABLED_MODULES"
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

Please note that after the modification above, the "Restricted Driver Manager" will signal "ATI accelerated graphics driver" not enabled (unticked). This is perfectly correct. At the end of the installation procedure it will signal in Status: "in use" (green light), but NOT enabled. It simply means that the fglrx module contained in the linux-restricted-modules package is not enabled, but another fglrx module (8.4) is in use.

You may also need to edit the file (if it exists):

gksu gedit /etc/modprobe.d/blacklist-restricted

Put a # in front of the line "blacklist fglrx", if it is present. Otherwise, the kernel module will not load automatically, and you will not get 3D acceleration.

Remove any old fglrx debs from /usr/src/:

sudo rm /usr/src/fglrx-kernel*.deb

Install .deb packages:

sudo dpkg -i xorg-driver-fglrx_8.476-0*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb

Additional 64-bit instructions

If you have a 64 bit install, the above dpkg command will likely complain that "Errors were encountered while processing: fglrx-amdcccle". This is because of a dependency of the amdccle package on 32 bit libraries. If you receive this error, issue the following command after the above dpkg command, which will force the installation of all of the 32 bit dependencies, and then the amdccle package:

sudo apt-get install -f

Catalyst 8.3 on 64-bit systems requires the --force-overwrite command in the above dpkg command:

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.476-0*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb

---

### Post by UbuntuNerd on 2008-06-26
Troubleshooting Installation Errors

Kernel -rt users

If you are running the -rt kernel, you will fail to compile the kernel module with "FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'". Follow the instructions on 64bitstudio.com for a workaround.


Missing kernel sources

Error! Your kernel source for kernel 2.6.22-14-386 cannot be found at
/lib/modules/2.6.22-14-386/build or /lib/modules/2.6.22-14-386/source.

You must install the specific headers package for your kernel:

$ uname -r
$ sudo aptitude install linux-headers-2.6.22-14-386

Where "2.6.22-14" is the version reported by uname.


Bad file descriptor

If you get a 'Bad file descriptor' message concerning the xorg.conf file try switching user to root and repeating the same command without sudo. This might be valid for the following commands too. (Ubuntu Gutsy installs with no password set for root by default. You can set a password for the root by typing 'sudo passwd root' first.)
[edit] Configure the Driver

    * NOTE THIS WILL ERASE SETTINGS IN /etc/X11/xorg.conf you should be sure there is a backup.
    * Note Method 2 Users: Before you carry out this step you must reboot your machine. Or else the fglrx driver will not be in use on xorg.conf and using the aticonfig options will cause a memory dump and not intialise the Driver properly.
    * Note: An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc. Another alternative is aticonfig --initial --force if you encounter issues with the first command. 

sudo aticonfig --initial

Then:

sudo aticonfig --overlay-type=Xv

    * Note: Alternative in the overlay-type to "Xv" can be "opengl" or "disable" if the TV-out makes problems in videos. 

[edit] Alternative: Configure the Driver, The Manual Way:

An alternative to the "sudo aticonfig" commands is to edit "/etc/X11/xorg.conf" and change the "Device" section for the video card as shown below. This way you won't lose your old settings.

gksu gedit /etc/X11/xorg.conf

Section "Device"
	[...]
#       Driver          "vesa"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	[...]
EndSection


[edit] TV - Out

The composite TV-Out is not working simultaneously with the VGA on my System. To use it I have turned the VGA off and only the TV on. Attention! This command turns off your Monitor!!

sudo aticonfig --enable-monitor=tv

To change back to VGA:

sudo aticonfig --enable-monitor=crt1

Some have had luck with both mirrored.

sudo aticonfig --force-monitor=crt1
sudo aticonfig --enable-monitor=crt1,tv

reboot after that and it should mirror the CRT1 onto the TV.
[edit] Finish the Installation

Now save any open document and reboot your system:

sudo shutdown -hr now

    * Note: An alternative to rebooting is to restart the X Server by pressing your CTRL ALT BACKSPACE keys. You must remove any old kernel modules such as "drm" "radeon" or "fglrx" using the "rmmod" command. Example: sudo rmmod fglrx
    * Note: Another way to reboot: 

sudo reboot

[edit] Post-Installation Checks and Tweaks
[edit] Verifying

Run the following command to check its output to ensure the fglrx driver is installed properly:

64bit Users only ( 32bit users can continue to the fglrxinfo test ), after rebooting you may have noticed that you cant open aticonfig and the fglrxinfo test below may not show ati in the info from the test, to fix this in terminal do the following command

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

$fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7415 Release

The OpenGL vendor string should read ATI and not Mesa.

If it still says Mesa and not ATI, even after re-enabling the driver from the Restricted-manager: You can try the following:

        *

          $ less /var/log/Xorg.0.log |grep EE

          if this command returns (EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work then remove the kernel module and reinstall it. 

        $ sudo dkms remove -m fglrx -v 8.471 --all

        * Remove all the packages provided by the xserver-xorg-video-all meta-package (search for it using Synaptic or Adept), then restart the machine. The X Server should now use the new fglrx driver by force (provided the driver is being used in xorg.conf). 

        If you can't log in after this, you'll have to log in to a terminal in the login screen, and reinstall the xserver-xorg-video-all package. Your problem is probably somewhere else. (taken from [1]). 

        * Remove the package xserver-xgl. 

        Explanation: If you installed this previously in order to make compiz work, it will not allow direct rendering on your display. You can check out if this is what it causing the problem by running 

        DISPLAY=:0 glxinfo | grep render

---

### Post by jjstein on 2008-06-27
Wow thanks.  I'll try these and let you know if anything worked.

---

### Post by dizee on 2008-06-27
I have the same graphics card as you. Just so you know, the Restricted drivers Ubuntu gave me didn't work, nor did Envy. The guide posted above is what you need, just use the manual way to install. The current driver is 8.6, the link for this is [here](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29) (same guide as one posted but updated)

It worked perfectly for me after using that guide.

---

### Post by jjstein on 2008-06-27
I was trying the method mentioned by Dizee and everything went alright up until the "install Debs" step:
```
sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
```

I got the following error:
```
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up fglrx-amdcccle (2:8.501-0ubuntu1) ...

Errors were encountered while processing:
 fglrx-kernel-source_8.501-0ubuntu1_i386.deb

```

Any Idea how I can fix this?

---

### Post by Canis familiaris on 2008-06-27
Maybe this will help
[http://ubuntuforums.org/showthread.php?t=832698]("http://ubuntuforums.org/showthread.php?t=832698")

---

### Post by socngill on 2008-06-27
All looks very interesting!  Have been having real trouble with my ATI Radeon X1650 card.  Shall try this when I get home and post the results in case anybody else is having issues with the same card.

Couldn't even watch video footage in full screen last night...

---

### Post by socngill on 2008-06-27
After installing the ATI drivers, I run the fglrxinfo in the terminal and get this message:

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Any ideas how to fix this (or what it means!).

---

### Post by dizee on 2008-06-28
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#libGL_error](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#libGL_error)

---

