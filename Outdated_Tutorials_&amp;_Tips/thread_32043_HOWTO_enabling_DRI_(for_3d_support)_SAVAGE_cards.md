---
title: "HOWTO: enabling DRI (for 3d support) SAVAGE cards"
date: 2005-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-05-05
**This is for Ubuntu Breezy ONLY**. Please do not use this howto on any other subsequent releases (Dapper, Edgy, etc)
This is how to do it:
**FOR OLDER INTEL AND AMD CHIPSETS (INTEL 386, 486 ETC.)**
Jump straight to "*COMMON FOR ALL CHIPSETS*"
**FOR INTEL 686 CHIPSETS (WITHOUT HYPERTHREADING)**
```
sudo apt-get install linux-image-2.6.10-5-686
sudo apt-get install linux-headers-2.6.10-5-686
sudo apt-get install linux-restricted-modules-2.6.10-5-686
```
Then restart the comp and boot into the 686 kernel image from grub (u will get that option).
Now remove
***linux-image-2.6.10-5-386*** and ***linux-headers-2.6.10-5-386***
from synaptic.
**FOR INTEL CHIPSETS (WITH HYPERTHREADING)**
```
sudo apt-get install linux-image-2.6.10-5-686-smp
sudo apt-get install linux-headers-2.6.10-5-686-smp
sudo apt-get install linux-restricted-modules-2.6.10-5-686-smp
```
Then restart the comp and boot into the 686-smp kernel image from grub (u will get that option).
Now remove
***linux-image-2.6.10-5-386*** and ***linux-headers-2.6.10-5-386***
from synaptic.
**FOR AMD CHIPSETS**
```
sudo apt-get install linux-image-2.6.10-5-k7
sudo apt-get install linux-headers-2.6.10-5-k7
sudo apt-get install linux-restricted-modules-2.6.10-5-k7
``` 
Then restart the comp and boot into the k7 kernel image from grub (u will get that option).
Now remove
***linux-image-2.6.10-5-386*** and [I][B]linux-headers-2.6.10-5-386
from synaptic. 
**COMMON FOR ALL CHIPSETS**
[PHP]sudo apt-get install build-essential
wget http://dri.freedesktop.org/snapshots/common-20050707-linux.i386.tar.bz2
wget http://dri.freedesktop.org/snapshots/savage-20050707-linux.i386.tar.bz2
tar -xjf common-20050707-linux.i386.tar.bz2
tar -xjf savage-20050707-linux.i386.tar.bz2 
cd dripkg
sudo ./install.sh[/PHP]

restart your comp (or just X server). 

enjoy tuxracer!

---

### Post by qrazi on 2005-05-06
after i type "sudo ./install.sh" i get the following error when ubuntu tries to compile: 

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

the dri.log says:

