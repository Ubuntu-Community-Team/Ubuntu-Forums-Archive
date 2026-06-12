---
title: "HOWTO: NVIDIA driver with Breezy kernels in Hoary"
date: 2005-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-07-29
If you want to install Nvidia driver with the nvidia installer (I've tried v.7667) and you use a kernel from Breezy or you compiled it from Breezy sources in Hoary, then just try this HOWTO.

These instructions are taken from one of kleeman's posts you can find below:
[http://www.ubuntuforums.org/showthread.php?t=39675&page=1&pp=10&highlight=xlibmesa](http://www.ubuntuforums.org/showthread.php?t=39675&page=1&pp=10&highlight=xlibmesa)

All the credits go to him. I've just made a HOWTO out of his post. 
This is the 1st time I write one. I hope it helps you.

Alberto

Make sure you graphic card is not among the ones which are NOT SUPPORTED by looking at the list you will find in the NOTES SECTION *

Download the installer from this page according to your architecture (32bit or 64bit)
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Make sure you have the kernel headers of your current kernel installed (If not just install them).

1) uninstall  nvidia-glx (if you don't have it just go to step 2)
2) then remove the file manually:
	sudo rm /etc/init.d/nvidia-glx
3)the default gcc compiler needs to match the one used by the kernel (gcc-3.4 in my case) so:

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

CC=gcc-3.4 (here you have to put the number of the gcc you used to compile your kernel, which is 3.4 in my case**)

export CC

cd  &#8220;directory where you have the nvidia installer&#8221;

If you have Ubuntu 64bit type: ***
sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run
Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x86-1.0-7667-pkg2.run

If you have Ubuntu 64bit you can't install OpenGL32bit compatibility libraries, so when the installer asks whether to install it just answer no.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf
scroll the file down until you find the line with &#8220;Modules&#8221; and either remove the first 2 lines in red and add Load "glx" or just make it look like this:



Section "Module"
[INDENT]Load	"bitmap"
Load	"dbe"
Load	"ddc"[/INDENT]
[COLOR=Red]#Load	    "dri"[/COLOR]
[COLOR=Red]#Load    &#8220;GLcore&#8221;[/COLOR]
[INDENT]Load	"extmod"
Load	"freetype"
[COLOR=Blue]Load	"glx"[/COLOR]
Load	"int10"
Load	"record"
Load	"type1"
Load	"vbe"[/INDENT]


Then find the section Device and make sure the word I put in red is &#8220;nvidia&#8221;:


Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
	Driver		"[COLOR=Red]nvidia[/COLOR]"
	BusID		"PCI:1:0:0"



CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

/etc/init.d/gdm start (or "kdm start" if you use KDE)

Enjoy!
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[COLOR=Magenta]NOTES SECTION[/COLOR]

* Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.

NVIDIA chip name Device PCI ID
------------------------------- -------------------------------
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153
----------------------------------------------------------------


**If you just downloaded a kernel from Breezy repositories it is likely that you don't have the right GCC installed. So install it in synaptic (perhaps it is 3.4, you'll have to find out)

***the name of the installer may vary:
e.g. it could be NVIDIA-Linux-x86_64-1.0-7667-pkg1.run.

So just put the name of the installer you've downloaded from Nvidia website.
-----------------------------------------------
[COLOR="Red"]PROBLEMS SECTION[/COLOR]

1) If the installer reports that the &#8220;Framebuffer&#8221; kernel module conflicts with the drivers you will have to recompile your kernel and disable this function
Here's a HOWTO for kernel compilation for newbies
[http://www.ubuntuforums.org/showthre...5&page=1&pp=10]("http://www.ubuntuforums.org/showthre...5&page=1&pp=10")

2) If the installer complains in this way (this is an example of part of the error):
...
nvidia: version magic '2.6.10-5-386 preempt 386 gcc-[COLOR="Blue"]3.4[/COLOR]' should be
'2.6.10-5-386 preempt 386 gcc-[COLOR="Red"]3.3[/COLOR]'
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details.
...

This means the installer tries to use gcc-3.4 instead of gcc-3.3(the right one).Type this before launching NVIDIA installer:

CC=gcc-3.3 
export CC

The number of the version of gcc has to be the same as the 2nd one reported in the error by nvidia installer (i.e. the word I put in red instead of the one I put in blue)

then run nvidia installer again.

3) If the installer complains in this way:
...
ERROR: Unable to find the development tool `cc` in your path; please make sure
that you have the package 'gcc' installed. If gcc is installed on your
system, then please check that `cc` is in your PATH.

The user Reid has suggested this solution:

To find out where 'gcc' is located I did:
Code:

which gcc


which returned:
Code:

/usr/bin/gcc


then I made a symbolic link to gcc called cc so programs trying to use 'cc' would get gcc, with this code:
Code:

sudo ln -s /usr/bin/gcc /usr/bin/cc

Then try the installer again.

4) If you have an AGP graphic card and your system freezes but you can still move the mouse pointer you will have to do this:
sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="#ff0000"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

EndSection


This will either disable 3d acceleration or make it slower (sorry but I haven't got an AGP card so I haven't tried them myself)

