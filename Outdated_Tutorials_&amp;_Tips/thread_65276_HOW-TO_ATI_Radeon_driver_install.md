---
title: "HOW-TO: ATI Radeon driver install"
date: 2005-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by mlomker on 2005-09-13
The first thing that you should try is the driver that came with your distribution.  The Hoary driver is an older 8.8.25 version and Breezy comes with 8.16.20.  

Only use this how-to for Hoary because many things have changed in Breezy.  [Check here]("http://www.ubuntuforums.org/showthread.php?t=75382") for the Breezy how-to's.

**_Trying the included drivers ([B]Hoary ONLY**)_[/b] 

In your terminal:

```

su
apt-get install fglrx-control
apt-get install xorg-driver-fglrx
apt-get install linux-restricted-modules-$(uname -r)
fglrxconfig

``` 

If you aren't sure about other answers then just take the defaults--they are read from your existing file.

When you are ready you can press Ctrl-Alt-Backspace to restart your desktop and refer to the *Testing if it worked* section below.  If you can't get back into your desktop then you'll need run **dpkg-reconfigure xserver-xorg** from the command-line and go back to the ATI driver.

**_Upgrading to the 8.16.20 drivers ([B]Hoary ONLY**)_[/b] 

If you use KDE then substitute **kate** for **gedit** in the commands (command-line junkies can use **nano** or **vi**).  The how-to was written primarily with Hoary 32-bit users in mind.  64-bit users will need to change the filenames when appropriate.

**_Deleting the included drivers_** 

Remove everything related to the fglrx driver (if currently installed).  Go into Synaptic and search on **fglrx** and **linux-restricted**.  Right-click on each package and perform a **complete removal**.  

The following **find** command will delete the remaining files on your hard disk that have fglrx in its name *(contributed by nuk130n)*.

In your terminal:

```

xhost local:
su
find / -iname '*fglrx*' -exec rm '{}' -r ';'

```

The rest of the how-to assumes that this terminal window was left open.

**_Downloading components for compiling_** 

Download the [32-bit](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27) or [64-bit](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)   driver source from ATI.  You'll want the Xorg 6.8 package in RPM format.

amd64:

```

apt-get install alien

```

All versions:

Change to the directory that you downloaded the file to.  

```

apt-get build-dep fglrx-kernel-source
alien -d fglrx_6_8_0-8.16.20-1.i386.rpm
ls #*look for the name of the .deb for the next command*
dpkg -i --force-overwrite fglrx-6-8-0-8.16.20-2.i386.deb
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh

```

**_Backup your current configuration_** 

In your terminal:

```

cp /etc/X11/xorg.conf /etc/X11/xorg.bak

```