make DRM_MODULES=savage.o modules
make[1]: Entering directory `/home/qrazi/dripkg/drm/linux-core'
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/home/qrazi/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/qrazi/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/qrazi/dripkg/drm/linux-core'
make: *** [savage.o] Error 2


as far as i know, i'm using X.org (i am running a clean ubuntu 5.04 hoary install).

the card used: Diamond stealth 540 16mb agp (Savage4 chip)

OT: would it be wiser to put my old voodoo5 in, performance and installation wise? or has the savage4 better support?

as you can read, i am a big newbie.... to both ubuntu and linux...

---

### Post by arnieboy on 2005-05-06
what is the processor that u use? 

what u would probably do is the following:

upgrade your kernel to 686 (from 386): how to do that?

go to synaptic and search for the string "2.6.10-5" . what u will get among other packages is a list of 686 packages which u need to install (DO NOT uninstall the 386 packages yet) . Also at the same go, search for "linux-headers" and remove "linux-headers-2.6.10-5" and install "linux-headers-2.6.10-5-686". Also install the appropriate "dev" packages as well in the same place. 
if u are using grub, reboot your comp and you will see an extra option of booting into the 686 kernel. Boot into the 686 kernel and go to synaptic again and remove the 386 kernel. 
if u are using lilo, do a "sudo lilo" before rebooting and it will backup ur old kernel config and make ur 686 the default.  

now try and run "install.sh" again and tell me how it goes.

---

### Post by qrazi on 2005-05-06
i use a celeron 800@1060MHz. i had the 2.6.10 kernel installed, 386 version. after i replied i did some more google work, and read somewhere that you need to have kernel 2.6.11 installed for it to work. and then i read your tip about the 686 version, so now i am running kernel 2.6.11-686

glxgears was ~130fps, now ~450fps..... still not a lot, but Cube is very playable now. 
and this isnt my game machine anyway, more of a "getting to know linux pc"

---

### Post by Obi on 2005-06-18
Does this system work with debian testing and XFree too???

---

### Post by jobezone on 2005-06-19
[QUOTE=Obi]Does this system work with debian testing and XFree too???[/QUOTE]
 I've searched a bit for this, and I've found out that the Savage driver for Xfree86 does not support DRI :( so we'll have to wait for X.org first.

---

### Post by brian.reading on 2005-07-13
I'm having trouble with mine now.  I performed the steps exactly as above, however I get this in my dri.log file:

"Makefile:163: *** Cannot find a kernel config file. Stop."

Any suggestions? Thanks.

---

### Post by arnieboy on 2005-07-13
what is your processor? (Intel/AMD etc)

---

### Post by brian.reading on 2005-07-13
[QUOTE=arnieboy]what is your processor? (Intel/AMD etc)[/QUOTE]
[QUOTE=cat /proc/cpuinfo]
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 4
model name      : AMD Athlon(tm) Processor
stepping        : 2
cpu MHz         : 1002.416
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr pni syscall mmxext 3dnowext 3dnow
bogomips        : 1982.46
[/QUOTE]

lspci identifies the card as "S3 Inc. ProSavage KM133".  It's an integrated chip. According to the install script that qualifies as the correct driver.

and uname -a says I have the version 2.6.10-5-386 kernel.

This is a Compaq Presario 5000 series from circa 2001.  A Compaq 5UVM11 to be exact.  Any ideas?

---

### Post by arnieboy on 2005-07-13
from synaptic install the following:
[I]linux-headers-2.6.10-5-k7
linux-image-2.6.10-5-k7
linux-restricted-modules-2.6.10-5-k7[/I]
then restart the comp and boot into the k7 kernel image from grub (u will get that option). 
Now remove 
*linux-image-2.6.10-5-386* 
from synaptic.
Now try and install the savage 3d drivers again.
make sure u note ur fps reading on glxgears before and after u install the drivers

---

### Post by brian.reading on 2005-07-13
[QUOTE=arnieboy]from synaptic install the following:
[I]linux-headers-2.6.10-5-k7
linux-image-2.6.10-5-k7
linux-restricted-modules-2.6.10-5-k7[/I]
then restart the comp and boot into the k7 kernel image from grub (u will get that option). 
Now remove 
*linux-image-2.6.10-5-386* 
from synaptic.
Now try and install the savage 3d drivers again.
make sure u note ur fps reading on glxgears before and after u install the drivers[/QUOTE]
Thanks for the fast help! I did all of this, and everything worked smoothly after that.  Before I got 135-145 FPS with glxgears, now I get around 260 or so.  Not SOO much of an increase, but it IS faster.  Again, thanks for the help! I could never have done it without you.

Brian

---

### Post by brian.reading on 2005-07-13
Hmm... Now for some reason some of my video apps such as VLC and Realplayer tend to quit on me when I try to open a file.  What do you think the problem is the new kernel or is it the video drivers?

---

### Post by az on 2005-07-13
I am not at home and am working from memory:

Both tarballs make the same dripkg directory.  Does it get rewritten?  Do you need the "-common" snapshot for it to work?  Can you just use the "savage" snapshot?

---

### Post by bored2k on 2005-07-13
[QUOTE=arnieboy]This is how to do it:

sudo apt-get install linux-headers-2.6.10-5
**OR**
sudo apt-get install linux-headers-2.6.10-5-686

depending on ur kernel version. 

wget [http://dri.freedesktop.org/snapshots/common-20050504-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20050504-linux.i386.tar.bz2)
wget [http://dri.freedesktop.org/snapshots/savage-20050504-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/savage-20050504-linux.i386.tar.bz2)
tar -xjf common-20050504-linux.i386.tar.bz2
tar -xjf savage-20050504-linux.i386.tar.bz2 
cd dripkg
sudo ./install.sh

restart your comp (or just X server). 

enjoy tuxracer![/QUOTE]
 Would this work for a SiS integrated Integrated video graphics accelerator ?

---

### Post by az on 2005-07-13
[QUOTE=bored2k]Would this work for a SiS integrated Integrated video graphics accelerator ?[/QUOTE]

No.  It is for Savage chipsets.

For Sis DRI which actually work, check out:
[http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz](http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz)

[http://www.ubuntuforums.org/showpost.php?p=232294&postcount=4](http://www.ubuntuforums.org/showpost.php?p=232294&postcount=4)

With Hoary, all you need to do is add

"MaxXFBMem" "12288"

To your xorg driver section.  You should have at least 32 megs of shared memory for your video card (64 is better)  Your's is an onboard card right? (Most Sis video are...)

And copy the above precompiled driver into

usr/X11R6/lib/modules/dri/sis_dri.so



I get pretty crappy acceleration because it is a pretty crappy technology, but it works and I can play tuxracer...

---

### Post by arnieboy on 2005-07-13
[QUOTE=bored2k]Would this work for a SiS integrated Integrated video graphics accelerator ?[/QUOTE]
yes it should. just go to [http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots) and download the latest for sis and make sure u get the corresponding "common" tar ball as well from the same release date. also make sure u untar the "common" tarball first.

---

### Post by arnieboy on 2005-07-13
[QUOTE=azz]I am not at home and am working from memory:

Both tarballs make the same dripkg directory.  Does it get rewritten?  Do you need the "-common" snapshot for it to work?  Can you just use the "savage" snapshot?[/QUOTE]
 u need both "common" and the relevant card based driver tarball to make this thing work and also make sure u untar the "common" tar ball first.. both of them will get unzipped into the dripkg directory.

---

### Post by arnieboy on 2005-07-13
[QUOTE=brian.reading]Hmm... Now for some reason some of my video apps such as VLC and Realplayer tend to quit on me when I try to open a file.  What do you think the problem is the new kernel or is it the video drivers?[/QUOTE]
 its possibly because of the new kernel. u shd try and recompile vlc and realplayer. or just reinstall them.

---

### Post by bored2k on 2005-07-13
[QUOTE=arnieboy]yes it should. just go to [http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots) and download the latest for sis and make sure u get the corresponding "common" tar ball as well from the same release date. also make sure u untar the "common" tarball first.[/QUOTE]
 Thanks. I'll try it now and come back in a bit with the results.

---

### Post by az on 2005-07-13
[QUOTE=arnieboy]u need both "common" and the relevant card based driver tarball to make this thing work and also make sure u untar the "common" tar ball first.. both of them will get unzipped into the dripkg directory.[/QUOTE]

The last time I had done this, both dripkg directories had different install scripts with the same name.  I had to untar them into different directories so that I could run both install scripts.  Otherwise, the second one would overwrite the first one.

Someone on the forums had mentioned that they did not need the common package to get Mach64 working.  Either because Hoary's installation was up-to-date enough or just plain old luck.

But I am at work and cannot untar anything to check....

---

### Post by arnieboy on 2005-07-13
[QUOTE=azz]The last time I had done this, both dripkg directories had different install scripts with the same name.  I had to untar them into different directories so that I could run both install scripts.  Otherwise, the second one would overwrite the first one.

Someone on the forums had mentioned that they did not need the common package to get Mach64 working.  Either because Hoary's installation was up-to-date enough or just plain old luck.

But I am at work and cannot untar anything to check....[/QUOTE]
the point is that u dont need to run both install scripts.. u just need to run one which is left over in the dripkg directory after u untar both (common and then the relevant chipset tarball).

---

### Post by bored2k on 2005-07-13
> Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.



I have linux-headers-2.6.10-5-686 installed... _ ?

I also installed linux-686 and I still get that message :-(
I noticed the script is trying to use XFRee. Wont this be a problem ¿?

---

### Post by az on 2005-07-13
[QUOTE=bored2k]I have linux-headers-2.6.10-5-686 installed... _ ?

I also installed linux-686 and I still get that message :-(
I noticed the script is trying to use XFRee. Wont this be a problem ¿?[/QUOTE]

Xorg uses 

usr/X11R6/lib/modules/dri

So, no it is not a problem.  Freedesktop.org _is_ xorg.

Do you have build-essential installed?

**edit**  I got SiS dri working without compiling anything for my kernel.  The SiS driver does not use sisfb...  I would suggest you try the updated package from Sir Winihopher.

---

### Post by arnieboy on 2005-07-13
[QUOTE=bored2k]I have linux-headers-2.6.10-5-686 installed... _ ?

I also installed linux-686 and I still get that message :-(
I noticed the script is trying to use XFRee. Wont this be a problem ¿?[/QUOTE]
do u have linux-image-2.6.10-5-686 installed as well? if not install that and then reboot into the 686 kernel image from grub (which will get auto created). Now remove linux-image-2.6.10-5-386 image from synaptic after u reboot and then try installing the script. make sure u also have linux-headers-2.6.10-5.386 removed as well.

---

### Post by bored2k on 2005-07-13
[QUOTE=azz]No.  It is for Savage chipsets.

For Sis DRI which actually work, check out:
[http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz](http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz)

[http://www.ubuntuforums.org/showpost.php?p=232294&postcount=4](http://www.ubuntuforums.org/showpost.php?p=232294&postcount=4)

With Hoary, all you need to do is add

"MaxXFBMem" "12288"

To your xorg driver section.  You should have at least 32 megs of shared memory for your video card (64 is better)  Your's is an onboard card right? (Most Sis video are...)

And copy the above precompiled driver into

usr/X11R6/lib/modules/dri/sis_dri.so



I get pretty crappy acceleration because it is a pretty crappy technology, but it works and I can play tuxracer...[/QUOTE]
 Just where in my /etc/X11/xorg.conf am I to add "MaxXFBMem" "12288" ??

---

### Post by bored2k on 2005-07-13
[QUOTE=azz]Xorg uses 

usr/X11R6/lib/modules/dri

So, no it is not a problem.  Freedesktop.org _is_ xorg.

Do you have build-essential installed?

**edit**  I got SiS dri working without compiling anything for my kernel.  The SiS driver does not use sisfb...  I would suggest you try the updated package from Sir Winihopher.[/QUOTE]
 Yes i have build-essential.

---

### Post by bored2k on 2005-07-13
[QUOTE=arnieboy]do u have linux-image-2.6.10-5-686 installed as well? if not install that and then reboot into the 686 kernel image from grub (which will get auto created). Now remove linux-image-2.6.10-5-386 image from synaptic after u reboot and then try installing the script. make sure u also have linux-headers-2.6.10-5.386 removed as well.[/QUOTE]
 Yes I have done that.

---

### Post by arnieboy on 2005-07-13
[QUOTE=bored2k]Yes I have done that.[/QUOTE]
The only possible reason that I can think of is that u have an intel processor with hyperthreading. if thats the case, read the first post on this thread that I have edited and updated. or else am out of ideas.. i havent tested this on any sis chipset because i dont have one and hence cant simulate your problem. sorry about that.

---

### Post by bored2k on 2005-07-13
[QUOTE=arnieboy]The only possible reason that I can think of is that u have an intel processor with hyperthreading. if thats the case, read the first post on this thread that I have edited and updated. or else am out of ideas.. i havent tested this on any sis chipset because i dont have one and hence cant simulate your problem. sorry about that.[/QUOTE]
 Intel yes. HT no.

Azz, is this the way my xorg.conf is supposed to look when after tweaking it?
> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
        MaxXFBMem "12288"
EndSection?

Edit: I just broke X. I got it back, but that was scary. Help  on 3d setup ?

---

### Post by az on 2005-07-13
[QUOTE=bored2k]Intel yes. HT no.

Azz, is this the way my xorg.conf is supposed to look when after tweaking it?
?

Edit: I just broke X. I got it back, but that was scary. Help  on 3d setup ?[/QUOTE]

Yes. That is correct.

What broke X? How did you get it back?

---

### Post by brian.reading on 2005-07-15
[QUOTE=arnieboy]its possibly because of the new kernel. u shd try and recompile vlc and realplayer. or just reinstall them.[/QUOTE]
It appears that doing a complete uninstall in Synaptic and then reinstalling has no effect.  I can't play DVD's anymore either.  It seems MPlayer is the only one that works, but still crashes on DVD's.  I sort of need RealPlayer too.  Anyone else with any further ideas? It only happens when I attempt to play a video file.  Otherwise, the apps seem to open fine.

---

### Post by arnieboy on 2005-07-15
[QUOTE=brian.reading]It appears that doing a complete uninstall in Synaptic and then reinstalling has no effect.  I can't play DVD's anymore either.  It seems MPlayer is the only one that works, but still crashes on DVD's.  I sort of need RealPlayer too.  Anyone else with any further ideas? It only happens when I attempt to play a video file.  Otherwise, the apps seem to open fine.[/QUOTE]
Do u have libdvdcss2 installed? try using totem-xine to play DVD's after u install libdvdcss2 and have the video codecs installed.
sudo apt-get install w32codecs
will install the codecs for u.
also check which video driver u are using. /etc/mplayer/mplayer.conf should have X11 or xv instead of vo.

---

### Post by az on 2005-07-16
[QUOTE=bored2k]Intel yes. HT no.

Azz, is this the way my xorg.conf is supposed to look when after tweaking it?
?

Edit: I just broke X. I got it back, but that was scary. Help  on 3d setup ?[/QUOTE]


Crap!

It is wrong!  It should read:

Option		"MaxXFBMem"	"12288"


Sorry about that.

Also, what kind of SiS chip do you have?  Does it support DRI?

From the site:
[http://www.winischhofer.net/](http://www.winischhofer.net/)

    * DRI ("Direct Rendering Infrastructure") is the basis for OpenGL and hardware 3D acceleration. Without DRI, X.org/XFree86 will use software rendering for OpenGL and 3D which is really slow.
    * The X driver this page is about has nothing to do with DRI. Instead, a separate driver is needed for this feature. This separate driver is developed by the DRI developers. I do not do any DRI related development, hence asking me questions about DRI is useless (and such questions won't be answered).
    * DRI is only supported on the 300 series (300/305, 630, 730). A DRI driver for the SiS 300 series is provided by XFree86 4.1, 4.2(.1), XFree86 4.4 and X.org 6.7.0 and later. XFree86 4.3 does not contain a SiS DRI driver; However, installing the drivers from 4.2(.1) works well.
    * Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number.
    * About XGI: Although there is a binary XGI DRI driver for the Volari Vx chips available from XGI, this DRI driver is not supported in connection with the X driver available here or in X.org/XFree86. Hence there is no DRI/OpenGL/3D support for the XGI Volari V3XT, V5, V8 chips yet, unless you dare to use XGI's "own" X driver which comes with the said binari DRI driver. (The Volari Z7 has no 3D engine, so thinking about DRI is moot.)
    * For a little more information on DRI on the 300 series, see here.






I hope this helps!



ArnieBoy:  You need build-essential to compile the module.  I just tried it for the mach64 driver.  This howto can cover the other chipset, too (mga, r200, SiS,...)  Also, you do not need to change your kernel if you run a 386 kernel.  Many machines cannot run anything else...  Just use linux-headers-2.6.10-5-386 which is on the install cd...

This would be a good candidate for the wiki:
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by bored2k on 2005-07-16
> * Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number.
I have a SiS 661FX, so I guess there's no DRI for me.

---

### Post by arnieboy on 2005-07-17
[QUOTE=azz]ArnieBoy:  You need build-essential to compile the module.  I just tried it for the mach64 driver.  This howto can cover the other chipset, too (mga, r200, SiS,...)  Also, you do not need to change your kernel if you run a 386 kernel.  Many machines cannot run anything else...  Just use linux-headers-2.6.10-5-386 which is on the install cd...

This would be a good candidate for the wiki:
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)[/QUOTE]

Azz: I agree with you on certain points: a) we need build-essential. b) We need the 386 kernel for older chipsets. I have edited the HOWTO to incorporate these points. Thanks for pointing them out.
However for newer chipsets, sometimes the 386 headers dont work and compilation errors get thrown up. I have had many users send me messages with the same concern. Upgrading to the 686 kernel for Intel and k7 kernel  for AMD respectively has solved this problem. Also, performance and fps improves quite a bit in most cases by upgrading to the 686 kernel.

---

### Post by =racoon= on 2005-07-25
Hi guys 
first thanks for the How to it is great. But I have a problem.
I did everything you said but the ./install.h gives me a fault:
:
Updating configuration:
        Running ldconfig...     Removing old kernel module "savage"...done
        Inserting new kernel module "savage"...ERROR

dri.log

make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
make[1]: Leaving directory `/home/racoon/dripkg/drm/linux-core'
/usr/X11R6/lib
WARNING: Error inserting drm (/lib/modules/2.6.10-5-686/kernel/drivers/char/drm/drm.ko): Invalid module format
FATAL: Error inserting savage (/lib/modules/2.6.10-5-686/kernel/drivers/char/drm/savage.ko): Invalid module format

