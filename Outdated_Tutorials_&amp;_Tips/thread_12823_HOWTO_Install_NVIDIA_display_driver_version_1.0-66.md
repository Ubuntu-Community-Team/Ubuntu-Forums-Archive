---
title: "HOWTO: Install NVIDIA display driver version 1.0-6629"
date: 2005-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Tichondrius on 2005-01-27
The version of Nvidia's display driver in the Ubuntu repositores is 1.0-6111 which does not support some of the new video cards, like the ones based on 6600/GT GPUs. There is a newer version 1.0-6629 which supports all the new video cards, as well as providing performance improvements of up to 10% for existing GPUs, especially the 6800 series.

The new driver is available on nvidia's web site, but it comes with a proprietary built in installer, so the installation is not tracked by debian's package management system apt/dpkg. Also, if you already installed the 6111 driver from Ubuntu's repository using apt, then the nvidia installer will overwrite some of the driver and configuration files, which could mess up the 6111 driver and make it hard to restore it.

This howto explains how to get and install the new driver's debian packages, which are available from the debian unstable repository. The driver includes three parts - 
(a) The X-Windows binary driver and libraries, which is contained in nvidia-glx package.
(b) The nvidia kernel module, contained in the nvidia-kernel-v.v.v.v package (which we need to create).
(c) Configuration files, contained in the nvidia-kernel-common package.

Note that (a) depends on (b) which depends on (c), so we install them in reverse order (c,b,a). The most difficult part is the nvidia kernel module (b), which must be compiled for your specific kernel version, so we will need to get the nvidia-kernel sources as well as linux kernel sources (although it's not required to compile a new kernel, it is in fact much safer and simpler, since we don't have to touch the existing kernel). We'll use the sources to create the nvidia-kernel package (which contains the nvidia kernel module) together with a matching kernel-image package (which contains the new kernel and the standard modules). 

This has worked for me on a computer with a 6600GT PCI-E, and another computer with a 6800GT AGP card. Both had the standard Woody release with XFree86. In the latter case, I already had the older nvidia driver 6111 installed before installing the new version 6629, and I noticed a significant performance increase with the new driver (by running a doom 3 timedemo). So here goes the comlete list of steps:

1. Download and install the 2.6.8.1 kernel source package and a few other packages required for compilation (or use synaptic if you prefer):

$ sudo apt-get install linux-source-2.6.8.1 build-essential fakeroot kernel-package libglade2-dev dpatch debhelper