Go to [this website](http://www.objorkum.com/scripts/fglrxconfig/)  to create a new xorg.conf file.  (As an alternative you may type **fglrxconfig** in your terminal, but the website creates a file that is easier to read.)

In your terminal:


```

gedit /etc/X11/xorg.conf

```

Paste the output from the online generator into the file and save it (you're replacing what was in there).

Restart your machine.

**_Testing if it worked_ **

If you get to your desktop successfully, then type **fglrxinfo** to see if the driver is loaded.

If you see this, then it isn't working:

[i]
Output from fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
[/i]

You want to see something like this:

[i]
root@mlomkernote:/etc/X11 # fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)
[/i]

Then you can run **glxgears** (Breezy users have to type **glxgears -iacknowledgethatthistoolisnotabenchmark**).  The output should be well over 1000 FPS.

[i]
root@mlomkernote:/etc/X11 # glxgears
10514 frames in 5.0 seconds = 2102.800 FPS
11332 frames in 5.0 seconds = 2266.400 FPS
12600 frames in 5.0 seconds = 2520.000 FPS
[/i]

_**Troubleshooting**_

If for some reason you can't get to your graphical login then log in as root and copy your backup xorg.conf file back over the one we just made using the **cp /etc/X11/xorg.bak /etc/X11/xorg.conf** command (or run the reconfigure command mentioned previously).

At this point you'll need to make a post to the hardware forum with relevant error messages for help (**not in this thread, please**).  Feel free to send me a private message with a link to your post.

You should paste the output of the following commands into your post.

In your terminal:

```

fglrxinfo
dmesg | grep fglrx
cat /etc/X11/xorg.conf | grep Driver

```

You can also search for your error(s) and/or make a post on the [ATI user's forum.](http://www.rage3d.com/board) 


**_Where is the ATI Control Panel?  Why won't it run?**_ 

KDE users will automatically get the ATI control panel in their menus, but I've been told that gnome users do not.  The filename is /usr/X11R6/bin/fireglcontrolpanel and you can create your own icon if you wish. 

amd64 users may find that it won't run.  This is because it is looking at the wrong shared library.  Download the attached (bottom of message) fireglcontrol script to fix that.  Save the script to /usr/bin and rename it fireglcontrol.  **chmod +x /usr/bin/fireglcontrol** will make it executable.  You should then be able to run it using the **fireglcontrol** command in a terminal (or create an icon if you prefer).



**_Fglrxinfo looks right but I'm stuck at 1024x768!_**

The 8.16.20 driver has a bug with certain monitors (laptops with Samsung LCD's are one) that causes the resolution to be misdetected.  If you cannot increase your resolution (after the driver is properly installed) then you can try the older driver if you are still on Hoary.[32-bit](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300), [64-bit](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) .  There is [a thread]("http://www.rage3d.com/board/showthread.php?t=33825861") about this on the rage3d forum.  Hopefully it'll be fixed in a future version.


**_Future updates to the operating system_**

Whenever they decide to update the xlibmesa-gl package (usually in a security update for Xorg) you will get an error that it cannot overwrite the /usr/X11R6/lib/libGL.so.1.2 file.  This file was overwritten by the new ATI package and we need to keep it.  

In your terminal:

```

cp /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1.2-ATI
apt-get upgrade --force-overwrite *#or apt-get install --force-overwrite packagename for one package*
cp /usr/X11R6/lib/libGL.so.1.2-ATI /usr/X11R6/lib/libGL.so.1.2

```

**_Errors related to DRI**_
*(Thanks to Jormagand for this section)*

Some breezy users see the following error in their /var/log/Xorg.0.log file:

```

(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Download the [updated libdri.a](http://www.eigenarbeit.org/tmp/libdri.a) (i386 only) and from the directory that you downloaded the file to:

```

mv /usr/X11R6/lib/modules/extensions/libdri.a /usr/X11R6/lib/modules/extensions/libdri.a_old
cp libdri.a /usr/X11R6/lib/modules/extensions/libdri.a

```

---

### Post by AtomixPain on 2005-09-13
great tutorial man...but one thing though :razz: 
> apt-get install alien 
alien -D fglrx_4_3_0-8.16.20-1.i386.rpm
 

the alien -D should be alien -d !!!

thx again!

---

### Post by AtomixPain on 2005-09-13
Also u need to have Xfree86 installed for the driver to install...xorg is installed by default

---

### Post by [Koba] on 2005-09-13
Hi

I tried that earlier today with no success (same instructions from another thread). However, at that point my system was such a mess from this ATI business I am not at all surprised.

My dillema is there are so many ways of trying this. There is this method, the ATI installer Xorg method, the ATI installer ubuntu package method etc. This is going to take me a long time to get working.

I'm going to reinstall Ubuntu and try your method first though. Thank you for this thread.

Koba

Edit: I figured out the -d bit instead of -D. But I DIDN'T know I needed XFree86! Can someone tell me which package *exactly* I need and whether  I need to change anything xorg.

---

### Post by luffy on 2005-09-13
Nah, it works perfectly with X.org, I just followed the guide an hour ago and I most definetely run X.org. 
Good guide...

---

### Post by mlomker on 2005-09-13
[QUOTE=AtomixPain]Also u need to have Xfree86 installed for the driver to install...xorg is installed by default[/QUOTE]

The driver that I've linked to is for Xorg 4.3.  Hoary actually uses Xorg 4.2--perhaps some of you noticed the 60+ file security update that was pushed out today?  The 4.3 driver works fine, though.

I have to warn you guys that after installing this package you will start getting errors about MESA not being able to update itself when you go to update.  That's because the ATI driver needs to overwrite one of MESA's key files in order to function.  Indeed, that's why most methods of installing this driver fail to work.  I'm personally happy to ignore the errors and enjoy the performance--the MESA driver isn't needed.

---

### Post by mlomker on 2005-09-13
[QUOTE=AtomixPain]the alien -D should be alien -d !!!
[/QUOTE]

Thanks, I fixed the typo.  I probably spent 1.5 hours typing this thing up--it's a lot of work.  It took me over a day to figure out how to get the drivers to work consistently, though, and I didn't want that time to go to waste.

---

### Post by pjbgravely on 2005-09-14
[QUOTE=mlomker]  I probably spent 1.5 hours typing this thing up--it's a lot of work.  It took me over a day to figure out how to get the drivers to work consistently, though, and I didn't want that time to go to waste.[/QUOTE]

That is the Hacker philosophy, "every problem should only be solved once"

One thing, I had to change dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb

to dpkg -i --force- fglrx-4-3-0_8.16.20-2_i386.deb 

so that /usr/X11R6/lib/libGL.so.1.2 could be over written.

I still got this error:

root@lucy:/lib/modules/fglrx # sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-k7/kernel/drivers/char/drm/fglrx.ko): No such device
failed.

I believe it is due to My K7 Kernel, I may go back to 386 and try again.

Thanks again for the great Tut.


Paul

---

### Post by fortnox on 2005-09-14
i get to the: sudo dpkg -i fglrx64-4-3-0_8.16.20-2_amd64.deb

Then o joy dependancy error. I was one of the trigger happy bunnies who updated to breezy  \\:D/ 

Selecting previously deselected package fglrx64-4-3-0.
(Reading database ... 87045 files and directories currently installed.)
Unpacking fglrx64-4-3-0 (from fglrx64-4-3-0_8.16.20-2_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx64-4-3-0:
 fglrx64-4-3-0 depends on lib32gcc1 (>= 1:4.0.1); however:
  Version of lib32gcc1 on system is 4.0.1-4ubuntu6.
dpkg: error processing fglrx64-4-3-0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx64-4-3-0   ](*,) 

Help PLEASE... hehehe

---

### Post by Benzima on 2005-09-14
When I run:
*****
apt-get install alien
alien -d fglrx_4_3_0-8.16.20-1.i386.rpm
dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh
gedit /etc/modules
*****
I got

*****benzima@ubuntu:~$ cd /home/benzima
benzima@ubuntu:~$ apt-get install alien
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
benzima@ubuntu:~$ su
Password:
root@ubuntu:/home/benzima # apt-get install alien
Reading package lists... Done
Building dependency tree... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
root@ubuntu:/home/benzima # alien -d fglrx_4_3_0-8.16.20-1.i386.rpm
fglrx-4-3-0_8.16.20-2_i386.deb generated
root@ubuntu:/home/benzima # dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
dpkg: error processing fglrx_4_3_0-8.16.20-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx_4_3_0-8.16.20-1.i386.deb
root@ubuntu:/home/benzima # cd /lib/modules/fglrx/build_mod
bash: cd: /lib/modules/fglrx/build_mod: No such file or directory
root@ubuntu:/home/benzima # sh make.sh
sh: make.sh: No such file or directory
root@ubuntu:/home/benzima # cd ..
root@ubuntu:/home # sh make_install.sh
sh: make_install.sh: No such file or directory
root@ubuntu:/home # gedit /etc/modules

(gedit:13559): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
*****
What should I do or is that normal?

If I just press enter, gedit opens modules (/etc) and I have:

*****
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
*****

So I just added the line flgrx so it reads

*****
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
fglrx
******
And saved it
Is that right? I will wait for instructions before I proceed.

Thanxxx in advance.

---

### Post by Jormungand on 2005-09-14
> root@ubuntu:/home/benzima # dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
dpkg: error processing fglrx_4_3_0-8.16.20-1.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
fglrx_4_3_0-8.16.20-1.i386.deb 

From the above error Im guessing the .deb file that alien created has a different filename than what you are using. Go into where the .rpm file is and check the .deb filename you see there. I had the same problem myself. Once you use the correct .deb filename you can just continue on from that point in the HowTo

---

### Post by Jormungand on 2005-09-15
Thanks for the post mlomker!

Ive added a HOW-TO guide for Breezy [here.](http://ubuntuforums.org/showthread.php?t=66334)

---

### Post by mlomker on 2005-09-15
> I believe it is due to My K7 Kernel, I may go back to 386 and try again.


Perhaps.  I've done this install a number of times while testing and sometimes I did have that overwrite error and sometimes I did not.  I suppose it wouldn't hurt to add that to the how-to.

Which card do you have?  I worked with a guy in IM the other day that had a PCI-X card and the how-to didn't work out for him.  I have an AGP card, so that's what this is based on.

---

### Post by mlomker on 2005-09-15
[QUOTE=fortnox]Then o joy dependancy error. I was one of the trigger happy bunnies who updated to breezy  \\:D/ 
[/QUOTE]

You've already tried the Breezy **xorg-driver-fglrx** package and it doesn't work?  That's disturbing.

---

### Post by mlomker on 2005-09-15
> 
root@ubuntu:/home/benzima # alien -d fglrx_4_3_0-8.16.20-1.i386.rpm
fglrx-4-3-0_8.16.20-2_i386.deb generated
root@ubuntu:/home/benzima # dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb


You must have aborted the process and restarted.  Notice that alien changed the filename to end in a 2_i386?  I'd recommend deleting everything and starting from the beginning.

---

### Post by mlomker on 2005-09-15
> Apologies for hijacking your thread mlomker but these two troubleshooting s

I think parts of it are suboptimal, based upon my experience so far.  

1) You are apt-getting quite a few packages when only the two are needed.

2) The xserver-xorg reconfigure is text-based and creates a file that is really difficult to read if someone has a problem.  The online configurator output is clean.

Disabling internal AGP Gart will not work with a stock Ubuntu kernel (you'll find a message in **dmesg | grep fglrx** that'll say it's using the internal AGP Gart anyway). The reason is that the feature is built into Ubuntu's kernel and, therefore, cannot be shut off.  Perhaps you have a PCI-Express card that doesn't use the Gart anyway?  Adding the command won't hurt but it won't do anything, either...that's why I don't mention it in the how-to.

The Videoverlay command is only needed if you use tv-output.  The online configurator will put that in if you select the option.

3) I could not get the .sh installer script to work, regardless of process.  That is why I go with the alien conversion.  I needed to delete more than the .ko file to get things working.

4) The depmod command is redundant for this kernel module.  ATI's make_install script handles that and goes a step further by loading and unloading the module.

The DRI fix is good information.

---

### Post by cbudden on 2005-09-15
delete

---

### Post by Jormungand on 2005-09-15
1) You are apt-getting quite a few packages when only the two are needed.

During the .sh run throughs I recieved a few errors about gcc-3.4 missing, i installed it and then the scripts went through perfect. Having libstdc++5 cant hurt but I installed it at the same time as gcc-3.4 as it was recommended in another thread so Im not sure if its necessary.

2) The xserver-xorg reconfigure is text-based and creates a file that is really difficult to read if someone has a problem.  The online configurator output is clean.

I tried the online conf maker but It wouldnt start X for some reason... although it might have been because of the DRI error. To each their own :)

3) I could not get the .sh installer script to work, regardless of process.  That is why I go with the alien conversion.  I needed to delete more than the .ko file to get things working.

It might have been because of the c lib errors because of the package missing, thats what happened to me and why I found your alien method a good workaround. But after installing gcc-3.4 and libstdc+5 the .run file worked out perfectly.

4) The depmod command is redundant for this kernel module.  ATI's make_install script handles that and goes a step further by loading and unloading the module.

Indeed it is.

I edited my post [here](http://ubuntuforums.org/showthread.php?t=66334) to reflect your recommendations. Thanks.

---

### Post by Benzima on 2005-09-15
I thought I had it but it still got the X server error at reboot.

*****
root@ubuntu:/home/benzima # xhost +
access control disabled, clients can connect from any host
root@ubuntu:/home/benzima # su
root@ubuntu:/home/benzima # apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
root@ubuntu:/home/benzima # apt-get install linux-headers-2.6.10-5-386
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
root@ubuntu:/home/benzima # updatedb
root@ubuntu:/home/benzima # locate fglrx | more
/usr/X11R6/lib/libfglrx_gamma.1
/home/benzima/.Trash/fglrx-4-3-0_8.16.20-2_i386.deb
/home/benzima/.Trash/fglrx-4-3-0_8.16.20-2_i386 (copy).deb
/home/benzima/.Trash/fglrx_4_3_0-8.16.20-1.i386.rpm
/home/benzima/.Trash/fglrx-4-3-0_8.16.20-2_i386 (another copy).deb
/home/blaxima/.Trash/fglrx_4_3_0-8.16.20-1.i386.rpm
/home/blaxima/.Trash/fglrx-4-3-0_8.16.20-2_i386.deb
/home/blaxima/.Trash/fglrx_6_8_0-8.16.20-1.i386.rpm
/home/blaxima/.Trash/fglrx-4-3-0_8.16.20-2_i386 (copy).deb
/home/blaxima/.Trash/fglrx-4-3-0_8.16.20-1_i386.deb
/home/blaxima/fglrx_4_3_0-8.16.20-1.i386.rpm
/home/blaxima/fglrx-4-3-0_8.16.20-2_i386.deb
/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko
/lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko
/lib/modules/fglrx
/lib/modules/fglrx/build_mod
/lib/modules/fglrx/build_mod/2.6.x
/lib/modules/fglrx/build_mod/2.6.x/agp3.c
/lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.c
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c
/lib/modules/fglrx/build_mod/2.6.x/i7505-agp.c
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c
/lib/modules/fglrx/build_mod/2.6.x/agp_backend.h
/lib/modules/fglrx/build_mod/2.6.x/agp.h
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h
/lib/modules/fglrx/build_mod/2.6.x/drm.h
/lib/modules/fglrx/build_mod/2.6.x/drmP.h
/lib/modules/fglrx/build_mod/2.6.x/drm_os_linux.h
/lib/modules/fglrx/build_mod/2.6.x/drm_proc.h
/lib/modules/fglrx/build_mod/2.6.x/drm_compat.h
/lib/modules/fglrx/build_mod/2.6.x/.tmp_versions
/lib/modules/fglrx/build_mod/2.6.x/.tmp_versions/fglrx.mod
/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
/lib/modules/fglrx/build_mod/2.6.x/.agp3.o.cmd
/lib/modules/fglrx/build_mod/2.6.x/agp3.o
/lib/modules/fglrx/build_mod/2.6.x/fglrx.o
/lib/modules/fglrx/build_mod/2.6.x/.nvidia-agp.o.cmd
/lib/modules/fglrx/build_mod/2.6.x/.i7505-agp.o.cmd
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/.agpgart_be.o.cmd
/lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
/lib/modules/fglrx/build_mod/2.6.x/.firegl_public.o.cmd
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/.fglrx.o.cmd
/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.c
/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
/lib/modules/fglrx/build_mod/2.6.x/.fglrx.mod.o.cmd
/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd
/lib/modules/fglrx/build_mod/make.sh.log
/lib/modules/fglrx/build_mod/patch
/lib/modules/fglrx/build_mod/patch/include
/lib/modules/fglrx/build_mod/patch/include/linux
/lib/modules/fglrx/build_mod/patch/include/linux/highmem.h
/lib/modules/fglrx/build_mod/libfglrx_ip.a
/lib/modules/fglrx/build_mod/fglrx.ko
/lib/modules/fglrx/fglrx.2.6.10-5-386.ko
/lib/modules/fglrx/make.2.6.10-5-386.log
/lib/modules/fglrx/fglrx.ko
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima #
root@ubuntu:/home/benzima # rm -fr /lib/modules/fglrx
root@ubuntu:/home/benzima # apt-get install alien
Reading package lists... Done
Building dependency tree... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
root@ubuntu:/home/benzima # alien -d fglrx_4_3_0-8.16.20-1.i386.rpm
fglrx-4-3-0_8.16.20-2_i386.deb generated
root@ubuntu:/home/benzima # dpkg -i --force-overwrite fglrx_4_3_0-8.16.20-1.i386.deb
dpkg: error processing fglrx_4_3_0-8.16.20-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx_4_3_0-8.16.20-1.i386.deb
root@ubuntu:/home/benzima # dpkg -i --force-overwrite fglrx-4-3-0-8.16.20-1.i386.deb
_dpkg: error processing fglrx-4-3-0-8.16.20-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx-4-3-0-8.16.20-1.i386.deb
root@ubuntu:/home/benzima # dpkg -i --force-overwrite fglrx-4-3-0_8.16.20-2._i386.deb
dpkg: error processing fglrx-4-3-0_8.16.20-2._i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx-4-3-0_8.16.20-2._i386.deb
root@ubuntu:/home/benzima # dpkg -i --force-overwrite fglrx-4-3-0_8.16.20-2_i386.deb
Selecting previously deselected package fglrx-4-3-0.
(Reading database ... 73105 files and directories currently installed.)
Unpacking fglrx-4-3-0 (from fglrx-4-3-0_8.16.20-2_i386.deb) ...
Setting up fglrx-4-3-0 (8.16.20-2) ...

root@ubuntu:/home/benzima # cd /lib/modules/fglrx/build_mod
root@ubuntu:/lib/modules/fglrx/build_mod # sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6070: warning: `ati_gart_base' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:498: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:500: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:520: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:551: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3428: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
include/linux/module.h: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1921: warning: `deferred_flush' defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================
root@ubuntu:/lib/modules/fglrx/build_mod # cd ..
root@ubuntu:/lib/modules/fglrx # sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
done.
root@ubuntu:/lib/modules/fglrx # gedit /etc/modules

(gedit:11204): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@ubuntu:/lib/modules/fglrx # cp /etc/X11/xorg.conf /etc/X11/xorg.bak
root@ubuntu:/lib/modules/fglrx # gedit /etc/X11/xorg.conf

(gedit:11233): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@ubuntu:/lib/modules/fglrx #
*****

I thought everything went well except for maybe the GnomeUI warning.

BTW, I have a Radeon 9700 pro.

Any ideas? 4 'daze' and still no drivers. Argh!

I tried it again and rm'd everything with fglrx including those in /usr. Same thing. I'm gonna try the other method.
Thanxxx again

---

### Post by Benzima on 2005-09-16
I get unknown id when I run the sh line

*****
root@ubuntu:/home/benzima # sudo apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
Package xorg-driver-fglrx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@ubuntu:/home/benzima # sudo apt-get remove linux-restricted-modules-2.6.10-5-386
Reading package lists... Done
Building dependency tree... Done
Package linux-restricted-modules-2.6.10-5-386 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@ubuntu:/home/benzima # sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@ubuntu:/home/benzima # sudo apt-get install gcc-3.4
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@ubuntu:/home/benzima # sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@ubuntu:/home/benzima # su sh ./ati-driver-installer-8.16.20-i386
Unknown id: sh
root@ubuntu:/home/benzima # su sh ./ati-driver-installer-8.16.20-i386.run
Unknown id: sh
root@ubuntu:/home/benzima # su .sh ./ati-driver-installer-8.16.20-i386.run
Unknown id: .sh
root@ubuntu:/home/benzima #
*****

Should both of the methods in this thread work on a brnad new install of 5.04 or are other drivers not listed here needed? Someone said you need freexb or something. 
Any ideas?

Thanxxx.

---

### Post by Jormungand on 2005-09-16
[QUOTE=Benzima]I thought I had it but it still got the X server error at reboot.

root@ubuntu:/home/benzima # rm -fr /lib/modules/fglrx
[/QUOTE]

You missed removing 
/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko
/lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko

I would start again but remove everything besides the rpm/deb files you have in /home/benzima/ this time. Hope that helps.

---

### Post by Eleka on 2005-09-16
I have followed the howto, and I have no problems with start in graphical mode and the output of fglxinfo is the suggested by you when all works fine (is this:)

```
joseluis@lk-laptop-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9000/9100 IGP Series DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)
```

But, when I try to change the resolution, the 1280x1024 doesn't appears in my list (it is wrted in my xorg.conf correct section), and, if I run glxgears, a medium-size black windows appears on my up-left corner and the computer went blocked, and I have to restart it with reset button.

I follow all the steps and anything get me a error or a warning,.. What can I do to solve this? 

Note: I post it here because the gnome have begun.
Note 2: Excuse me my english, it's poor i know  :-#

---

### Post by Jormungand on 2005-09-16
[QUOTE=Benzima]
Should both of the methods in this thread work on a brnad new install of 5.04 or are other drivers not listed here needed? Someone said you need freexb or something. 
Any ideas?[/QUOTE]

Its sudo sh ,/filename.run

---

### Post by Eleka on 2005-09-16
[QUOTE=Jormungand]redoing[/QUOTE]
 But if I do the same, Won't I get the same ...?

I will retry it, but I think that it won't work :(

---

### Post by Jormungand on 2005-09-16
Eleka post the results from these two commands in your message above.

dmesg | grep fglrx
grep WW /var/log/Xorg.0.log

---

### Post by Eleka on 2005-09-16
First:
```
joseluis@lk-laptop-ubuntu:~$ sudo dmesg | grep fglrx
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 373 MBytes.
[fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[fglrx] Internal AGP support requested, but kernel AGP support active.
[fglrx] Have to use kernel AGP support to avoid conflicts.
[fglrx] Kernel AGP support doesn't provide agplock functionality.
[fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[fglrx] free  AGP = 21245952
[fglrx] max   AGP = 21245952
[fglrx] free  LFB = 55570432
[fglrx] max   LFB = 55570432
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 8192

```

and second

```
joseluis@lk-laptop-ubuntu:~$ sudo grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/X11R6/lib/X11/fonts/CID" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Speedo" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/TTF" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/local" does not exist.
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 1
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)

```

---

### Post by pjbgravely on 2005-09-16
[QUOTE=pjbgravely] I believe it is due to My K7 Kernel, I may go back to 386 and try again.[/QUOTE]


[QUOTE=mlomker]Perhaps.  I've done this install a number of times while testing and sometimes I did have that overwrite error and sometimes I did not.  I suppose it wouldn't hurt to add that to the how-to.

Which card do you have?  I worked with a guy in IM the other day that had a PCI-X card and the how-to didn't work out for him.  I have an AGP card, so that's what this is based on.[/QUOTE]

It is a Radeon Mobility U1 onboard chip using PCI in a hp pavilion ze4805 wm laptop. I know I am crazy for trying it now that I have read that ATI doesn't even support it for windows but having TV out would be great. This was my third try, and I have 2 more install methods left to try.


Paul

---

### Post by mlomker on 2005-09-16
> 
During the .sh run throughs I recieved a few errors about gcc-3.4 missing, i installed it and 


That's because you are running *Breezy* aren't you?  Breezy installs only the 4.x compiler by default (insanity if you ask me since very little will compile with it yet).  

My how-to is for Hoary.  The latest drivers are already included with Breezy so this whole process shouldn't be necessary on Breezy.  If you tried the stock drivers and it didn't work then I'd be curious to hear about that.

I updated my preamble and renamed my thread to clarify.  Want to clean up your how-to and post it in a new thread?

---

### Post by mlomker on 2005-09-16
[QUOTE=Benzima]I thought I had it but it still got the X server error at reboot.

*****
root@ubuntu:/home/benzima # xhost +
access control disabled, clients can connect from any host
root@ubuntu:/home/benzima # su
root@ubuntu:/home/benzima # apt-get install build-essential
Reading package lists... Done
[/quote]

Please edit/delete your post and create a new post in the hardware forum.  Feel free to send me a pvt with a link to it, but I do read the ATI-related posts anyway.  Brief questions in a how-to are okay but this is way too long.  

Offhand it looks like you failed to delete two files and I need the output from the troubleshooting commands to speculate beyond that.

---

### Post by mlomker on 2005-09-16
[QUOTE=Benzima]
Should both of the methods in this thread work on a brnad new install of 5.04 or are other drivers not listed here needed? Someone said you need freexb or something. 
[/QUOTE]

Please do not discuss this in this thread since it is unrelated to my how-to.  Send a private note to the original poster if you want help with his method.  

I couldn't get the .sh to work, which is why I didn't use it.

---

### Post by mlomker on 2005-09-16
[QUOTE=Eleka]I follow all the steps and anything get me a error or a warning,.. What can I do to solve this? [/QUOTE]

Post the output of the troubleshooting commands in a new thread on the hardware forum and we'll take a look at it.  Your card is fairly old but the driver is supposed to work with Radeon 8500 and up.

Another option is to post a mesage on the [ATI user forum](http://www.rage3d.com/board) with the error messages.

---

### Post by mlomker on 2005-09-16
[QUOTE=pjbgravely]It is a Radeon Mobility U1 onboard chip using PCI in a hp pavilion ze4805 [/QUOTE]

I had that in my last laptop, an Emachines.  The video out can be made to work in conjunction with the 'radeon' driver but 3D is a bear.  Last I heard you had to make some changes to the Xorg server source code and recompile it.  Yikes!  Too much work for me.

Check out [this page](http://rzr.online.fr/docs/comp/gfxcard.htm) and try the [ATI user's forum.](http://www.rage3d.com/board).

---

### Post by gelse on 2005-09-16
just wanted to post to [this](http://www.ubuntuforums.org/showthread.php?t=65827) thread.

summary:
if everything else fails - check if framebuffer is disabled in your kernel. or LET it check someone who can compile a kernel. ;)

and thanks alot to mlomker!

---

### Post by mlomker on 2005-09-16
[QUOTE=gelse]
if everything else fails - check if framebuffer is disabled in your kernel.
[/QUOTE]

Judging from the many people that I've come into contact on these forums, I can assure you that only a small percentage could successfully recompile their kernels.  For that reason I'll leave it off my how-to because it's atypical.  Besides, breezy will be out and a couple months from now this how-to might be unecessary.

---

### Post by rimmer on 2005-09-16
What's the problem with new ATI drivers ?

It worked fine for me. Download and run! (after getting rid of all your old files ) 

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

I used the dreaded builtin config maker, it workes !

I've never had a problem with my ATI card (only when I've got to upgrade my headers then I've got to reinstall the drivers)

Its worked for me for the past 1 1/2 years, I really don't understand why people try and make it like voodoo it's not it's ATI.

---

### Post by Jormungand on 2005-09-16
[QUOTE=mlomker]That's because you are running *Breezy* aren't you?  Breezy installs only the 4.x compiler by default (insanity if you ask me since very little will compile with it yet).  

My how-to is for Hoary.  The latest drivers are already included with Breezy so this whole process shouldn't be necessary on Breezy.  If you tried the stock drivers and it didn't work then I'd be curious to hear about that.

I updated my preamble and renamed my thread to clarify.  Want to clean up your how-to and post it in a new thread?[/QUOTE]

Yea breezy was the culprit on lack of 3.4 by default. And I did try the stock drivers and they wouldnt load, fglrx module wouldnt load to give me direct rendering support. Ill clean up my posts in the thread and start a new one. Thanks again.

---

### Post by mlomker on 2005-09-16
> Its worked for me for the past 1 1/2 years, I really don't understand why people try and make it like voodoo it's not it's ATI.

I'm glad to hear it, but I don't think many people would agree with your assessment.  There are multiple posts every day asking why they don't work.  Feel free to help those people out.

---

### Post by gelse on 2005-09-17
> I'm glad to hear it, but I don't think many people would agree with your assessment. There are multiple posts every day asking why they don't work. Feel free to help those people out.
was about to write the same, but not as friendly as you. thanks for saving me from making myself unpopular.

anyway - to come back to direct rendering:
i agree to you at the kernel-compile point - regarding its no good idea for most people - but what i wondered:
if framebuffer (at laptops?) makes really that much problem with OpenGL, and framebuffer is activated (not even modularized - its activated as far as i remember) in the precompiled kernel - why dont have more people the same problem like me?
when dealing with my problem the framebuffer was the last i thought could be the problem, just because noone else mentioned it.
ok, stanchina drops ONE line in his howto, but noone else.
what could be the difference? noone using a laptop? newer cards not  affected?

---

### Post by mlomker on 2005-09-17
> ok, stanchina drops ONE line in his howto, but noone else.
what could be the difference? noone using a laptop? newer cards not  affected?

I have a laptop and use the stock kernel with 2200-2500 framerates and no errors.  

One of the problems with computer support in general is the diversity of hardware combinations out there.  One of the keys to Apple's success is drastically limiting your choices!  We don't have that luxury on the white-box side of the house and everything becomes a compromise.

We could file a bug report and ask the developers to modularize the pieces that can be modularized--at least that'd allow adding the modules to /etc/hotplug/blacklist.  I'm also still pretty new to Ubuntu with only a month or so behind my belt...I haven't figured out how to best report those kind of matters.  I saw a reference in another post to bugzilla.

---

### Post by darrensnospam on 2005-09-17
mlomker,

I followed your install exactly and xorg wouldn't load. I reread your thread and noticed that you had me install the xfree4.3 drivers.

In the meantime, I had updated all my xorg files from the Ubuntu repository.

So I uninstalled all of my fglrx files following your instructions and built a custom install using your instructions for xorg6.8 rather than xfree4.3.

I used the online fglrx online configurator. 

Rebooting - an not expecting much - I was so happy when X came up and glxgears were working great.

I've been pounding on this thing for a week and a half.

Thanks for your help. This is really fantastic.

---

### Post by mlomker on 2005-09-17
> I followed your install exactly and xorg wouldn't load. I reread your thread and noticed that you had me install the xfree4.3 drivers.


One of the first posters make a reference to Xfree and I didn't understand what they were talking about.  I was linking to wrong driver all of this time!  I intended to link to the Xorg driver that you ended up using but got confused when I cut/pasted the links for the how-to.

Needless to say, I've fixed the links to point to Xorg so this won't be a problem for others.

EDIT: I've learned the XOrg is actually a refined version of the work that was originally done by the Xfree project.  Therefore, the Xfree drivers should work fine for most people but the Xorg are the best choice.

---

### Post by martmort on 2005-09-18
Hi!
I've always had problems getting my ati graphic card to cooporate with linux.. So therefore if I get this guide to work, I would be very glad..

But I got this error somewhere in the guide:

[COLOR=Green][i]root@ubuntu:/lib/modules/fglrx/build_mod # sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h[/i][/COLOR]

do anyone have any idea of what's wrong?

---

### Post by mlomker on 2005-09-18
> do anyone have any idea of what's wrong?

The kernel headers are not installed or the symbolic link is missing.  Did you apt-get them in the beginning of the how-to?  If so, then force them to reinstall and see if that resolves it.

```

apt-get install --reinstall linux-headers-$(uname -r)

```

That symbolic link can get overwritten when downloading certain packages, such as the kernel source.

---

### Post by martmort on 2005-09-18
wow.. well something happened.. I will try to do that make.sh thing again now.. so I'll inform you soon

[EDIT] WOW.. it worked totally..

---

### Post by martmort on 2005-09-18
it's just one thing

every other second the whole screen freezez for like a half second.. what's that??

---

### Post by mlomker on 2005-09-18
> every other second the whole screen freezez for like a half second.. what's that??

Post the output from the troubleshooting commands.  I haven't seen that issue before.  There are so many combinations of cards and monitors that it's hard to say.  If the troubleshooting output looks right then you may have to jump on the rage3d site.

---

### Post by PSyMastR on 2005-09-18
HOLY HELL!!!
I have been searching for over 4 months to get my driver working, and it works!  You are the best!

---

### Post by martmort on 2005-09-18
[QUOTE=mlomker]Post the output from the troubleshooting commands.  I haven't seen that issue before.  There are so many combinations of cards and monitors that it's hard to say.  If the troubleshooting output looks right then you may have to jump on the rage3d site.[/QUOTE]

ahh.. yeah sorry about that.. I saw afterwards that problems on other things than the guide shouldn't be posted here.. sorry =]

but you rock man.. nice guide :D

---

### Post by fortnox on 2005-09-19
When running sh make.sh

i get the following.

ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.12-8-amd64-xeon/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-amd64-xeon'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_init':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8166: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_cleanup':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8176: warning: `pm_unregister_all' is deprecated (declared at include/linux/pm.h:116)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6070: warning: 'ati_gart_base' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:124:25: asm/ioctl32.h: No such file or directory
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:498: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:500: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:520: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:551: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_get_user_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1067: warning: assignment makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_put_user_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_verify_area':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1428: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:54)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_register_ioctl32_conversion':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2177: warning: implicit declaration of function `register_ioctl32_conversion'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_unregister_ioctl32_conversion':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2182: warning: implicit declaration of function `unregister_ioctl32_conversion'
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-amd64-xeon'
make: *** [kmod_build] Error 2
build failed with return value 2


If this has been mentioned in a earlier post i apologise.

Could someone please help me out with this

---

### Post by mlomker on 2005-09-19
> If this has been mentioned in a earlier post i apologise.

Post #12.

That being said, I've thrown in the towel and have updated my how-to for Breezy.  I didn't want to put anything in for that because I will not run Breezy until it is released (my computer is a laptop that I use at work and I can't have things crashing on it).

The fact that I don't run Breezy makes it tough for me to help people troubleshoot problems related to the install.  Having Breezy info on the how-to more or less obligates me to help them if they have any trouble.  See my dilemma?

---

### Post by zarathustra on 2005-09-21
Followed this guide to the letter and the install seemed to go smoother than usual (no errors about inserting fglrx.ko like others have reported and I've had before). However it did not work, the graphical interface did not start up and I've got this error I've always got when attempting to install the latest drivers:

> (II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

---

### Post by mlomker on 2005-09-21
>  the graphical interface did not start up and I've got this error I've always got when attempting to install the latest drivers:

Are you running a custom 2.6.13 kernel?  I found a reference to that error [here.](http://lists.debian.org/debian-amd64/2005/09/msg00218.html)

---

### Post by Billquinn1 on 2005-09-21
Everything went great until:


root@ubuntu:/lib/modules/fglrx/build_mod # sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
Makefile:50: *** mixed implicit and normal rules.  Stop.
build failed with return value 2


Any ideas?

This is my first post as I almost always find my answers here by just searching.

Athlon 2800+, 1024MB, 40GB, Asus Radeon 9600 xt,  Kubuntu 5.04

---

### Post by mlomker on 2005-09-21
> Any ideas?

This is my first post as I almost always find my answers here by just searching.


I ran a search on that error and [came up with this](http://ubuntuforums.org/archive/index.php/t-32495.html). 

> 
this seems to be caused by an error(?) in the ATI makefile where your verison of GCC is detected or parsed incorrectly. To work around this change the first line of /lib/modules/fglrx/build_mod/2.6.x/Makefile to read : -

GCC_VER_MAJ = 3


Judging from that I'd say that you are running Breezy and for some reason it's trying to use the 4.x compiler rather than the 3.4.

---

### Post by Billquinn1 on 2005-09-21
> Judging from that I'd say that you are running Breezy and for some reason it's trying to use the 4.x compiler rather than the 3.4.

> this seems to be caused by an error(?) in the ATI makefile where your verison of GCC is detected or parsed incorrectly. To work around this change the first line of /lib/modules/fglrx/build_mod/2.6.x/Makefile to read : -

GCC_VER_MAJ = 3

I found the same post and tried his suggestion but it had no effect.  I am not to sure how else attack the possible GCC version trouble.


BTW, I am running Hoary but can't wait to try out Breezy.

---

### Post by mlomker on 2005-09-21
[QUOTE=Billquinn1]I found the same post and tried his suggestion but it had no effect.  I am not to sure how else attack the possible GCC version trouble.
[/quote]

What is the output of **gcc --version** (should be 3.3.5)?  Do you have more than one version of gcc installed (search in synaptic)?


> BTW, I am running Hoary but can't wait to try out Breezy.

The Kubuntu amd64 version is still too unstable...that I can tell you for certain.  I've heard a lot of varying reports so far.

---

### Post by Billquinn1 on 2005-09-21
> What is the output of gcc --version (should be 3.3.5)? Do you have more than one version of gcc installed (search in synaptic)?

bill@ubuntu:~ $ gcc --version
gcc.real (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)

Synaptic shows:
gcc  ____                   4:3.3.5-1
gcc-3.3____               1:3.3.5-8
gcc-3.3-base  ____   1:3.3.5-8
gcc-4.0-base _____   4.0.0-7

I looked at uninstalling the gcc-4.0-base but it threatened me with removing open office and a slew of other stuff.

All this started after that last round of updates. I guess it updated a package that is making the ATI script unhappy.

---

### Post by mlomker on 2005-09-22
> All this started after that last round of updates. I guess it updated a package that is making the ATI script unhappy.

Are you sure that you deleted the /lib/modules/fglrx directory prior to installing the package that alien created?  It's the only thing that I can think of because everything else checks out in your setup.  It took me an entire day to come up with this process and it failed until I was fanatical about deleting everything with **fglrx** in its name.  That's a critical step in my how-to.

---

### Post by zarathustra on 2005-09-22
> Are you running a custom 2.6.13 kernel? I found a reference to that error here. 

It's the default kernel that comes with hoary.

---

### Post by mlomker on 2005-09-22
[QUOTE=zarathustra]It's the default kernel that comes with hoary.[/QUOTE]

That file comes with the xserver-xorg package and the package has never been updated by Ubuntu, afaik.

What is the output of **ls -l /usr/X11R6/lib/modules/linux/libint10.a**?  I have a freshly installed /updated Hoary and it is dated 2005-08-30 and is 29504 in size.

---

### Post by zarathustra on 2005-09-22
-rw-r--r--  1 root root 295582 2005-04-05 17:16 /usr/X11R6/lib/modules/linux/libint10.a

---

### Post by mlomker on 2005-09-22
[QUOTE=zarathustra]-rw-r--r--  1 root root 295582 2005-04-05 17:16 /usr/X11R6/lib/modules/linux/libint10.a[/QUOTE]

If your system is up-to-date then the only thing I'd suggest is forcing a reinstall for xserver-xorg in Synaptic--and that's a *grasping at straws* thing.  If you haven't been on the rage3d forum then it's worth a try--the ATI developers visit there.

---

### Post by gelse on 2005-09-23
shouldnt the 8.16.20 drivers be compatible with gcc-4 ? at least they mention it in the changelogs.

---

### Post by mlomker on 2005-09-23
[QUOTE=gelse]shouldnt the 8.16.20 drivers be compatible with gcc-4 ? at least they mention it in the changelogs.[/QUOTE]

I read that as well.  The issue here is that kernel modules always have to be compiled using the exact same version of GCC that the kernel was compiled with.  In the case of Breezy, that's 3.4.  

I think it comes with 4.x because KDE and some other parts of the operating system are now compiled with it.

I'm not a programmer...I'm just a systems admin.  For my job I just have to make things work; I don't always understand why and usually don't have the time.

---

### Post by Quirky on 2005-09-23
Excellent, finally worked after following the howto. 

One part that didn't 'Just Work' was the *sh make_install.sh* of the drivers. It couldn't modprobe fglrx. I had to add fglrx to /etc/modules and reboot. After that, worked a treat. The Hoary default drivers when added to /etc/modules or modprobe'd in caused the whole 'puter to hand when running glxgears. They worked for 2D stuff, but not for 3D.

As an aside, does this have any known issues when upgrading from Hoary to Breezy? i.e. will the alien flgrx drivers be overwritten by the upgrade?

---

### Post by mlomker on 2005-09-23
> It couldn't modprobe fglrx. I had to add fglrx to /etc/modules and reboot. After that, worked a treat. The Hoary default drivers when added to /etc/modules or modprobe'd in caused 


My how-to originally included adding fglrx to /etc/modules.  I was correct by someone who told me that the X server would load it automatically due to the Driver line in xorg.conf.  I tested that and confirmed it to be true...and removed that step from my how-to.

> 
the whole 'puter to hand when running glxgears. They worked for 2D stuff, but not for 3D.


Yup, all I got was a black screen.  The driver that came with Hoary was fairly old.

> 
As an aside, does this have any known issues when upgrading from Hoary to Breezy? i.e. will the alien flgrx drivers be overwritten by the upgrade?

I don't know what will happen because I'm not going to upgrade until it is released.  In theory Breezy has the latest driver so things should work fine.  Dist-upgrades are failing anyway right now and people have to do a **dpkg-reconfigure xserver-xorg** to update the xorg.conf file before they can go graphical (caused by an upgraded version of the X server being incompatible with the xorg.conf files generated by Hoary).

I've had a number of Breezy users tell me that the included driver didn't work but I have no way of knowing if they are installing it properly.

---

### Post by imrazor on 2005-09-26
I'd be perfectly happy with the fglrx compiled for Hoary, but I can't seem to get it to install. When I attempt 

apt-get install xorg-driver-fglrx

I get:

E: Couldn't find package xorg-driver-fglrx

Restricted drivers do show up as installed in kynaptic, but when I attempt to change the Driver in xorg.conf to fglrx, the X server will not load. Is the fglrx driver out there somewhere and I have an improperly built xorg.conf? Why can't I apt-get xorg-driver-fglrx? I also tried the command to rebuild the xorg.conf, but fglrx was not one of the available drivers.

Any assistance would be greatly appreciated.

---

### Post by mlomker on 2005-09-26
> Why can't I apt-get xorg-driver-fglrx?

No idea.  Did you search in Kynaptic for **fglrx**?

What version of Ubuntu and what repositories are you using?  What video card do you have?

---

### Post by imrazor on 2005-09-26
[quote=mlomker]No idea.  Did you search in Kynaptic for **fglrx**?

What version of Ubuntu and what repositories are you using?  What video card do you have?[/quote] 
Ubuntu version: Kubuntu, Hoary Hedgehog (5.04)

Video card: ATI Radeon Mobility 9600

Repositories: from my sources.list
=====
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe

 deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
=====
Thanks for replying...

---

### Post by mlomker on 2005-09-26
[QUOTE=imrazor]main restricted[/quote]

Change all of those to read: main restricted universe multiverse

Your card should work fine.

---

### Post by shaul26 on 2005-09-27
> 
shaul@ubuntu:/lib/modules/fglrx$ sudo sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): Operation not permitted
failed.


What's the problem?

---

### Post by mlomker on 2005-09-27
[QUOTE=shaul26]What's the problem?[/QUOTE]

I don't know.  What model of video card do you have?

---

### Post by shaul26 on 2005-09-27
9200se

---

### Post by mlomker on 2005-09-27
[QUOTE=shaul26]9200se[/QUOTE]

I found a similar error on a Fedora chat board.  They said that the currently loaded video driver can sometimes conflict with the fglrx module loading.  I'd suggest finishing the how-to and updating your xorg.conf file and reboot.  The worst that could happen is that you'll have to copy back your backup copy of the file, as mentioned in the how-to.

---

### Post by shaul26 on 2005-09-27
Ok now It works :)

I tried play RTCWolfenstein and It's very slow... why is that?

---

### Post by Petawa on 2005-09-27
I'm running Breezy 64-bit, and I've followed until this part:
apt-get build-dep fglrx-kernel-source (I'm using sudo to run it)

I get
[I]Reading package lists... Done
Building dependency tree... Done
E: You must put some 'source' URIs in your sources.list[/I]

Then I try to continue w/ sh make.sh and get
[I]make.sh: line 39: gcc: command not found
make.sh: line 45: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h[/I]

Can anyone tell me how to fix it? 
Thanks.

---

### Post by mlomker on 2005-09-27
> E: You must put some 'source' URIs in your sources.list[/I]


Either you have the deb-src lines commented out of your /etc/apt/sources.list or you removed them.  Refer to the list that I have attached as an example.

---

### Post by mlomker on 2005-09-27
> I tried play RTCWolfenstein and It's very slow... why is that?

If glxgears is providing a decent output then you'd be better off asking on the games forum.  I actually don't play games.  I installed the upgraded drivers just because I paid for a nice video card and wanted my money's worth.  :D

---

### Post by imrazor on 2005-09-27
OK, OpenGL now works beautifully. fglxgears and Neverwinter Nights run at wonderful framerates. Now here's the rub: 2d support under fglrx sucks. kaffeine and gxine play videos play very  choppily and there's a persistent jaggie effect. As near as I can figure I have two choices: a) install the latest fglrx from ATI, which may or may not have decent 2d support, or b) find a way to alternate between the fglrx and ati drivers. a) sounds iffy and complicated, so let's examine b). Seems simple enough; replace fglrx in the xorg.conf with ati. Doesn't work. The mouse cursor is garbage along with a significant portion of the screen. Also tried reverting to my old (pre-fglrx) xorg.conf, and also uninstalling the fglrx driver completely with kynaptic, neither of which worked. Going back to the fglrx driver fixes the mouse, but leaves me with choppy video. Any one have any ideas?...Thanks.

Relevant info:

OS:Kubuntu 5.04 i386
System: eMachines M6805
Processor: AMD Mobile Athlon64 3000+ 
Video Card: ATI Mobility Radeon 9600
Chipset: VIA K8T800

---

### Post by mlomker on 2005-09-27
>  Now here's the rub: 2d support under fglrx sucks. kaffeine and gxine play videos play very  choppily and there's a persistent jaggie effect. 


I've never noticed that, but then again I've only played one DVD and that was just to test out Kaffeine.

> As near as I can figure I have two choices: a) install the latest fglrx from ATI, which may or may not have decent 2d support, 


If you are running the stock 8.8.25 then that's worth a shot.  Those are old.

>  b). Seems simple enough; replace fglrx in the xorg.conf with ati. Doesn't work. The mouse cursor is garbage along with a significant portion of the screen.

No, there are significant differences.   My how-to instructs you to back up your current xorg.conf (presumably the ATI config in your case) to xorg.bak.  Is that the one that you tried using?

If you didn't make the backup then you could save a copy of the fglrx xorg.conf and then run **dpkg-reconfigure xserver-xorg** to create one for the ATI.  You can then copy that somewhere and copy them back and forth if you like.

---

### Post by imrazor on 2005-09-27
Thanks for the really quick reply.

Before I started experimenting I created a file called xorg.ati that had my original Ubuntu-created config. When I copy it over xorg.conf, I get the garbage mouse. I know I shouldn't, but I do. I also tried dpkg-reconfigure xserver-xorg, selected the ati driver, and still got garbage for a cursor. It's too late to try right now, but tomorrow I'll try building an updated fglrx from source, as covered in the latter half of your FAQ. I'll have to print it out first though and do everything from a tty, because once I remove the old fglrx, X will become garbage. Strange. 

Thanks again.

---

### Post by shaul26 on 2005-09-28
[QUOTE=mlomker]If glxgears is providing a decent output then you'd be better off asking on the games forum.  I actually don't play games.  I installed the upgraded drivers just because I paid for a nice video card and wanted my money's worth.  :D[/QUOTE]

Yeah glxgears works very well... thanks for your help :)

---

### Post by Curlydave on 2005-09-28
> david@ubuntu:/lib/modules/fglrx/build_mod$ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

What's going on here?

---

### Post by mlomker on 2005-09-28
[QUOTE=Curlydave]What's going on here?[/QUOTE]

It looks like you don't have the kernel headers installed.  Try **apt-get install linux-headers-$(uname -r)** to be sure, but the **apt-get build-dep fglrx-kernel-source** command should have taken care of that.

---

### Post by xthaparian on 2005-09-28
After doing dmsg | grep  fglrx I get

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 805 MBytes.
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx:firegl_unlock] *ERROR* Process 6906 using kernel context 0


---
after doing
dmesg | grep fglrx
I get...


fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 805 MBytes.
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx:firegl_unlock] *ERROR* Process 6906 using kernel context 0
xthaparian@ubuntu:~$ cat /etc/X11/xorg.conf | grep Driver
     Driver "kbd"
     Driver "mouse"
     Driver "fglrx"


