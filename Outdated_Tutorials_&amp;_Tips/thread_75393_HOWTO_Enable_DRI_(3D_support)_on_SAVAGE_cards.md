---
title: "HOWTO: Enable DRI (3D support) on SAVAGE cards"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-13
This is how to do it (**only on Breezy**):
first of all
```
sudo apt-get install gcc-3.4 build-essential
```
**FOR OLDER INTEL AND AMD CHIPSETS (INTEL 386, 486 ETC.)**
do
```
sudo apt-get install linux-headers-2.6.12-10-386
```
and **jump straight to** *"COMMON FOR ALL CHIPSETS"*
----------------------------------------------------------------------------
**FOR INTEL 686 CHIPSETS (WITHOUT HYPERTHREADING)**
```
sudo apt-get install linux-image-2.6.12-10-686
sudo apt-get install linux-headers-2.6.12-10-686
sudo apt-get install linux-restricted-modules-2.6.12-10-686
```
Then **restart the comp and boot into the 686 kernel image** from grub (u will get that option).
Now do
```
sudo apt-get remove linux-image-2.6.12-10-386 linux-headers-2.6.12-10-386
```
and **jump straight to** *"COMMON FOR ALL CHIPSETS"*
----------------------------------------------------------------------------
**FOR INTEL CHIPSETS (WITH HYPERTHREADING)**
```
sudo apt-get install linux-image-2.6.12-10-686-smp
sudo apt-get install linux-headers-2.6.12-10-686-smp
sudo apt-get install linux-restricted-modules-2.6.12-10-686-smp
```
Then **restart the comp and boot into the 686-smp kernel image** from grub (u will get that option).
Now do
```
sudo apt-get remove linux-image-2.6.12-10-386 linux-headers-2.6.12-10-386
```
and **jump straight to** *"COMMON FOR ALL CHIPSETS"*
----------------------------------------------------------------------------
**FOR AMD CHIPSETS**
```
sudo apt-get install linux-image-2.6.12-10-k7
sudo apt-get install linux-headers-2.6.12-10-k7
sudo apt-get install linux-restricted-modules-2.6.12-10-k7
```
Then **restart the comp and boot into the k7 kernel image** from grub (u will get that option).
Now do
```
sudo apt-get remove linux-image-2.6.12-10-386 linux-headers-2.6.12-10-386
```
and **jump straight to** *"COMMON FOR ALL CHIPSETS"*
----------------------------------------------------------------------------
**COMMON FOR ALL CHIPSETS**
```

wget http://dri.freedesktop.org/snapshots/archive/common-20051127-linux.i386.tar.bz2 
wget http://dri.freedesktop.org/snapshots/archive/savage-20051125-linux.i386.tar.bz2 
tar -xjf common-20051127-linux.i386.tar.bz2 
tar -xjf savage-20051125-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
```  
restart your comp (or just X server). 
check ur fps count with:
```
glxgears -printfps
```

---

### Post by cyfer on 2005-10-14
please forgive my ignorance ..i'm kinda newb to ubuntu 

i didn't try what you explain here as i'm getting kde right now  ..but last night i recompiled my  2.6.12.9 ......and thank god i think it was successfull.........
trying to work the BLUEZ "3Ddesk"  i get 3d is found but not enabled ...please configure you hardware acceleration 

this i think is interesting ... 

```
 
wget http://dri.freedesktop.org/snapshots/common-20050707-linux.i386.tar.bz2 
wget http://dri.freedesktop.org/snapshots/savage-20050707-linux.i386.tar.bz2 
tar -xjf common-20050707-linux.i386.tar.bz2 
tar -xjf savage-20050707-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
```

so ..after downloading the new kernel OR  recompiling it ....it will work ..yes .but why uninstall the previous version ??? can't get that at all  

btw , is this for all savage cards? even those S3_Unichrome?

---

### Post by Charon on 2005-10-14
thanks, this actually worked like a charm! :D 

