---
title: "HOWTO: Nvidia 9742 beta drivers in Edgy/Feisty"
date: 2006-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by PriceChild on 2006-11-10
[SIZE=4][B][COLOR=Red][SIZE=5][COLOR=black]UPDATE - Ok consider this guide "working"... its worked for someone other than me :)[/COLOR][/SIZE]

Nvidia's 9742 drivers are BETA... Do NOT use on Production Machines

[/COLOR][/B][/SIZE][COLOR=Red]**> Starting with 1.0-9742, all NV2x & older (NV1x & NVx) GPUs will only be supported in the legacy driver branches (1.0-7184 & 1.0-9629).I.e. if you have one they won't work here.**[/COLOR]
[SIZE=4][B][COLOR=Red] 
[SIZE=3][COLOR=Black]Do not attempt this guide unless you feel competent reinstalling your previous drivers from the cli and recovering from any breakage which may or may not occur.

These instructions worked for me, they may for you, they may not. After all these warnings its not my fault if you get hosed :)
[/COLOR][/SIZE][/COLOR][/B][/SIZE]
Hey there, something's changed with the latest Nvidia 97** drivers to do with dash and bash and things so that they won't install "normally"... I won't bore you :)
[B]
I recommend you already have the latest drivers installed via method 2 from [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
[/B][SIZE=2]If you don't... run [/SIZE]```
[SIZE=-1]sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev pkg-config[/SIZE]
```[SIZE=-1]NOW!!!
&[/SIZE]```
[SIZE=2]sudo nvidia-xconfig[/SIZE]
```[SIZE=2]at the end.[/SIZE]

If you want to install the latest drivers, then head [here]("http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9742.html") for i386 or [here]("http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9742.html") for 64bit. (the instructions below will be for i386... pretty simple to figure out how to alter a line or two for 64bit :) )

download to home.

```
[SIZE=-1]sh ~/NVIDIA-Linux-x86-1.0-9742-pkg1.run --extract-only
cd [/SIZE][SIZE=-1]NVIDIA-Linux-x86-1.0-9742-pkg1/[/SIZE][SIZE=-1]usr/src/nv
gedit conftest.sh[/SIZE]
```[SIZE=-1]Search for the line[/SIZE]>                               if [ "$RET" == "0" ]; thenand replace with>                               if [ "$RET" = "0" ]; thenSave and quit.

Write down the rest of these instructions, as you will have to shutdown the X server and type them in the cli

Ctrl+Alt+F1 and log in
```
sudo /etc/init.d/gdm stop
cd ~/[SIZE=-1]NVIDIA-Linux-x86-1.0-9742-pkg1[/SIZE]
```[SIZE=-1]For i386:[/SIZE]```
[SIZE=-1]sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`[/SIZE]
```[SIZE=-1]For 64bit:[/SIZE]```
[SIZE=-1]sudo ./nvidia-installer -n -s --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`[/SIZE]
```[SIZE=-1]

This *"should" *install the drivers... it takes a minute or two.

If it complains that the nvidia module is already loaded, restart your computer. Don't log in, but Ctrl+Alt+F1 immediately when you see the log in screen and try again.
```
sudo /etc/init.d/gdm restart
```And you should be in business.

Oh I also recommend a quick restart once you know it works :)

Feedback appreciated :)

Pieces picked from [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) & [http://www.nvnews.net/vbulletin/showthread.php?t=79831&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=79831&page=2)
[/SIZE]

---

### Post by ImaMadGoat on 2006-11-10
I'm getting an error. 

unrecognized command '--kernel-source-path=/usr/src/linux-headers-`uname -r`'

Am I supposed to replace '--kernel-source-path' with something else?

Forgive me, I'm a total noob.

I am currently running 9629 with beryl 0.1.1

---

### Post by PriceChild on 2006-11-10
> **ImaMadGoat said:**
> I'm getting an error. 

unrecognized command '--kernel-source-path=/usr/src/linux-headers-`uname -r`'

Am I supposed to replace '--kernel-source-path' with something else?

Forgive me, I'm a total noob.

I am currently running 9629 with beryl 0.1.1Have you got your linux headers installed?

I just retested the command and it works perfectly fine for me.

---

### Post by ImaMadGoat on 2006-11-10
```
sudo apt-get install linux-headers-2.6.17-10-generic
```

got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libimlib2 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by PriceChild on 2006-11-10
Well then i don't know.

You could try it without it maybe... see what happens.
[B]
I DON'T recommend this though[/B], i don't know what will happen either, and you may be stuck having to reinstall your old drivers again.

---

### Post by ImaMadGoat on 2006-11-10
Ok, I was finally able to install kernal sources for 2.6.17-10. 

Ran the command but had a few warnings pop up. I had to reconfigure the xserver with the standard 'nv' driver. I'll post the log when I get back home...had to come to work for a few hours. 

Really liked your previous guide. I hope I can get the new beta in there along with the new beryl.

---

### Post by smeager on 2006-11-11
Well I tried it and well... nope nada;

here is the nvidia-installer.log

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Nov 11 15:55:00 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : /usr/lib/xorg/
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.17-10-generic
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> There appears to already be a driver installed on your system (version: 1.0-
   9629).  As part of installing this driver (version: 1.0-9742), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> Not probing for precompiled kernel interfaces.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.17-10-generic' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.17-10-generic'
-> Kernel output path: '/usr/src/linux-headers-2.6.17-10-generic'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
   rm -f Makefile
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.1
   7-10-generic SYSOUT=/usr/src/linux-headers-2.6.17-10-generic'...
   sh ./conftest.sh "cc" "cc" /usr/src/linux-headers-2.6.17-10-generic /usr/src
   /linux-headers-2.6.17-10-generic cc_sanity_check full_output
   sh ./conftest.sh "cc" "cc" /usr/src/linux-headers-2.6.17-10-generic /usr/src
   /linux-headers-2.6.17-10-generic select_makefile full_output
   make --no-print-directory -f Makefile module
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.17-10-generic SUB
   DIRS=/home/smeager/Downloaded Programs/Nvidia Drivers/Beta/NVIDIA-Linux-x86-
   1.0-9742-pkg1/usr/src/nv modules
   make[2]: *** No rule to make target `Programs/Nvidia'.  Stop.
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

Back to 9626 for me it is since 97** won't install and 9629 doesn't work properly.

---

### Post by User_Program on 2006-11-11
Didn't work for me either.  I got about 4 "Warning" messages the last one being couldn't find modules in usr/lib/xorg and it will install to usr/lib/xorg/modules  or somthing similar to that (it could have also been usr/lib/lib/xorg/modules  sorry didn't write it down)  It also said something in that line line about the pkg config was wrong. Anyone have any ideas?   I have no problem being a guinea pig ;)

I'm using a 6800 GT card  and 2.6.17-10-generic kernel

---

### Post by PriceChild on 2006-11-12
Bit scary that it isn't working for any of you guys...

> $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5600XT/AGP/SSE/3DNOW!
_**OpenGL version string: 2.1.0 NVIDIA [COLOR=Red]97.42[/COLOR]**_
OpenGL extensions:

<<snip>>Definately working for me...

I'm getting someone else to check.

---

### Post by User_Program on 2006-11-12
I'm glad you responded.  
A couple of questions before I give it a go again.  

Should I  uninstall the old drivers also do I have to edit the conftest.sh ? or can I just  
> sudo bash
and install from the nvidia package?

One last thing after reading endless guides for nvidia and edgy well only about 4, I've read on one that I need xserver-xorg-dev granted the guide for the pre releases of edgy just want to make sure.

Thanks in advance!

---

### Post by PriceChild on 2006-11-12
> **User_Program said:**
> I'm glad you responded.  
A couple of questions before I give it a go again.  

Should I  uninstall the old drivers also do I have to edit the conftest.sh ? or can I just  

and install from the nvidia package?

One last thing after reading endless guides for nvidia and edgy well only about 4, I've read on one that I need xserver-xorg-dev granted the guide for the pre releases of edgy just want to make sure.

Thanks in advance!For the first bit, i'm unsure... _This is the method approved by nvidia devs on the forums._ (changing conftest.sh)

Try it and see :)

Ok maybe you need xserver-xorg-dev.... I'll take a look :)

Thanks for info.

---

### Post by PriceChild on 2006-11-12
Yeah you need xserver-xorg-dev.

I mentioned in the guide that i was assuming you had already followed step 2 from the edgy guide.

Added this to the guide.

---

### Post by User_Program on 2006-11-12
See that's what I get for not reading ;) 

It is all working great now thanks for the guide!  Also the sudo bash did NOT work for me I DID have to edit the conftest.sh

Also 

> if [ "$RET" == "0" ]; then

Is on Line 350





name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap,
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6800 GT/AGP/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 97.42

---

### Post by PriceChild on 2006-11-12
> **User_Program said:**
> It is all working great now thanks for the guide!Wahey thanks :)