and the fglrxinfo is as...
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


I dont know what wrong did i do..

Well the thing is I followed the HOWTO AND DID exactly the same as described.
I did backup too..and restarted..

Now It started..and i get these messages???

please any help would be appreciated.

---

### Post by mlomker on 2005-09-28
> [fglrx:firegl_unlock] *ERROR* Process 6906 using kernel context 0


What card do you have and what kernel are you using (**uname -r**)?  

I did a couple Google searches and all of the errors pointed to a kernel/AGP problem.  You need to look at **dmesg | less** from the time that fglrx starts until the last entry.  [Look here]("http://forums.fedoraforum.org/showthread.php?t=63910&page=3") for a post of a similar problem.

You might want to jump on the ATI forums mentioned in the how-to.

---

### Post by imrazor on 2005-09-28
After much frustration with the stock fglrx that's available for Hoary, I tried building a driver from the 8.16.20 rpm. The results were disappointing. Firstly I found that 1280x800 was no longer a supported resolution. Even though the xorg.conf built with dpkg-reconfigure xserver-xorg *clearly* specified 1280x800, the displayed resolution was 1024x768 scaled to fit the larger screen, resulting in a distorted image. (I also tried building xorg.conf with the specified website, but I still only got 1024x768.) On top of this, video playback was still choppy, with a wacked aspect ratio to boot. So I tried reverting to the old fglrx, but everytime I checked the GL version I was getting the Mesa library no matter what I tried. I then decided to nuke the whole install and retry with the stock fglrx. I now have choppy video and nice 3d performance. Any other tricks I can try?