If this doesn't work for you try asking at this Forum and you might be talking to some of the developers of the NVIDIA drivers (there's a Linux section) (it's very useful)
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

Alberto

---

### Post by haddog on 2005-08-02
This works great. Getting the corect version of gcc is the key. When you run the Nvidia installer, if it fails  because of your version of gcc, it will tell you what version of gcc you need based on what your kernel is compiled with. Make sure to get gcc-X.X and not just gcc-X.X- base.

AMD Sempron 3000
1Gig DDR400 RAM
128 Meg Nvidia Video Card
Ubuntu Linux 5.10 Colony 2
2.6.12-6-386 kernel

---

### Post by grendelkhan on 2005-08-29
I run into issues doing this where the nvidia installer complains about the locations for the kernel source and kernel headers.  Where did you have these installed to and what parameters did you pass to the installer package to get a successful compile?

---

### Post by tseliot on 2005-08-29
[QUOTE=grendelkhan]I run into issues doing this where the nvidia installer complains about the locations for the kernel source and kernel headers.  Where did you have these installed to and what parameters did you pass to the installer package to get a successful compile?[/QUOTE]
Please post the output of the error of the installer after you try ton install the driver.

You can find it under /var/log  the name of the log file contains the word "nvidia"

---

### Post by Twiggy003 on 2005-09-07
Ive had the same problem about the locations for the kernel source and kernel headers. After accepting the agreement and something to do with runlevels.

the log:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Sep  7 12:07:34 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).



please help

---

### Post by tseliot on 2005-09-07
install linux tree in synaptic and make sure you also have kernel headers installed.

---

### Post by Arktis on 2005-09-08
Hi, and thanks for the quick guide.

I'm having some trouble. First I installed gcc-3.4 and it's base with synaptec. I used ctrl+alt+F1 and then did a login as normal user. I stopped gdm with /etc/init.d/gdm stop and then set cc=gcc-3.4 which is what the nvidia installer claims my kernel (2.6.12-8-k7-smp) was compiled with. Then I did export cc and then went to the NVIDIA installer and ran it with sudo sh NVIDIA-blah-blah. The installer still claims that my compiler is set to 4.0.

What am I missing?

Edit: Oh, silly me. I forgot to capitalize CC! It wasn't setting the proper variable without the 'cc' being in caps. Oh well, live and learnux linux. :razz:

[color=red]Also, why does the driver version 7676 not work?  Why are we forced to use the *OLDER* 7667?  Hmmm?[/color]

---

### Post by tseliot on 2005-09-09
[QUOTE=Arktis][color=red]Also, why does the driver version 7676 not work?  Why are we forced to use the *OLDER* 7667?  Hmmm?[/color][/QUOTE]
Because if you go to nvidia forums you can see all the problems they cause. There's no improvement if you don't have a Geforce 7800.

---

### Post by h0tpants on 2005-09-13
i have been trying to get the nvidia drivers installed correctly for a couple days now.  i just found the nvidia driver install guide, which says that i need to exit Xserver and reset default run level...how do i do this??

---

### Post by tseliot on 2005-09-13
[QUOTE=h0tpants]i have been trying to get the nvidia drivers installed correctly for a couple days now.  i just found the nvidia driver install guide, which says that i need to exit Xserver and reset default run level...how do i do this??[/QUOTE]
It suggests to do something about "init3" and "init5": this means the computer will boot without starting the graphical interface (GNOME or KDE). I used that method on PCLinuxOS.

BUT

In Ubuntu (it's written in my guide) you can disable the graphical interface temporarly by doing (when you are using the graphical interface):

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE) (this will stop the graphical interface) (THERE'S NO NEED TO USE INIT3!)

AND

PLEASE, follow EVERY step of the guide.

---

### Post by h0tpants on 2005-09-13
when i enter sudo /etc/init.d/gdm stop it says something about it not being a valid command...but i'm going reinstall ubuntu(again) and try following your guide step by step.  how do i found what gcc version i used, cuz i have no idea?

---

### Post by tseliot on 2005-09-13
[QUOTE=h0tpants]when i enter sudo /etc/init.d/gdm stop it says something about it not being a valid command...but i'm going reinstall ubuntu(again) and try following your guide step by step.  how do i found what gcc version i used, cuz i have no idea?[/QUOTE]
You have to try to install the drivers, then if the installer gives you an error you have to go and see the nvidia log file under /var/log. If you look at the end of the file you will see the error.

For instance:

This is a quotation from my other guide (I suggest you to have a look at it)

 If the installer complains in this way (this is an example of part of the error):
...
nvidia: version magic '2.6.10-5-386 preempt 386 gcc-3.4' should be
'2.6.10-5-386 preempt 386 gcc-3.3'
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details.
...

This means the installer tries to use gcc-3.4 instead of gcc-3.3(the right one).Type this before launching NVIDIA installer:

CC=gcc-3.3 
export CC

The number of the version of gcc has to be the same as the 2nd one reported in the error by nvidia installer (i.e. the word I put in red instead of the one I put in blue)

then run nvidia installer again.

---

### Post by tseliot on 2005-09-13
By the way, why are you using a Breezy kernel?

---

### Post by h0tpants on 2005-09-13
> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Sep 13 20:51:01 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com). 

ok so that is what i got when i followed your guide, i didnt see it complaining about a specific gcc, just that i cant find the cc dev. tool.  what should i do now??

also, is breezy not good or what?

---

### Post by h0tpants on 2005-09-13
i was reading the nvidia driver readme and it was saying that prerelease versions of kernel are NOT supported.

> OS Kernel: Linux version 2.6.12-8-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Debian 3.4.4-6ubuntu6)) #1 Tue Aug 30 22:41:30 BST 2005   

 this is my current kernel version, right?  and if so where do i go to get a supported version of kernel/and how do i install it??  or would it be easier to download the hoary release and install that?