I hope you can help me.

THx

racoon

---

### Post by arnieboy on 2005-07-26
[QUOTE==racoon=]Hi guys 
first thanks for the How to it is great. But I have a problem.
I did everything you said but the ./install.h gives me a fault:
FATAL: Error inserting savage (/lib/modules/2.6.10-5-686/kernel/drivers/char/drm/savage.ko): Invalid module format

I hope you can help me.

THx

racoon[/QUOTE]

Please paste the contents of *cat /proc/cpuinfo* (type the command in terminal and copy and paste the output that u get in ur reply.

---

### Post by =racoon= on 2005-07-27
Hi
 here is the output of cat /proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 11
model name      : Mobile Intel(R) Pentium(R) III CPU - M  1200MHz
stepping        : 4
cpu MHz         : 1199.167
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 2375.68


But what should the cpu has to do with it? i thought it would be a problem with the kernel or the kernel-source.

thx 

racoon

---

### Post by arnieboy on 2005-07-27
[QUOTE==racoon=]Hi
 here is the output of cat /proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 11
model name      : Mobile Intel(R) Pentium(R) III CPU - M  1200MHz
stepping        : 4
cpu MHz         : 1199.167
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 2375.68


But what should the cpu has to do with it? i thought it would be a problem with the kernel or the kernel-source.

thx 

racoon[/QUOTE]

which kernel image and header source did u install? i wud suggest u go for 686 (without hyperthreading). follow the instructions for doing that in the first post on this thread. i needed ur cpu info to find out which kernel image was suitable for ur machine.

---

### Post by =racoon= on 2005-08-02
Hi

can't anyone Help me ???

cya racoon

---

### Post by arnieboy on 2005-08-02
[QUOTE==racoon=]Hi

can't anyone Help me ???

cya racoon[/QUOTE]
sorry about the late reply.. was out of town.. whats ur video card? I know its savage.. but whats the exact make? also.. u can try with the 386 headers and image instead of the 686 and see if that works for u. install the 386 before u uninstall the 686.

---

### Post by gorkhal on 2005-08-06
woot!!! worked great thanks ppl....

jumped from 120 to 356 in glxgears.....

---

### Post by juanej on 2005-08-11
Im getting the same "DRI drivers can not be installed without the latest kernel modules." error with the last kernel :(

---

### Post by Varox on 2005-08-18
hi, i started using ubuntu yesterday so i don't want to change a thing unless i'm very sure of what i'm doing, so please, can anyone tell me step by step how to enable dri? my pc is a Athlon Thunderbird 800mhz, and the video card is an old Diamond Stealth 3 s540 Xtreme (savage 4 32mb), thanks a lot!!!!  :-P

---

### Post by arnieboy on 2005-08-18
[QUOTE=Varox]hi, i started using ubuntu yesterday so i don't want to change a thing unless i'm very sure of what i'm doing, so please, can anyone tell me step by step how to enable dri? my pc is a Athlon Thunderbird 800mhz, and the video card is an old Diamond Stealth 3 s540 Xtreme (savage 4 32mb), thanks a lot!!!!  :-P[/QUOTE]
The first post (according to me) should be easy enough to understand if you are a beginner/intermediate user. 
If all u know about linux is how to spell it, then you should wait a while and get a little more hands on experience before u start dabbling with 3D acceleration because it would be extremely difficult for you to troubleshoot anything at this stage.

---

### Post by laue on 2005-08-19
You sir, are an angel!

went from 127 to 452 in glxgears! thanks a bunch

---

### Post by qrazi on 2005-08-19
[QUOTE=bored2k]Thanks. I'll try it now and come back in a bit with the results.[/QUOTE]
 maybe a bit off topic, but suppose i want to install another card, do i have to uninstall anything?

---

### Post by TheSavage on 2005-08-19
I'm now stuck at 640x480?

---

### Post by arnieboy on 2005-08-19
[QUOTE=qrazi]maybe a bit off topic, but suppose i want to install another card, do i have to uninstall anything?[/QUOTE]
if u install another card, its drivers will overwrite the kernel modules which this savage driver installed or overwrote. so u dont need to worry.

---

### Post by arnieboy on 2005-08-19
[QUOTE=TheSavage]I'm now stuck at 640x480?[/QUOTE]
Too bad!
Please try to be a little more verbose in explaining your problem. Have u tried to change the resolution to something different?

---

### Post by foxy123 on 2005-08-20
[QUOTE=arnieboy]This is how to do it:
**FOR OLDER INTEL AND AMD CHIPSETS (INTEL 386, 486 ETC.)**
**FOR INTEL 686 CHIPSETS (WITHOUT HYPERTHREADING)**
**FOR INTEL CHIPSETS (WITH HYPERTHREADING)**
[/QUOTE]

Sorry for very stupid question. I've got Intel 2.8GHz processor on my laptop.
```
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Genuine Intel(R) CPU 2.80GHz
stepping        : 9
cpu MHz         : 2798.241
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat p se36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5554.17
``` 

which one is it in the avove classification?

---

### Post by TheSavage on 2005-08-20
[QUOTE=arnieboy]Too bad!
Please try to be a little more verbose in explaining your problem. Have u tried to change the resolution to something different?[/QUOTE]

Hehe, sorry about that.

Actualy, I've try pretty much everything I found on the net, redo my xorg.conf, delete all the other screen resolution that was in it to force 1 in particular ( 1024x768 ), etc...

The last I need to try now is to add my screen statistic into the xorg.conf file (vertical and horizontal refresh) after that I'll see if it's the driver who give me problem or not.

Just to make sure, my CPU is a Celeron 2.4Ghz so I took the step for i686 w/o hyperthread.

Everything else is working perfectly so I'll work my a** off to get my screen resolution back  :razz:

Thanks for the reply, BTW ;-)

---

### Post by foxy123 on 2005-08-20
Just let you all know that this howto worked seamlessly for 915i driver. Maybe it is worth to rename the topic to something like "How to install DRI Open Source Project drivers (Savage, Intel etc)"?

---

### Post by arnieboy on 2005-08-20
[QUOTE=foxy123]Sorry for very stupid question. I've got Intel 2.8GHz processor on my laptop.
```
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Genuine Intel(R) CPU 2.80GHz
stepping        : 9
cpu MHz         : 2798.241
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat p se36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5554.17
``` 

which one is it in the avove classification?[/QUOTE]
FOR INTEL 686 CHIPSETS (WITHOUT HYPERTHREADING)

---

### Post by foxy123 on 2005-08-20
[QUOTE=arnieboy]FOR INTEL 686 CHIPSETS (WITHOUT HYPERTHREADING)[/QUOTE]
thanks a lot...

---

### Post by arnieboy on 2005-08-20
[QUOTE=foxy123]Just let you all know that this howto worked seamlessly for 915i driver. Maybe it is worth to rename the topic to something like "How to install DRI Open Source Project drivers (Savage, Intel etc)"?[/QUOTE]
The DRI project is aimed towards many different cards (the savage group being one of them). The problem is however, that some cards of a group are unsupported... and since I dont own those cards and havent tested them myself, I dont want to be in charge of troubleshooting problems that people might face while using my HowTo with such cards. Thanks for the suggestion though.

---

### Post by Varox on 2005-08-22
hello once again, i succesfully installed dri without problems but when i execute glxgears my computer crashes... i don't know what went wrong.,... hints please

thanks

---

### Post by Varox on 2005-08-22
sorry, i forgot smth.. its a Diamond Stealth 3 Xtreme S540 (Savage4), i did everything on the how-to succesfully but it crashes when a start glxgears. Thanx

---

### Post by Varox on 2005-08-22
i also tried installing the 2.6.11-1-k7 kernel and its headers, (couldn't find restricted modules for this kernel version....) anyway, gnome crashes at start up, right after i log in.... so i'm out of clues... help please

---

### Post by arnieboy on 2005-08-22
[QUOTE=Varox]i also tried installing the 2.6.11-1-k7 kernel and its headers, (couldn't find restricted modules for this kernel version....) anyway, gnome crashes at start up, right after i log in.... so i'm out of clues... help please[/QUOTE]
u did too many things. Please try to be a little more patient and careful next time especially with regard to upgrading kernels outside the official repositories. I cannot help you with kernel 2.6.11 because I havent used it yet. U should not have upgraded so fast. I would have simply asked u to send me ur /etc/X11/xorg.conf and tried to work with u and got to the root of the glxgears crash. anyway, when u get back to the 2.6.10-5 kernel give me a holler.

---

### Post by Varox on 2005-08-22
hi arniboy heres my zorg.conf

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. Savage 4"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x450" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x450" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x450" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x450" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x450" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x450" "640x480"
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



Thanks

---

### Post by arnieboy on 2005-08-22
question 1: which kernel are u running now?  are u back to 2.6.10-5-k7?
question 2: if answer to question 1 is yes, is Gnome still crashing at startup?
question 3: if answer to question 1 is yes,  did u try following the HowTo on how to enable DRI?
question 4: if answer to question 3 is yes, did glxgears crash again?
also please post the contents of cat /proc/cpuinfo

---

### Post by Varox on 2005-08-22
arnyboy: hi, 1) yes i'm back to 2.6.10-5-k7  
                   2)gnome never crashed up at start up on this kernel, only did on kernel 2.6.11
                   3) i followed the how toy exactly as u posted it on kernel 2.6.10-5-k7, i never got to try it on 2.6.11 
                  4) glxgears still crashes, the window opens and right after that CRASH.... 

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 4
model name	: AMD Athlon(tm) Processor
stepping	: 2
cpu MHz		: 802.260
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr pni syscall mmxext 3dnowext 3dnow
bogomips	: 1585.15