just two things : 
instead of the files you mentioned i downloaded these newer ones
[http://dri.freedesktop.org/snapshots/common-20050714-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20050714-linux.i386.tar.bz2) 
[http://dri.freedesktop.org/snapshots/savage-20050714-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/savage-20050714-linux.i386.tar.bz2)

the other thing was with with the compiling-stage during the install. on first try it hung up because it couldn't find gcc-3.4.4 (apparently the kernel-headers told the install script to use gcc-3.4.4, i though everything is now compiled with gcc-4.0.0? :???: )

after installing gcc-3.4.4 i started the install-script again and it worked!

so one last question : isnt the kernel compiled with gcc-4.0.0? wouldn't it usually create problems if i load a gcc-3.4.4 compiled module into a gcc-4.0.0 compiled kernel?

/me goes off to play some more ppracer..

[edit]
forgot to mention that since i use an IBM Thinkpad T22 i installed the linux-image-2.6.12-9-686
[/edit]

---

### Post by radiazo on 2005-10-14
a lot of thanks!!!

---

### Post by leezer3 on 2005-10-14
The kernel is still currently compiled with gcc3.4.
@ Cyfer: You are not re-compiling the kernel, but rather the drivers for the vid card.


Cheers

-Leezer-

---

### Post by cyfer on 2005-10-14
=====>arnieboy<======
```

-$ getting errors
-$ reconfiguring the shit 
-$ downloading the right driver
-$ oooops , this is gonna work !
-$ it really works 
-$ getting the BLUEZ
-$ the BLUEZ works
-$ thanks for DAEMON "arnieboy"

```

---

### Post by GeneralZod on 2005-10-15
Just out of interest, will this need to be performed after every kernel update (i.e. security updates), or just the one time?

Either way, thanks - I wanted to do this in Hoary, but you had to update to a newer kernel which broke my synaptics touchpad! :(

---

### Post by arnieboy on 2005-10-15
[QUOTE=GeneralZod]Just out of interest, will this need to be performed after every kernel update (i.e. security updates), or just the one time?

Either way, thanks - I wanted to do this in Hoary, but you had to update to a newer kernel which broke my synaptics touchpad! :([/QUOTE]
I think u would need to run the install script (and just the install script) everytime the kernel gets a security upgrade. nothing else is necessary because the breezy kernel is going to stay at the 2.6.12-9 version. it wont change.

---

### Post by assan on 2005-10-15
Thanks arnieboy it worked like a charm.
But there is another problem after few moments of fast animation glxgears is slowing down, almost stopping. Any ideas what to do? It was the same before enabling DRI and after.
glxgears is not showing any fps? It is maybe silly question but in hoary it was fps was just there and -? and -help want help me.

---

### Post by arnieboy on 2005-10-15
[QUOTE=assan]Thanks arnieboy it worked like a charm.
But there is another problem after few moments of fast animation glxgears is slowing down, almost stopping. Any ideas what to do? It was the same before enabling DRI and after.
glxgears is not showing any fps? It is maybe silly question but in hoary it was fps was just there and -? and -help want help me.[/QUOTE]
do the following to get the fps count on glxgears:
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```
the slowing down of the gears is nothing to worry about.

---

### Post by assan on 2005-10-15
Results are pretty slow:

1806 frames in 5.2 seconds = 348.711 FPS
2660 frames in 5.1 seconds = 519.943 FPS
2660 frames in 5.2 seconds = 516.076 FPS
1960 frames in 5.0 seconds = 391.679 FPS
2660 frames in 5.3 seconds = 505.836 FPS
2660 frames in 5.1 seconds = 525.939 FPS

Do I need to reconfigure Xserver?

---

### Post by arnieboy on 2005-10-15
[QUOTE=assan]Results are pretty slow:

1806 frames in 5.2 seconds = 348.711 FPS
2660 frames in 5.1 seconds = 519.943 FPS
2660 frames in 5.2 seconds = 516.076 FPS
1960 frames in 5.0 seconds = 391.679 FPS
2660 frames in 5.3 seconds = 505.836 FPS
2660 frames in 5.1 seconds = 525.939 FPS

Do I need to reconfigure Xserver?[/QUOTE]
this is the best u can get with ur card on linux. if u had run the glxgears command before installing the drivers u wud have probably seen around 100 fps. generally there is a jump of nearly 3-4 times with the installation of the savage modules.

---

### Post by assan on 2005-10-15
Is it ok for Intel 855GM? (sorry for not mentioning that :)
Installation with i915
Before was the same, result in hoary was about 550fps.
Some people had results with this chip 950-1100 fps.

---

### Post by ubunxpm on 2005-10-15
There is a problem;

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

and the dri.log;

Makefile:163: *** Cannot find a kernel config file.  Stop.

so what does all this mean? since i'm using the latest kernel(for ubuntu) 
2.6.12-9-386

I found that someone else had the same problem here in forums and another person suggested using the kernel headers.
So...  where are the headers?

Any suggstions?

---

### Post by arnieboy on 2005-10-15
> **ubunxpm]There is a problem said:**
> http://dri.sourceforge.net[/url] ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

and the dri.log;

Makefile:163: *** Cannot find a kernel config file.  Stop.

so what does all this mean? since i'm using the latest kernel(for ubuntu) 
2.6.12-9-386

I found that someone else had the same problem here in forums and another person suggested using the kernel headers.
So...  where are the headers?

Any suggstions?
u havent followed the instructions.. u need to install the 686 kernel and headers. read the first post again.

---

### Post by assan on 2005-10-16
Yes I did follow the instruction, instalation script finished ok after compiling DRI modules. How to check where is a problem?

---

### Post by GeneralZod on 2005-10-16
Another satisfied customer here; thanks again!

It appears to be fully stable, too! Has anyone had any X lockups with it yet?

I haven't tried it with hibernation yet; I'll do that when I get a chance and report back.

Back to gazing at MirrorBlob for me...

Edit:

It survives a hibernation and restore OK, but the first time I go to use a opengl app afterwards, it hard-locks :( Oh well....

---

### Post by arnieboy on 2005-10-16
[QUOTE=assan]Yes I did follow the instruction, instalation script finished ok after compiling DRI modules. How to check where is a problem?[/QUOTE]
if the installation script "FINISHED OK" why the hell do u think there SHOULD BE any problem?

---

### Post by kmi on 2005-10-16
First of all, thanx for this GREAT tip, but the following lines seem to need an edit :

[QUOTE=arnieboy]
```
wget http://dri.freedesktop.org/snapshots/common-20050714-linux.i386.tar.bz2 
wget http://dri.freedesktop.org/snapshots/savage-20050714-linux.i386.tar.bz2 
tar -xjf common-20050707-linux.i386.tar.bz2 
tar -xjf savage-20050707-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
```  
[/QUOTE]

I think it should be :

```
sudo apt-get install build-essential 
wget http://dri.freedesktop.org/snapshots/common-20050714-linux.i386.tar.bz2 
wget http://dri.freedesktop.org/snapshots/savage-20050714-linux.i386.tar.bz2 
tar -xjf common-20050714-linux.i386.tar.bz2 
tar -xjf savage-20050714-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
```

I've noticed there are "common-20050718-linux.i386.tar.bz2" and "savage-20050718-linux.i386.tar.bz2" in [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

Is there any reason to stay with the 20050714 versions and not to use the 20050718 ones ?

---

### Post by arnieboy on 2005-10-16
[QUOTE=kmi]First of all, thanx for this GREAT tip, but the following lines seem to need an edit :



I think it should be :

```
sudo apt-get install build-essential 
wget http://dri.freedesktop.org/snapshots/common-20050714-linux.i386.tar.bz2 
wget http://dri.freedesktop.org/snapshots/savage-20050714-linux.i386.tar.bz2 
tar -xjf common-20050714-linux.i386.tar.bz2 
tar -xjf savage-20050714-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
```

I've noticed there are "common-20050718-linux.i386.tar.bz2" and "savage-20050718-linux.i386.tar.bz2" in [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

Is there any reason to stay with the 20050714 versions and not to use the 20050718 ones ?[/QUOTE]
no reason at all. the updates keep coming.. but more often than not.. they dont have any major updates. if u check tomorrow u might find a 20051017 version.

---

### Post by Lem on 2005-10-16
I have a Via Epia M10000 board with a C3 processor. I've tried to use your instructions as listed above, but to install the via DRI driver for Unichrome.
All looks good, but I get the error saying it can't find a kernel config file. I've made sure I have linux-header etc. installed.

I'm currently using the default 386 kernel.. is this the right one for my chip?

---

### Post by assan on 2005-10-16
I have interesting hint, after reading [http://wiki.linuxquestions.org/wiki/OpenGL#OpenGL_on_Linux](http://wiki.linuxquestions.org/wiki/OpenGL#OpenGL_on_Linux)

I run anoher check
~$ glxinfo |grep rendering
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No

Any idea how to correct it. What is and where is fbconfigs?

---

### Post by assan on 2005-10-17
[QUOTE=arnieboy]if the installation script "FINISHED OK" why the hell do u think there SHOULD BE any problem?[/QUOTE]

well I rerun install script and there were errors:

Installing files:
        DRI XFree86 modules...done
        kernel modules...done
        GL & GLU libraries...done
        core libraries...done
        Copying extra files...done

Updating configuration:
        Running ldconfig...     Removing old kernel module "i915"...ERROR
        Inserting new kernel module "i915"...done

There were errors updating the system configuration.
See the dri.log file for more information.

Checking configuration...ldd: /usr/X11R6/bin/glxinfo: Nie ma takiego pliku ani katalogu [it means there is no such catalog or file]

        second copy of DRI libraries found in
        libraries have been backed up to dri-old.* in

done

what is wrong?:confused:

---

### Post by arnieboy on 2005-10-17
[QUOTE=assan]well I rerun install script and there were errors:

Installing files:
        DRI XFree86 modules...done
        kernel modules...done
        GL & GLU libraries...done
        core libraries...done
        Copying extra files...done

Updating configuration:
        Running ldconfig...     Removing old kernel module "i915"...ERROR
        Inserting new kernel module "i915"...done

There were errors updating the system configuration.
See the dri.log file for more information.

Checking configuration...ldd: /usr/X11R6/bin/glxinfo: Nie ma takiego pliku ani katalogu [it means there is no such catalog or file]

        second copy of DRI libraries found in
        libraries have been backed up to dri-old.* in

done

what is wrong?:confused:[/QUOTE]
alright.. i915 video cards have a different module driver.. am not sure why u are using the savage howto for that.
anyway this will work for i915 as well but u need to download a different package:
```
wget http://dri.freedesktop.org/snapshots/i915-20050718-linux.i386.tar.bz2
```
The "common" package remains the same. now follow all the other instructions (untarring and installing and see what happens)
also delete the dripkg directory before u download this package.
untar the "common" package first followed by the i915 package.

also make sure u have the "common" package with the same release date as the i915 package (that is 20050718)

---

### Post by assan on 2005-10-17
I did install with 20050714 version common and i915. 
few moments ago I did with 20050718 and it is the same:
Installing files:
        DRI XFree86 modules...done
        kernel modules...done
        GL & GLU libraries...done
        core libraries...done
        Copying extra files...done

Updating configuration:
        Running ldconfig...     Removing old kernel module "i915"...ERROR
        Inserting new kernel module "i915"...done

There were errors updating the system configuration.
See the dri.log file for more information.

Checking configuration...ldd: /usr/X11R6/bin/glxinfo: Nie ma takiego pliku ani katalogu

        second copy of DRI libraries found in
        libraries have been backed up to dri-old.* in

done

dri.log: 

make DRM_MODULES=i915.o modules
make[1]: Wej&#347;cie do katalogu `/home/adrian/dripkg/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/sis_ds.c sis_ds.c
+ ln -s ../shared-core/sis_ds.h sis_ds.h
+ ln -s ../shared-core/sis_mm.c sis_mm.c
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_mm.h via_mm.h
+ ln -s ../shared-core/via_ds.h via_ds.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_ds.c via_ds.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_mm.c via_mm.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.12-9-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_auth.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_bufs.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_context.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_dma.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_drawable.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_drv.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_fops.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_ioctl.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_irq.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_lock.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_memory.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_proc.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_stub.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_vm.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_sysfs.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_pci.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_agpsupport.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_scatter.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/drm_memory_debug.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/ati_pcigart.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/i915_drv.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/i915_dma.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/i915_irq.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/i915_mem.o
  CC [M]  /home/adrian/dripkg/drm/linux-core/i915_pm.o
  LD [M]  /home/adrian/dripkg/drm/linux-core/drm.o
  LD [M]  /home/adrian/dripkg/drm/linux-core/i915.o
  Building modules, stage 2.
  MODPOST
  CC      /home/adrian/dripkg/drm/linux-core/drm.mod.o
  LD [M]  /home/adrian/dripkg/drm/linux-core/drm.ko
  CC      /home/adrian/dripkg/drm/linux-core/i915.mod.o
  LD [M]  /home/adrian/dripkg/drm/linux-core/i915.ko
make[2]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.12-9-686'
make[1]: Opuszczenie katalogu `/home/adrian/dripkg/drm/linux-core'
/usr/X11R6/lib
FATAL: Module i915 is in use.

More ideas?
I installed everything with i915 driver this time and previously

---

### Post by arnieboy on 2005-10-17
alright try the following:
press ctrl-alt-F1 . u will go into console mode. 
there log in with your user name and password and do the following (write this down somewhere because u wont have any browser to copy from there):
```
sudo /etc/init.d/gdm stop
```
now do 
```
cd dripkg
sudo ./install.sh
```
now do a 
```
sudo /etc/init.d/gdm start
``` and enjoy DRI.

---

### Post by assan on 2005-10-17
I will try that in a minute

---

### Post by assan on 2005-10-17
unfortunately no change, still no fbconfigs.
Little deppressed going to sleep.
Maybe tomorrow I will be more lucky with DRI...

---

### Post by assan on 2005-10-18
I received answer what is wrong from Roland Scheidegger dri-user list.
Problem is I have in Xorg old ddx (2D) driver version 1.3 and should be 1.4.x and is 1.3.0
Strange thing is it should be ok in xorg 6.8.2 like in hoary and breezy. Solution is to install xorg 6.9 what will be my next try.

---

### Post by alex-gurgel on 2005-10-18
Problems, problems, problems.....

dri.freedesktop.org is out.... I can't download common and savage files...

Can someone send these files to me ??


**Edited:** Ok this is not a problem anymore.... dri.freedesktop.org is back ! I've downloaded and save the files I need. Thanks !

---

### Post by Knowles on 2005-10-25
Thanks Arnieboy YOU ARE A LEDGEND

---

### Post by Eleaf on 2005-10-30
How awesome!!  This actually worked!  Thank you so much!! =-)

---

### Post by arnieboy on 2005-11-02
herez some good news: kernel 2.6.14 has drm support for savage cards.. and yeah it does work! that means this howto wudnt be required for dapper drake! cheers!!

---

### Post by IanH on 2005-11-03
Has anyone gotten this working with the "ShadowStatus" option? It works as long as I disable this, but with this option on (which I need to keep X from locking up), X freezes on load. This is on a thinkpad T20.

Thanks,

---

### Post by indusnecro on 2005-11-10
[QUOTE=arnieboy]herez some good news: kernel 2.6.14 has drm support for savage cards.. and yeah it does work! that means this howto wudnt be required for dapper drake! cheers!![/QUOTE]

I have downloaded the kernel 2.6.14.1 and compiled that. But DRI does not work. 

I compiled the tarballs as stated here and everything worked correctly.

---

### Post by buedi on 2005-11-10
Now I got it running too. I have a SuperSave IX in my Thinkpad T23. But it didn´t work with the latest Drivers 20051107. It compiled and installed properly, but I couldnt get a "direct rendering: YES" in glxinfo and ppracer / glxgears had very poor Performance.

Because I used the DRI Package before, I had the Version 20050504 on my HD from previous usage. I compiled / installed this Version and now it works like a charm :D

---

### Post by foxy123 on 2005-11-10
Just to let yu guys know, there are new snapshots on dri.freedesktop.org. However, I tried all of them (i915 though) and nothing worked for me... so I rolled back to 20050714.

---

### Post by tirant on 2005-11-14
Hello!!!

Thanks for the Howto.

Tried it today with my IBM T23 and Ubuntu Hoary. I got no errors but DRI is not working at all.

I used the latest modules from the snapshots, but i will try again with the older ones found in the archive directory.

Just to share my experience :)

---

### Post by tirant on 2005-11-14
Ok, i just used the 200507???? ones and now everything works ok.

I get DRI acceleration and my screensavers work fine :)

Congrats to the DRI team, keep improving the driver!!

---

### Post by MButterman on 2005-11-18
Hi Arnie,

I have Breezy w/ Diamond Stealth II video card. I followed your direction and the process went with out a hitch. I'm still not getting 3-D. I'll send you a copy of xorg.conf.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"S3 Inc. Savage 4"
	Driver		"savage"
	BusID		"PCI:0:9:0"
	VideoRam	32000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Envision EFT"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. Savage 4"
	Monitor		"Envision EFT"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Kinda long but I think this will explain things better then trying to explain it. Any help will be much appreciated and let me know if you need any more info.

BTW. Used Automatix and works greats, thanks for making this available to me.

AMB,
MButterman

---

### Post by arnieboy on 2005-11-18
how did u decide u dont have dri?
did u try playing ppracer?
```
sudo apt-get install ppracer

```
what is the fps count on
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

---

### Post by MButterman on 2005-11-18
Hi Arnie,

I suspect an issue with my graphics card but I also understand that this graphics card is very old. I hope I didn't strike a nerve with my last post and opologize if I did. I didn't find ppracer but went to synaptic and installed panet penguin racer (I'm assuming at this point these are the same packages under different names. I took the frame rates w/ glx gears as you have requested and here is the results.

1248 frames in 5.5 seconds = 225.895 FPS
1183 frames in 5.2 seconds = 228.631 FPS
1200 frames in 5.0 seconds = 238.748 FPS
1200 frames in 5.0 seconds = 238.830 FPS
1200 frames in 5.0 seconds = 238.552 FPS
1200 frames in 5.0 seconds = 238.624 FPS
1200 frames in 5.0 seconds = 238.603 FPS
1200 frames in 5.0 seconds = 238.745 FPS
1200 frames in 5.0 seconds = 238.320 FPS
1200 frames in 5.0 seconds = 239.127 FPS
1200 frames in 5.0 seconds = 239.044 FPS
1200 frames in 5.0 seconds = 238.837

 I am not sure if these are typical of the Savage card I have installed and just needed your thoughts on it. thanks for helping me through this. I have built in S3 Unichrome graphics but was under the understanding that there is limited support for these chipsets so I figure this new card will have to do for the time being. Thanks and appreciate your time to assist me with this issue.

AMB,
MButterman

---

### Post by arnieboy on 2005-11-18
[QUOTE=MButterman]Hi Arnie,

I suspect an issue with my graphics card but I also understand that this graphics card is very old. I hope I didn't strike a nerve with my last post and opologize if I did. I didn't find ppracer but went to synaptic and installed panet penguin racer (I'm assuming at this point these are the same packages under different names. I took the frame rates w/ glx gears as you have requested and here is the results.

1248 frames in 5.5 seconds = 225.895 FPS
1183 frames in 5.2 seconds = 228.631 FPS
1200 frames in 5.0 seconds = 238.748 FPS
1200 frames in 5.0 seconds = 238.830 FPS
1200 frames in 5.0 seconds = 238.552 FPS
1200 frames in 5.0 seconds = 238.624 FPS
1200 frames in 5.0 seconds = 238.603 FPS
1200 frames in 5.0 seconds = 238.745 FPS
1200 frames in 5.0 seconds = 238.320 FPS
1200 frames in 5.0 seconds = 239.127 FPS
1200 frames in 5.0 seconds = 239.044 FPS
1200 frames in 5.0 seconds = 238.837

 I am not sure if these are typical of the Savage card I have installed and just needed your thoughts on it. thanks for helping me through this. I have built in S3 Unichrome graphics but was under the understanding that there is limited support for these chipsets so I figure this new card will have to do for the time being. Thanks and appreciate your time to assist me with this issue.

AMB,
MButterman[/QUOTE]
I am not sure about the support on diamond stealth II and the glx count looks really low. have u tried playing planet penguin racer. does that work smoothly? if it does, and u do have dri enabled on ur xorg.conf, and there are no other conflicts that i can see, I guess u have got the best possible performance with your card on ubuntu and linux as such.

---

### Post by elempoimen on 2005-11-19
absu-friggin-lutely AWESOME!!!

You have no CLUE how happy this makes me!  I'm delighted with this setup.  My one big problem was video performance...and you've solved it!

I recommend the 07xx drivers--the latest ones didn't work for me either.  Just replace the common driver with 0707 and the savage driver with 0717 (I think)--and it will just rock!

Running SuperSavage IX on a Thinkpad T23.

Maybe it's just me...but everything seems snappier now.  Anybody else experience this?  I remembered to enable DRI in xorg.conf, too... I think that could be important.

---

### Post by ranf on 2005-11-28
Thanks arnieboy

Just some notes:
- you install `build-essential' twice
- the older files are no longer at: [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) but under 
[http://dri.freedesktop.org/snapshots/archive/](http://dri.freedesktop.org/snapshots/archive/)
- I've used the last common from July and the last mach64 from June 2005 (yes I adapted this HowTo for my mach64)

---

### Post by bacchus_3 on 2005-11-30
Hi arnieboy,

I tried to download the common and i915 (I know but it's supposed to be the same as savage, right?) tar.bz2 files...and unpacked them.

What I'm curious of is where's the dripkg directory?  I unpacked common and i915 in sequence.  I checked on the package file but there's no dripkg there too.  I just see the common and i915 directory from where I downloaded and unpacked the file. I think I missed something...or I misunderstood something in reading this HowTo.


I tried to run each install.sh on the common directory and on the i915 directory.  Both ran correctly but I still have the MESA library used when I ran glxinfo.

P.S. I'm using 5.10 Breeze with 2.6.12-9-686 kernel.

---

### Post by foxy123 on 2005-11-30
[QUOTE=bacchus_3]Hi arnieboy,

I tried to download the common and i915 (I know but it's supposed to be the same as savage, right?) tar.bz2 files...and unpacked them.

What I'm curious of is where's the dripkg directory?  I unpacked common and i915 in sequence.  I checked on the package file but there's no dripkg there too.  I just see the common and i915 directory from where I downloaded and unpacked the file. I think I missed something...or I misunderstood something in reading this HowTo.


I tried to run each install.sh on the common directory and on the i915 directory.  Both ran correctly but I still have the MESA library used when I ran glxinfo.

P.S. I'm using 5.10 Breeze with 2.6.12-9-686 kernel.[/QUOTE]
you need to use 20050714 version as all the more recent snapshots are supposedly for X11R6.9/7.0, while Breezy uses 6.8. They are in an 'archive' folder.

---

### Post by bacchus_3 on 2005-11-30
yes, you're right. I just realized this when I was reading more on the dri.freedesktop.org site.  tried the archive ones and it's packaged inside a 'dripkg' folder.

---

### Post by Nasso on 2005-11-30
i got a weird problem!

I followed this guide and it works, every second time.
After startup number 1 I log in and run 'startx' or 'startxfce4' and the screen just gets black.
After startup number 2 everything works as it should.

I have to try to start X the first startup or it wont work on the second startup.

All this started after completing this guide.

Some specs:

Ubuntu Breezy 
XFCE 4.2 or Fluxbox (depending on mood ;) )
IBM Thinkpad T20
Intel P3 700MHZ
378mb RAM
S3 Savage GFX card

Does anyone have any idea at all what the reason of this problem might be?

Should i post any other info?

---

### Post by arnieboy on 2005-11-30
Thanks for the updates (ranf and foxy123).
I have updated the first post with the necessary changes.

---

### Post by arnieboy on 2005-11-30
[QUOTE=Nasso]i got a weird problem!

I followed this guide and it works, every second time.
After startup number 1 I log in and run 'startx' or 'startxfce4' and the screen just gets black.
After startup number 2 everything works as it should.

I have to try to start X the first startup or it wont work on the second startup.

All this started after completing this guide.

Some specs:

Ubuntu Breezy 
XFCE 4.2 or Fluxbox (depending on mood ;) )
IBM Thinkpad T20
Intel P3 700MHZ
378mb RAM
S3 Savage GFX card

Does anyone have any idea at all what the reason of this problem might be?

Should i post any other info?[/QUOTE]

please delete the dripkg directory in your home folder and try following the steps with the updated howto. that might fix your problems.

---

### Post by ranf on 2005-11-30
[QUOTE=Nasso]
I followed this guide and it works, every second time.
After startup number 1 I log in and run 'startx' or 'startxfce4' and the screen just gets black.
After startup number 2 everything works as it should.

I have to try to start X the first startup or it wont work on the second startup.

All this started after completing this guide.
Does anyone have any idea at all what the reason of this problem might be?

Should i post any other info?[/QUOTE]
When startx doesn't work have a look at `/var/log/Xorg.0.log'.

---

### Post by Nasso on 2005-11-30
[QUOTE=arnieboy]please delete the dripkg directory in your home folder and try following the steps with the updated howto. that might fix your problems.[/QUOTE]

done... and it seems to work now :) thanks alot!

---

### Post by Mizutsuki on 2005-12-01
For whatever reason I used your howto and it demanded I have version 2.6.12-10 of everything.  It may be because I was running the image so I ran into some trouble for not having the headers installed properly.  The point is, it'd probably be a good idea to update all of your instructions to include the newer version number.
Thank you,
Stephen

---

### Post by arnieboy on 2005-12-01
[QUOTE=Mizutsuki]For whatever reason I used your howto and it demanded I have version 2.6.12-10 of everything.  It may be because I was running the image so I ran into some trouble for not having the headers installed properly.  The point is, it'd probably be a good idea to update all of your instructions to include the newer version number.
Thank you,
Stephen[/QUOTE]
it would be an even better idea to tell me what version of Ubuntu u are using, and ur CPU information and ur graphics card.

---

### Post by Mizutsuki on 2005-12-01
[QUOTE=arnieboy]it would be an even better idea to tell me what version of Ubuntu u are using, and ur CPU information and ur graphics card.[/QUOTE]
Breezy, 2.6.12-10, PIII, Savage IX-8
Stephen

---

### Post by Nasso on 2005-12-02
[QUOTE=Nasso]done... and it seems to work now :) thanks alot![/QUOTE]

I have to take that back :( it doesnt work.

It only hangs up when i startup the computer after letting it rest for a while, it seems. It worked directly after i installed the new drivers and restarted. Tried several times.

This is the output i get in /var/log/Xorg.0.log

> 
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux naslap 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-686 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:25:32 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  2 11:27:00 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.



Any ideas? :/

Off topic, but.... is there any way of disabling that annoying 8) dude in the quote up there?

---

### Post by ranf on 2005-12-02
[QUOTE=Nasso]I have to take that back :( it doesnt work.

It only hangs up when i startup the computer after letting it rest for a while, it seems. It worked directly after i installed the new drivers and restarted. Tried several times.

This is the output i get in /var/log/Xorg.0.log
[/QUOTE]
That looks a bit short. Even when X fails.
[QUOTE=Nasso]Any ideas? :/
[/QUOTE]
Look if the kernel modules got loaded:
```
lsmod | grep drm
```
[QUOTE=Nasso]
Off topic, but.... is there any way of disabling that annoying 8) dude in the quote up there?[/QUOTE]
I use the CODE element. It's this button [#]

---

### Post by Mizutsuki on 2005-12-03
Hey, btw, is there any reason that I shouldn't use the same steps from this howto but use a newer snapshot?  I'm a little confused by that whole snapshots directory, it looks like they're putting out a new version of the driver nearly every day, is there a reason I shouldn't use one of the packages from yesterday?  Even if I'm sticking to the archive directory (is there a reason to do so, are those the stable versions?) there's one in there that's from last month, might I use that one?  Also, if I use a newer savage driver, is there a reason that I have to use a certain common driver, do they have to be of the same generation or something like that?  Is there any way to keep these up to date automatically?
Thank you,
Stephen

---

### Post by ranf on 2005-12-03
[QUOTE=Mizutsuki]Hey, btw, is there any reason that I shouldn't use the same steps from this howto but use a newer snapshot?  I'm a little confused by that whole snapshots directory, it looks like they're putting out a new version of the driver nearly every day, is there a reason I shouldn't use one of the packages from yesterday?  Even if I'm sticking to the archive directory (is there a reason to do so, are those the stable versions?) there's one in there that's from last month, might I use that one?  Also, if I use a newer savage driver, is there a reason that I have to use a certain common driver, do they have to be of the same generation or something like that?  Is there any way to keep these up to date automatically?
[/QUOTE]
Please look at this reply (I think he/she is right):
[http://ubuntuforums.org/showpost.php?p=532200&postcount=47](http://ubuntuforums.org/showpost.php?p=532200&postcount=47)

---

### Post by arnieboy on 2005-12-03
[QUOTE=Mizutsuki]Hey, btw, is there any reason that I shouldn't use the same steps from this howto but use a newer snapshot?  I'm a little confused by that whole snapshots directory, it looks like they're putting out a new version of the driver nearly every day, is there a reason I shouldn't use one of the packages from yesterday?  Even if I'm sticking to the archive directory (is there a reason to do so, are those the stable versions?) there's one in there that's from last month, might I use that one?  Also, if I use a newer savage driver, is there a reason that I have to use a certain common driver, do they have to be of the same generation or something like that?  Is there any way to keep these up to date automatically?
Thank you,
Stephen[/QUOTE]
the reason why the first post on this howto makes u use older snapshots is because the newer ones are compiled for newer versions of xorg while breezy is built around an older version, hence the most recent snapshots will have compatibility issues with breezy.

---

### Post by arnieboy on 2005-12-03
[QUOTE=ranf]I use the CODE element. It's this button [#][/QUOTE]
the best way to do it is to check "disable smileys"

---

### Post by Mizutsuki on 2005-12-03
[QUOTE=ranf]Please look at this reply (I think he/she is right):
[http://ubuntuforums.org/showpost.php?p=532200&postcount=47](http://ubuntuforums.org/showpost.php?p=532200&postcount=47)[/QUOTE]

Will I have to wait for Dapper to use a newer version then, or will breezy upgrade eventually?
Stephen

---

### Post by foxy123 on 2005-12-04
[QUOTE=Mizutsuki]Will I have to wait for Dapper to use a newer version then, or will breezy upgrade eventually?
Stephen[/QUOTE]
new xorg is due to be realised in December, I guess, but I doubt if it will make its way to Breezy. It is very different from current 6.8 version and backport team will unlikely want to backport it (although 6.9 is going to be transitional package which should be easier to backport). Frankly speaking I am not 100% sure that X11R7.0 will manage into Dapper...

---

### Post by Nasso on 2005-12-05
[QUOTE=ranf]Look if the kernel modules got loaded:
```
lsmod | grep drm
```
[/QUOTE]

If i run that command  before x is started they arnt loaded. After x is started, (if it starts without crashing) it is loaded.

---

### Post by ranf on 2005-12-05
[QUOTE=Nasso]If i run that command  before x is started they arnt loaded. After x is started, (if it starts without crashing) it is loaded.[/QUOTE]
Aha. 
In what way is X crashing?

Hav ea look at the kernel log for drm messages:
```
dmesg | grep drm
```

---

### Post by kamaaina on 2005-12-05
I have encountered the following errors:

Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


Looking in the log file as indicated:

rm -f linux
ln -s . linux
make -C /lib/modules/2.6.12-10-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
make[2]: *** No rule to make target `savage/dripkg/drm/linux-core'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/noah/Desktop/super savage/dripkg/drm/linux-core'
make: *** [savage.o] Error 2

I am running an IBM T23.  And I must confess initially thought my processor had hyperthreading.  But I ran apt-get remove on all those packages and tried again for the 686 without hyper threading from the beginning.  Any help is appreciated.

---

### Post by widjajayd on 2005-12-10
Yes I got same problem 

I have download and install common-20050707-linux.i386.tar.bz2 without problem.

but when I tried to run sis-20050628-linux.i386.tar.bz2

it said The DRI drivers can not be installed without the latest kernel modules

Below is my steps and my error

Thank you for your help

```


tar -xjf sis-20050628-linux.i386.tar.bz2
cd dripkg
sudo ./install.sh


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


Dri.log

make DRM_MODULES=sis.o modules
make[1]: Entering directory `/home/kid/dripkg/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
.
.
.
  CC [M]  /home/kid/dripkg/drm/linux-core/drm_agpsupport.o
  CC [M]  /home/kid/dripkg/drm/linux-core/drm_scatter.o
  CC [M]  /home/kid/dripkg/drm/linux-core/drm_memory_debug.o
  CC [M]  /home/kid/dripkg/drm/linux-core/ati_pcigart.o
  CC [M]  /home/kid/dripkg/drm/linux-core/sis_drv.o
/home/kid/dripkg/drm/linux-core/sis_drv.c:62: error: `sis_PCI_IDS' undeclared here (not in a function)
/home/kid/dripkg/drm/linux-core/sis_drv.c:62: error: initializer element is not constant
/home/kid/dripkg/drm/linux-core/sis_drv.c:62: error: (near initialization for `pciidlist[0]')
make[3]: *** [/home/kid/dripkg/drm/linux-core/sis_drv.o] Error 1
make[2]: *** [_module_/home/kid/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/kid/dripkg/drm/linux-core'
make: *** [sis.o] Error 2

My X version

X -version

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux edubuntu 2.6.12-satu #1 Sun Dec 11 01:10:45 EST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-satu (root@edubuntu) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Sun Dec 11 01:10:45 EST 2005
```

---

### Post by arnieboy on 2005-12-10
the real problem with this howto is that I only tested it with savage cards. Other cards like sis etc need to be tested but I cant help directly since I dont have any sis cards.
Hopefully, someone who has used this howto for sis cards can help..

---

### Post by widjajayd on 2005-12-11
[QUOTE=arnieboy]the real problem with this howto is that I only tested it with savage cards. Other cards like sis etc need to be tested but I cant help directly since I dont have any sis cards.
Hopefully, someone who has used this howto for sis cards can help..[/QUOTE]

Thanks Arnie, you helped me a lot 
my I915 notebook is working from your tips and your Automatics is super big jump :p

---

### Post by Dam on 2006-01-16
Thanks! It works!

However, the "tar" commands did not create the dripkg directory... I did it myself by creating it and pasting into it the files and directories of the two uncompressed tar.bz2 files (common first, savage second). Dit it happen to other people too?

Anyway, it works fine now! I enjoy tuxracer with my ProSavageDDR (32Mb shared memory).

Regards from Belgium!

---

### Post by indusnecro on 2006-01-26
Thanks. DRI worked on my system finally. I have  been trying to get this from one year in many distros. Finally I got it to work.

---

### Post by barthel on 2006-02-28
Great howto--I got bitten by not verifiying the X version used in Breezy, so everything worked when I used the 200507XX packages instead.

One suggestion, however. The best test for DRI is to look at the output from **glxinfo** (or even "glxinfo | grep direct" for a short & sweet answer).

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIS_multisample
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI Twister 20050501 AGP 1x x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.3
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_separate_specular_color, GL_EXT_subtexture, GL_EXT_texture,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, GL_MESA_window_pos,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x28 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x30 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x31 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x32 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
$

```

---

### Post by Selbstmord on 2006-03-04
This HOWTO was very good, but didnt work for me, I still get direct rendering: no

Although I do get a slight increase in FPS in glxgears. Im running an S3 Savage/MX card, if anyone has gotten it to work, please tell me how.

---

### Post by lettas on 2006-03-05
Direct rendering works out of box in thinkpad t23 (Dapper flight 4).

---

### Post by Denhez on 2006-03-12
Ok, I have done everything correctly (yes I have installed i-686 and removed i-386) with no error but I still dont have Direct rendering enabled:confused: 

glxgears shows that my fps is just over 100, both before and after I did the installation of the drivers. Glxinfo does NOT say that direct rendering is enabled.

The video card is a s3 savage/MX/IX.This is what is shown in my xorg.conf file ```
Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"savage"
	BusID		"PCI:1:1:0"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Any help would be appreciated.:(

---

### Post by MerZo on 2006-03-16
Hello! 

I can't it to get it work on Breezy. The logs doesn't say anything that help of what i can gather. I have one question!

Should I use gcc 4 (default) or is 3.4 neccesary? :)

Thanks for any help!

Edit:
Got i working by using an older driver (050311) using older driver than that gave me black menus in ppracer :D

Tip for everyone not getting it working, try different drivers!

---

### Post by Dauphinfay on 2006-03-18
I am losing my mind with this issue! I have been trying for DAYS to get DRI on my thinkpad T20. I have seen about five different ways to do it and I even went so far as to compile a new custom kernel (2.6.15-6) and I thought that I had solved the issue but "glxinfo" tells me that direct rendering = no. Tar'ing the common and savage files DOES NOT CREATE a dripkg dir. So, how is this working for anyone? What am I doing wrong? Any help or pointing in the right direction would be appreciated.


Help a newbie find his way...  :KS

---

### Post by Dauphinfay on 2006-03-19
I am furious right now!!! I have been trying for a week to get this working. I have managed to get this close but I cannot get this figured out. Here are the results from the dri.log:


make DRM_MODULES=savage.o modules
make[1]: Entering directory `/usr/src/dripkg/drm/linux-core'
make -C /lib/modules/2.6.15.6-dauphin/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-2.6.15.6'
  Building modules, stage 2.
  MODPOST
*** Warning: "pci_pretty_name" [/usr/src/dripkg/drm/linux-core/savage.ko] undefined!
make[2]: Leaving directory `/usr/src/linux-2.6.15.6'
make[1]: Leaving directory `/usr/src/dripkg/drm/linux-core'
/usr/X11R6/lib
WARNING: Error inserting drm (/lib/modules/2.6.15.6-dauphin/kernel/drivers/char/drm/drm.ko): Invalid module format
FATAL: Error inserting savage (/lib/modules/2.6.15.6-dauphin/kernel/drivers/char/drm/savage.ko): Invalid module format

---

### Post by aenertia on 2006-03-26
Hi,

I am trying to get dri working on a clients laptop. it is an older model Fujitsu Amilo, p3, it uses a via chipset with a Prosavage card.

I can not get direct rendering working. it will happily use the savage driver, but fails to load the drm or glx extensions.

I managed to get a working combination of common/savage drivers working at one point (by working I mean compilation a,nd installation steps went ok) But I always get unresolved symbol errors, and I must manually modprobe them for them to be loaded.

So some questions:

can someone tell me what is the last working snapshot archives that work (the ones posted on the original thread... which has been edited by the looks of it) do not work. I.e the 2006 snapshots do not work at all with breezy.

Can someone post the 20050707-savage and -common files somewhere (they are no-longer in the freedesktop archives at all) as it seems people have had success with these versions.

What modules/extensions should be included in the xorg.conf? i.e does glcore need not to be there.

The best I have managed to get, is manual modprobing and loading x (via xinit with xterm only) with the drm loading, and then having the screen blank. (console is not switchable at all either). 

However machine is still sshable and going. Only on reboot does the screen flicker and show the moire for a second, and then the console output return.

Most of the time I am getting unresolved symbol errors regardless of what combination I try of common/savage.

Suggestions welcome. But If someone could post the 20050707 tarballs that would be great.

---

### Post by ranf on 2006-03-26
@aenertia, Look here:
[http://dri.freedesktop.org/snapshots/archive/](http://dri.freedesktop.org/snapshots/archive/)

---

### Post by Dauphinfay on 2006-03-26
Installing files:
        DRI XFree86 modules...done
        kernel modules...done
        GL & GLU libraries...done
        core libraries...done
        Copying extra files...done

Updating configuration:
        Running ldconfig...done
        Removing old kernel module "savage"...done
        Inserting new kernel module "savage"...done

Checking configuration...ldd: /usr/X11R6/bin/glxinfo: No such file or directory

        second copy of DRI libraries found in
        libraries have been backed up to dri-old.* in

mv: cannot stat `/libGL.so': No such file or directory
mv: cannot stat `/libGL.so.1': No such file or directory
mv: cannot stat `/libGL.so.1.2': No such file or directory
done

Press ENTER to continue.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The DRI installation is complete.

Restart your X server to try the new DRI drivers.

If you have problems with the DRI after upgrading your drivers
please visit the DRI website and read the Help and FAQ section.
The FAQ contains solutions to many common problems.

Report any bugs, problems and comments on the dri-devel mailing list.

Thank you for using the DRI.


#any help would be appreciated. TIA

---

### Post by aenertia on 2006-03-27
[QUOTE=ranf]@aenertia, Look here:
[http://dri.freedesktop.org/snapshots/archive/](http://dri.freedesktop.org/snapshots/archive/)[/QUOTE]


I did I would have thought that was obvious from my post. 

There are no 0707 releases. I tried a number of combinations of newer common slightly older savage... etc. etc... I did get one combination that didn't spit tac's when compiling, but gave me unresolved or undefined symbol errors when loading.

I want the 0707 pair that people have reported success with. They are not in the archives.

In fact there is no common/savage combination in the archives with the same build date. I am guessing they have only kept the ones where there are chnages... But that does not help me any.

---

### Post by stairwayoflight on 2006-03-29
**_EDIT: SOLVED W/ UPGRADE TO DAPPER DRAKE F5!_**
Hey everybody,

I'm a noob & having trouble. I did this:

[QUOTE=arnieboy]This is how to do it (**only on Breezy**):
first of all
```
sudo apt-get install gcc-3.4 build-essential
```
**FOR AMD CHIPSETS**
```
sudo apt-get install linux-image-2.6.12-10-k7
sudo apt-get install linux-headers-2.6.12-10-k7
sudo apt-get install linux-restricted-modules-2.6.12-10-k7
```
Then **restart the comp and boot into the k7 kernel image** from grub (u will get that option).
Now do
```
sudo apt-get remove linux-image-2.6.12-10-386 linux-headers-2.6.12-10-386
```
and **jump straight to** *"COMMON FOR ALL CHIPSETS"*
----------------------------------------------------------------------------
**COMMON FOR ALL CHIPSETS**
```

wget http://dri.freedesktop.org/snapshots/archive/common-20051127-linux.i386.tar.bz2 
wget http://dri.freedesktop.org/snapshots/archive/savage-20051125-linux.i386.tar.bz2 
tar -xjf common-20051127-linux.i386.tar.bz2 
tar -xjf savage-20051125-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
```  
restart your comp (or just X server). 
check ur fps count with:
```
glxgears -printfps
```[/QUOTE]

running **glxinfo** shows direct rendering isn't enabled. that means its not working right? tuxracer is real slow..

i have a emachines t2341, amd athlon xp 2400+
ubuntu 5.10 release dual boot w/ xp
xorg setup correctly as far as i can tell with the savage driver, i get 1280x1024 ok

lspci gives:
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]


i assume **cd dripkg** really means
cd savage-20051125-linux.i386

i ran both install scripts, one from the 'common' dir and one from the 'savage'...

how do i fix it?
it is an integrated card, do i have to specify somewhere in a cfg file how much shared memory i dedicated to gfx in the bios settings, or does the driver detect it?

thanks ](*,)

---

### Post by NoWhereMan on 2006-04-03
same problem here :(
please help :)

**edit** Didn't have gcc3.4 installed :mrgreen:

d'oh, still no luck, i don't get any benefits; the installer(s) said driver were installed right... i don't know O.o

---

### Post by stairwayoflight on 2006-04-04
hey nowhereman,

are you bent on breezy?

dapper drake is more up to date in terms of software, but less stable. i am running it with no problems. a couple of pkg's have segfaulted on me (legacy doom, crap like that) but no prob's other than that.

you can get the "flight 5" install cd from the ubuntu site, it ships with 3d accel for savage and "it just works." 'xept with dapper i had to edit my xorg.conf and change "vesa" to "savage." i had to add normal screen resolutions "eg. 1024x768" and tweak my monitor settings, but after that i was playing chromium full speed.

---

### Post by Tuomio on 2006-04-07
I've been trying to get acceleration working on my thinkpad t22 with savage IX for days now.  I tried practically every versions of the common and savage packages from dri.freedesktop.org with no luck.

According to this page [http://ubuntuthinkpad.blogspot.com/](http://ubuntuthinkpad.blogspot.com/) files  common-20050714-linux.i386.tar.bz2.tar and savage-20050714-linux.i386.tar.bz2.tar should work but I cannot find them anywhere. 

If anyone has them, PLEASE send them to me. I would be eternally grateful.

---

### Post by stairwayoflight on 2006-04-09
hi,

i posted about problems here before, and moved on to dapper drake... but for certain reasons i am switching back to breezy.

i followed the howto exactly for my system, athlon-xp. then, because i have no "dripkg" directory and i don't know the correct cmd-line opts for "tar", i just used the tar commands in the howto. that gave me to directories, one for the "savage" archive and one for the "common". i simply created a "dripkg" dir, and did a drag-n-drop copy of folder contents to that directory, 1st the contents of the "common" directory, then the "savage". i say this explicitly because i am 99.5% sure this is the same as untarring to "dripkg/".

ok now the install.sh seemed to run okay, but i got this output the 1st time (excerpt from 2nd last page of output):

Checking configuration...ldd: /usr/X11R6/bin/glxinfo: No such file or directory

second copy of DRI libraries found in
libraries have been backed up to dri-old.* in

mv: cannot stat `/libGL.so': No such file or directory
mv: cannot stat `/libGL.so.1': No such file or directory
mv: cannot stat `/libGL.so.1.2': No such file or directory
done

Press ENTER to continue.


*****************
ok after running the script again, i get

Checking configuration...ldd: /usr/X11R6/bin/glxinfo: No such file or directory

second copy of DRI libraries found in
libraries have been backed up to dri-old.* in

done

Press ENTER to continue.

**********************

that thing about /usr/bin/glxinfo dir not found.. thats bad right?

OFFTOPIC: i have instructions on a driver disc for building a linux driver for my usb wifi device. i can't find a driver elsewhere. it includes instructions to tell the scripts where to find your /usr/src/linux-blahblah etc. if i get 3d support as per this howto, will it break adding wifi??


CPU: AMD ATHLON XP 2400+
kernel: 2.6.12-10-k7
Ubuntu Breezy Badger 5.10
S3 Graphics ProSavage8 (onboard)
lspci output: 0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
I think 64mb of shared video ram

2 questions:

1) what is the most direct route to discovering the problem and fixing it?
2) if the drm/dri/savage/whatever drivers work for me with dapper, is it elementary to just replace the concerned breezy pkg's with the working dapper ones, but stay with breezy for the rest of the system?

thnx

---

### Post by stairwayoflight on 2006-04-09
hi,

sorry to repost.. but is it possible for me to use the files compiled by someone else? ie does the script do certain things based on my hardware, or as long as i use the same kernel and savage driver as someone else it should work?

---

### Post by Mortuis on 2006-04-11
I get an error when I get to the sh ./install.sh step.  I get the following error message:
```
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
```

So I go ahead and check the dri.log and get:

```
root@uriel:/home/john/work2/dripkg# cat dri.log
make DRM_MODULES=savage.o modules
make[1]: Entering directory `/home/john/work2/dripkg/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/sis_ds.c sis_ds.c
+ ln -s ../shared-core/sis_ds.h sis_ds.h
+ ln -s ../shared-core/sis_mm.c sis_mm.c
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_mm.h via_mm.h
+ ln -s ../shared-core/via_ds.h via_ds.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_ds.c via_ds.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_mm.c via_mm.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.12-10-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
/home/john/work2/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/john/work2/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/john/work2/dripkg/drm/linux-core'
make: *** [savage.o] Error 2

```

It looks like I need to enable CONFIG_X86_CMPXCHG in the kernel, but I don't know how to do this, could someone please advise?

---

### Post by Mortuis on 2006-04-12
Well after beating my head for awhile I realized I followed the wrong steps and had followed the 386 path when I should have followed the 686 path, it works for me now. :-)

---

### Post by SpeedTriple on 2006-04-25
I just did it and it worked. Thx a lot for this great HOWTO. :)

[QUOTE=Dauphinfay]Installing files:
        DRI XFree86 modules...done
        kernel modules...done
        GL & GLU libraries...done
        core libraries...done
        Copying extra files...done

Updating configuration:
        Running ldconfig...done
        Removing old kernel module "savage"...done
        Inserting new kernel module "savage"...done

Checking configuration...ldd: /usr/X11R6/bin/glxinfo: No such file or directory

        second copy of DRI libraries found in
        libraries have been backed up to dri-old.* in

mv: cannot stat `/libGL.so': No such file or directory
mv: cannot stat `/libGL.so.1': No such file or directory
mv: cannot stat `/libGL.so.1.2': No such file or directory
done

Press ENTER to continue.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The DRI installation is complete.

Restart your X server to try the new DRI drivers.

If you have problems with the DRI after upgrading your drivers
please visit the DRI website and read the Help and FAQ section.
The FAQ contains solutions to many common problems.

Report any bugs, problems and comments on the dri-devel mailing list.

Thank you for using the DRI.


#any help would be appreciated. TIA[/QUOTE]

I got the same output, but that didn't stop dri from working. glxinfo is in /usr/bin, not in /usr/X11R6/bin, as the script expects. You can put a symlink in /usr/X11R6/bin by ```
ln -s /usr/bin/glxinfo /usr/X11R6/glxinfo
``` but I guess you don't need to.

One thing I found:
There are now symlinks in / dir for libGl.so, libGl.so.1, libGl.so.1.2 pointing to appropriate files in /usr/X11R6/lib. Could this come from said ' cannot stat ...' lines?

I used a self-compiled 2.6.12 kernel. I did this because I couldn't get ACPI sleep and hibernation to work properly with Ubuntu Kernel-Images and somewhere in a debian mailing list I had read, there could be problems with the T23 when acpi and apm is compiled into the kernel.

Then I used the common-20050707 and savage-20050718, being the latest archives I found giving me that dripkg dir after unpacking.

Here are some outputs:

```
ralf@trinity:~/Source$ dmesg | grep drm
[4294724.558000] [drm] Initialized drm 1.0.0 20040925
[4294724.627000] [drm] Initialized savage 2.4.1 20050313 on minor 0:
 S3 Inc. SuperSavage IX/C SDR
[4294724.628000] [drm] Used old pci detect: framebuffer loaded
```

```
ralf@trinity:~/Source$ lsmod | grep dr
drm                    75832  2 savage
agpgart                36136  2 drm,intel_agp

```

```
ralf@trinity:~/Source$ glxinfo | grep -2 direct
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
```

```
ralf@trinity:~/Source$ glxgears
-iacknowledgethatthistoolisnotabenchmark
2428 frames in 5.0 seconds = 485.506 FPS
2416 frames in 5.0 seconds = 483.171 FPS
2425 frames in 5.0 seconds = 484.988 FPS
2427 frames in 5.0 seconds = 485.320 FPS
2424 frames in 5.0 seconds = 484.691 FPS
```

Before I had about 250 FPS. I haven't yet tested any apps or GL-screensavers, it's late enough for today. ;)

Xorg.log tells success, too. Well, it works for me, thanks very much for the HOWTO and this thread, with gave me some useful hints (i. e. about using right version). I hope my post isn't too long and could help anyone still being unsuccessful.

---

### Post by encompass on 2006-05-09
I have tried exactly what you have posted here... The first time I dide it it worked... But the second time while using xubuntu it didn't work.  Am I missing something.  Where can I go to get the error output?
All test to find DRI support tell me I don't have support yet...
My card is:
> 0000:01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
At least according to lspci
Ideas?  I trying using both the newer and older version of the driver with no effect.
I noticed one difference between your instructions and files I downloaded.
When I had untared the files I didn't find a dripkg directory.
Could something have changed from your download?
Thanks for the help...

---

### Post by SpeedTriple on 2006-05-09
The last package giving you a dripkg directory after unpacking seems to be common-20050707-linux.i386.tar.bz2 and savage-20050718-linux.i386.tar.bz2.

```
0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
```

With newer ones I was successless on the thinkpad. Give it a try. What I'm looking for now is a package or _working_ patch to switch my S-Video output to PAL mode. But what I've read til now there seems to be no way of doing that with an S3 and a 1400x1050 display, only with that 1024x768 one. The patch one finds by searching the web doesn't do it, and noone got SXGA and need for PAL like me with an T23. :(

---

### Post by encompass on 2006-05-09
[QUOTE=SpeedTriple]The last package giving you a dripkg directory after unpacking seems to be common-20050707-linux.i386.tar.bz2 and savage-20050718-linux.i386.tar.bz2.

```
0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
```

With newer ones I was successless on the thinkpad. Give it a try. What I'm looking for now is a package or _working_ patch to switch my S-Video output to PAL mode. But what I've read til now there seems to be no way of doing that with an S3 and a 1400x1050 display, only with that 1024x768 one. The patch one finds by searching the web doesn't do it, and noone got SXGA and need for PAL like me with an T23. :([/QUOTE]


I think I have your solution... I ahve not tested it... but if it works, make a howto here on the forums...
> sudo apt-get install s3switch
hope it helps and yes I will download those and try them when I exams are over...  ;)

---

### Post by encompass on 2006-05-09
I have this ready:
> jason@lappy:~$ lspci | grep Savage
0000:01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)jason@lappy:~$ uname -r
2.6.12-10-686
jason@lappy:~$

I have everything installed concerning the 686 kernel that I know of.
But I get this while trying to compile:
> Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

the dri.log file doesn't give me much:
> cc      -o .o
cc: no input files
make: *** [.o] Error 1

and I have the directories that the installer checks including /lib/modules/2.6.12-10-686
> This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.12-10-686
Module Directory : /lib/modules/2.6.12-10-686

Am I missing something somewhere?](*,)

---

### Post by encompass on 2006-05-11
> wget [http://dri.freedesktop.org/snapshots/archive/common-20051127-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/archive/common-20051127-linux.i386.tar.bz2) 
wget [http://dri.freedesktop.org/snapshots/archive/savage-20051125-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/archive/savage-20051125-linux.i386.tar.bz2) 
tar -xjf common-20051127-linux.i386.tar.bz2 
tar -xjf savage-20051125-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
these links do not give the dripkg directories... which one should I use?

---

### Post by SpeedTriple on 2006-05-13
[QUOTE=encompass]these links do not give the dripkg directories... which one should I use?[/QUOTE]

[http://dri.freedesktop.org/snapshots/archive/common-20050707-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/archive/common-20050707-linux.i386.tar.bz2")
[http://dri.freedesktop.org/snapshots/archive/savage-20050718-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/archive/savage-20050718-linux.i386.tar.bz2")
worked for me.

About your compilation error: Have you installed kernel-headers or kernel-source packages?

About apt-get install s3switch: That would do, if I had a 1024x768 display, but I got an T23 with 1400x1050. After all I found on the web s3switch doesn't support it, and there is a patch around to fix, but not for that resolution and outpul in PAL, only NTSC.

---

### Post by encompass on 2006-05-14
> About your compilation error: Have you installed kernel-headers or kernel-source packages?

I have installed them, and made sure by typing the commands again.  Weird huh?
IM me if you would like to get any details and I would be more than happy to help you help me.
I have used those packages and yes, they had the dripkg that I was looking for.  But the error is the same.  I have tryied totally removing the packages and then reinstalling them, with no luck.
Feel free to contact me.

---

### Post by SpeedTriple on 2006-05-16
Sorry, don't use IM, what about email? I'll try to help you, if I can.

---

### Post by Nasso on 2006-06-04
Does this work with dapper?

---

### Post by encompass on 2006-06-04
According to previous posts here... it should be fixed with dapper... built into the kernel... but if it is not... it may or may not... I am installing dapper in about 5 minutes... I hope to report back with some good news.8)

---

### Post by NoWhereMan on 2006-06-04
[QUOTE=encompass]According to previous posts here... it should be fixed with dapper... built into the kernel... but if it is not... it may or may not... I am installing dapper in about 5 minutes... I hope to report back with some good news.8)[/QUOTE]

on dapper dri works out of the box ;)

---

### Post by Nasso on 2006-06-04
[QUOTE=NoWhereMan]on dapper dri works out of the box ;)[/QUOTE]

Really? Not for me. The graphics is laggy as hell and i cant run with -vo xv in mplayer. flashmovies and such are really slow and i have to use framedrop to be able to watch video.

I used this guide in breezy and it worked wonderfully!

EDIT:
I ran a 
```
sudo dpkg-reconfigure xserver-xorg
```
and now it all works like a charm! ^_^ 
xv works as output in mplayer and everything is smooth and sexy, just like ubuntu should be :)

Wierd that it didnt autodetect/autoconfigure during install :/

---

### Post by killbill on 2006-06-07
That's awesome.

But, anybody knows how to enable DRI for intel 845GM video card?

which driver should I use ? i810 or i915? the driver in "//snapshot" or "//snapshot/archieve" on freedesktop website?

and the release of what date should work?

I tried 915-20050707 and common-20050707, not working.

dri.log
```
make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/tobey/dripkg/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/sis_ds.c sis_ds.c
+ ln -s ../shared-core/sis_ds.h sis_ds.h
+ ln -s ../shared-core/sis_mm.c sis_mm.c
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_mm.h via_mm.h
+ ln -s ../shared-core/via_ds.h via_ds.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_ds.c via_ds.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_mm.c via_mm.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.15-23-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-686'
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_auth.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_bufs.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_context.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_dma.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_drawable.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_drv.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_fops.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_ioctl.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_irq.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_lock.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_memory.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_proc.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_stub.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_vm.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_sysfs.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_pci.o
/home/tobey/dripkg/drm/linux-core/drm_pci.c:57:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:88:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:136:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:143:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:159:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:57:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:88:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:136:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:143:5: warning: "DRM_DEBUG_MEMORY" is not defined
/home/tobey/dripkg/drm/linux-core/drm_pci.c:159:5: warning: "DRM_DEBUG_MEMORY" is not defined
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_agpsupport.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_scatter.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/drm_memory_debug.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/ati_pcigart.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/i915_drv.o
/home/tobey/dripkg/drm/linux-core/i915_drv.c: In function 'postinit':
/home/tobey/dripkg/drm/linux-core/i915_drv.c:45: warning: implicit declaration of function 'pci_pretty_name'
/home/tobey/dripkg/drm/linux-core/i915_drv.c:45: warning: format '%s' expects type 'char *', but argument 8 has type 'int'
/home/tobey/dripkg/drm/linux-core/i915_drv.c: At top level:
/home/tobey/dripkg/drm/linux-core/i915_drv.c:107: warning: initialization from incompatible pointer type
  CC [M]  /home/tobey/dripkg/drm/linux-core/i915_dma.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/i915_irq.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/i915_mem.o
  CC [M]  /home/tobey/dripkg/drm/linux-core/i915_pm.o
  LD [M]  /home/tobey/dripkg/drm/linux-core/drm.o
  LD [M]  /home/tobey/dripkg/drm/linux-core/i915.o
  Building modules, stage 2.
  MODPOST
*** Warning: "pci_pretty_name" [/home/tobey/dripkg/drm/linux-core/i915.ko] undefined!
  CC      /home/tobey/dripkg/drm/linux-core/drm.mod.o
  LD [M]  /home/tobey/dripkg/drm/linux-core/drm.ko
  CC      /home/tobey/dripkg/drm/linux-core/i915.mod.o
  LD [M]  /home/tobey/dripkg/drm/linux-core/i915.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
make[1]: Leaving directory `/home/tobey/dripkg/drm/linux-core'
/usr/X11R6/lib
FATAL: Error inserting i915 (/lib/modules/2.6.15-23-686/kernel/drivers/char/drm/i915.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by encompass on 2006-06-07
[QUOTE=killbill]That's awesome.

But, anybody knows how to enable DRI for intel 845GM video card?

which driver should I use ? i810 or i915? the driver in "//snapshot" or "//snapshot/archieve" on freedesktop website?

and the release of what date should work?

I tried 915-20050707 and common-20050707, not working.

dri.log
[/QUOTE]

First, concidering it is an 800 series card try the 810 chipset.
Secondly, if you are running dapper, it may not compile with the new xorg or kernel... not sure though.
Lastly, this is a post for savage... NOT your intel chip.  Please use another post or make your own post.
Thanks...

---

### Post by sean12345 on 2006-06-14
Hi,

I am having trouble getting 3d to work.  Im running 6.06 on a T22 with kernal 2.6.15-23-686.  

Here is what happens to me when I use the code provided.
```

sean@becca-laptop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After unpacking 47.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com dapper/main linux-kernel-headers 2.6.11.2-0ub untu18 [1039kB]
Get:2 http://security.ubuntu.com dapper-security/main binutils 2.16.1cvs20060117 -1ubuntu2.1 [1407kB]
Get:3 http://us.archive.ubuntu.com dapper/main libc6-dev 2.3.6-0ubuntu20 [2822kB ]
Get:4 http://us.archive.ubuntu.com dapper/main cpp-4.0 4.0.3-1ubuntu5 [1987kB]
Get:5 http://us.archive.ubuntu.com dapper/main cpp 4:4.0.3-1 [31.0kB]
Get:6 http://us.archive.ubuntu.com dapper/main gcc-4.0 4.0.3-1ubuntu5 [513kB]
Get:7 http://us.archive.ubuntu.com dapper/main gcc 4:4.0.3-1 [5048B]
Get:8 http://us.archive.ubuntu.com dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5  [1471kB]
Get:9 http://us.archive.ubuntu.com dapper/main g++-4.0 4.0.3-1ubuntu5 [2271kB]
Get:10 http://us.archive.ubuntu.com dapper/main g++ 4:4.0.3-1 [1386B]
Get:11 http://us.archive.ubuntu.com dapper/main make 3.80+3.81.b4-1 [286kB]
Get:12 http://us.archive.ubuntu.com dapper/main dpkg-dev 1.13.11ubuntu6 [163kB]
Get:13 http://us.archive.ubuntu.com dapper/main build-essential 11.1 [6826B]
Fetched 12.0MB in 23s (521kB/s)
Selecting previously deselected package binutils.
(Reading database ... 79268 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18 _i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.de b) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
sean@becca-laptop:~$ wget http://dri.freedesktop.org/snapshots/archive/common-20 051127-linux.i386.tar.bz2
--20:25:55--  http://dri.freedesktop.org/snapshots/archive/common-20051127-linux .i386.tar.bz2
           => `common-20051127-linux.i386.tar.bz2.1'
Resolving dri.freedesktop.org... 131.252.208.82
Connecting to dri.freedesktop.org|131.252.208.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,922,004 (1.8M) [application/x-tar]

100%[====================================>] 1,922,004    757.31K/s

20:26:13 (755.66 KB/s) - `common-20051127-linux.i386.tar.bz2.1' saved [1922004/1 922004]

sean@becca-laptop:~$ wget http://dri.freedesktop.org/snapshots/archive/savage-20 051125-linux.i386.tar.bz2
--20:26:33--  http://dri.freedesktop.org/snapshots/archive/savage-20051125-linux .i386.tar.bz2
           => `savage-20051125-linux.i386.tar.bz2.1'
Resolving dri.freedesktop.org... 131.252.208.82
Connecting to dri.freedesktop.org|131.252.208.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,199,487 (2.1M) [application/x-tar]

100%[====================================>] 2,199,487    778.15K/s

20:26:51 (776.26 KB/s) - `savage-20051125-linux.i386.tar.bz2.1' saved [2199487/2 199487]

sean@becca-laptop:~$ tar -xjf common-20051127-linux.i386.tar.bz2 sean@becca-laptop:~$ tar -xjf savage-20051125-linux.i386.tar.bz2 sean@becca-laptop:~$ cd dripkg
bash: cd: dripkg: No such file or directory

```

Can anyone figure out what I did wrong?  I have tried useing other snapshots, but they timed out and I have read that there are no really important updates in the later snapshots.

I noticed that gcc4.0 was installed with the build essential.  The first time I ran the code as posted by arnie without the build essential. "cd dripkg" didn't work with the version of gcc that I had before (I'm assuming it was gcc3.4) either.

Thanks for the help.
-Sean

---

### Post by nomeat on 2006-06-16
Seeing we are talking of Dapper now, and this thread is very frequented I am hoping to find more help here rather than starting a new thread.
I am using Xubuntu installed from the DesktopCD

Nothing that requires 3D power works on my Laptop with S3 Savage.

This includes: 
Stellarium ->black screen with an x, can not exit and have to hard power down like a windows crash
and
Google earth -> just splash sceen, wont go away, have to log out
and games like 
Tuxracer -> just black screen, have to power down. 

However I can play large mpg videos smoothly and with very little CPU activity.

My savage seems to be installed in Xorg.conf.:
Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/MX-MV"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection


I don't know how to identify if DRI is active or working.

This is the DRI entry in Xorg.conf:
Section "DRI"
	Mode	0666
EndSection

Any help would be wonderful.

---

### Post by w0rds on 2006-06-16
[QUOTE=nomeat]
I don't know how to identify if DRI is active or working.
[/QUOTE]

run "[glxinfo]("http://linuxcommand.org/man_pages/glxinfo1.html")" from the console and check its output :)

---

### Post by nomeat on 2006-06-16
[QUOTE=w0rds]run "[glxinfo]("http://linuxcommand.org/man_pages/glxinfo1.html")" from the console and check its output :)[/QUOTE]

Thanks mate.:) 

Looked all jibberish to me but I didn't see anything that looked like an error.
Got this feedback that looks like a discription of my system:
```

visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
```

Anything there that could be related to my problems?
Otherwise any clue where I should look next?

Thanks again
Cheers
Peter

---

### Post by w0rds on 2006-07-22
> **nomeat said:**
> Anything there that could be related to my problems?
Otherwise any clue where I should look next?

it should say something about direct rendering, in the first lines of the output. if it says "yes", it's enabled! ;)
it never said "yes" to me, tho. dri doesn't like me, i think.




when i try to enable dri here on my thinkpad t20, it says i don't have enough memory [doesn't matter how low i set the resolution/color depth]. i tried it on 5.04, anyone knows if the problem is fixed on 6.06?

thanks

---

### Post by nomeat on 2006-07-23
Linux and older Laptops (4 or more years) is a pain.

Sorry I had enough of ](*,) and gave up. 

It is a happy WinME system again and the kids are happy with it too.

---

### Post by avilella on 2006-09-02
hi all,

I tried this howto on Dapper and it seems I can't get it to work.

The compilation of the drivers went fine, but when I restart the X server, I still don't get DRI enabled.

I even did a:

sudo dpkg-reconfigure xserver-xorg

and recompiled the drivers again, but no luck.

Any idea of why this may not be working for my on Dapper?

Thanks in advance,

Cheers

---

### Post by NoWhereMan on 2006-09-02
try setting the DefaultDepth to 16 and not 24, when doing sudo dpkg-reconfigure xserver-xorg or manually editing xorg.conf; that was the problem for me. 

btw, has anybody here with a (pro)savage managed to make it work with xgl/aiglx+compiz ?

bye!

---

### Post by avilella on 2006-09-02
yes, tried that, no luck.

This is the snippet of my xorg.conf file...

-----

Section "Device"
        Identifier      "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
        Driver          "savage"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by NoWhereMan on 2006-09-02
> **avilella said:**
> 
Section "Screen"
[...]
[b]
        SubSection "Display"
[COLOR="Red"]                  Depth           24[/COLOR]
              Modes           "1024x768"
        EndSubSection[/b]
EndSection
[..]

try setting that to 16, too
of course reboot, then (restarting gdm may not work)

---

### Post by terry98 on 2006-11-08
hi guys ive got a omnibook xe3-gc with a savage-MX/IX ive everything in the post ans cant get the F#@$%& drivers to work.... ive downloaded the latest common and savage even compiled the latest drm all these from dri.freedesktop.org...... HELP!!!

PS.: I only got 192Mb in ram, ive tried to install dapper but it hangs while installing....

---

### Post by dpm on 2006-11-12
> **NoWhereMan said:**
> btw, has anybody here with a (pro)savage managed to make it work with xgl/aiglx+compiz ?

The savage driver does not work with compiz. See this info I posted a few minutes ago about this:

[http://www.ubuntuforums.org/showpost.php?p=1747736&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1747736&postcount=5)

BTW, in edgy I got the savage driver working with dri with no trouble (no compilation, etc.)

Cheers.

---

### Post by encompass on 2006-12-09
> **desp said:**
> The savage driver does not work with compiz. See this info I posted a few minutes ago about this:

[http://www.ubuntuforums.org/showpost.php?p=1747736&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1747736&postcount=5)

BTW, in edgy I got the savage driver working with dri with no trouble (no compilation, etc.)

Cheers.
I have the savage driver... in edgy, but if I remember seeing the xorg log file dri is disabled.  How did you enable it?

---

### Post by dpm on 2006-12-10
> **encompass said:**
> I have the savage driver... in edgy, but if I remember seeing the xorg log file dri is disabled.  How did you enable it?

I don't think dri is disabled by default in Edgy. I believe simply the following line is required in /etc/X11/xorg.conf:

```
    Load    "dri"
```In any case, I've attached my **/etc/X11/xorg.conf** and **/var/log/Xorg.0.log** files for reference. Note that the 

```
  Option        "AIGLX" "true"
```and

```
Section "Extensions"
    Option        "Composite" "Enable"
EndSection
```lines in my xorg.conf are probably not needed, since all this is enabled per default in Edgy's X, but I haven't bothered removing them since last time I was playing around with the driver.

I hope this helps.

Cheers.

---

### Post by encompass on 2006-12-11
I don't need aiglx support... just for it to simply say I have dri working.
I have checked for the dri section and is there.
I have no idea why it doesn't work.  It did way back when I manually installed it in Breezy.
As for my lspci output with the graphics card...
> 
jason@lappy:~$ lspci | grep Savage
01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
jason@lappy:~$


---

### Post by po0f on 2006-12-11
encompass,

This works for my T22 with the same graphics chip:
```
[FONT="Courier New"]Section "Device"
    Identifier	"MyVideoCard"
    Driver	"savage"
    Option	"BusType"		"AGP"
    Option	"DmaType"		"AGP"
    Option	"DmaMode"		"None"
    Option	"AGPMode"		"2"
    Option	"AGPSize"		"16"
    Option	"SWCursor"		"true"
    #VideoRam	8192
EndSection[/FONT]
```

glxgears ~390, ~130 without.  HTH.

---

### Post by encompass on 2006-12-12
I didn't see much of an improvement.  Looks like I am stuck with what I have.  Does your's say it has direct rendering?  Mine doesn't.
And your settings run fine... but if I try to shutdown the X server it won't go down.  But in the background I can shut it down softly.

---

### Post by dpm on 2006-12-12
> **encompass said:**
> I didn't see much of an improvement.  Looks like I am stuck with what I have.  Does your's say it has direct rendering?  Mine doesn't.
And your settings run fine... but if I try to shutdown the X server it won't go down.  But in the background I can shut it down softly.

well, what does your Xorg.0.log say when trying to load the dri module?

Have you had a look at [https://bugs.freedesktop.org](https://bugs.freedesktop.org) for any open bugs related to your video chip?

---

### Post by encompass on 2006-12-12
jason@lappy:~$ grep /var/log/Xorg.0.log test
grep: test: No such file or directory
jason@lappy:~$ grep dri /var/log/Xorg.0.log
        X.Org XInput driver : 0.6
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
        ABI class: X.Org XInput driver, version 0.6
        ABI class: X.Org XInput driver, version 0.6
        ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
        ABI class: XFree86 XInput driver, version 0.3
(II) SAVAGE: driver (version 2.1.1) for S3 Savage chipsets: Savage4,
(II) Synaptics touchpad driver version 0.14.6 (1406)
jason@lappy:~$ grep DRI /var/log/Xorg.0.log
(II) Loading extension XFree86-DRI
(**) SAVAGE(0): DRI is disabled by default on this chipset as it is experimental and unstable.
(EE) SAVAGE(0): DRI isn't enabled
(EE) AIGLX: Screen 0 is not DRI capable
jason@lappy:~$ 

wierd huh?
I will search for a bug...

---

### Post by jakewiz247 on 2006-12-19
Hey guys,

I'm having the same DRI problem here.  I have a T23 thinkpad with superSavage IXC SDR video card and have tried all the common and savage drivers and i keep getting an unable to compile error.  Just installed this today and did all the updates and have 2.6.17-10-386 kernel running on here.  What do i need to do to get this thing running right?

---

### Post by Aifel on 2006-12-19
Wow, thanks to the above guy who posted a bunch of xorg.conf options. It boosted my FPS by a good 200! I'm still having trouble installing the latest DRI drivers. Im running Edgy (Ubuntu 6.10),  kernel 2.6.17-10-generic. It says I am missing some packages... What packages do I need?

---

### Post by dpm on 2006-12-19
> **jakewiz247 said:**
> Hey guys,

I'm having the same DRI problem here.  I have a T23 thinkpad with superSavage IXC SDR video card and have tried all the common and savage drivers and i keep getting an unable to compile error.  Just installed this today and did all the updates and have 2.6.17-10-386 kernel running on here.  What do i need to do to get this thing running right?

I believe you do not have to compile anything in Edgy.

Why are you using the -386 kernel instead of the -generic?

Could you post the output of:

```
lspci

```and

```
lspci -n
```and

```
lsmod | grep savage
```and if possible, could you please add a couple of attachments with your current /etc/X11/xorg.conf and /var/log/Xorg.0.log files?

Cheers

---

### Post by tyrewt on 2007-01-02
Mainly my interests lay in getting Beryl working on a ThinkPad T23.  3d acceleration is a must, does anyone have beryl working with this video card?

I've also posted a separate thread if you're interested in getting Beryl working with a S3 supersavage card.
[http://ubuntuforums.org/showthread.php?p=1958294#post1958294](http://ubuntuforums.org/showthread.php?p=1958294#post1958294)

---

### Post by Cjames on 2007-03-12
Hi, I have a Supersavage/IXC16 card as well in a IBM/T23 Notebook. I'm really needing help enabling 3D support on this card. (trying to set it up to play some of the older Tomb Raider games).

this is the results of the above posted commands. 

lspci

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420
02:00.1 CardBus bridge: Texas Instruments PCI1420
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

lspci -n

00:00.0 0600: 8086:3575 (rev 02)
00:01.0 0604: 8086:3576 (rev 02)
00:1d.0 0c03: 8086:2482 (rev 01)
00:1d.1 0c03: 8086:2484 (rev 01)
00:1d.2 0c03: 8086:2487 (rev 01)
00:1e.0 0604: 8086:2448 (rev 41)
00:1f.0 0601: 8086:248c (rev 01)
00:1f.1 0101: 8086:248a (rev 01)
00:1f.3 0c05: 8086:2483 (rev 01)
00:1f.5 0401: 8086:2485 (rev 01)
01:00.0 0300: 5333:8c2e (rev 05)
02:00.0 0607: 104c:ac51
02:00.1 0607: 104c:ac51
02:02.0 0780: 11c1:0449 (rev 01)
02:08.0 0200: 8086:1031 (rev 41)
03:00.0 0280: 14e4:4318 (rev 02)

lsmod | grep savage

savage                 35200  2 
drm                    74644  3 savage

And here is a copy of part of my xorg.conf. (if I need to post the whole thing, please let me know)


Section "Device"
	Identifier	"S3 Inc. SuperSavage IX/C SDR"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. SuperSavage IX/C SDR"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Thank you very much in advance for any help ya'll can give. I installed Ubuntu over the weekend and love it so far.

James

---

### Post by keith.burgoyne on 2007-04-01
I have the same trouble with Feisty Fawn. 3D worked perfectly in Edgy, but after I did a clean install of Feisty, it seems to have broken.

Here's my xorg.conf file:

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/wacom"    # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/wacom"    # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/wacom"    # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "S3 Inc. SuperSavage IX/C SDR"
        Driver          "savage"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. SuperSavage IX/C SDR"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Also, lspci output:

01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)

lsmod | grep savage
savage                 34048  1
drm                    81044  2 savage

Anyone have any suggestions?

---

### Post by compartist on 2007-05-07
Keith.Burgoyne,

I followed these instructions:

Download this attachment: [http://librarian.launchpad.net/7385659/drm.tar.bz2](http://librarian.launchpad.net/7385659/drm.tar.bz2)

tar xjvf drm.tar.bz2
cd drm/linux-core/
make DRM_MODULES="savage"
sudo mv /lib/modules/2.6.20-15-generic/kernel/drivers/char/drm/savage.ko /lib/modules/2.6.20-15-generic/kernel/drivers/char/drm/savage.ko.old
sudo mv /lib/modules/2.6.20-15-generic/kernel/drivers/char/drm/drm.ko /lib/modules/2.6.20-15-generic/kernel/drivers/char/drm/drm.ko.old
sudo cp savage.ko /lib/modules/2.6.20-15-generic/kernel/drivers/char/drm/savage.ko
sudo cp drm.ko /lib/modules/2.6.20-15-generic/kernel/drivers/char/drm/drm.ko
sudo depmod -a

After rebooting, "glxinfo | grep direct" reports "direct rendering: Yes".


from here: 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905")

and they really helped me...I hope it helps you too

---

### Post by ageilers on 2007-06-04
Thanks to Compartist, I now have fixed something I did not realize was broken. IBM T23 with supersavage graphics running Kubuntu Feisty. I followed your directions but changed for kernel upgrade 2.6.20-16.

---

### Post by rah1420 on 2007-06-06
I have tried the instructions in the thread here because my 7.04 installation was generally crap, with only 1024 X 768 resolution and blurry text images no matter which fonts were used.  They made absolutely no difference, despite my having a T23 with the SAVAGE integrated display. 

I heaved a deep sigh and swapped back in my 6.06 LTS installation hard disk, where I'm running with crystal clear fonts at 1400 X 1050.   Guess it just wasn't in the cards for me.  So to speak.

Just so some of you know, there can be an installation that it DOESN'T work on.  And if anyone wants to help me get my 7.04 running again, I'd be happy to entertain suggestions.  Swapping hard disks isn't that difficult.

---

### Post by Talon2 on 2007-06-10
> **rah1420 said:**
> And if anyone wants to help me get my 7.04 running again, I'd be happy to entertain suggestions.

My suggestion is to forget Fiesty on a T23.  In my experience too many things have been broken since Dapper for it to be worth the effort.

My approach is to install Gutsy and post/add to as many bugs in Launchpad as possible.  There are decisions be made that are breaking this os on our T23's and I'd like to see it stopped.  Fiesty sucks as far as I' concerned.

---

### Post by K.B. on 2007-07-03
I've been trying to get this to work on my T23 since I upgraded and I finally found the answer AND an easy one too!

check out this posting and when I did what he suggested and ran his installer it fixed everything and now my laptop says:

[I][B]
direct rendering: Yes[/B][/I]

[B]
follow this link:[/B]
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905/comments/46]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905/comments/46")

---

### Post by wvhtrn on 2007-07-13
Hey K.B.   I went to the link you suggested , I followed the instructions as posted... guess what... it worked on my T23 as well.  Thanks for that great link, it was so easy even I could do it.

---

### Post by binger on 2008-03-02
So I think I have my savage drivers working with DRI on my thinkpad T22 Ubuntu Gutsy.  Though I only get about 200fps in glxgears, and I get some weird errors in my xorg log.  the relavant files are attached, anyone have any idea what the errors are about?  and can you do compiz with a 8mb savage card?
Thanks!

---

### Post by echellon7 on 2008-06-04
Hi, this may sound a bit stupid to ask but this is the only forum where I found people seriously dealing with this.So...does anyone know about a way of enabling 3d in windows?I've got T23 SuperSavage IXC 16MB.
I'll appreciate any idea,link or advice.
Thanks very much.

---

### Post by Matteran on 2008-07-08
So, I tried the first post and when installing the second driver (the savage specific) I got an error saying my kernel wasn't up to date.

I'm running xubuntu 8.04 on an HP XT936 (link to specifications on HP's site: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph06583&lc=en&cc=us&dlc=en&product=59042&lang=en#N433](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph06583&lc=en&cc=us&dlc=en&product=59042&lang=en#N433) )

this is the output of lspci
```
$ lspci | grep Savage
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)
```

I'm not sure if that's any help. I wanted to try some of the more updated drivers linked earlier in the thread but the links are dead.

Please if someone could try to help me today it would be much appreciated, I'm trying to setup this computer for a friend's parents and it would be really nice to have this working perfectly instead of having to just install windows back on it.

Thanks for any help you can provide (also I'm a bit of a noob for some things, so explanation of how to do something might be necessary)

In the mean time i'll read the rest of this thread a second time and see if I missed anything.

**Edit:** Okay, maybe I'm dumb, I see in Synaptic drivers for S3 chips, and I installed them, but I'm not sure how to get them working, obviously they aren't working, because video performance is horrendous.

**Edit 2:** So I found some up-to-date snapshots to give that a try and same problem... I'm thinking it's because I need to edit the kernal to enable DRM (idea from this thread: [http://www.linuxquestions.org/questions/linux-hardware-18/direct-rendering-infrastructure-dri-on-vias3-savage-168951/](http://www.linuxquestions.org/questions/linux-hardware-18/direct-rendering-infrastructure-dri-on-vias3-savage-168951/) ) But I don't know how to do that...
Also, here's the error part of dri.log:
```
In file included from /home/karen/Desktop/savage-20060403-linux.i386/drm/linux-core/drm_auth.c:36:
/home/karen/Desktop/savage-20060403-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/home/karen/Desktop/savage-20060403-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/karen/Desktop/savage-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/karen/Desktop/savage-20060403-linux.i386/drm/linux-core'
make: *** [savage.o] Error 2
```
and the output of trying to update the kernal in the first post (i'm assuming it doesn't work because 8.04 is so far ahead the kernel version in that post)
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.12-10-686
```

---

### Post by noel32 on 2008-09-17
are these steps applicable to hardy?

i am having problems with my video (s3 vt8375 prosavage8 km266/kl266), i can't run compiz and can't enable desktop effects. i checked direct rendering (using glxinfo |grep rendering), the result was 'yes'. 

here is what i got when i ran  lspci -vvv:
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266] (prog-if 00 [VGA controller])
	Subsystem: Jetway Information Co., Ltd. Unknown device 8d04
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (1000ns min, 63750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at d9000000 (32-bit, non-prefetchable) [size=512K]
	Region 1: Memory at d0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at d8000000 [disabled] [size=64K]
	Capabilities: <access denied>

when i checked the screen and graphics preferences, the graphics card is s3 savage4 but without driver and blank video memory. when i try using other s3 savage drivers, the display would go blank.

what can i do so i can use the 3d and other capabilities of my video card?

---

### Post by Axerated on 2010-05-12
Hi will this work on Ubuntu 9.10? I have problem in getting my graphic card working.

---