---

### Post by tseliot on 2005-09-13
[QUOTE=h0tpants]i was reading the nvidia driver readme and it was saying that prerelease versions of kernel are NOT supported.

  

 this is my current kernel version, right?  and if so where do i go to get a supported version of kernel/and how do i install it??  or would it be easier to download the hoary release and install that?[/QUOTE]
Breezy is still unstable BUT as you've notice my guide is about "NVIDIA driver with Breezy kernels" and this means it is possible to install them on your current kernel.

Open synaptic, press the search button and type "gcc" in the search field. You will see a list: select all the gcc version you can see in there and then press Apply to install them all.

Then try the installer again and tell me if it complains again (and post the log file again)

---

### Post by h0tpants on 2005-09-13
[PHP]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Sep 13 23:53:38 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).[/PHP] 
so by the time i read your above post i already had Hoary installed.  i installed the upgrades. then i tried installing the drivers, no good. then i did your synaptic stuff and applied them all and the above is what i got.

[PHP]X Window System Version 6.8.2 (Ubuntu 6.8.2-10.1 20050831033957 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.10-5-386 #1 Thu Sep 8 06:18:41 UTC 2005 i686
Build Date: 31 August 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Sep 8 06:18:41 UTC 2005[/PHP]

---

### Post by tseliot on 2005-09-14
install "linux tree" in synaptic and try again

---

### Post by h0tpants on 2005-09-14
okay i did that and it still gave me the same error messages

---

### Post by tseliot on 2005-09-14
[COLOR=Red]did you install kernel headers? [/COLOR]
-------------------------------------------------------------------------------------------------------------------------------
You can do it in this way

uname -r (this will tell you the name and version of the kernel you are using)

Open either Synaptic or Kynaptic

press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-the name you got from uname -r"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

click on the files and select "Mark for installation"

Press the "Apply" button.

You can close Synaptic (or Kynaptic) after it has finished installing the headers.
-------------------------------------------------------------------------------------------------------------------------------

And try the nvidia installer again.

[COLOR=Red]IF IT DOESN'T WORK YET:[/COLOR]

1) Make sure you have all the repositories enabled (see Ubuntu starter's guide)

2) Open Synaptic and install kernel 2.6.11 (image, headers and source)

3) restart your computer (it will boot automatically in the new kernel)

uname -r   (just to see if you are using kernel 2.6.11)

4) follow the guide again

Install the nvidia drivers

Tell me if it works

---

### Post by h0tpants on 2005-09-14
so here is where i am so far...
i installed the kernel header 2.6.10-5-386
installed the drivers successfully
edited the sudo nano /etc/X11/xorg.conf EXACTLY like in your walkthrough
saved&exited
tried to restart gdm and got "I cannot start X server.  It is likely not set up correctly" and asked if i wanted to view the log.
then i rebooted and the same thing happened.

---

### Post by tseliot on 2005-09-14
[QUOTE=h0tpants]so here is where i am so far...
i installed the kernel header 2.6.10-5-386
installed the drivers successfully
edited the sudo nano /etc/X11/xorg.conf EXACTLY like in your walkthrough
saved&exited
tried to restart gdm and got "I cannot start X server.  It is likely not set up correctly" and asked if i wanted to view the log.
then i rebooted and the same thing happened.[/QUOTE]
At least the driver compiled successfully.

sudo nano /etc/X11/xorg.conf
Add the lines in red (NOT the one in blue) at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"[/COLOR]
[COLOR=Blue]Option "Accel" "Off"[/COLOR]
[COLOR=Red]Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

EndSection

ONLY IF it doesn't work you can ADD the LINE IN BLUE

---

### Post by 23meg on 2005-09-14
i did everything as you specified but the installer is still asking me for the kernel source. i'm now manually downloading linux-tree and linux-source packages for 2.6.12-8 .. grrr

---

### Post by h0tpants on 2005-09-14
"At least the driver compiled successfully.

sudo nano /etc/X11/xorg.conf
Add the lines in red (NOT the one in blue) at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" “Off"

i'll try that tomorrow and let you know. thanks.

---

### Post by prelude on 2005-09-15
howdies

first off, great howto. without this I'd still be ripping my hair off my head :D

allthough it works Ive got two questions regarding the xorg.conf file but still very nvidia related and possibly should be added to the howto as 'extra options'.

what do I have to put into this file to make the nvidia driver use the DVI output of my 6600GT card?

```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```
my xorg.conf file seems so 'naked' somehow, Ive seen others posting their configs and theyve got all sorts of options added. is my graphics card working at full 100% performance or are there any tweaks I could try putting in to get the extra punch?

ps. how do I bench my graphics performance?

---

### Post by h0tpants on 2005-09-15
> 
sudo nano /etc/X11/xorg.conf
Add the lines in red (NOT the one in blue) at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" “Off”

EndSection

well tried that without the accel-off option and got the same error message then tried it with the accel-off option and the same thing happened.

---

### Post by tseliot on 2005-09-15
[QUOTE=h0tpants]well tried that without the accel-off option and got the same error message then tried it with the accel-off option and the same thing happened.[/QUOTE]
Is your Geforce FX 5500 a PCI or an AGP card?

I'm asking because I have the AGP version and it works (not only for me) with both "nv" (nvidia opensource drivers) and "nvidia" (proprietary) drivers.

You should ask for help in the Nvidia forums at the Linux section:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) 