Hey, thanks a lot for all the help, i really apreciate it

---

### Post by arnieboy on 2005-08-22
[QUOTE=Varox]arnyboy: hi, 1) yes i'm back to 2.6.10-5-k7  
                   2)gnome never crashed up at start up on this kernel, only did on kernel 2.6.11
                   3) i followed the how toy exactly as u posted it on kernel 2.6.10-5-k7, i never got to try it on 2.6.11 
                  4) glxgears still crashes, the window opens and right after that CRASH.... 

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 4
model name	: AMD Athlon(tm) Processor
stepping	: 2
cpu MHz		: 802.260
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr pni syscall mmxext 3dnowext 3dnow
bogomips	: 1585.15

Hey, thanks a lot for all the help, i really apreciate it[/QUOTE]

Hey no  problem:)
Try changing the line "load dri" to "# load dri" in /etc/X11/xorg.conf .
This line is under section "modules"
try running glxgears again.
also try installing tuxracer by:
```
sudo apt-get install tuxracer
```
and try running it from a terminal and  post the errors that u get if any.
EDIT: restart x server after u make changes to xorg.conf.

---

### Post by Varox on 2005-08-22
I changed the line "load dri" to "# load dri" in /etc/X11/xorg.con andf glxgears runs fine now!, only problem is that it runs at only 148fps... any ideas? another thing: # before load, doesn't this means i will not be using dri?

---

### Post by arnieboy on 2005-08-22
[QUOTE=Varox]I changed the line "load dri" to "# load dri" in /etc/X11/xorg.con andf glxgears runs fine now!, only problem is that it runs at only 148fps... any ideas? another thing: # before load, doesn't this means i will not be using dri?[/QUOTE]
try and install the Savage drivers again with the HowTo without changing xorg.conf and tell me if u see any improvement in FPS.