2. Download and install the 6629  [nvidia-kernel-common](http://http.us.debian.org/debian/pool/contrib/n/nvidia-kernel-common/nvidia-kernel-common_1.0.6629+1_all.deb) and [nvidia-kernel-source](http://http.us.debian.org/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-kernel-source_1.0.6629+1-1_i386.deb) packages from debian unstable (click on the links to download, and use the following commands to install):

$ sudo dpkg -i nvidia-kernel-common_1.0.6629+1_all.deb
$ sudo dpkg -i nvidia-kernel-source_1.0.6629+1-1_i386.deb

3. Check that you are added to the src group, by typing "groups". If you are not, do the folowing (you will need to logout and login again for this to take effect):

$ sudo addgroup `whoami` src

4. Unpack the sources (make sure to move/rename any previous directories which conflict, like /usr/src/modules/nvidia-kernel and /usr/src/linux-source-2.6.8.1)

$ cd /usr/src
$ tar jxvf linux-source-2.6.8.1.tar.bz2
$ tar zxvf nvidia-kernel-source.tar.gz
$ ln -s linux-source-2.6.8.1 linux

5. If you want to use your current kernel's configuration (which you probably do) you can copy it from /boot like this (if your current kernel version is older, it will tell you about any new kernel configuration options. You can choose the defaults by pressing enter):

$ cd /usr/src/linux
$ cp /boot/config-`uname -r` .config
$ make oldconfig

6. Configure the kernel to not include the Nvidia Riva framebuffer driver (FB_RIVA under Device Drivers->Graphics Support->Support for frame buffer devices), because it might conflict with the new nvidia driver. You can also change any other kernel option you like, then save the kernel configuration and exit. Note that this step is recommended by Nvidia in their README file which accompanies their kernel module source package, but in most cases the module will work even without performing this step:

$ cd /usr/src/linux
$ make gconfig

7. Compile the kernel and nvidia module (note you can replace "custom1" with any string to append to the version. This guarantees that your new kernel version is unique, so there are no conflicts with existing kernels):

$ cd /usr/src/linux
$ make-kpkg clean
$ fakeroot make-kpkg --initrd --append-to-version custom1 kernel_image modules_image

8. Install the new kernel-image and nvidia-kernel packages

$ cd /usr/src
$ sudo dpkg -i kernel-image-2.6.8.1custom1*.deb
$ sudo dpkg -i nvidia-kernel-2.6.8.1custom1*.deb

9. Download the 6629 [nvidia-glx](http://http.us.debian.org/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-glx_1.0.6629+1-1_i386.deb) package from debian unstable (the binary driver and libs for X windows) by clicking the link. (Note that if you are currently running an older nvidia driver, then it's safer to exit from X windows before installing this package, because the installation it will replace some files used by the old driver. To exit X windows, you can press ctrl-alt-F1 to get a console, login and then kill gdm using the command "sudo killall gdm").  Now install the package:

$ sudo dpkg -i nvidia-glx_1.0.6629+1-1_i386.deb

10. Save a backup of the X server configuration file /etc/X11/XF86Config-4. Now change the file t use the nvidia driver, by changing the argument string of the "Driver" line in the Section "Device" to "nvidia". Also, in the Section "Module", comment out "GLCore" and "dri" lines, and make sure there is a "glx" line there.

11. To make sure the nvidia module is loaded at boot time, add a line "nvidia" to the end of the file /etc/modules. You can do it like this (or just edit the files /etc/modules  with your favorite editor):

$ sudo sh -c "echo nvidia >> /etc/modules"

12. Reboot into your new kernel. 

If something goes wrong, for example if X doesn't start, then login with text console and check if the nvidia kernel module was loaded:

$ lsmod | grep nvidia

If it's not listed, it may be that modules dependencies were not updated (usually installing the nvidia-kernel package takes care of that automatically, but sometimes it doesn't...). So do it manually, and start X (next time it should boot without problem):

$ sudo depmod
$ sudo modprobe nvidia
$ startx

Also, if this doesn't work you can easily go back to your previous configuration by restoring your old XF86Config-4 file which you saved in step 10.  If you were previously using the an older nvidia driver (e.g. 6111), and you want to go back to it, you also need to uninstall the nvidia-glx-1.0.6629 package, and re-install nvidia-gix-1.0.6111 package from Ubuntu's repositorues. Then boot your old kernel (the one your were using previously).

---

### Post by oddabe19 on 2005-01-27
No offense, but i find it much MUCH easier to
1. apt-get install kernel-headers-`uname -r`
2. download the nvidia driver from their site
3. sh nvidia-xxxxxxxxxxxxxxx-6629.run
4. edit XF86Config file
5. poof done....


but your steps are pretty good, very well done How-to!!! :-D

---

### Post by Tichondrius on 2005-01-27
Yes, I mentioned you could do that, but doing it as I explained - building a nvidia-kernel package - has many advantages, like not having to copy or re-install the module when you build a new kernel, and being able to manage the driver using apt/dpkg package tracking system. This is the recommended way of compiling third party modules - put their source under /usr/src/modules, and build them using "modules_image" target of the kernel source makefile. That's the way I used to install the previous nvidia display driver, and it has been much more reliable, versatile and ultimately convenient then using proprietary install scripts. You see, I like to understand what's going on, which usually helps when things go wrong.

---

### Post by xyverz on 2005-01-29
The links to packages.debian.org have timed out for me.  Any suggestions?

---

### Post by Tichondrius on 2005-01-29
[QUOTE=xyverz]The links to packages.debian.org have timed out for me.  Any suggestions?[/QUOTE]

Fixed the links in the instructions. Please try again.

---

### Post by bchapman on 2005-01-31
Thanks for posting these instructions! Apart from helping with the nvidia issue, this is very helpful for those of us who are not very familiar with the Debian way of doing things.

Best, Ben

---

### Post by lilpac on 2005-01-31
Hi all,
how can i actualy exit X windows?

:)

lilpac

---

### Post by pseudonym on 2005-01-31
[QUOTE=lilpac]Hi all,
how can i actualy exit X windows?

:)

lilpac[/QUOTE]

So you can install the driver/deb package, you mean? Just do this-

Ctrl+Alt+F1 (to get into console mode)