You need to register (it's free) and you might get an answer from the developers of the drivers (which are obviously much more qualified than me)

Sorry, pal.

---

### Post by tseliot on 2005-09-15
[QUOTE=prelude]howdies

first off, great howto. without this I'd still be ripping my hair off my head :D

allthough it works Ive got two questions regarding the xorg.conf file but still very nvidia related and possibly should be added to the howto as 'extra options'.

what do I have to put into this file to make the nvidia driver use the DVI output of my 6600GT card?

```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```
my xorg.conf file seems so 'naked' somehow, Ive seen others posting their configs and theyve got all sorts of options added. is my graphics card working at full 100% performance or are there any tweaks I could try putting in to get the extra punch?

ps. how do I bench my graphics performance?[/QUOTE]
I haven't got a DVI monitor but someone has it in this forum. Use the search function and type "nvidia DVI", I'm sure you will find something interesting.

If you want to benchmark your graphic card type "glgears" in the command line.

For any other tweaks I can recommend the "Hoary 5.04 Customization Tips & Tricks" section, it's filled with good guides.

---

### Post by h0tpants on 2005-09-15
> 
Is your Geforce FX 5500 a PCI or an AGP card?

I'm asking because I have the AGP version and it works (not only for me) with both "nv" (nvidia opensource drivers) and "nvidia" (proprietary) drivers.

You should ask for help in the Nvidia forums at the Linux section:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

You need to register (it's free) and you might get an answer from the developers of the drivers (which are obviously much more qualified than me)

Sorry, pal

it's a pci.  i'll try their forums. thanks again for all the help!

---

### Post by prelude on 2005-09-15
[QUOTE=tseliot]I haven't got a DVI monitor but someone has it in this forum. Use the search function and type "nvidia DVI", I'm sure you will find something interesting.

If you want to benchmark your graphic card type "glgears" in the command line.

For any other tweaks I can recommend the "Hoary 5.04 Customization Tips & Tricks" section, it's filled with good guides.[/QUOTE]
 so basically, to get DVI output I need to unplug my vga cable and just leave the DVI in. funny this, it worked with DVI on both VESA and nv driver that came with the install of breezy but the moment I install a up-to-date driver the DVI 'dies'. fine, Ill yank that cable out, dont really need it anyways ;)

**glgears**? I only have gl**x**gears and that gives me no output nomatter how long I run it. are there any commands I should give to it or?

---

### Post by sertmann on 2005-09-21
no source for the 2.6.12-8 breezy kernel eh?


guess i'll just wait until they come out, should be by the finals release...

---

### Post by tseliot on 2005-09-21
[QUOTE=sertmann]no source for the 2.6.12-8 breezy kernel eh?


guess i'll just wait until they come out, should be by the finals release...[/QUOTE]
There is the source and you might as well get the kernel tree (source + patches).

Can you post your repositories? Type:
sudo gedit /etc/apt/sources.list (use kate or nano if you use KDE or something else)

and post the entire file (copy and paste here)

---

### Post by flowerHercules on 2005-09-24
I had a couple notes to add.

There were 7 things I installed to make this work:

gcc-3.4
gcc-3.4-base
make
libc6-dev
linux-kernel-headers
linux-sources
linux-tree

exporting the CC path did nothing for me, so I just made a sym link like so:

ln -s /usr/bin/gcc-3.4 /usr/bin/cc

That worked great.

I also had a bit of trouble killing with gdm stop, so I just used the command:

killall -9 gdm

and killed the X session the standard way. The problem with stopping gdm was that, for some odd reason, it decided to re-initialize itself. Odd, no worries, though.

Other than those things, great HOWTO. I'm actually a Gentoo noob setting up an Ubuntu machine to migrate someone from Windows to Ubuntu, and so far, it has proven very good. It is a lot easier to use than a lot of distributions and it is very clean. Great choice of Gnome over KDE, IMO, very intuitive.

---

### Post by tseliot on 2005-09-24
Thanks for the information!  :)

---

### Post by Owdy on 2005-09-24
N00b quoestion. Why do i wanna install Nvidia drivers like this if drivers come with breezy package. Whats the differense?

---

### Post by tseliot on 2005-09-25
[QUOTE=Owdy]N00b quoestion. Why do i wanna install Nvidia drivers like this if drivers come with breezy package. Whats the differense?[/QUOTE]
The title of my guide is HOWTO: NVIDIA driver with Breezy kernels in [COLOR=Red]Hoary[/COLOR]. The drivers that come with Breezy can't be installed in Hoary (problems with dependencies). BUT you can have drivers 7667 thanks to my guide.

If you use Breezy there is no need to install 7667 using my guide BUT you can use my guide to install other (and newer) versions of the drivers (I don't recommend 7676 though).

---

### Post by TakisX on 2005-09-25
Tseliot finally made it with nvidia drivers.
I installed breezy 5.10
I did not installed drivers with synaptic
I installed 7174 drivers with your how to and its ok 

I compiled the kernel and i installed again 7174 and it works again
Finally everything is ok

---

### Post by tseliot on 2005-09-25
[QUOTE=TakisX]Tseliot finally made it with nvidia drivers.
I installed breezy 5.10
I did not installed drivers with synaptic
I installed 7174 drivers with your how to and its ok 

I compiled the kernel and i installed again 7174 and it works again
Finally everything is ok[/QUOTE]
I'm very happy for you!  :)

---

### Post by NZ-Wanderer on 2005-09-28
Ok, real silly question here... - How do I setup CC in my path (I think this is why my install keeps failing..) - One of the errors I getting is:

> ERROR: Unable to find the development tool `cc` in your path; please make sure that you have the package 'gcc' installed.  If gcc is installed on your system, then please check that `cc` is in your PATH.

---

### Post by tseliot on 2005-09-28
[QUOTE=NZ-Wanderer]Ok, real silly question here... - How do I setup CC in my path (I think this is why my install keeps failing..) - One of the errors I getting is:[/QUOTE]
Open synaptic or kynaptic and type gcc in the search field. You should need gcc and gcc-3.4. Install them (not only the base package). You might want to install "build essential" as well. Then try to install the driver again.

Tell me if it works

---

### Post by NZ-Wanderer on 2005-09-28
well I got a little further this time :)