---

### Post by Varox on 2005-08-23
> try and install the Savage drivers again with the HowTo without changing xorg.conf and tell me if u see any improvement in FPS. 

no changes at all,i think changes will arrive when i start using dri with out problems... i will never get more than 140fps in software mode...  ... Question: any ideas on making dri work? if I change the line "load dri" to "# load dri" in /etc/X11/xorg.conf as i did, i'm shutting dri down, right? so... i have to find the way to make dri work with out gnome crashing... correct me if i'm wrong please, and thanks again

---

### Post by arnieboy on 2005-08-23
[QUOTE=Varox]no changes at all,i think changes will arrive when i start using dri with out problems... i will never get more than 140fps in software mode...  ... Question: any ideas on making dri work? if I change the line "load dri" to "# load dri" in /etc/X11/xorg.conf as i did, i'm shutting dri down, right? so... i have to find the way to make dri work with out gnome crashing... correct me if i'm wrong please, and thanks again[/QUOTE]
yes when u add a "#" u are commenting a line and hence DRI does not get loaded. i wanted to see if the savage drivers automatically altered the xorg.conf file or not. since its not and u are saying the installation of the DRI drivers is going flawlessly, my immediate conclusion is that DRI for savage drivers does not support ur specific video card though its a savage card. hence u wud have to do without 3D acceleration till linux comes up with something better in its kernel.

---

### Post by Varox on 2005-08-24
[QUOTE=qrazi]i use a celeron 800@1060MHz. i had the 2.6.10 kernel installed, 386 version. after i replied i did some more google work, and read somewhere that you need to have kernel 2.6.11 installed for it to work. and then i read your tip about the 686 version, so now i am running kernel 2.6.11-686

glxgears was ~130fps, now ~450fps..... still not a lot, but Cube is very playable now. 
and this isnt my game machine anyway, more of a "getting to know linux pc"[/QUOTE]


Hi once again, as you may see grazi made his Diamond Stealth 3 16mb Savage 4 work with kernel 2.6.11, only diference is i'm running an amd athlon not a celeron, so i have to install the 2.6.11 kernel for k7.. and my video card has 32 mb ram, the model is almost the same and the vendor is exactly the same one... do u have any idea where i can get the restricted modules for 2.6.11-1-k7 kernel? or any other idea?

---

### Post by arnieboy on 2005-08-24
[QUOTE=Varox]Hi once again, as you may see grazi made his Diamond Stealth 3 16mb Savage 4 work with kernel 2.6.11, only diference is i'm running an amd athlon not a celeron, so i have to install the 2.6.11 kernel for k7.. and my video card has 32 mb ram, the model is almost the same and the vendor is exactly the same one... do u have any idea where i can get the restricted modules for 2.6.11-1-k7 kernel? or any other idea?[/QUOTE]
u cannot get the restricted-modules for 2.6.11-1 yet because this package can only be released by ubuntu. u already have got the updated kernel from kernel.org possibly but support packages like restricted modules will only be released by ubuntu. so u gotta wait. i can suggest u do try something else.
but before u do anything, always backup ur /etc/X11/xorg.conf so that it is easy to replace in case things go wrong.
u can try commenting the line "load glx" and uncomment "load dri" and restart xserver and see how it goes.

---

### Post by jmn2k1 on 2005-09-02
Hi!

I have a ProSavage8, an Intel 686 w/o HT, i installed the latest dripkg without errors, until I restart the X server, and it show me a "Frecuency out of range" error from the monitor...
The xorg.conf file is modified by the dri install?? cause still have the mesa driver set...
I changed manually for values like the files that are posted here.

Any idea of what can i do??

Thanks!

---

### Post by arnieboy on 2005-09-02
[QUOTE=jmn2k1]Hi!

I have a ProSavage8, an Intel 686 w/o HT, i installed the latest dripkg without errors, until I restart the X server, and it show me a "Frecuency out of range" error from the monitor...
The xorg.conf file is modified by the dri install?? cause still have the mesa driver set...
I changed manually for values like the files that are posted here.

Any idea of what can i do??

Thanks![/QUOTE]
what values did u change? its possible that your horizontal and vertical refresh rates are screwed up. look for the section "monitor" in /etc/X11/xorg.conf and correct your vertical and horizontal refresh rates according to those given in the monitor manual.
use "nano" as the command line editor.
do a :
```
sudo nano /etc/X11/xorg.conf
```
and then make the changes.

---

### Post by jmn2k1 on 2005-09-03
Thanks for your reply!

I only change the "device" and "module" sections, and use the same values for monitor each time (when works fine w/o the acceleration and when it gives the error), this is the values I have in my xorg.conf:

```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

#Section "Module"
#       Load    "GLcore"
#       Load    "bitmap"
#       Load    "dbe"
#       Load    "dri"
#       Load    "extmod"
#       Load    "freetype"
#       Load    "glx"
#       Load    "int10"
#       Load    "pex5"
#       Load    "record"
#       Load    "speedo"
#       Load    "type1"
#       Load    "vbe"
#       Load    "xie"
#EndSection

#Section "Device"
#	Identifier "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
#	Driver "savage"
#	BusID "PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"    
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

```

The commented lines are the ones I change... I try switching between the commented lines... but only works with vesa driver.

---

### Post by arnieboy on 2005-09-03
[QUOTE=jmn2k1]Thanks for your reply!

I only change the "device" and "module" sections, and use the same values for monitor each time (when works fine w/o the acceleration and when it gives the error), this is the values I have in my xorg.conf:

```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

#Section "Module"
#       Load    "GLcore"
#       Load    "bitmap"
#       Load    "dbe"
#       Load    "dri"
#       Load    "extmod"
#       Load    "freetype"
#       Load    "glx"
#       Load    "int10"
#       Load    "pex5"
#       Load    "record"
#       Load    "speedo"
#       Load    "type1"
#       Load    "vbe"
#       Load    "xie"
#EndSection

#Section "Device"
#	Identifier "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
#	Driver "savage"
#	BusID "PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"    
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

```

The commented lines are the ones I change... I try switching between the commented lines... but only works with vesa driver.[/QUOTE]
well for one thing, u should not have changed anything manually, because the HowTo does not ask u to. u should try overwriting the current xorg.conf with the previous version (the one that was there before u installed the DRI drivers) and then install the DRI modules again as explained in my Howto. then see how it goes.

---

### Post by jmn2k1 on 2005-09-09
[QUOTE=arnieboy]well for one thing, u should not have changed anything manually, because the HowTo does not ask u to. u should try overwriting the current xorg.conf with the previous version (the one that was there before u installed the DRI drivers) and then install the DRI modules again as explained in my Howto. then see how it goes.[/QUOTE]

I overwrite my xorg.conf with a previous one, then I follow the how-to step by step and theres is no errors... but the dri is no loaded, and the xorg.conf file has no change...

---