---

### Post by mlomker on 2005-09-28
> Firstly I found that 1280x800 was no longer a supported resolution. Even though the xorg.conf built with dpkg-reconfigure xserver-xorg *clearly* specified 1280x800, 
Did you try this?
> 
**Fglrxinfo looks right but I'm stuck at 1024x768!**
The 8.16.20 driver has a bug with certain monitors (laptops with Samsung LCD's are one) that causes the resolution to be misdetected. If you cannot increase your resolution (after the driver is properly installed) then you may want to try the same steps using the 8.14.13 driver: 32-bit, 64-bit . There is a thread about this on the rage3d forum and I'm sure they'll fix it in the next version.


---

### Post by oxEz on 2005-09-29
Is there a way to mke Xorg recognize changes made to xorg.conf without rebooting? That's quite annoying when I'm trying to get X to start, and I need to reboot everytime I edit something :???:

nvm, figured out I runned /etc/init.d/gdm as user, not with sudo or as root. (sad face)

---

### Post by Gorauma on 2005-09-29
hmm. I struggled with the drivers several hours and they just didn't seem to work. I had the [fglrx:firegl_unlock] *ERROR* Process 6906 using kernel context 0 string popping up and hw opengl accerelation disabled. I was about to give up when i found this:

1. download official driver .rpm from ATI
2. remove fglrx packages using Synaptic
3. shut down Gnome (terminal: sudo /etc/init.d/gdm stop)
4. cd to download-location
5. sudo alien fglrx_ ... .rpm
6. sudo mv 
/lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. sudo dpkg --force-overwrite -i fglrx- ... .deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. sudo modprobe fglrx
13. sudo fglrxconfig

worked for me, i hope it works for others as well
EDIT: Oh, note the 6. step, i think that did the trick.

---

### Post by mlomker on 2005-09-29
> Is there a way to mke Xorg recognize changes made to xorg.conf without rebooting? 

Ctrl-Alt-Backspace will restart your graphical environment...close everything first because it's not a friendly restart for your applications.

---

### Post by mlomker on 2005-09-29
> 
13. sudo fglrxconfig


That process is pretty much the same as my how-to in the end.  One of the first steps is to delete everything named fglrx, so line 6 is the same.  The only thing that makes sense to me is that the fglrxconfig might have worked better for you than the dpkg-reconfigure command.  

I've decide to change the reconfigure to the fglrxconfig in my how-to.  Thanks for the feedback.

---

### Post by xthaparian on 2005-09-30
[QUOTE=mlomker]What card do you have and what kernel are you using (**uname -r**)?  

I did a couple Google searches and all of the errors pointed to a kernel/AGP problem.  You need to look at **dmesg | less** from the time that fglrx starts until the last entry.  [Look here]("http://forums.fedoraforum.org/showthread.php?t=63910&page=3") for a post of a similar problem.

You might want to jump on the ATI forums mentioned in the how-to.[/QUOTE]

I did follow the tutorail from scratch and deleted the fglrx stuff manually. Now I got the stuff up and running..

I must be an error in following the tutorial.

Thanks a lot..

I am getting glxgears @ 1800 fps.

---

### Post by pachequin on 2005-09-30
Hi ! tried the HOWTO when I run fglrxinfo it gave the right answer but when I run glxgears my laptop freezess. I have a Toshiba laptop A75-S209 with a ATI Mobility Radeon 9000, The results from sudo dmesg | grep fglrx :
[fglrx] Maximum main memory to use for locked dma buffers: 373 MBytes.
[fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[fglrx] Internal AGP support requested, but kernel AGP support active.
[fglrx] Have to use kernel AGP support to avoid conflicts.
[fglrx] Kernel AGP support doesn't provide agplock functionality.
[fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[fglrx] free  AGP = 21245952
[fglrx] max   AGP = 21245952
[fglrx] free  LFB = 55570432
[fglrx] max   LFB = 55570432
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 8192
grep WW /var/log/Xorg.0.log:
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/X11R6/lib/X11/fonts/local/" does not exist.
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 1
could you please help me? thank you so much!

---

### Post by Paulo Wageck on 2005-09-30
[http://del.icio.us/drpaulo?setcount=100](http://del.icio.us/drpaulo?setcount=100)

there you can find some useful links.. i have managed to get it working in hoary... lots of work!!!!

---

### Post by mlomker on 2005-09-30
> could you please help me? thank you so much!

I'd recommend trying the ATI forum linked in the troubleshooting section.  I don't work for ATI and I don't have a Toshiba laptop, so I won't be able to figure that out.  

Generally speaking, hard lockups indicate a hardware problem and not a software issue.  You are saying that you can't event Ctrl-Alt-F2 to another console?  I usually start troubleshooting by confirming that I have the latest system BIOS and unplugging any peripherals that aren't necessary.

---

### Post by pachequin on 2005-09-30
thanks you for your answer but, I have a question which page did you use? Theres a lot of pages on the link that you post.

thank you.

---

### Post by pachequin on 2005-09-30
Nop! the computer freezes completly! have to reboot manually (turning off the computer). Do you think that I must post on some toshiba forum?

thank you!

---

### Post by mlomker on 2005-09-30
> Do you think that I must post on some toshiba forum?

You could try that.  It sounds like your machine is pretty new, but I'd check to see if the system BIOS is the latest.

---

### Post by pachequin on 2005-09-30
Thank you so much!

---

### Post by mjreged on 2005-10-01
Hey, how about this
I sudo apt-get  install xorg-driver-fglrx
then the fglrx-control
run the fglrxconfig then reboot
get the x running 
but  openGL renderer string : Mesa GLX inderect

xorg log says

(WW) kernel modules version does not match driver
(EE) incompatible kernel module detected -HW accelerated OpenGL will not work

(WW) DRI initialization failed;


my system is as follows : AMD64 +3500
Gigabyte Nforce4
ati X800  -  PCI-Express

any ideas about the incompatibility would be great

---

### Post by NikoC on 2005-10-02
Major thanks mlomker, I'm a total linux noob, but your 'how to on installing ATI drivers' was excellent and written very clear!

---

### Post by PGHammer on 2005-10-04
[QUOTE=AtomixPain]Also u need to have Xfree86 installed for the driver to install...xorg is installed by default[/QUOTE]

This driver also works with Xorg (I'm running 5.04 Hoary with Xorg and the same driver).

I found this FAQ solved my woes with lack of acceleration in Hoary (AIW 9700 Pro) rather neatly.  I was even able to get 1280x960 (a custom 4:3 resolution that my monitor supports) back in my options.  (Most 17" CRT displays that are NOT based on Sony and Mitsubishi aperture-grille tubes will function better at 1280x960 as opposed to 1280x1024 at 60 Hz.  This is especially true of lowre-end CRTs.)

---

### Post by SwedishElk on 2005-10-09
Great guide. Got it all to work. But I am only getting ~500 FPS with gears. Any ideas what could be wrong?

---

### Post by mlomker on 2005-10-09
> Got it all to work. But I am only getting ~500 FPS with gears. Any ideas what could be wrong?

What card is it?  I've heard similar from X800 owners.  The problem is that the card is newer than the drivers.  I should think it'll get fixed with the next version.

---

### Post by SwedishElk on 2005-10-09
Oh sorry, must have forgot that. ;-)

It is a Radeon 9600 PRO

---

### Post by mlomker on 2005-10-09
> It is a Radeon 9600 PRO

That isn't normal.  Breezy or Hoary?  Ubuntu package or downloaded driver?

Post the diagnostic output for me:

```

fglrxinfo
dmesg | grep fglrx
cat /etc/X11/xorg.conf | grep Driver

```

---

### Post by SwedishElk on 2005-10-09
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

Driver      "kbd"
Driver "mouse"
#    Driver      "mouse"
#    Driver     "magellan"
#    Driver     "spaceorb"
#    Driver     "microtouch"
#    Driver     "elo2300"
# The Driver line must be present.  When using run-time loadable driver
Driver      "vga"
Driver       "fglrx"

dmesg gives nothing about fglrx, but it is present and in use with lsmod

fglrx                 245412  7
agpgart                32328  2 fglrx,intel_agp

---

### Post by mlomker on 2005-10-09
> OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


Looks normal.  You can look through the /var/log/Xorg.0.log file for fglrx messages.  I wonder if it is failing to set it to 8x AGP or something like that?  

If so, then that's a motherboard conflict of some sort.  I'd offer the usual generic advice of verifying that you have the latest motherboard BIOS.

---

### Post by SwedishElk on 2005-10-09
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x8213560
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00000000"
(**) fglrx(0): Option "CapabilitiesEx" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "(null)"
(**) fglrx(0): Option "HSync2" "unspecified"
(**) fglrx(0): Option "VRefresh2" "unspecified"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
(**) fglrx(0): Option "Stereo" "off"
(**) fglrx(0): Option "StereoSyncEnable" "1"
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "off"
(**) fglrx(0): Option "FSAAScale" "1"
(**) fglrx(0): Option "FSAAEnable" "no"
(**) fglrx(0): Option "FSAADisableGamma" "no"
(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
(**) fglrx(0): Option "FSAAMSPosX0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX5" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY5" "0.000000"
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(**) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x00000000
(**) fglrx(0): Gamma Correction for II is 0x00000000
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "RADEON 9600 (RV350 4150)" (Chipset = 0x4150)
(--) fglrx(0): (PciSubVendor = 0x148c, PciSubDevice = 0x2066)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xf8020000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): No EDID information available.
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(**) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 17 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz
(II) fglrx(0): Modeline "1152x864"   64.68  1152 1208 1328 1504  864 865 868 915 +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 +hsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525 -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497 -hsync
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  600 601 605 742 -hsync
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  480 491 493 525 -hsync
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  400 457 459 524 -hsync -vsync
(++) fglrx(0): DPI set to (100, 100)
(**) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000000
(**) fglrx(0): CapabilitiesEx: 0x00000000
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x00000a65
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: yes
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xd0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xd0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf93dc000
(II) fglrx(0): [drm] mapped SAREA 0xf93dc000 to 0xb7b54000
(II) fglrx(0): [drm] framebuffer handle = 0xd0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-9-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xf8020000
(II) fglrx(0): [agp] Mode=0x1f004a1b bridge: 0x8086/0x2570
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f004b1a
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf9501000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled

---

### Post by mlomker on 2005-10-09
I don't see anything obvious.  I know that the glxgears that comes with Breezy is different than Hoary but your numbers still sound too low.  Have you checked one of the threads on the Gaming boards to see what others are getting with your card?

I don't run Breezy yet, so I can't tell you what I'd see with my 9700.

---

### Post by SwedishElk on 2005-10-09
Thanks for checking anyway. I will go and check with gaming boards.

/Cheers

---

### Post by websurrfr on 2005-10-09
I am getting the following error when trying the first step (I am using Breezy RC1) for testing if the driver that comes with Breezy works.

root@danlaptop:/# apt-get install fglrx-control
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fglrx-control


Am I doing something wrong?

---

### Post by mlomker on 2005-10-09
> Am I doing something wrong?

Your /etc/apt/sources.list file must be incomplete. Compare yours to the one that I've attached (or replace yours by renaming this file).

---

### Post by websurrfr on 2005-10-09
I used the list you provided and ran an apt-get update and now everything appears to be working.  Thank you.

---

### Post by websurrfr on 2005-10-09
Wow, it took a bit more work after the install to get the resolutions and refresh rate right and working after restarts, but a big thank you to the author or this thread.  Ubuntu now looks so much better and works much faster with these drivers installed.

---

### Post by Stupid on 2005-10-09
In post number 49 fortnox reported that the make.sh script that builds ATI's driver failed in Breezy.  I had the same problem, the script fails because it can't find the file ioctl32.h.  The relevent error line is 
```
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:124:25: asm/ioctl32.h: No such file or directory
```
This went away when I re-downloaded the linux source, as suggested below.

Now that I have built the ATI provided driver though I have another problem.  When I run glxgears I still get pretty crappy performance (about 150 fps).  I looked in my /var/log/Xorg.0.log file and found the warning from the troubleshooting section about DRI initialization failing.  Then I downloaded the updated libdri.a from that page and rebooted my system.  This caused X to not start, I'm assuming because it is built for a 32 bit operating system, and I'm running the AMD64 version of Breezy.  

So I guess I'll finally get to my question (sorry this is so long winded) where did the updated libdri come from, and do they have an updated libdri for AMD64?

Thanks.  And I appreciate the detailed howto, it has helped me a lot.

---

### Post by mlomker on 2005-10-09
> ioctl32.h. 

That file is actually in the full kernel source and not a part of the headers.  I'd recommend downloading the [linux-source]("http://ubuntuforums.org/showpost.php?p=361253&postcount=10") for your kernel and unpacking it and try the install again.

I just looked at the post that you referenced and this appears to be an amd64-only problem.  For some reason that file is not in the kernel headers, whereas it is on i386.  I run an amd64 myself, but I have to run the older drivers due to my LCD panel.

> Now that I have built the ATI provided driver though I have another problem.  When I run glxgears I still get pretty crappy performance (about 150 fps). 

That's an understatement.  MESA gets about 500.

> where did the updated libdri come from, and do they have an updated libdri for AMD64?

That was contributed by another user (I listed a credit in the how-to).

I think you should try downloading the source and giving it another go first...

---

### Post by soonindallas on 2005-10-10
I have an ATI 9700 Mobility Radeon that worked fine in 3D in Hoary after I got the fglrx driver installed and working.

I just can't get it working under Breezy.  I use a 1280x800 display.

glxgears gives rubbish performance.  not even looking at fps numbers here: the gears are not moving smoothly to the naked eye.

fglrxinfo says mesa is being used:

```
peter@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

though xorg.conf says "fglrx"

```

peter@ubuntu:~$ cat /etc/X11/xorg.conf | grep Driver
[snip]
        Driver          "fglrx"
```


dmesg gives scary messages: process 7790 is Xorg.

```
peter@ubuntu:~$ dmesg | grep fglrx
[4294708.324000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies , Starnberg, GERMANY' taints kernel.
[4294708.325000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294708.326000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294818.780000] [fglrx:firegl_unlock] *ERROR* Process 7790 using kernel context 
```

and Xorg log gives me stuff I don't understand.... except that I doesn't work.  maybe related to "tainted kernel" remark above ???

```

(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x000006a3
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM area:     0xd85e9000 (size=0x03a17000)
(II) fglrx(0): driver needs X.org 6.8.x
(II) fglrx(0): detected X.org 6.8.2
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xe0d03000
(II) fglrx(0): [drm] mapped SAREA 0xe0d03000 to 0xb7cb7000
(II) fglrx(0): [drm] framebuffer handle = 0xd8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0d03000 at 0xb7cb7000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x04000000
(==) fglrx(0): Write-combining range (0xd8000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 800)
(II) fglrx(0): Largest offscreen area available: 1280 x 7387
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled

```

Kernel version is 2.6.12-9-686

I have tried the how-to, rewritten xorg.conf and this and that, without success.  obviously missing something.  what should I try ?

---

### Post by mlomker on 2005-10-10
> (WW) fglrx(0): Kernel Module version does *not* match driver.


I assume that you've rebooted since installing the driver?  This seems to indicate that you have an older version loaded and are trying to also load the one.

Try:

```

sudo depmod -a
modinfo fglrx

```

---

### Post by mlomker on 2005-10-10
[QUOTE=zarathustra]I've got this error I've always got when attempting to install the latest drivers:

Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a
[/QUOTE]

I found the solution for this problem today.  Edit your /etc/X11/xorg.conf file and comment out the int10 line in the Module section.

```

Section "Module"
#       Load    "int10"
EndSection

```

---

### Post by soonindallas on 2005-10-10
[QUOTE=mlomker]I assume that you've rebooted since installing the driver?  This seems to indicate that you have an older version loaded and are trying to also load the one.[/QUOTE]

I rebooted a few times, yes.


[QUOTE=mlomker]
Try:

```

sudo depmod -a
modinfo fglrx

```[/QUOTE]

```
peter@ubuntu:~$ sudo depmod -a
Password:
peter@ubuntu:~$ modinfo fglrx
filename:       /lib/modules/2.6.12-9-686/volatile/fglrx.ko
vermagic:       2.6.12-9-686 686 gcc-3.4
depends:        agpgart
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
parm:           firegl:s

```

ok.  so this is what I get.

oh yeah, I forgot to mention that it still doesn't work.

---

### Post by mlomker on 2005-10-10
> filename:       /lib/modules/2.6.12-9-686/volatile/fglrx.ko


This indicates that you have the linux-restricted-modules-* package installed.  You have to remove it or it'll overwrite your installed driver on every bootup.

Remove it and reboot.  Verify that the /lib/modules/2.6.12-9-686/volatile/ directory is totally empty.  Then go to /lib/modules/fglrx and run the make_install.sh again.

---

### Post by soonindallas on 2005-10-10
[QUOTE=mlomker]This indicates that you have the linux-restricted-modules-* package installed.  You have to remove it or it'll overwrite your installed driver on every bootup.

Remove it and reboot.  Verify that the /lib/modules/2.6.12-9-686/volatile/ directory is totally empty.  Then go to /lib/modules/fglrx and run the make_install.sh again.[/QUOTE]

ok.  I did this.  I go to run make_install.sh:

```
peter@ubuntu:/lib/modules/fglrx$ sudo bash make_install.sh
*** WARNING ***
Tailored kernel module for fglrx not present in your system.
You must go to /lib/modules/fglrx/build_mod subdir
and execute './make.sh' to build a fully customed kernel module.
Afterwards go to /lib/modules/fglrx and run './make_install.sh'
in order to install the module into your kernel's module repository.
(see readme.txt for more details.)
As of now you can still run your XServer in 2D, but hardware acclerated
OpenGL will not work and 2D graphics will lack performance.

failed.

```

... so I follow these instructions...

```
peter@ubuntu:/lib/modules/fglrx/build_mod$ sudo bash ./make.sh
gcc: couldn't run 'i486-linux-gnu-gcc-3.4.5': No such file or directory
./make.sh: line 60: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
ln: `./libfglrx_ip.a.GCC4': File exists
make: *** [libfglrx_ip.a.GCC4] Error 1
build failed with return value 2
```

I am stuck.

---

### Post by mlomker on 2005-10-10
> I am stuck.

You'll have to to remove the fglrx package that you installed (easiest to just use Synaptic and select 'complete removal') and then reinstall it.  I ran into that myself this morning.

---

### Post by soonindallas on 2005-10-10
[QUOTE=mlomker]You'll have to to remove the fglrx package that you installed (easiest to just use Synaptic and select 'complete removal') and then reinstall it.  I ran into that myself this morning.[/QUOTE]

ok.  I did this and buggered up my X.

synaptic told me it would uninstall xserver-xorg or some such, so I did.

On boot I have the good old command line.

if you help me get X running again, I promise I will stop asking questions about ati and fglrx -- it's just too da*n complicated -- and wait for the gods to get it fixed in the next update.

what commands do I need to issue to get x installed and running ?

---

### Post by mlomker on 2005-10-10
> what commands do I need to issue to get x installed and running ?

I'm not totally sure because I've never removed it.

Try

```

sudo apt-get install xorg-common
sudo apt-get install xserver-xorg-core

```

---

### Post by soonindallas on 2005-10-10
it tells me x can't start because there's no fglrx module.  i guess i need to renconfigure x

---

### Post by souled on 2005-10-10
YAY! I think it works. I get about 2104 FPS when running glxgears. And I don't get that stupid MESA driver anymore when I run fglrxinfo. Thanks a lot!

---

### Post by mlomker on 2005-10-10
> i guess i need to renconfigure x

Sure.

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Téragone on 2005-10-13
[QUOTE=mlomker]I found the solution for this problem today.  Edit your /etc/X11/xorg.conf file and comment out the int10 line in the Module section.

```

Section "Module"
#       Load    "int10"
EndSection

```[/QUOTE]


Thanks very much, I will try it. I will give you a feedback if it work or not for me.

---

### Post by barongas on 2005-10-24
I used this guide to install the fglrx drivers on my hoary system and it worked super except when it came to certain games where some polygons tended to loose grip on thier coordinates. I learned to live with it but now a couple of months later any opengl app (even glxgears) gives me small, flickering horizontal lines all over the screen.

I don't even know where to start troubleshooting so if anyone has any ideas on how to do this please reply to this.

---

### Post by rockonkenshin on 2005-11-04
[QUOTE=barongas]I used this guide to install the fglrx drivers on my hoary system and it worked super except when it came to certain games where some polygons tended to loose grip on thier coordinates. I learned to live with it but now a couple of months later any opengl app (even glxgears) gives me small, flickering horizontal lines all over the screen.

I don't even know where to start troubleshooting so if anyone has any ideas on how to do this please reply to this.[/QUOTE]

It sounds like your card is dying. Check the fans and temperatures in BIOS.

Also, I finally got the drivers to load after 3498792837492873423 tries, many hours and quite a few copy and paste sessions with xorg.conf. Thanks! :cool:

---

### Post by mlomker on 2005-11-04
> It sounds like your card is dying. Check the fans and temperatures in BIOS.

I'd agree.  A gradually worsening problem is usually hardware-related.

> Also, I finally got the drivers to load after 3498792837492873423 tries, many hours and quite a few copy and paste sessions with xorg.conf. Thanks! :cool:

I'm glad to hear it!  It isn't much easier in Breezy to install the latest drivers, either. :(

---