Got a GCC version check failed this time around...

I have installed 
gcc
gcc 3.3 base
gcc 3.4
gcc 3.4 base
gcc 4.0
gcc 4.0 base

so I think I got all my bases covered (so to speak)

I have been typing in 4.0 as thats what it says I have.. (Can't remember how I got that conclusion tho)

btw, I running breezy, and am wanting to goto the latest drivers, and as was said above this guide is good for that as well.. :)

---

### Post by tseliot on 2005-09-28
[QUOTE=NZ-Wanderer]well I got a little further this time :)

Got a GCC version check failed this time around...

I have installed 
gcc
gcc 3.3 base
gcc 3.4
gcc 3.4 base
gcc 4.0
gcc 4.0 base

so I think I got all my bases covered (so to speak)

I have been typing in 4.0 as thats what it says I have.. (Can't remember how I got that conclusion tho)

btw, I running breezy, and am wanting to goto the latest drivers, and as was said above this guide is good for that as well.. :)[/QUOTE]
could you post your nvidia log file (copy and paste the content here)? you can find it under /var/log

---

### Post by NZ-Wanderer on 2005-09-28
[QUOTE=tseliot]could you post your nvidia log file (copy and paste the content here)? you can find it under /var/log[/QUOTE]

Here it is

[php]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Sep 28 19:04:53 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.12-9-386/build'
-> Performing CC test with CC="gcc4.0".
-> gcc-version-check failed:
   
   ./usr/src/nv/conftest.sh: line 9: gcc4.0: command not found
   Could not compile gcc-version-check.c
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
-> Performing rivafb check.
ERROR: Unable to determine the NVIDIA kernel module filename.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).[/php]

---

### Post by tseliot on 2005-09-28
> **NZ-Wanderer]Here it is

[php]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Sep 28 19:04:53 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel said:**
> ftp://download.nvidia.com)?[/url] (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.12-9-386/build'
-> Performing CC test with CC="gcc4.0".
-> gcc-version-check failed:
   
   ./usr/src/nv/conftest.sh: line 9: gcc4.0: command not found
   Could not compile gcc-version-check.c
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
-> Performing rivafb check.
ERROR: Unable to determine the NVIDIA kernel module filename.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).[/php]
If you did: 

CC=gcc-4.0 
export CC

before trying to install the driver and it didn't work (if you didn't, please TRY it) then you can use this workaround:

sudo ln -s /usr/bin/gcc-4.0 /usr/bin/cc

Then log out or restart the computer (so as to lose the export CC setting)

then try to install the driver [COLOR="Red"][B]WITHOUT USING these lines "CC=gcc-4.0 
export CC"[/B][/COLOR]

Tell me if it works

---

### Post by stanner on 2005-09-28
I was able to get the nvidia driver installed, but for some reason when x starts my screen just goes black

here is a snipit from /var/log/syslog on the crash

Sep 28 13:01:46 localhost gdm[8102]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Sep 28 13:01:49 localhost postfix/master[8355]: daemon started -- version 2.2.4, configuration /etc/postfix
Sep 28 13:01:51 localhost anacron[8652]: Anacron 2.3 started on 2005-09-28
Sep 28 13:01:52 localhost anacron[8652]: Normal exit (0 jobs run)
Sep 28 13:01:52 localhost /usr/sbin/cron[8719]: (CRON) INFO (pidfile fd = 3)
Sep 28 13:01:52 localhost /usr/sbin/cron[8723]: (CRON) STARTUP (fork ok)
Sep 28 13:01:52 localhost /usr/sbin/cron[8723]: (CRON) INFO (Running @reboot jobs)
Sep 28 13:01:52 localhost Xprt_64: No matching visual for __GLcontextMode with visual class = 0 (32775), nplanes = 8

X starts just fine using the NV driver, the nvidia driver worked prior to upgrading to breezy, but I have not been able to get it to work since.  Any help would be much appreciated.

---

### Post by FLeiXiuS on 2005-09-28
Stanner, try re-installing the drivers..

```
sudo CC=gcc-3.4; sudo export CC; sudo sh /path/to/driver.sh
```

I've had this problem in the past.

---

### Post by NZ-Wanderer on 2005-09-28
[QUOTE=tseliot]If you did: 
CC=gcc-4.0 
export CC
before trying to install the driver and it didn't work (if you didn't, please TRY it) then you can use this workaround:
sudo ln -s /usr/bin/gcc-4.0 /usr/bin/cc
Then log out or restart the computer (so as to lose the export CC setting)
then try to install the driver [COLOR="Red"][B]WITHOUT USING these lines "CC=gcc-4.0 
export CC"[/B][/COLOR]
Tell me if it works[/QUOTE]