### Post by mthaddon on 2005-09-21
I've read through all the posts and am hoping someone can help me out. I had started a separate thread because I was having glxgears problems, but now I think it's more appropriate here ([http://ubuntuforums.org/showthread.php?t=67518](http://ubuntuforums.org/showthread.php?t=67518) ).

Basically, I've installed dri according to the how to in the first post, and everything seems to be working okay, except that I'm only getting about 140fps from glxgears. Unfortunately I have no readings from glxgears from before I installed dri (as I was having problems with it), but in any case, for the specs of my machine (not the one in my sig - specs below), I think this FPS is very slow. TuxRacer is unusably slow... Oh, and I'm using Breezy Badger...

I have a S3 Inc. ProSavage KM133 (rev 03) (according to lspci), and installed the DRI packages from the dri website common-20050718-linux.i386.tar.bz2 and savage-20050718-linux.i386.tar.bz2. 

I don't think this is how it should be, since dmesg | grep agp gives me:
[4294741.350000] Linux agpgart interface v0.101 (c) Dave Jones
[4294741.366000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[4294741.396000] agpgart: AGP aperture is 64M @ 0xe0000000
[4295113.338000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4295113.338000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4295113.338000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

(i.e. I think I should be getting up to 64MB of shared video memory).

My cat /proc/cpuinfo is:
processor : 0
vendor_id : AuthenticAMD
cpu family : 6
model : 8
model name : AMD Athlon(tm) XP 1700+
stepping : 0
cpu MHz : 1467.174
cache size : 256 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips : 2899.96

And I'm running this kernel: Linux ubuntu 2.6.12-8-k7 #1 Thu Sep 15 22:09:23 UTC 2005 i686 GNU/Linux.

Any help appreciated.

Thanks, Tom

---

### Post by ted209 on 2005-10-09
Edit: Sorry - my mistake here.  The HOWTO works as described in the 1st post.

Ed

---

### Post by arnieboy on 2005-10-09
[QUOTE=ted209]I just got this working on my thinkpad T22, but with a small change in the procedure:

press ctrl+alt+f1 before running ./install.sh

this exits the GUI.  By doing this, direct rendering is now set to yes and I get ~450 fps from glxgears.

Read more on my ubuntu thinkpad blog:

[http://ubuntuthinkpad.blogspot.com/]("http://ubuntuthinkpad.blogspot.com/")

Hope that helps someone!
Ed[/QUOTE]
u dont need to necessarily exit GUI to install the DRI modules or to enable DRI in your xorg.conf. a simple x-server restart will get DRI working after u have installed it.

---

### Post by ted209 on 2005-10-09
Ok, I did try without exiting the GUI, but it didn't work.
I am a beginner though, so it may have been something else I did wrong.

I'll try again when I do a fresh install of the final 5.10 and I'll report back!

Thanks for the guide by the way - it's great to have 3D graphics working properly.
One thing I noticed: the gltext screensavers crash after a few seconds on my thinkpad T22 - anyone else experienced this?

Ed

---

### Post by ted209 on 2005-10-14
I just installed this on the final version of 5.10 breezy badger.  Arnieboy is right - you do not need to exit the GUI to install the drivers.  2 things I noticed:

1) For the savage drivers on my IBM T22 laptop, the 20050718 drivers do not work properly, but the 20050714 drivers do.

2) The gltext screensaver freezes my computer (I suspect this is related to this driver, but I'm not sure).

Ed

---

### Post by andres3cv on 2005-10-26
I have follow this steps but for a i915, evrething good except by the resolution i could not change it to 1200x800 that is what i need (acer travelmate 4021wlmi)

---

### Post by buedi on 2005-11-08
I upgraded from Hoary to Breezy today. It comes with Kernel 2.6-12-9-686. When starting the install.sh it stops with the following Error:

> 
Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


So I watched into the dri.log and saw the following Text. I doubt there is a Problem with my GCC Version (when I do a gcc --version I get 4.0 and not 3.4).

> 
ln -s . linux
make -C /lib/modules/2.6.12-9-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Kommando nicht gefunden
make[2]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.12-9-686«
  CC [M]  /home/mine/OperaDownloads/dri/dripkg/drm/linux-core/drm_auth.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/mine/OperaDownloads/dri/dripkg/drm/linux-core/drm_auth.o] Fehler 127
make[2]: *** [_module_/home/mine/OperaDownloads/dri/dripkg/drm/linux-core] Fehler 2
make[2]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.12-9-686«
make[1]: *** [modules] Fehler 2
make[1]: Verlasse Verzeichnis »/home/mine/OperaDownloads/dri/dripkg/drm/linux-core«
make: *** [savage.o] Fehler 2


I just did an Upgrade as it is described in the Wiki and the System works fine so far. So I wonder why the others here with 5.10 could compile the Package. I am sure I did something wrong.

Just to complete the Info: I downloaded the common / savage 20051107 Versions. I hope you can help me.

Thanks in Advance, buedi ;-)

---

### Post by buedi on 2005-11-10
OK, for all boys and girls who find this thread and don´t find an answer, please go to [THIS FAQ]("http://ubuntuforums.org/showthread.php?t=75393&highlight=dri+compil%2A") which I found now too ;)

---

### Post by arnieboy on 2005-11-10
[QUOTE=buedi]I upgraded from Hoary to Breezy today. It comes with Kernel 2.6-12-9-686. When starting the install.sh it stops with the following Error:



So I watched into the dri.log and saw the following Text. I doubt there is a Problem with my GCC Version (when I do a gcc --version I get 4.0 and not 3.4).



I just did an Upgrade as it is described in the Wiki and the System works fine so far. So I wonder why the others here with 5.10 could compile the Package. I am sure I did something wrong.

Just to complete the Info: I downloaded the common / savage 20051107 Versions. I hope you can help me.

Thanks in Advance, buedi ;-)[/QUOTE]
alright try the following before u run **install.sh**
```
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
cd dripkg 
sudo ./install.sh
```
**please follow the steps exactly as mentioned. I am using su (and NOT sudo) for a reason. so plz dont do otherwise.**

---

### Post by foxy123 on 2005-11-10
new snapshots have appeared on [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

I tried to untar the latest ones but they are extracted into different dirs, not dripkg. Should I just copy driver contents to common to merge them?

---

### Post by buedi on 2005-11-10
[QUOTE=foxy123][...]they are extracted into different dirs, not dripkg. Should I just copy driver contents to common to merge them?[/QUOTE]
This is what I did. After sorting out the Problem with my GCC and making all as it was mentioned in the HowTo (I linked to that above) I could compile and install the Version 20051107 (I think this is the newest).

In the end they didn´t work for me, so I used a older version. But I don´t think that it was the problem with the 2 dirs, because compiling / installing worked without an error.

@arnieboy:
Thanks for the Tip, I got it running now. You are great :p

---

### Post by w0rds on 2005-11-24
hi... i can't compile these. :(
i'm on an ibm thinkpad t20 (savage ix) ubuntu 5.04, kernel 2.6.10-5-386.

dri.log:
```

make DRM_MODULES=savage.o modules
make[1]: Entering directory `/home/w0rds/common-20051123-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/home/w0rds/common-20051123-linux.i386/drm/linux-core/Makefile:282: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/w0rds/common-20051123-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/w0rds/common-20051123-linux.i386/drm/linux-core'
make: *** [savage.o] Error 2

```


help anyone?

---

### Post by arnieboy on 2005-11-24
[QUOTE=w0rds]hi... i can't compile these. :(
i'm on an ibm thinkpad t20 (savage ix) ubuntu 5.04, kernel 2.6.10-5-386.

dri.log:
```

make DRM_MODULES=savage.o modules
make[1]: Entering directory `/home/w0rds/common-20051123-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/home/w0rds/common-20051123-linux.i386/drm/linux-core/Makefile:282: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/w0rds/common-20051123-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/w0rds/common-20051123-linux.i386/drm/linux-core'
make: *** [savage.o] Error 2

```
 
help anyone?[/QUOTE]
The error is being thrown because u are using the 386 kernel. U need to upgrade to the 686 kernel (refer to the first post on this thread) to make this work. make sure u delete the dripkg directory in your home folder and redo all the steps again as outlined in the first post for the 686 kernel.

---

### Post by foxy123 on 2005-11-24
[QUOTE=buedi]This is what I did. After sorting out the Problem with my GCC and making all as it was mentioned in the HowTo (I linked to that above) I could compile and install the Version 20051107 (I think this is the newest).

In the end they didn´t work for me, so I used a older version. But I don´t think that it was the problem with the 2 dirs, because compiling / installing worked without an error.

@arnieboy:
Thanks for the Tip, I got it running now. You are great :p[/QUOTE]
as understand the latest snapshots are for xorg 7.0 so they do not work well with Breezy's current 6.8...

---

### Post by w0rds on 2005-11-25
[QUOTE=arnieboy]The error is being thrown because u are using the 386 kernel. U need to upgrade to the 686 kernel (refer to the first post on this thread) to make this work. make sure u delete the dripkg directory in your home folder and redo all the steps again as outlined in the first post for the 686 kernel.[/QUOTE]

sorry for the stupid error. i did it, and managed to compile the modules and install them, but they don't work. 
i still get "direct rendering: No" on glxinfo.

first i tried with a pretty new snapshot (common-20051123-linux.i386.tar.bz2 and savage-20051123-linux.i386.tar.bz2). it compiled and installed ok, but it didn't work. it seems it wasn't loaded or something. and then i tried with some older ones (common-20050707-linux.i386.tar.bz2 and savage-20050718-linux.i386.tar.bz2) and they still don't seem to be loaded when i look at glxinfo. 
any ideas of what it could be?

thanks in advance.

---

### Post by foxy123 on 2005-11-25
[QUOTE=w0rds]sorry for the stupid error. i did it, and managed to compile the modules and install them, but they don't work. 
i still get "direct rendering: No" on glxinfo.

first i tried with a pretty new snapshot (common-20051123-linux.i386.tar.bz2 and savage-20051123-linux.i386.tar.bz2). it compiled and installed ok, but it didn't work. it seems it wasn't loaded or something. and then i tried with some older ones (common-20050707-linux.i386.tar.bz2 and savage-20050718-linux.i386.tar.bz2) and they still don't seem to be loaded when i look at glxinfo. 
any ideas of what it could be?

thanks in advance.[/QUOTE]
I've got a feeling that none of the snapshot after 20050714 will work. I guess they are for X11R6.9/7.0

---

### Post by w0rds on 2005-11-25
[QUOTE=foxy123]I've got a feeling that none of the snapshot after 20050714 will work. I guess they are for X11R6.9/7.0[/QUOTE]

i've been thinking about it too. i'll try something older than that.
thanks :)