login

sudo killall gdm (to shutdown gnome completely)

You are now ready to continue on your merry way. :)

---

### Post by Tichondrius on 2005-01-31
[QUOTE=bchapman]Thanks for posting these instructions! Apart from helping with the nvidia issue, this is very helpful for those of us who are not very familiar with the Debian way of doing things.

Best, Ben[/QUOTE]

Actually, the Debian way to install the Nvidia display drivers is also the way Ubuntu set up the packages in their universe repositories. The only difference with Ubuntu's repository, is that the Nvidia kernel module is already available pre-compiled in the linux-restricted-modules package, so you don't have to compile it yourself (if you are running a stock kernel). Also, Ubuntu added a convenience script (nvidia-glx-config) in the nvidia-glx package to perform the change in the X config file, so you don't have to edit it manually. But the problem is that these packages only have the older 6111 driver for the warty release, so if you want to install the new nvidia driver for warty (using the debian way) you have to follow the instructions above.

Note that the repositories for the hoary beta release do include the new driver packages, but it's not advisable to use them with warty.

---

### Post by lilpac on 2005-02-01
[QUOTE=pseudonym]So you can install the driver/deb package, you mean? Just do this-

Ctrl+Alt+F1 (to get into console mode)

login

sudo killall gdm (to shutdown gnome completely)

You are now ready to continue on your merry way. :)[/QUOTE]

thankyou very much :d il go and try it right now

---