Oooppps. I made a very STUPID mistake, I had been typing CC=gcc4.0 instead of CC=gcc-4.0
Anyway, I did that and it errored out again, BUT this time it told me my gcc was 3.4, so I changed the line and tried again...
It installed it all perfectly...

BUT (yea there always a but....)

When I rebooted after editing the file as you said in the how-to, loading stops, and I get the following error:

Error: API mismatch: the Nvidia kernel module is version 1.0.7667, but this X module is version 1.0.7676. Please be sure that your kernel module and all Nvidia driver files have the same driver version.
Nvidia(0) Failed to initialize the Nvidia kernel module. Please ensure that there is a supported Nvidia GPU in this system and that the nvidia device files have been created properly.

Help please..

---

### Post by tseliot on 2005-09-29
[QUOTE=NZ-Wanderer]Oooppps. I made a very STUPID mistake, I had been typing CC=gcc4.0 instead of CC=gcc-4.0
Anyway, I did that and it errored out again, BUT this time it told me my gcc was 3.4, so I changed the line and tried again...
It installed it all perfectly...
BUT (yea there always a but....)
When I rebooted after editing the file as you said in the how-to, loading stops, and I get the following error:
Error: API mismatch: the Nvidia kernel module is version 1.0.7667, but this X module is version 1.0.7676. Please be sure that your kernel module and all Nvidia driver files have the same driver version.
Nvidia(0) Failed to initialize the Nvidia kernel module. Please ensure that there is a supported Nvidia GPU in this system and that the nvidia device files have been created properly.
Help please..[/QUOTE]
A previous installation of 7676 is conflicting with 7667. Unless someone has some brilliant idea I think you should try to reinstall Ubuntu.

About the reinstallation I can give you an advice:

When you partition your harddisk make at least 3 partitions:
1) / (root) (my root's size is 10gb)
2) /home/ (this is where you keep your datas)
3) swap

In this way every time you reinstall you will only (you have to choose it manually) overwrite your root partition and keep your files (on home) and (make sure you use the same username as before) the same settings for your internet broweser, email account and messages, etc.

In this way your future reinstallations will be much less painful (a breeze indeed)

---

### Post by NZ-Wanderer on 2005-09-29
thanks for the reply....
I actually have my partitions already laid out how you described, this was the first thing I learnt when I started installing ubuntu...
I think what I will do is try to install the older version of the drivers by following the guide again...
Then when I get back into X see if I can uninstall the old drivers from within Synaptic, and then try the new drivers again :) 
Hope this works :)

Update: I re-ran the guide, and installed the older drivers.. - I am now writing this using Ubuntu :)
Now all I have to do is figure out how to get rid of the drivers I have installed before I try to update to the new ones... (Shouldn't Synaptic be able to handle that?? )

---

### Post by tseliot on 2005-09-29
[QUOTE=NZ-Wanderer]thanks for the reply....
I actually have my partitions already laid out how you described, this was the first thing I learnt when I started installing ubuntu...
I think what I will do is try to install the older version of the drivers by following the guide again...
Then when I get back into X see if I can uninstall the old drivers from within Synaptic, and then try the new drivers again :) 
Hope this works :)
Update: I re-ran the guide, and installed the older drivers.. - I am now writing this using Ubuntu :)
Now all I have to do is figure out how to get rid of the drivers I have installed before I try to update to the new ones... (Shouldn't Synaptic be able to handle that?? )[/QUOTE]
Probably I didn't get you were trying to use 7676 and you had installed 7667 before. I thought it was the other way round.

Why do you want to install 7676? I don't recommend it because its buggy for some cards. (I'm running 7667)

---

### Post by NZ-Wanderer on 2005-09-29
[QUOTE=tseliot]Probably I didn't get you were trying to use 7676 and you had installed 7667 before. I thought it was the other way round.
Why do you want to install 7676? I don't recommend it because its buggy for some cards. (I'm running 7667)[/QUOTE]

Well, lets put it this way, I like to try things out... (thought you might be able to tell that by a newbie running Breezy :)  ) - I have heard both good and bad reports of the new drivers, and thought I would see for myself as I not seen anything mentioned about the FX5900XT which I am running..
Might take your advise tho and stay away from 7676 for now until I do a bit of research over on the Nvidia and Guru3D forums :)

One other little thing I might mention in passing too...
I originally installed the 7667 drivers using Synaptic, and it never installed properly (in the nvidia gui I only had 1 screen of options, not the 1 screen of 9 options I have now after using your guide..) - so your guide installed everything properly whereas Synaptic didn't.

Thanks for all the help and tips etc tho, much appreciated :)

---

### Post by tseliot on 2005-09-29
[QUOTE=NZ-Wanderer]Well, lets put it this way, I like to try things out... (thought you might be able to tell that by a newbie running Breezy :)  ) - I have heard both good and bad reports of the new drivers, and thought I would see for myself as I not seen anything mentioned about the FX5900XT which I am running..
Might take your advise tho and stay away from 7676 for now until I do a bit of research over on the Nvidia and Guru3D forums :)
One other little thing I might mention in passing too...
I originally installed the 7667 drivers using Synaptic, and it never installed properly (in the nvidia gui I only had 1 screen of options, not the 1 screen of 9 options I have now after using your guide..) - so your guide installed everything properly whereas Synaptic didn't.
Thanks for all the help and tips etc tho, much appreciated :)[/QUOTE]
The driver in Synaptic might not work (I haven't tried it myself but I've read some complaints) as Breezy is not the stable version yet. I'm happy the guide worked for you and I look forward to support Breezy users better when Breezy is stable (I'm running Hoary because I need a stable system to write my thesis).