---

### Post by w0rds on 2005-11-25
i was taking a look at the xorg logs, and look what i've found:

```

(II) SAVAGE(0): 9348 kB of Videoram needed for 3D; 8192 kB of Videoram available(EE) SAVAGE(0): Insufficient Videoram available for 3D -- Try a lower color depth or smaller desktop.  For integrated savages try increasing the videoram in the BIOS.
(EE) SAVAGE(0): DRI isn't enabled

```

yay. (and i can't increase my vram.)
i just can't understand why it needs 9mb. 
i already tried changing the resolution and color depth, and it still doesn't work.

thanks for the help anyway guys =)

---

### Post by self0 on 2006-02-12
I'm a n00b on this but I do this

[B][I]COMMON FOR ALL CHIPSETS

PHP Code:
sudo apt-get install build-essential
wget [http://dri.freedesktop.org/snapshots/common-20050707-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20050707-linux.i386.tar.bz2)
wget [http://dri.freedesktop.org/snapshots/savage-20050707-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/savage-20050707-linux.i386.tar.bz2)
tar -xjf common-20050707-linux.i386.tar.bz2
tar -xjf savage-20050707-linux.i386.tar.bz2 
cd dripkg[/I][/B]

but when I get to the part of "cd dripkp" it says "bash: cd: dripkp: No such file or directory" where is this folder? or what I'm doing wrong!? helpp

---

### Post by foxy123 on 2006-02-12
I've just upgraded to Dapper and DRI does not work for me. I wonder if I can uninstall previously installed snapshot driver in case there is a conflict between xorg 7.0 and old snapshot.

---

### Post by tormod on 2006-02-19
[QUOTE=foxy123]I've just upgraded to Dapper and DRI does not work for me. I wonder if I can uninstall previously installed snapshot driver in case there is a conflict between xorg 7.0 and old snapshot.[/QUOTE]
Dapper (at least since Flight 2) supports DRI on savage out-of-the-box. Try a fresh install, or apt-get install --reinstall [all the relevant xorg, mesa, glx packages]

---

### Post by nickhuang on 2006-03-09
If I don't have a Internet connection, how should I do?
What packages should I download?

---

### Post by tormod on 2006-03-12
[QUOTE=nickhuang]If I don't have a Internet connection, how should I do?
What packages should I download?[/QUOTE]
You'd better get hold of a CD then. At this time, a few weeks before the final Dapper release, I recommend you to either wait for the release, or if you are a little more daring, get a Dapper Flight 5 CD. Maybe somebody can help you to get a CD.

---

### Post by FloSynergy on 2006-04-04
[QUOTE=azz]No.  It is for Savage chipsets.

For Sis DRI which actually work, check out:
[http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz](http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz)

[http://www.ubuntuforums.org/showpost.php?p=232294&postcount=4](http://www.ubuntuforums.org/showpost.php?p=232294&postcount=4)

With Hoary, all you need to do is add

"MaxXFBMem" "12288"

To your xorg driver section.  You should have at least 32 megs of shared memory for your video card (64 is better)  Your's is an onboard card right? (Most Sis video are...)

And copy the above precompiled driver into

usr/X11R6/lib/modules/dri/sis_dri.so



I get pretty crappy acceleration because it is a pretty crappy technology, but it works and I can play tuxracer...[/QUOTE]


ok,

this sounds good...
i'm trying to reach the point where i can play planeshift and/or eternal lands.
i run a kubuntu linux breezy badger distro on an asus a2 laptop.
the machine has 345mb ram,
with an additional 1gb swap memory partition
an intel celeron 2.4ghz processor
and an audigy zs 2 pcmcia sound card.
on-board graphics card: vga compatible Silicone Integrated Systems 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])

now that i've downloaded winishofer's driver,
how do i install it?

i'm really still quite new at all this, and your posts seem well-researched.

thanks for your help so far...

be well,

flo

---

### Post by MASTo on 2006-06-21
I have 

```
~$ glxinfo |grep direct
direct rendering: Yes
```


but:

```
$ glxgears -printfps
717 frames in 5.0 seconds = 143.315 FPS
844 frames in 5.0 seconds = 168.751 FPS
859 frames in 5.0 seconds = 171.766 FPS
849 frames in 5.0 seconds = 169.686 FPS
852 frames in 5.0 seconds = 170.329 FPS
836 frames in 5.0 seconds = 167.033 FPS
```


any idea?

---

### Post by tormod on 2006-06-22
[QUOTE=MASTo]any idea?[/QUOTE]

Can you attach the output from ```
 LIBGL_DEBUG=verbose glxinfo 
``` (See [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting) for more info)

Exactly which card do you have, and hardware in general (i.e. CPU speed)? What fps values did you get before?

You can also check the DefaultDepth in /etc/X11/xorg.conf: Sometimes 16 works better than 24.

Tormod

---

### Post by Kimmo_S on 2006-07-05
[QUOTE=tormod]You can also check the DefaultDepth in /etc/X11/xorg.conf: Sometimes 16 works better than 24.[/QUOTE]

I have once read that to have OpenGL acceleration, one should use either DefaultDepth 16, or DefaultDepth 24 _and_ DefaultFbBPP 32.  So, this is possibly true, possibly not.

With an IBM Thinkpad T22 (S3 Savage IX-MV with 8MB on-chip memory) I can get direct rendering by
1. setting DefaultDepth to 16
2. making sure the following lines are in the device section of /etc/X11/xorg.conf
```
Option          "ShadowStatus"
Option          "HWcursor"     "false"
Option          "SWcursor"     "true"
Option          "DmaMode"       "none"
Option          "ForcePCImode"
Option          "BusType"       "PCI"
```

Some of these are not strictly necessary.  Removing too many will result in either kind of malfunction: a lockup (or an almost infinite slowdown of the whole system) when any program using OpenGL is started, or a lockup when X is started.  My guesses include that ShadowStatus could be optional.

For some odd reason, glxgears refused to report any FPS.  On another linux in the same machine, with an identical X configuration, I get frame rates in the vicinity of 400 to 500.  glxinfo does report that direct rendering is enabled.

---

### Post by Michele84 on 2007-01-13
Hi. Everytime I found in these forums te correct answer for my problem. First of all thanks to all the people who help the "ignorant" guys like me using ubuntu. This is now my problem.
 I'm using a savage s3 twister video card. Drivers installed. At the beginning everything was good, also the OpenGl. But now, (I don't know what I did... but I did a lot of thing that I don't know! ) the Kinfocenter says: COULD NOT INIZIALIZE OPENGL. Can I come back to te default options? I don't want reinstall all the OS. 
 Please, help!!!
 PS: in /etc/X11/ I have a lot of file xorg.conf.XXXXXXXXXX(date). If I delete all of these??? Yes, I know, I'm terribly ignorant. But I wanna emprove. Thanks

---

### Post by tormod on 2007-01-14
> **Michele84 said:**
> But now, (I don't know what I did... but I did a lot of thing that I don't know! ) the Kinfocenter says: COULD NOT INIZIALIZE OPENGL. Can I come back to te default options? I don't want reinstall all the OS.
If you did a lot of things you don't know, it's not sure it's gonna be easy to fix it :)
You can start by attaching (!) the /etc/X11/xorg.conf and /var/log/Xorg.0.log files here. What version are you running? Have you done updates?
> 
 PS: in /etc/X11/ I have a lot of file xorg.conf.XXXXXXXXXX(date). If I delete all of these??? Yes, I know, I'm terribly ignorant. But I wanna emprove. Thanks

Do not delete these files! They are backup files, from older configurations, and might be handy in such a situation.

---

### Post by Michele84 on 2007-01-15
hi!! thanks for the answer. these are the two files (/etc/X11/xorg.conf and /var/log/Xorg.0.log. I compressed this file 'cause it was too big)
thanks

---

### Post by Michele84 on 2007-01-15
!

---

### Post by Michele84 on 2007-01-15
!

---

### Post by tormod on 2007-01-15
> **Michele84 said:**
>  The file is too long...so I copy it in two post!

That's why I asked you to *attach* the files !:roll: Please edit your posts and remove the long, pasted files and use Attach Files instead. Add a .txt extension to the files if necessary.

---

### Post by Michele84 on 2007-01-19
So?? Any answer?Please...

---

### Post by tormod on 2007-01-19
> **Michele84 said:**
> So?? Any answer?Please...

Thanks for attaching the files, it is much easier to download and compare files this way. I have the same video card, so I can compare them with my own setup. Is this a laptop with shared video memory?

The only difference between your and my xorg.conf is that I have a: **Load "i2c"**

Tormod
ps. Sorry for the late response, but there's no e-mail notification when posts are edited...

---

### Post by tormod on 2007-01-19
Michele,
You have some nvidia glx libraries for some reason. You will have to reinstall the xserver-xorg-core package at least:```
sudo apt-get install --reinstall xserver-xorg-core

```
> (II) Loading /usr/lib/xorg/modules/libglx.so
> (II) Module glx: vendor="NVIDIA Corporation"
>       compiled for 4.0.2, module version = 1.0.8776

BTW, is there any reason you are running the -i386 kernel instead of the -generic kernel?

---

### Post by Michele84 on 2007-01-19
No..I have both -i386 and generic...but (defaults) I use -i386..Do I have to run the generic kernel? Now I try the command: sudo apt-get install --reinstall xserver-xorg-core and I'll post the result.
I don't understand this part of your post:

> (II) Loading /usr/lib/xorg/modules/libglx.so
 > (II) Module glx: vendor="NVIDIA Corporation"
 > compiled for 4.0.2, module version = 1.0.8776

ThankS!!!!!
Michele

---

### Post by Michele84 on 2007-01-19
The problems started when I try to follow this forum (the first post) to enable again opengl...anyway I make sudo apt-get install --reinstall xserver-xorg-core (it installs a packet) and reboot into the generic kernel. Now? IN Kinfo on opengl it says: Could not inizializa opengl.
Thanks so much!

---

### Post by tormod on 2007-01-19
> **Michele84 said:**
> 
I don't understand this part of your post:

> (II) Loading /usr/lib/xorg/modules/libglx.so
 > (II) Module glx: vendor="NVIDIA Corporation"
 > compiled for 4.0.2, module version = 1.0.8776

That was just a snippet from your Xorg.0.log that shows the nvidia modules.

---

### Post by tormod on 2007-01-19
> **Michele84 said:**
> No..I have both -i386 and generic...but (defaults) I use -i386..Do I have to run the generic kernel? 
The standard kernel in edgy is -generic. You may deinstall i386 if you want. On the other hand it shouldn't matter much, just that it can be more complicated to keep everything updated and in order if you have several kernels installed, and debugging doesn't get simpler either.

---

### Post by tormod on 2007-01-19
> **Michele84 said:**
> The problems started when I try to follow this forum (the first post) to enable again opengl...anyway I make sudo apt-get install --reinstall xserver-xorg-core (it installs a packet) and reboot into the generic kernel. Now? IN Kinfo on opengl it says: Could not inizializa opengl.
Thanks so much!
You have a savage card, so you should not use any nvidia or ati packages. If you have reinstalled and rebooted, please attach the new Xorg.0.log

Maybe you have to reinstall more packages, that got broken when you installed the nvidia stuff. Exactly what did you install and how? Which howto did you follow?

---

### Post by Michele84 on 2007-01-19
This is my new Xorg.0.log. 
Of sure I made these commands to enable the DRI:

sudo apt-get install build-essential
wget [http://dri.freedesktop.org/snapshots/common-20050707-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20050707-linux.i386.tar.bz2)
wget [http://dri.freedesktop.org/snapshots/savage-20050707-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/savage-20050707-linux.i386.tar.bz2)
tar -xjf common-20050707-linux.i386.tar.bz2
tar -xjf savage-20050707-linux.i386.tar.bz2 
cd dripkg
sudo ./install.sh

But I had some problems because the folder DRIPKG didn't appear.

If I make glxinfo appears:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

I had a look in Adept. I have this two nvidia packages installed: nvidia-glx (NVIDiA binary XFree86 4.x/X.org driver) and nvidia-common-kernel (NVIDIA binary kernel module common files). I also have installed xserver-xorg-video-ati (X.org X server --ATI display driver) You said that I don't need nvidia and ATi packages, is it? So could be a problem that I have these installed? I have to remove them?

---

### Post by tormod on 2007-01-19
> **Michele84 said:**
> Of sure I made these commands to enable the DRI:
Oh no, those commands were for applying dri-snapshots in Breezy. Those who wrote that should make clear it was for Breezy.

In Dapper and Edgy savage has DRI working out of the box.

> I had a look in Adept. I have this two nvidia packages installed: nvidia-glx (NVIDiA binary XFree86 4.x/X.org driver) and nvidia-common-kernel (NVIDIA binary kernel module common files). I also have installed xserver-xorg-video-ati (X.org X server --ATI display driver) You said that I don't need nvidia and ATi packages, is it? So could be a problem that I have these installed? I have to remove them?

Yes, you can safely uninstall all that nvidia stuff. You can leave xserver-xorg-video-ati as it is,  because it comes with the standard install.

---

### Post by tormod on 2007-01-19
Moderators, why is this HowTo here in "Faqs, Howto, Tips & Tricks"? It is not valid for Dapper and Edgy, and belongs to the Breezy forum.

---

### Post by Michele84 on 2007-01-19
YES YES YES!!
I uninstalled the nvidia packages, I reboot and now in Kinfo Opengl seems to run!!! Thanks!!!
But In the terminal I made glxinfo and appears this:

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI Twister 20050829 AGP 1x
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_env_add,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_texture_mirrored_repeat,
    GL_NV_texgen_reflection, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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
0x42 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


So, direct rending: NO! What can I do??
But one problem is solved. Thanks so much!

---

### Post by tormod on 2007-01-19
> **Michele84 said:**
> So, direct rending: NO! What can I do??
But one problem is solved. Thanks so much!

I think we should move this to the support tracker, instead of spamming this Howto forum more: [https://answers.launchpad.net/ubuntu/+addticket](https://answers.launchpad.net/ubuntu/+addticket)

Attach the Xorg.0.log file again (on launchpad you won't need to add .txt) and also the gldebug.txt file you get from running this:
```
LIBGL_DEBUG=1 glxinfo >gldebug.txt 2>&1
```

---

### Post by Michele84 on 2007-01-19
ok..this is the link: [https://answers.launchpad.net/ubuntu/+ticket/3260](https://answers.launchpad.net/ubuntu/+ticket/3260)

---

### Post by cyberlion on 2007-01-23
Please, sorry my carelessness. But I install the driver of DRI in the Ubuntu Edgy. Now I can remove it... How I make this?!](*,)

---

### Post by cyberlion on 2007-01-23
:D hehehehe I solved my problem... I reinstalled kernel...
but, one problem it continues: In Ubuntu Edgy, my video card (ProSavage8 KM266/KL266) have problem with the glx:  3D driver claims to not support visual 0x42.

This message it appears when I try execute the openoffice, for example. This when the Xserver does not restart.

---

### Post by tormod on 2007-01-24
If you had read through that support ticket, you would have seen that this message is harmless, and has nothing to do with X not restarting.

---