---

### Post by Marquis_de_Carabas on 2006-11-12
Thanks a lot for this; it worked like a charm! Now I can get my fix of Postal 2 again! :D

---

### Post by smeager on 2006-11-12
You know what is funny. I tried this last night and it wouldn't work for anything and then I couldn't even use the Official Release 9629 because X would crash every time I tried to run a 3d Accelerated app. 

I was almost ready to give up when I decided to give it one more shot and to my surprise it worked. Running fully on 9742 Beta goodness. 

I am surprise though that I get better performance out of beta drivers then release ones. I can run Quake4, Doom III, etc.... without crashing X and being force back to the login screen which was happening with 9629.

Thanks again.

```
glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6800/PCI/SSE2
**[COLOR="Red"]OpenGL version string: 2.1.0 NVIDIA 97.42[/COLOR]**

```

---

### Post by PriceChild on 2006-11-13
Wahey :D
 
Considering this officially working now then :)

---

### Post by ChadMC on 2006-11-13
Thanks for the HowTo!
This driver runs a lot better than the official release on my system. It fixed my choppy HD video playback problem and just runs better overall.

---

### Post by KillerBOB on 2006-11-13
Hi!

You can also repackage the .run installer after you have altered conftest.sh as PriceChild notes in this How-To.

I followed this post on Nvnews [http://www.nvnews.net/vbulletin/showthread.php?t=62021]("http://www.nvnews.net/vbulletin/showthread.php?t=62021") and managed to repackage the installer so I could install the driver as usual after conftest.sh was corrected for dash.

Just follow the instructions for repackaging in the post, just remember to change all instances of "8178" to "9742" and you are set. Oh, and also the "\":s in the instructions aren't supposed to be entered in the terminal, it's just to symbolise that everything after the # is one line.

I hope I made sense, otherwise just tell me and I will try to help

---

### Post by Aditz on 2006-11-13
I manage to install the driver using your guide. Thank you!

---

### Post by ePlus on 2006-11-13
This error has been bugging me for some time now:

> ERROR: The kernel source path '=/usr/src/linux-headers-2.6.17-10-generic' does
       not exist.  Please make sure you have installed the kernel source files
       for your kernel and that they are properly configured; on Red Hat Linux
       systems, for example, be sure you have the 'kernel-source' or
       'kernel-devel' RPM installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' command line option.

I have installed via the Synaptic Package Manager the following:

linux-headers-2.6.17-10-generic
linux-headers-2.6.17-10
kernel-headers-2.4.27-2-386
kernel-headers-2.4.27-2

...Or at least that's what's in /usr/src/. Any help would be greatly apriciated. 


ePlus

---

### Post by Marquis_de_Carabas on 2006-11-15
Okay, this worked perfectly for me until I rebooted, at which point I got an error saying: "API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9742..."

I tried a few things, none of which worked, then came across [this nvnews post]("http://www.nvnews.net/vbulletin/showthread.php?t=72490").

What worked for me was the very last bit:

> you can edit the /etc/default/linux-restricted-modules configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"

Hope this helps if anybody else has similar problems.

---

### Post by the ev on 2006-11-15
Worked like magic.  Thank ye.

---

### Post by whitewizardcoder on 2006-11-15
Do you need to uninstall the restricted modules packages for this to work?  I need them for my wireless card, but I'd love to get the beta driver...

---

### Post by User_Program on 2006-11-15
My linux-restricted-modules are installed and everything is working fine.

---

### Post by MeduZa on 2006-11-16
At last running on 6.10..

The only way that I get the drivers to compile is uninstalling the restricted modules packages, if not, lot of errors or driver different version of X11 happens

Thank for the guide

---

### Post by PriceChild on 2006-11-16
> **whitewizardcoder said:**
> Do you need to uninstall the restricted modules packages for this to work?  I need them for my wireless card, but I'd love to get the beta driver...Follow this post as well...

(it is explained in the UDSF doc)> **Marquis_de_Carabas said:**
> Okay, this worked perfectly for me until I rebooted, at which point I got an error saying: "API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9742..."

I tried a few things, none of which worked, then came across [this nvnews post]("http://www.nvnews.net/vbulletin/showthread.php?t=72490").

What worked for me was the very last bit:
> you can edit the /etc/default/linux-restricted-modules configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"
Hope this helps if anybody else has similar problems.

---

### Post by whitewizardcoder on 2006-11-17
That worked!  Thanks for the guide!

---

### Post by mjpoetic on 2006-11-17
> **whitewizardcoder said:**
> That worked!  Thanks for the guide!

Works for me too.  Just a quick note to everyone.  Make sure you aren't neglecting to use "**[COLOR=SeaGreen]uname -r[/COLOR]**" in the command for the nvidia installer.  That is to say:

```

sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-**[COLOR=SeaGreen]`uname -r`[/COLOR]**
```and **NOT** something like:

```

sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-[COLOR=SeaGreen]**2.6.17-10**[/COLOR]
```I say this because I was just hitting TAB to complete my directory info and it didn't work with the "...2.6.17-10" path (but the `uname -r` did instead).  It seems weird that it didn't though, seeing as how I am using that kernel.

---

### Post by Shinoda on 2006-11-18
> **mjpoetic said:**
> I say this because I was just hitting TAB to complete my directory info and it didn't work with the "...2.6.17-10" path (but the `uname -r` did instead).  It seems weird that it didn't though, seeing as how I am using that kernel.

That's because you've got more than one item (dir/file) in [FONT="Courier New"]/usr/src/[/FONT] starting with [FONT="Courier New"]linux-headers-2.6.17-10[/FONT], and since tabbing can't guess which one you want, it just completes the first (piece of) string that is common to all such items. Double-tab then to display all possibilities.

Additionally, type in a terminal [FONT="Courier New"]uname -r[/FONT], [FONT="Courier New"]echo `uname -r`[/FONT], or [FONT="Courier New"]echo $(uname -r)[/FONT] to see what [FONT="Courier New"]`uname -r`[/FONT] and [FONT="Courier New"]$(uname -r)[/FONT] are replaced with when parsed in a command, and what was missing when you tried using [FONT="Courier New"]linux-headers-2.6.17-10[/FONT] through tabbing (possibly [FONT="Courier New"]-386[/FONT], [FONT="Courier New"]-686[/FONT], [FONT="Courier New"]-generic[/FONT], etc).

---

### Post by mjpoetic on 2006-11-18
Yea, you're right.  I was the one neglecting things ;)  I know about the uname -r command, but forgot the "-386" for my kernel (as I also had the generic one installed)...I am such a noob.

---

### Post by Kalinda on 2006-11-21
When typing that extremely long command into the terminal, it informs me that 'uname -r' is not a recognized command for the nvidia-installer.

Is there another way I should be doing it?

EDIT: Okay, nevermind.. it's working now; I had to enter the name of the kernel header becauise 'uname -r' wouldn't work, which probably wasn't a good idea.. but whatever.

Annnd... the beta driver behaves exactly the same as the 96xx one I was using before, with the annoying stretched movie/DVD aspect ratios *sigh* There's gotta be something wrong with my setup...

EDIT 3: Yeah, something with my setup. It had the monitor all wrong, I think.. it thought it was smaller then it actually was and so it didn't display anamorphic video correctly. Changed it to Generic 1024x768 and all is well :)

---

### Post by Shinoda on 2006-11-21
> **Kalinda said:**
> When typing that extremely long command into the terminal, it informs me that 'uname -r' is not a recognized command for the nvidia-installer.

The characters around [FONT="Courier New"]uname -r[/FONT] are supposed to be graves, not apostrophes, but you can always use [FONT="Courier New"]$(uname -r)[/FONT] instead if you prefer.

---

### Post by KayoPs on 2006-11-21
For all those like me who have an NV2x or older (NV1x & NVx) chipset (I have a GeForce 4 Ti4600), I advise not to use the 1.0-9629 driver but the 1.0-9626 instead, ([Can be found here](http://www.nvidia.com/object/linux_display_ia32_1.0-9626.html), the link is actually for x86 arch... you'll have to google for a 64bit version).
In fact with the *9629 i had a segfault on every glx app i tried to use, even glxinfo.
Using the *9626 beta driver seems to fix the problem and i am now using beryl without a glitch :P ([Used your guide PriceChild]("http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+edgy"), thx for such good guides. Just skip the "STEP 2: Install nvidia drivers" from that guide if u use this one ;) )

Btw, if you use the 1.0-9626 driver you may want to skip this section aswell:

> **PriceChild]
```
sh ~/NVIDIA-Linux-x86-1.0-9742-pkg1.run --extract-only
cd NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv gedit conftest.sh
```

Search for the line
> if [ "$RET" == "0" ] said:**
> 
and replace with
[QUOTE]if [ "$RET" = "0" ]; then
Save and quit.

Because there's no need to change the file (well, i know i didn't). So you can directly do:
```
sudo sh NVIDIA-Linux-x86-1.0-9742-pkg1.run -n -s --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`
```

If after configuring all and rebooting if you have an X crash and the reason is that there is a version mismatch, just follow this:

[QUOTE=Marquis_de_Carabas]Okay, this worked perfectly for me until I rebooted, at which point I got an error saying: "API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9742..."

I tried a few things, none of which worked, then came across this nvnews post.

What worked for me was the very last bit:

> you can edit the /etc/default/linux-restricted-modules configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv"
Hope this helps if anybody else has similar problems.[/QUOTE]

The only difference with Marquis was that the file i had to edit is located in:
```
/etc/default/linux-restricted-modules-common
```

Worked well for me, other NV2x chipset users, give feedback plz !!

---

### Post by Jonathan2007 on 2006-11-22
Had a few errors along the way but finally got it working. It gave me some error about couldn't overwrite something .so I think. But I loaded up kdm and it worked and it shows I am running 9742 drivers with Direct Rendering enabled. I loaded up beryl-manager and it works great. I am using Aquamarine and it is so cool. Thanks a ton.

---

### Post by ~LoKe on 2006-11-22
Worked flawlessly for me.

---

### Post by neymac on 2006-11-23
Thanks. It worked at first try!
With this nvidia beta driver I can use beryl without XGL.

---

### Post by zelcom@gmail.com on 2006-11-26
Hi! I'm pretty new to (k)ubuntu.
I tried the 9742 driver after this how-to, and it worked very well. I did all the steps to the "sudo /etc/init.d/kdm restart" (KDM, because I'm running Kubuntu. And it loaded the driver nicely. So I tried to check if some of the problems I had with the old driver (believe i had 96** or something) had dissapeard, and it had...

So I was pretty happy that all my problems were gone, ***BUT*** when i rebooted my computer, (as the guide recommended me to do), it had problems running KDM, and I was stuck with "tty1" (ctrl-alt-F1). I tried "kdm restart", but it didn't work. So i tried the long phrase (sudo ./nvidia-installer -n -s ... ...), and then took an kdm-restart, and it worked again, but on reboot, i was stuck in the same situation again. I've also tried to run "sudo nvidia-xconfig", to make it write a new xorg.conf, but it didn't help.

I really love the driver, so I'll rather boot up and "install the driver" every time, than using some of the older ones. But of course I love to get this working so I don't have to do this every time i boot my system. 

Any thoughts on how to fix this problem. Some specs:
AMD XP 64bit 3500+
Gainward GeForce 7800GT
Kubuntu Edgy

BTW.. Is it wrong for me to ask in the ubuntuforum when running kubuntu? Heh, it's just that this forum is WAY better than kubuntu's own forum.

Thanks in advance for all the help i can get!

-- Fredrik

---

### Post by Dagger576 on 2006-11-28
I've not had any luck with installing this driver yet... I just recently started poking around linux and I'm still trying to get the hang of it... I managed to make my way through the guide and everything worked great, until the very last command. When I get to ```
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r'
``` it starts to work correctly but then it says, "Warning: You do not appear to have an nvidia GPU supported by the 1.0-9742 nvidia linux graphics driver installed in this system..." Then a little further down, "Error: Kernel Source Path '/usr/src/linux-headers-uname-r' does not exist."

Anyone have any ideas?

---

### Post by ~LoKe on 2006-11-28
> **Dagger576 said:**
> I've not had any luck with installing this driver yet... I just recently started poking around linux and I'm still trying to get the hang of it... I managed to make my way through the guide and everything worked great, until the very last command. When I get to ```
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r'
``` it starts to work correctly but then it says, "Warning: You do not appear to have an nvidia GPU supported by the 1.0-9742 nvidia linux graphics driver installed in this system..." Then a little further down, "Error: Kernel Source Path '/usr/src/linux-headers-uname-r' does not exist."

Anyone have any ideas?

```
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`
```
Try that.