---

### Post by hanover.fiste on 2005-09-30
[QUOTE=tseliot]Because if you go to nvidia forums you can see all the problems they cause. There's no improvement if you don't have a Geforce 7800.[/QUOTE]

If you go to the nvnews forums (nvidia doesn't have any forums of its own), you'll see people having problems with *every* release. And since I do have a 7800, having to recompile my own deb with the 7676 was kind of annoying. I fail to see why both can't be offered. Especially when you look at all the people having problems with xid errors on the 7667.

---

### Post by tseliot on 2005-10-01
[QUOTE=hanover.fiste]If you go to the nvnews forums (nvidia doesn't have any forums of its own), you'll see people having problems with *every* release. And since I do have a 7800, having to recompile my own deb with the 7676 was kind of annoying. I fail to see why both can't be offered. Especially when you look at all the people having problems with xid errors on the 7667.[/QUOTE]
Of course they are not "nvidia forums", I call them in this way so as to be understood.

If you are referring to the drivers in Synaptic I'm not responsible for that. I'm not a developer, I'm just a user like you who wants to make users' life a bit easier.

---

### Post by benjy on 2005-10-03
HI there, first of all tseliot thank you very much for you howto - I learnt a lot!

However... not enough it seems...

After spending quite some time actually getting the nvidia driver to install I finally did - followed all the rest of your instructions to the letter I started gdm.

Only to be faced with a blank white screen... a little demoralising!

My graphics card is an fx 5200 agp. I wanted to use the nvidia drivers as everything is very slow using the nv driver - scrolling down a page in firefox using a fixed background is just embarrassing...

INterestingly - starting ubuntu in recovery mode the white screen changes to the nvidia bootscreen but then hangs all the same.

I'm also running a standard installed breezy (nothing done to it except updated).

To be honest, I don't really know what else you need to know to help me so I hope you can tell me what you need.

Thanks again for the howto :D

---

### Post by tseliot on 2005-10-03
[QUOTE=benjy]HI there, first of all tseliot thank you very much for you howto - I learnt a lot!
However... not enough it seems...
After spending quite some time actually getting the nvidia driver to install I finally did - followed all the rest of your instructions to the letter I started gdm.
Only to be faced with a blank white screen... a little demoralising!
My graphics card is an fx 5200 agp. I wanted to use the nvidia drivers as everything is very slow using the nv driver - scrolling down a page in firefox using a fixed background is just embarrassing...
INterestingly - starting ubuntu in recovery mode the white screen changes to the nvidia bootscreen but then hangs all the same.
I'm also running a standard installed breezy (nothing done to it except updated).
To be honest, I don't really know what else you need to know to help me so I hope you can tell me what you need.
Thanks again for the howto :D[/QUOTE]
Boot in recovery mode
nano /etc/X11/xorg.conf

Add the lines in red (NOT the one in blue) at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"[/COLOR]
[COLOR="Blue"]Option "Accel" "Off"[/COLOR]
[COLOR="#ff0000"]Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

EndSection

ONLY IF it doesn't work you can ADD the LINE IN BLUE

---

### Post by tpischke on 2005-10-03
Probably wishful thinking, but given the frequency of installing the nvidia binary drivers and configuring xorg to work properly, wouldn't it be reasonable to provide some sort of wizard to assist in the installation so people wouldn't have to struggle with this when setting up/upgrading ubuntu?  For instance, the Windows Wireless Drivers utility in Breezy is brilliant.  Would be nice to see something similar for the Nvidia drivers.

I had the drivers working okay under Hoary after a few hours of struggle to get xorg working and to get the correct screen resolutions, but I'm reluctant to keep repeating the process.  I'm sure the time required to develop the wizard would be well rewarded in time/frustration saved by users with an NVIDIA graphics card.

---

### Post by tseliot on 2005-10-04
[QUOTE=tpischke]Probably wishful thinking, but given the frequency of installing the nvidia binary drivers and configuring xorg to work properly, wouldn't it be reasonable to provide some sort of wizard to assist in the installation so people wouldn't have to struggle with this when setting up/upgrading ubuntu?  For instance, the Windows Wireless Drivers utility in Breezy is brilliant.  Would be nice to see something similar for the Nvidia drivers.
I had the drivers working okay under Hoary after a few hours of struggle to get xorg working and to get the correct screen resolutions, but I'm reluctant to keep repeating the process.  I'm sure the time required to develop the wizard would be well rewarded in time/frustration saved by users with an NVIDIA graphics card.[/QUOTE]
It depends on NVIDIA. However there are some unofficial projects ([http://ubuntuforums.org/forumdisplay.php?f=86]("http://ubuntuforums.org/forumdisplay.php?f=86"))  such as Easy Ubuntu and Automatix which can install the drivers (from Ubuntu repositories) from a GUI making the process easier.

---

### Post by FLeiXiuS on 2005-10-04
The only problem I have noticed it performance.  I'm getting poor poor performance now.

---

### Post by stanner on 2005-10-04
[QUOTE=FLeiXiuS]Stanner, try re-installing the drivers..

```
sudo CC=gcc-3.4; sudo export CC; sudo sh /path/to/driver.sh
```

I've had this problem in the past.[/QUOTE]
FLeiXiuS
I have actually tried that a few times with both the 7676 and 7667 driver, I currently have the 7667 driver installed.

---

### Post by tseliot on 2005-10-05
[QUOTE=stanner]FLeiXiuS
I have actually tried that a few times with both the 7676 and 7667 driver, I currently have the 7667 driver installed.[/QUOTE]
Perhaps a clean Breezy installation could solve your problem. I can't support Breezy users 100% until I try Breezy myself (when it is stable).

---

### Post by stanner on 2005-10-05
that might work, however I may just wait until breezy is official, and then give the drivers yet another uninstall/reinstall, until then I will just cope with using the NV drivers.

---

### Post by tseliot on 2005-10-05
[QUOTE=stanner]that might work, however I may just wait until breezy is official, and then give the drivers yet another uninstall/reinstall, until then I will just cope with using the NV drivers.[/QUOTE]
I think it's a wise decision ;)

---

### Post by beta.tester on 2005-10-17
Can anyone please help.

I can get so far but it appears installiny 5.10 (Gnome) and then apt-get install kubuntu-desktop creates problems for stopping X Sessions. It says (In either Gnome or KDE my preference) that is cannot find the x sesssion to stop, ie:

Go into terminal mode and try to stop X Session and it reosrts the relevane (ked or gnome) session not detected.

Any help appreciated as I really would like to get the NVidia driver for my simple FX 5200 installed and 3d enabled for bzflag :)

Pax eet bonuim and many thanks in advance

john

Base line: How can I stop anyu X Session and work in single user mode (ie init 3)

---

### Post by tseliot on 2005-10-17
[QUOTE=beta.tester]Can anyone please help.

I can get so far but it appears installiny 5.10 (Gnome) and then apt-get install kubuntu-desktop creates problems for stopping X Sessions. It says (In either Gnome or KDE my preference) that is cannot find the x sesssion to stop, ie:

Go into terminal mode and try to stop X Session and it reosrts the relevane (ked or gnome) session not detected.

Any help appreciated as I really would like to get the NVidia driver for my simple FX 5200 installed and 3d enabled for bzflag :)

Pax eet bonuim and many thanks in advance

john

Base line: How can I stop anyu X Session and work in single user mode (ie init 3)[/QUOTE]
Try this: 

Ctrl-Alt-F1, log in

and

sudo kill -9 XXX (Xorg PID)

---

### Post by stanner on 2005-10-17
[QUOTE=tseliot]I think it's a wise decision ;)[/QUOTE]
After they official realease of ubuntu 5.10 flatulant ferret, I decided to go ahead and try a reinstall.  Unfortunately I encountered the same problem when trying to startx, the screen froze on a blank screen. :(  Do you have any more tricks or tips that I might try?

---

### Post by tseliot on 2005-10-17
[QUOTE=stanner]After they official realease of ubuntu 5.10 flatulant ferret, I decided to go ahead and try a reinstall.  Unfortunately I encountered the same problem when trying to startx, the screen froze on a blank screen. :(  Do you have any more tricks or tips that I might try?[/QUOTE]
1) What's the model of your graphic card?

2) try this:

sudo nano /etc/X11/xorg.conf

Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
[COLOR="Blue"]Option "Accel" "Off"[/COLOR]
Option "AllowGLXWithComposite" &#8220;Off&#8221;
[/COLOR]
EndSection

And then try to use the nvidia drivers again. If it doesn't work you can try to add the line in blue.

---

### Post by stanner on 2005-10-17
> **tseliot]1) What's the model of your graphic card?