### Post by lilpac on 2005-02-03
all i get is a black screen? :(

---

### Post by crane on 2005-02-03
[QUOTE=lilpac]all i get is a black screen? :([/QUOTE]
are you talking about when you ctrl>alt>f1?

---

### Post by lilpac on 2005-02-03
[QUOTE=crane]are you talking about when you ctrl>alt>f1?[/QUOTE]

no i loaded the module, now when i boot i just get a black screen, it can't load x

---

### Post by crane on 2005-02-03
After you get to the black screnn use >ctrl>alt>f1 to get to command. then look at your XF86Config file.
Make sure the driver is nvidia. if it asn't try changing it. If it is change it back to nv and try srating X again.

---

### Post by lilpac on 2005-02-05
[QUOTE=crane]After you get to the black screnn use >ctrl>alt>f1 to get to command. then look at your XF86Config file.
Make sure the driver is nvidia. if it asn't try changing it. If it is change it back to nv and try srating X again.[/QUOTE]

i did change the driver back to nv, this way i could enter X, 
but after that i had some troubles with gdm + i coul'd install the old drivers back
so i just installed ubuntu all over again :)

---

### Post by RadixLecti on 2005-02-09
Hi...

I followed instructions to the letter, but when I try step 9b,

$ sudo dpkg -i nvidia-glx_1.0.6629+1-1_i386.deb

I get an error stating that dependancy problems are hindering configuration of nvidia-glx.

According to what it says, this is because of nvidia-kernel-1.0.6629, and that the package is not installed.

Any suggestions as to why I get this message? I've doublechecked, I HAVE followed the instructions correctly, to the best of my limited knowledge.

EDIT:

According to synaptic, I should install nvidia-kernel-source (which I have), and that the file is in conflict with nvidia-glx-src.
Synaptic also suggests I should install nvidia-settings. It's all greek to me. ;)

---

### Post by artnay on 2005-02-09
[QUOTE=RadixLecti]Hi...

I followed instructions to the letter, but when I try step 9b,

$ sudo dpkg -i nvidia-glx_1.0.6629+1-1_i386.deb

I get an error stating that dependancy problems are hindering configuration of nvidia-glx.

According to what it says, this is because of nvidia-kernel-1.0.6629, and that the package is not installed.

Any suggestions as to why I get this message? I've doublechecked, I HAVE followed the instructions correctly, to the best of my limited knowledge.

EDIT:

According to synaptic, I should install nvidia-kernel-source (which I have), and that the file is in conflict with nvidia-glx-src.
Synaptic also suggests I should install nvidia-settings. It's all greek to me. ;)[/QUOTE]

Exactly the same happened here. So I grabbed the official nVidia.run package from nVidia's page, installed it, edited xorg.conf a bit and then it was fully functional. Using 6800 LE, Hoary, XOrg 6.8.1, 2.6.10-smp (compiled by myself) and everything is apt-get upgraded and dist-upgraded. This happened two days ago.

---

### Post by RadixLecti on 2005-02-09
I gave up and resorted to the older 6611 drivers (tested nvidias own installer too, got it working, but it didn't want to install properly) which I installed via apt-get. 
Hey, at least my graphics card is functioning now. Not bad for a complete newbie. ;)

---

### Post by blitze on 2005-02-10
Good to know I wasn't the only one to end up with a dead X Server trying it the .deb way.  I think I'll stick with the Nvidia way in future as I don't do kernel upgrades all the time and it's easy to deal with if I do upgrade the kernel.   :| 

I ended up re-installing hoary to get back to a functioning desktop but that's only cause I'm still remembering the apt way, been a few years.

---

### Post by orvalax on 2005-02-10
I've been trying to find out how to install the drivers for my Nvidia card for a few days now. This HOWTO is pretty cool. I ran into a problem when I tryed to complete step 2 though.

> 2. Download and install the 6629 nvidia-kernel-common and nvidia-kernel-source packages from debian unstable (click on the links to download, and use the following commands to install):

$ sudo dpkg -i nvidia-kernel-common_1.0.6629+1_all.deb
$ sudo dpkg -i nvidia-kernel-source_1.0.6629+1-1_i386.deb

```
$ sudo dpkg -i nvidia-kernel-source_1.0.6629+1-1_i386.deb
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 74117 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_1.0.6629+1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.
dpkg: error processing nvidia-kernel-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-kernel-source

```

I haven't been using Linux for very long and I don't know what to do. Any help?

---

### Post by orvalax on 2005-02-11
Ok, I rebooted after awhile and then try doing the second step again and it work so I'm thinking rebooting did the trick but now I get anothe error on the next step. Something aboput file permissions so I changed the file permissions and then everything worked.  :p
------
Everything worked till I rebooted. I can't get X to start up automaticly.
I have to:

$ sudo depmod
$ sudo modprobe nvidia
$ startx

I have to do this each time I start up. Did I do something wrong?

---

### Post by Tichondrius on 2005-02-11
You need to add "nvidia" line to /etc/modules (I added this in step 11 of the howto). This will make sure the module gets loaded at boot time:

$ sudo sh -c "echo nvidia >> /etc/modules"

---

### Post by Tichondrius on 2005-02-11
[QUOTE=orvalax]I've been trying to find out how to install the drivers for my Nvidia card for a few days now. This HOWTO is pretty cool. I ran into a problem when I tryed to complete step 2 though.



```
$ sudo dpkg -i nvidia-kernel-source_1.0.6629+1-1_i386.deb
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 74117 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_1.0.6629+1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.
dpkg: error processing nvidia-kernel-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-kernel-source


```

I haven't been using Linux for very long and I don't know what to do. Any help?[/QUOTE]

You need to install the dpatch and debhelper packages (I also added this to step 1):

$ sudo apt-get install dpatch debhelper

---

### Post by Ronbo on 2005-02-11
New Ubuntu user here, I have tried several times to install the Nvidia drivers but can't seem to get them working. Don't know if I am doing something wrong.  In the steps provided what does the **'uname -r'** mean is that something that I have to change. And if I do what does it refer to.  Any help would be greatly appreciated, I am becoming a big fan of Ubuntu and these drivers would be a big help.

---

### Post by Tichondrius on 2005-02-11
[QUOTE=Ronbo]New Ubuntu user here, I have tried several times to install the Nvidia drivers but can't seem to get them working. Don't know if I am doing something wrong.  In the steps provided what does the **'uname -r'** mean is that something that I have to change. And if I do what does it refer to.  Any help would be greatly appreciated, I am becoming a big fan of Ubuntu and these drivers would be a big help.[/QUOTE]
 uname -r returns the version name of the current running kernel, which is used to find the right configuration file and copy it to /usr/src/linux. Note that `uname -r` is used inside back quotes, not regular quotes, in

$ cp /boot/config-`uname -r` .config

the back quotes causes uname -r to be replaced by the version string. But you can always just use the actual version string, for example "2.6.8.1-4-386".

---

### Post by Ronbo on 2005-02-11
Thank you, that is exactly what I was doing wrong.  I didn't realize they were backquotes, I was using regular quotes.  Thanks for the help I appreciate it.

---

### Post by dejitarob on 2005-02-18
First I just want to say thanks for this well-written guide. But I have a question dealing with a new kernel and this method. Do I need to re-compile everytime I upgrade to a new kernel? Using apt-get I got the latest kernel from the repositories but when I try to boot into it I get: ```
Error: API mismatch: The NVIDIA kernel module is version 1.0.6111 but this X 
module is version 1.0.6299. Please be sure that your kernel module and all 
NVIDIA driver files have the same driver versions.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.
```So obviously there is a conflict with the old driver somewhere. Is there anyway to force the use of the X module instead of the one in the kernel?

---

### Post by Tichondrius on 2005-02-18
[QUOTE=dejitarob]First I just want to say thanks for this well-written guide. But I have a question dealing with a new kernel and this method. Do I need to re-compile everytime I upgrade to a new kernel? Using apt-get I got the latest kernel from the repositories but when I try to boot into it I get: ```
Error: API mismatch: The NVIDIA kernel module is version 1.0.6111 but this X 
module is version 1.0.6299. Please be sure that your kernel module and all 
NVIDIA driver files have the same driver versions.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.
```So obviously there is a conflict with the old driver somewhere. Is there anyway to force the use of the X module instead of the one in the kernel?[/QUOTE]
 If you upgrade to a pre-compiled kernel, you  can copy the kernel module from your compiled kernel to the new kernel, and it should usually work fine (unless there were big changes in the kernel versions).

Suppose your compiled kernel version is "2.6.8custom1". This is what you can do:

1. Boot your new kernel
2. After X fails to start, log in with a text terminal

3. Copy the kernel module:

$ sudo mkdir /lib/modules/`uname -r`/nvidia
$ sudo cp /lib/modules/2.6.8custom1/nvidia/nvidia.ko /lib/modules/`uname -r`/nvidia

4. Load the module:

$ sudo depmod
$ sudo modprobe nvidia

5. Start X:

$ startx

---

### Post by dejitarob on 2005-02-19
When I try to load the module using sudo depmod and sudo modprobe nvidia I get this: ```
FATAL: Error inserting nvidia (/lib/modules/2.6.8.1-5-k7/nvidia/nvidia.ko) 
invalid file format.
``` It is just an upgrade from 2.6.8.1-4-k7, which I used to compile the custom kernel, to 2.6.8.1-5-k7. Synaptic could not locate a changelog but major changes are not likely right?

---

### Post by dejitarob on 2005-02-21
Hmm, maybe I am just missing something but I fail to see the point in doing all these steps if you need to do them everytime you upgrade kernels.

---

### Post by orvalax on 2005-03-25
The links to the nvidia-kernal-source and the nvidia-kernal-common files are outdated. The new links for them are as follows

nvidia-kernal-source:
[http://http.us.debian.org/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-kernel-source_1.0.7167-1_i386.deb](http://http.us.debian.org/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-kernel-source_1.0.7167-1_i386.deb)

nvidia-kernal-common:
[http://http.us.debian.org/debian/pool/contrib/n/nvidia-kernel-common/nvidia-kernel-common_1.0.7167-1_all.deb](http://http.us.debian.org/debian/pool/contrib/n/nvidia-kernel-common/nvidia-kernel-common_1.0.7167-1_all.deb)

The link for the nvidia-glx package was also out of date, heres the new one

nvidia-glx
[http://http.us.debian.org/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-glx_1.0.7167-1_i386.deb](http://http.us.debian.org/debian/pool/non-free/n/nvidia-graphics-drivers/nvidia-glx_1.0.7167-1_i386.deb)
--------------------------------

While trying to install the nvidia-kernal-module I get an error.

```

# sudo dpkg -i nvidia-kernel-2.6.8.1custom1*.deb
dpkg: error processing nvidia-kernel-2.6.8.1custom1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 nvidia-kernel-2.6.8.1custom1*.deb
```

for some reason the file isn't there. so I looked back and it seems I get sometype of error when its making the file.

```
make[1]: Leaving directory `/usr/src/linux-source-2.6.8.1'
echo done >  stamp-kernel-configure
echo done >  stamp-configure
for module in  ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.8.1custom1" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG="EXTRAVERSION=.1custom1"        \
                             KDREV="10.00.Custom" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  fi;                                                      \
        done
``` 
I'm not sure if this is the error or not but I am sure when it made the first package this didn't happen. I'm still very new to Linux. Somone please give me a hand. =) thanks.  :)

---