---

### Post by Dagger576 on 2006-11-29
Good call, Loke... I managed to proceed past that point but was immediately halted by "unable to load kernel module 'nvidia.ko'"

---

### Post by lakersforce on 2006-11-29
When I write ..."/linux-headers-'uname -r'" it says that the path'/usr/src/linux-headers-uname -r' does not exist (please note the difference in what I wrote and what the program outputs). Then, instead of 'uname -r', I used 2.6.17-10-386 (which is what "uname -r" outputs at a terminal), thereby getting further in the installation. But then it halts at "unable to load kernel module 'nvidia.ko'"

---

### Post by lakersforce on 2006-11-29
I got the line working with $(uname -r) instead, but it still complains about the 'nvidia.ko' thing. Does this mean I'll have to recompile my linux kernel? And if that is the case, how does one do that?

---

### Post by mjpoetic on 2006-11-29
> **lakersforce said:**
> I got the line working with $(uname -r) instead, but it still complains about the 'nvidia.ko' thing. Does this mean I'll have to recompile my linux kernel? And if that is the case, how does one do that?

I am sure I have read of the solution to this somewhere.  Just doing a quick google of the "nvidia.ko" search term pulled up this page on NVIDIA's forums (where linux users are very present):

[http://www.nvnews.net/vbulletin/showthread.php?t=49951](http://www.nvnews.net/vbulletin/showthread.php?t=49951)

It basically says to make sure you are using the latest gcc version for installing the NVIDIA drivers (i.e., later than gcc 3.3).  At least that's what a quick read of that link seemed like it was saying.

So try to install the latest gcc, install the driver again, and maybe this will go away.  Also, check this page (as it may help):

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by Dagger576 on 2006-11-29
I've tried a couple other things and discovered that running glxgears and glxinfo results in an empty box opening then a crash. Here's the nvidia-installer.log... any light you guys could provide would be greatly appreciated. 

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Nov 29 00:51:41 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : /usr/lib/xorg
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.19-6-386
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
WARNING: The NVIDIA GeForce4 Ti 4200 GPU installed in this system is supported
         through the NVIDIA legacy Linux graphics drivers.  Please visit
         http://www.nvidia.com/object/unix.html for more information.  The
         1.0-9742 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 1.0-9742
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         www.nvidia.com.
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.19-6-386' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.19-6-386'
-> Kernel output path: '/usr/src/linux-headers-2.6.19-6-386'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
   rm -f Makefile
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.1
   9-6-386 SYSOUT=/usr/src/linux-headers-2.6.19-6-386'...
   sh ./conftest.sh "cc" "cc" /usr/src/linux-headers-2.6.19-6-386 /usr/src/linu
   x-headers-2.6.19-6-386 cc_sanity_check full_output
   sh ./conftest.sh "cc" "cc" /usr/src/linux-headers-2.6.19-6-386 /usr/src/linu
   x-headers-2.6.19-6-386 select_makefile full_output
   make --no-print-directory -f Makefile module
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.19-6-386 SUBDIRS=
   /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.tmp_versions
   rm -f /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.tmp_versions/*
   make -f scripts/Makefile.build obj=/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1
   /usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /home/paul/NVIDIA-L
   inux-x86-1.0-9742-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.nv.o.d  -
   nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Ii
   nclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe 
   -msoft-float -mpreferred-stack-boundary=2  -march=i486 -mtune=generic -mregp
   arm=3 -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG_A
   S_CFI_SIGNAL_FRAME=1 -Iinclude/asm-i386/mach-default -fomit-frame-pointer -f
   asynchronous-unwind-tables  -fno-stack-protector -Wdeclaration-after-stateme
   nt -Wno-pointer-sign -I/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv 
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith  -Wno-multichar  -Werror  -O -fno-common -msoft-float  
       -MD   -Wsign-compare -Wno-cast-qual -Wno-
   error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION
   =1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9742  -UDEBUG -U_DEBUG -DNDEBUG -DNV
   _SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_
   PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI
   _CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOIN
   T_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VM
   AP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv
   )"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /home/paul/NVIDIA-Linux-x86-
   1.0-9742-pkg1/usr/src/nv/.tmp_nv.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1
   /usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-linux.h:19,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.nv-vm.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -
   Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef 
   -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pip
   e -msoft-float -mpreferred-stack-boundary=2  -march=i486 -mtune=generic -mre
   gparm=3 -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG
   _AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-i386/mach-default -fomit-frame-pointer 
   -fasynchronous-unwind-tables  -fno-stack-protector -Wdeclaration-after-state
   ment -Wno-pointer-sign -I/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith  -
   Wno-multichar  -Werror  -O -fno-common -msoft-float       -MD   -Wsign-compa
   re -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -D
   NVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9742  -UDEBUG
   -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESE
   NT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESS
   AGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV
   _OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAG
   E_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_
   BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /ho
   me/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.tmp_nv-vm.o /home/paul/NV
   IDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-linux.h:19,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.os-agp.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__
   -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef
   -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pip
   e -msoft-float -mpreferred-stack-boundary=2  -march=i486 -mtune=generic -mre
   gparm=3 -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG
   _AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-i386/mach-default -fomit-frame-pointer 
   -fasynchronous-unwind-tables  -fno-stack-protector -Wdeclaration-after-state
   ment -Wno-pointer-sign -I/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg
   1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscri
   pts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror  -O -fno-common -
   msoft-float       -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KE
   RNEL_NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VER
   SION=0 -DNV_PATCHLEVEL=9742  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RL
   IM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSC
   TL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRE
   SENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_RE
   MAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD
   _MODNAME=KBUILD_STR(nvidia)" -c -o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1
   /usr/src/nv/.tmp_os-agp.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/
   nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-linux.h:19,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/o
   s-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.os-interf
   ace.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KE
   RNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -O2 -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i486 -mtune=gene
   ric -mregparm=3 -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-i386/mach-default -fomit-frame-
   pointer -fasynchronous-unwi
   nd-tables  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-s
   ign -I/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv -Wall -Wimplicit 
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith  -Wno-multichar  -Werror  -O -fno-common -msoft-float       -MD   -Wsign
   -compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODU
   LE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9742  -
   UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGAR
   T_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_
   PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESE
   NT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHA
   NGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvid
   ia)" -c -o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.tmp_os-inte
   rface.o /home/paul/NVIDIA-Linux-x86-
   1.0-9742-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-linux.h:19,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/o
   s-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.os-regist
   ry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -
   Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -
   O2 -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i486 -mtune=gener
   ic -mregparm=3 -ffreestanding -ma
   ccumulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -Ii
   nclude/asm-i386/mach-default -fomit-frame-pointer -fasynchronous-unwind-tabl
   es  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -I/
   home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv -Wall -Wimplicit -Wretur
   n-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -W
   no-multichar  -Werror  -O -fno-common -msoft-float       -MD   -Wsign-compar
   e -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DN
   VRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9742  -UDEBUG 
   -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESE
   NT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESS
   AGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV
   _OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAG
   E_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_
   BASENAME=KBUILD_STR(os_registry)"  -
   D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /home/paul/NVIDIA-Linux-x86-1.0-9
   742-pkg1/usr/src/nv/.tmp_os-registry.o /home/paul/NVIDIA-Linux-x86-1.0-9742-
   pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-linux.h:19,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/o
   s-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.nv-i2c.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__
   -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef
   -Wstrict-prototypes -Wno-trigraphs -fno-st
   rict-aliasing -fno-common -O2 -pipe -msoft-float -mpreferred-stack-boundary=
   2  -march=i486 -mtune=generic -mregparm=3 -ffreestanding -maccumulate-outgoi
   ng-args -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-i386/
   mach-default -fomit-frame-pointer -fasynchronous-unwind-tables  -fno-stack-p
   rotector -Wdeclaration-after-statement -Wno-pointer-sign -I/home/paul/NVIDIA
   -Linux-x86-1.0-9742-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch 
   -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -W
   error  -O -fno-common -msoft-float       -MD   -Wsign-compare -Wno-cast-qual
   -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VE
   RSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9742  -UDEBUG -U_DEBUG -DNDEBUG
   -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CL
   ***_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV
   _PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAK
   POINT_PRESENT -DNV_REMAP_PFN_RANGE
   _PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUI
   LD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUI
   LD_STR(nvidia)" -c -o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.
   tmp_nv-i2c.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-linux.h:19,
                    from /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -m elf_i386 -m elf_i386  -r -o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg
   1/usr/src/nv/nvidia.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-kernel.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nv.o /home/p
   aul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nv-vm.o /home/paul/NVIDIA-Linu
   x-x86-1.0-9742-pkg1/usr/src/nv/os-agp.o /home/paul/NVIDIA-Linux-x86-1.0-9742
   -pkg1/usr/src/nv/os-interface.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/us
   r/src/nv/os-registry.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/
   nv-i2c.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.19-6-386/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.19-6-386/Module.sy
   mvers -I /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/Module.symvers
   -o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/Module.symvers -w  /
   home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nvidia.o
   WARNING: could not find /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv
   /.nv-kernel.o.cmd for /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   v-kernel.o
     cc -Wp,-MD,/home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/.nvidia.mo
   d.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERN
   EL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -W
   undef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O
   2 -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i486 -mtune=generi
   c -mregparm=3 -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 -D
   CONFIG_AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-i386/mach-default -fomit-frame-po
   inter -fasynchronous-unwind-tables  -fno-stack-protector -Wdeclaration-after
   -statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUI
   LD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /h
   ome/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nvidia.mod.o /home/paul/N
   VIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1
   /usr/src/nv/nvidia.ko /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/n
   vidia.o /home/paul/NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   53.744574] ibm_acpi: ec object not found
   [   53.799461] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
   [   54.942303] eth0: no IPv6 routers present
   [   56.456049] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
   [   56.456064] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
   [   56.456118] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
   [   57.698405] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
   [   57.698411] apm: overridden by ACPI.
   [   61.890682] Bluetooth: Core ver 2.11
   [   61.890739] NET: Registered protocol family 31
   [   61.890741] Bluetooth: HCI device and connection manager initialized
   [   61.890745] Bluetooth: HCI socket layer initialized
   [   61.931508] Bluetooth: L2CAP ver 2.8
   [   61.931512] Bluetooth: L2CAP socket layer initialized
   [   61.934315] Bluetooth: RFCOMM socket layer initialized
   [   61.934331] Bluetooth: RFCOMM TTY layer initialized
   [   61.934334] Bluetooth: RFCOMM ver 1.8
   [  155.761349] ISO 9660 Extensions: Microsoft Joliet Level 1
   [  155.848331] ISOFS: changing to secondary root
   [  234.641961] NVRM: The NVIDIA GeForce4 Ti 4200 GPU installed in this
   system is
   [  234.641964] NVRM:  supported through the NVIDIA Legacy drivers. Please
   [  234.641966] NVRM:  visit http://www.nvidia.com/object/unix.html for more
   [  234.641968] NVRM:  information.  The 1.0-9742 NVIDIA driver will ignore
   [  234.641970] NVRM:  this GPU.  Continuing probe...
   [  234.642828] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by dragonfyre13 on 2006-12-01
Wow! Snappy, responsive, beautiful. The HOWTO worked great! Thanks!

Also, now I can run Full Screen OpenGL apps again. Finally!

---

### Post by slimdog360 on 2006-12-03
Now not only does the beta driver not work but I cant get any other Nvidia driver working.

edit: okay I managed to get the Nvidia non-beta driver from their site version 1.0-9629.  It was pretty easy really, all I done was shut down kdm and run it. This has never worked in the past. But it still didnt fix what I wanted to use the beta driver for, getting enemy territory working. Oh well, I guess Im just not meant to play it.

---

### Post by smartbei on 2006-12-06
I followed the howto, and the beta driver works well, 
```
OpenGL version string: 2.1.0 NVIDIA 97.42
```
but every time I restart I have to go through the install procedure again. How do I fix this? I seem to recall reading somewhere someone with a similar problem, but I forget the solution he used.

Thanks!

EDIT: I found the other post I recalled - he didn't have a solution. See [This]("http://ubuntuforums.org/showthread.php?t=296933&page=4&highlight=howto+beta+nvidia#post1810020").

EDIT2: I found a proposed solution [Here]("http://ubuntuforums.org/showthread.php?p=1852810"), but it didn't work for me.

EDIT3: I managed to solve the problem by using the solution presented above (in Edit2) but adding 'nv nvidia' instead of just nvidia. Hope this helps someone!

---

### Post by quik77 on 2006-12-07
got it to work on amd64 edgy

did it remotely via ssh too

took me sec at first cause I forgot to change a path the first time though when I was cut and pasting

well it says it works.. don't know till I get home ^^

is their a full list anywhere of changes in this driver or whats improved? or is it just updated to work with the new gpus? checking the forums now for it ^^

---

### Post by JediPottsy on 2006-12-14
I used automatix2 to install drivers, they worked fine. But i want to test these new beta drivers. Put the whole thing into a script:

```

sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev pkg-config
sudo nvidia-xconfig
sh ~/NVIDIA-Linux-x86-1.0-9742-pkg1.run --extract-only
cd NVIDIA-Linux-x86-1.0-9742-pkg1/usr/src/nv
nano conftest.sh

```

then another script

```

sudo /etc/init.d/gdm stop
cd ~/NVIDIA-Linux-x86-1.0-9742-pkg1
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`

sudo /etc/init.d/gdm restart

```

then ran
chmod 755 nvidia_1
chmod 755 nvidia_2

then went ctrl+alt+f1

./nvidia_1

change the line to 
```
if [ "$RET" = "0" ]; then
```

./nvidia_2

however i then get blurscreen and gdm wont start, i have to revert back to the xorg that edgy generated (using "nv" driver). This has happened twice. How do i get them working?

---

### Post by sebi k on 2007-01-01
Hi, thanx for the HOWTO, it worked very well for me the first time.=D> 

Due to kernel update to 2.6.20 i'll do it again.

Just to let you know:
I took 9746 this time, ( hoping its even better :) ) and in this version the step:
> **PriceChild said:**
> 
Search for the line
> if [ "$RET" == "0" ]; then
and replace with
[QUOTE]if [ "$RET" = "0" ]; then
Save and quit.[/QUOTE]is not necessary, its allready changed.
i guess its a typo in the script. ??

Edit:
Yeah, and it works =)

---

### Post by mts-fi on 2007-01-15
I had my nvidia 6600 GT working with these instructions earlier, thank you all for that!

After updating kernel I had to install it all over again...
I had no troubles installing driver again, but it didn't work as smooth as the first time.

As I was searching answers to my broblem I read sebi k's post (earlier in this thread) about 9746 beta driver, had to try that too...

I found it from: [http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)

Feeling a bit fustrated of all that installing and things not working right, i desided to go with nvidias instructions simply "sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run" (I had driver downloated in my home directory).

Followed intructions, and ignored all warnings and errors...

Managed to install nvidia 9746 beta -driver succesfully!!!!

... or did I ??

It looks that everything is working fine now, but I still want to check if the driver is installed properly?

Is there any way to check it?

I hope that someone can help me!

---

### Post by Kobalt on 2007-01-15
I tried to install the drivers as described in the initial HowTo : didn't work (error 896...) :confused: 
So I moved on reading what mts-fi wrote, I tried it (with instructions from the Nvidia website) and it worked like a charm for my Geforce Go 7200 ! :rolleyes: 

I must say I am really astonished by the simplicity of the installer from Nvidia, very simple and clear. And even though it's still a command line thing it's giving you all the infos to proceed ... Bravo Nvidia !

---

### Post by gaspar on 2007-01-24
I´m trying to install the latest drivers after recompilimg my kernel to the latest stable (2.6.19.2), but can´t download the linux-headers... so, I tried with the .run from nvidia site, but it says I need to use the legacy drivers. My question is, I have a NVidia Ti4200 (128 Mb), and with the edgy default kernel, I can get the "latest" drivers, but the .run from Nvidia say I can´t have them? :confused: 
Any ideas?

---

### Post by thomas.curtis on 2007-04-04
My friend.. you are a genius. thanks

---