2) try this:

sudo nano /etc/X11/xorg.conf

Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
[COLOR="Blue"]Option "Accel" "Off"[/COLOR]
Option "AllowGLXWithComposite" &#8220 said:**
> 
EndSection

And then try to use the nvidia drivers again. If it doesn't work you can try to add the line in blue.
yeah I tried that and still nothing, I have a GeForce4 440MX, I am thinking that I might just switch back to Sarge, I never really had any video problems in sarge, but I really like the user community around ubuntu.

---

### Post by tseliot on 2005-10-18
[QUOTE=stanner]yeah I tried that and still nothing, I have a GeForce4 440MX, I am thinking that I might just switch back to Sarge, I never really had any video problems in sarge, but I really like the user community around ubuntu.[/QUOTE]
Try EasyUbuntu then

---

### Post by stanner on 2005-10-18
I'll give that a whirl and let you know how it goes.

---

### Post by tseliot on 2005-10-19
[QUOTE=stanner]I'll give that a whirl and let you know how it goes.[/QUOTE]
Another trick (after you have installed the nvidia drivers)
sudo rmmod nvidia
sudo modprobe nvidia

Then the xserver might start

---

### Post by DarkNemesis618 on 2006-04-26
I have Ubuntu 5.10 (2.6.12-10-amd64-generic) and I'm installing the x86_64 8756 nvidia drivers.  It says that my graphics card (nVidia GeForce 7900GT GPU is supported but after the install of the drivers, the X-server won't start.  Attached is the error log for the x server and a text version of my xorg.conf.  Any ideas would be appreciated.  Thanks

---

### Post by tseliot on 2006-04-28
[QUOTE=DarkNemesis618]I have Ubuntu 5.10 (2.6.12-10-amd64-generic) and I'm installing the x86_64 8756 nvidia drivers.  It says that my graphics card (nVidia GeForce 7900GT GPU is supported but after the install of the drivers, the X-server won't start.  Attached is the error log for the x server and a text version of my xorg.conf.  Any ideas would be appreciated.  Thanks[/QUOTE]
Try this guide (which is for Breezy):
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

