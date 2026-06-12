---
title: "Tip: Linux on an IBM T42 - DRI/GL heads up"
date: 2005-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by borzwazie on 2005-04-26
So I just found Ubuntu, and I'm installing it on every piece of hardware I own.

I ran into trouble on Hoary, and I hope I can save someone else some trouble.

Hoary reported that my laptop display chipset was:

ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)

This led me to believe that I could use the ATI fglrx drivers. This is incorrect.

What this really should have been was:

ATI Technologies, Inc. Radeon 7500 Mobility (M7 LW)

This chipset uses the DRI project "radeon" driver. Big difference! I spent some time chasing this problem.

I got the latest snapshot from the DRI website:

[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

and used the following in my xorg.conf (device section):

```

Section "Device"
        Identifier      "Radeon Mobility M7 LW"
        Driver          "radeon"
        VendorName      "ATI Technologies Inc."
        BoardName       "Radeon Mobility M7 LW"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"        "true"
EndSection

```

be sure to add:
     Option "omit xfree86-dga"

to a subsection in Section "Module" as well.

EDIT:

By the way, if you've done all this successfully, by *all* means, download and install DRIConf - I went from about 970 frames/sec in glxgears to 2100 frames/sec!

[http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)

If you are using the latest snapshots from the DRI website, and you're using DriConf to tweak things, be sure to change the TCL mode to "Use software TCL pipeline" - it's much, much faster than the hardware TCL. Also, the hardware TCL displays weird lighting on quads (3d objects flicker and are lighted badly).

Choosing Software TCL gives you by far the biggest performance boost.

Also, be sure to run DriConf as the user that's actually logged in (not just as root!) - it doesn't seem to affect all applications (like screensavers) otherwise.

hope this helps someone!

---

### Post by NeoChaosX on 2005-04-26
[QUOTE=borzwazie]be sure to add:
     Option "omit xfree86-dga"

to a subsection in Section "Module" as well.[/QUOTE]
Can you give an example on how to add a subsection? I tried adding the line to xorg.conf, and when I tried restarting the X server, it wouldn't start.

---

### Post by emendelson on 2005-04-26
Are you able to suspend, sleep, hibernate, etc., with this driver??

---

### Post by NeoChaosX on 2005-04-26
Um, this is about video hardware, not power management. I think the thread creator should've made that a little more clear.

---

### Post by borzwazie on 2005-04-26
I'm not sure about ACPI - I did enable it in the configuration file, but I haven't tried it yet. The release notes at the DRI site might say something about it.

As far as the subsection thing:

```

SubSection "extmod"
              Option "omit xfree86-dga"
EndSubSection

```

This should go in the: Section "Modules"

I put mine right under : Load     "dri"

HTH.

---

### Post by bathala on 2005-04-28
Hello. 

I have an IBM T42 laptop and I followed the publicly available tutorials on how to setup ubuntu on this machine.

The only problem is that when I use th fglrx for my ATI, I'm getting a device not found error. I believe that fglrx is not usable for my machines since I have the following entry in my xorg.conf file:
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection


So I did the following:
1. I've downloaded the file radeon-20050427-linux.i386.tar.bz2
2. Unpacked it in my /root/projects directory
3. I "su" and switched to /root/projects/dripkg and executed ./install.sh

I pressed enter on all the question, taking time to verify that the directories required actually exist in my machine. They do.

Unfortunately, it said that the "kernel did not compile" and the dri.log contains the following:
> 
Makefile:163: *** Cannot find a kernel config file.  Stop.


I actually don't know what do to now. :(

Any help is appreciated. Thanks.

---

### Post by tnilsson on 2005-04-28
[QUOTE=bathala]Hello. 

I have an IBM T42 laptop and I followed the publicly available tutorials on how to setup ubuntu on this machine.

The only problem is that when I use th fglrx for my ATI, I'm getting a device not found error. I believe that fglrx is not usable for my machines since I have the following entry in my xorg.conf file:


So I did the following:
1. I've downloaded the file radeon-20050427-linux.i386.tar.bz2
2. Unpacked it in my /root/projects directory
3. I "su" and switched to /root/projects/dripkg and executed ./install.sh

I pressed enter on all the question, taking time to verify that the directories required actually exist in my machine. They do.

Unfortunately, it said that the "kernel did not compile" and the dri.log contains the following:


I actually don't know what do to now. :(

Any help is appreciated. Thanks.[/QUOTE]
 I just changed my xorg.conf file and it worked fine. I used the radeon driver that was included in Ubuntu Hoary.

---

### Post by kfc on 2005-04-28
[QUOTE=borzwazie]So I just found Ubuntu, and I'm installing it on every piece of hardware I own.

I ran into trouble on Hoary, and I hope I can save someone else some trouble.

Hoary reported that my laptop display chipset was:

ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)

This led me to believe that I could use the ATI fglrx drivers. This is incorrect.

What this really should have been was:

ATI Technologies, Inc. Radeon 7500 Mobility (M7 LW)

This chipset uses the DRI project "radeon" driver. Big difference! I spent some time chasing this problem.

I got the latest snapshot from the DRI website:

[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

and used the following in my xorg.conf (device section):

```

Section "Device"
        Identifier      "Radeon Mobility M7 LW"
        Driver          "radeon"
        VendorName      "ATI Technologies Inc."
        BoardName       "Radeon Mobility M7 LW"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"        "true"
EndSection

```

be sure to add:
     Option "omit xfree86-dga"

to a subsection in Section "Module" as well.

hope this helps someone![/QUOTE]
 can u please give us a little details on which driver to use and the process of installation?
i'm kinda lost here and i don't want to break my system by faulty installations.
Thanks

---

### Post by kfc on 2005-04-28
[QUOTE=bathala]Hello. 

I have an IBM T42 laptop and I followed the publicly available tutorials on how to setup ubuntu on this machine.

The only problem is that when I use th fglrx for my ATI, I'm getting a device not found error. I believe that fglrx is not usable for my machines since I have the following entry in my xorg.conf file:


So I did the following:
1. I've downloaded the file radeon-20050427-linux.i386.tar.bz2
2. Unpacked it in my /root/projects directory
3. I "su" and switched to /root/projects/dripkg and executed ./install.sh

I pressed enter on all the question, taking time to verify that the directories required actually exist in my machine. They do.

Unfortunately, it said that the "kernel did not compile" and the dri.log contains the following:


I actually don't know what do to now. :(

Any help is appreciated. Thanks.[/QUOTE]



I have exactly the same problem.
sigh...
btw, i'm running exactly the same graphic card. It'd be great to have someone to gives us a better guideline other than using the ubuntu ati drivers.
The drivers from ubuntu is fine. But currently i've some problems with it in maya. It just doesn't shows vertices in the correct size. vertices just look too small and it hurts my eye to search for it. but when i disable the default ati ubuntu driver. vertices just looks fine.

Seems like Dri is a good alternative for us. too bad i'm a total noob in this and can't figure out this part. however, i've been following this.
[http://dri.sourceforge.net/doc/DRIbeginner.html](http://dri.sourceforge.net/doc/DRIbeginner.html)

---

### Post by NTolerance on 2005-04-28
I've been through some of this before in another thread, so I'll repost what I did before for reference regarding the DRI drivers:

[quote=NTolerance]I would strongly recommend using the [Debian packages](http://dri.freedesktop.org/wiki/Download#head-0578b19757b79fb1eed3812b628ec6746db4478b) when trying to update the DRI drivers.  I attempted to compile them from source yesterday and got all sorts of cryptic compiler errors that don't mean anything to anybody.  Installing the Debian packages isn't easy either though - they are dependent on several other packages and errors will pop up about the packages not being able to overwrite some of the installed xorg files.  I did some Googling and the 2nd to last suggestion on [this page](http://www.mepis.org/node/2947) helped me to get the packages installed.

Also, at the end of the DRI installation it will ask if you want to compile some stuff for S3TC support.  I could never get this to work, so I had to uninstall and run the setup again without S3TC support.[/quote]

At any rate, these cards should have accelerated 3D with the DRI drivers that are included with Ubuntu.  Run this to check and see if you have accelerated 3D enabled:

```
glxinfo
```

Look for a line at the beginning that says "direct rendering".  If it says yes, then you have accelerated 3D with the built-in Ubuntu DRI drivers.  If your 3D is working at an acceptable level, don't worry about upgrading your DRI drivers.  If you want a speed boost, then get into it and try the Debian packages as I have described above.  

Whether you're using the newer DRI drivers or not, having some options turned on in your xorg.conf will enable some extra features of your card. 

Here's what I have under the modules section:

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
	# new stuff
	Load 	"radeon"
	Load 	"xtrap"
	Load	"drm"
EndSection

```

And this is my "device" section:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	#new stuff
	Option 		"RenderAccel" 		"true"
	Option 		"AGPMode" 		"4"
	Option 		"EnablePageFlip" 	"True"
	Option 		"UseInternalAGPGART" 	"no"
	Option          "backingstore" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

```

[QUOTE=borzwazie]

be sure to add:
     Option "omit xfree86-dga"

to a subsection in Section "Module" as well.

hope this helps someone![/QUOTE]

Can you shed some light on what this setting does?

---

### Post by borzwazie on 2005-04-28
I don't recall exactly - just do a search on it.

By the way, if you've done all this successfully, by *all* means, download and install DRIConf - I went from about 970 frames/sec in glxgears to 2100 frames/sec!

[http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)

---

### Post by borzwazie on 2005-04-28
In DriConf - 

If you are using the latest snapshots from the DRI website, and you're using DriConf to tweak things, be sure to change the TCL mode to "Use software TCL pipeline" - it's much, much faster than the hardware TCL. Also, the hardware TCL displays weird lighting on quads (3d objects flicker and are lighted badly).

This is by far the biggest performance gain.

Also, be sure to run DriConf as the user that's actually logged in (not just as root!) - it doesn't seem to affect all applications (like screensavers) otherwise.

---

### Post by jstreed on 2005-05-05
Here's what I get when I try to install the DRI Snapshot.  I've already gotten my glxgears score up from 400/sec to over 1300/sec just by changing the xorg.conf file as you said.  Unfortunately, all 3d rendering flashes periodically.  I'm hoping the drive upgrade will fix this.  


Thanks for your help



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver:

Driver Name    : radeon
Description    : ATI Radeon Driver
Architecture   :
Build Date     : 20050504
Kernel Module  : radeon

Optional Information

Driver Version      :
Special Description :

Press ENTER to continue or CTRL-C to exit.


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will need to copy the DRI XFree86 driver modules to
your XFree86 directory.

The script will use the following XFree86 directory:

 /usr/X11R6

If this is correct press ENTER, press C to change or CTRL-C to exit.









DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script also needs to copy the DRM kernel modules to your
kernel module directory.

This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.10-5-386
Module Directory : /lib/modules/2.6.10-5-386

If this is correct press ENTER, press C to change or CTRL-C to exit.








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

---

### Post by erzhong on 2005-05-05
Just a reminder: 
To enable hardware rendering, the 'common-20050503-linux.i386.tar.bz2' package should also be downloaded and installed from DRI website.  I did not notice this at first......

---

### Post by bathala on 2005-05-06
First off, I'm no Linux Guru. I'm an Economic Major whos working as a Visual Basic developer. So although I got the DRI to compile with the following steps ... I cannot guarantee that you'll be as lucky as me. ;)

1. Update your APT-GET sources.
- Add the following entries to your "/etc/apt/sources.list". You can do this by opening a terminal and do:
> 
sudo gedit /etc/apt/sources.list

Here are the entries to add:
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse


2. Update your APT-GET cache.
- You can do this by typing the following in the terminal:
> 
sudo apt-get update


3. Get the Kernel Headers and Build Depency
- This is what your system really needs so that you can compile the DRI module
> 
sudo apt-get install build-essential linux-headers-$(uname -r) autoconf automake libtool flex bison

NOTE: Please have your Ubuntu linux installer CD on hand before doing this. It is needed. :D Also, I know some of you will point out that some of the stuff are not needed ... but remember, I'm a VB developer so I always install everything. Bwahahahahaha!!!

Although I don't think that you need to restart your system ... but being an M$ peon, I did so out of habit.  :razz: 

You should try running the DRI "install.sh" now.  :D

---

### Post by bathala on 2005-05-06
Oh I forgot ... silly me!

When I got it to compile, I get the error saying that "radeon" was in use. So I what I did reboot into the console. Its like when windows was still version 3.11 and we boot into DOS before starting windows (gawd I feel really old). Its a bit tricky with ubuntu so if you don't know how,  say so and I'll try to post here how I did it. You'll have to jump through hoops with ubuntu unlike with Fedora and Mandrake where all you have to do is modify /etc/inittab file.

So, reboot the machine into the console (you should not get the graphical login) and run the "install.sh" for DRI.

 O:)

---

### Post by kfc on 2005-05-06
[QUOTE=bathala]Oh I forgot ... silly me!

When I got it to compile, I get the error saying that "radeon" was in use. So I what I did reboot into the console. Its like when windows was still version 3.11 and we boot into DOS before starting windows (gawd I feel really old). Its a bit tricky with ubuntu so if you don't know how,  say so and I'll try to post here how I did it. You'll have to jump through hoops with ubuntu unlike with Fedora and Mandrake where all you have to do is modify /etc/inittab file.

So, reboot the machine into the console (you should not get the graphical login) and run the "install.sh" for DRI.

 O:)[/QUOTE]
 I'd need to know how to reboot in to console.
seems like my radeon driver still can't be compiled.
I've successfully compiled the common DRI drivers. still got the radeon dri drivers left.

---

### Post by p0rnflake on 2005-05-06
I'm one happy T42 owner right now - followed the steps in the first post - and got blazing performance now :D

---

### Post by kfc on 2005-05-07
what i currently can't achieve is to compile the radeon dri driver.
But i manage to compile the 'common' drivers tho.
I'm not sure what i've done wrong. I've been following the instructions on 


3. Get the Kernel Headers and Build Depency
- This is what your system really needs so that you can compile the DRI module
Quote:
sudo apt-get install build-essential linux-headers-$(uname -r) autoconf automake libtool flex bison

But still no luck.
Its still reads "no latest kernel module" at the end of the compiling radeon.

I'm trying the debian DRI drivers now in the meantime waiting for an answer.

Thanks.

---

### Post by NeoChaosX on 2005-05-07
I did the TCL thing in DriConf, and there was a speed boost, but in TuxRacer, Tux is now completely white. Anyone know how to fix this? For now, I've set the settings back to the default.

---

### Post by kfc on 2005-05-08
ok. now i've got it.
the reason why alot of us can't compile the radeon driver is just a minor change we need to do in the kernel version.
Instead of using the 386 kernel. we got to updates it to 686 version in order to work.
But after i've doing all of the steps mentioned. My glxgears now seems to performing at 1700fps. But a problem now is the 3d graphics looks like having scanlines, noises, scratches. I'm not sure what's the problem is. 
I can't launch any app with 3d graphics now except some screen saver and glxgears. But it's graphics just buggy like i've mentioned above.

as for the driconf, i can't get it installed to. it has got a dependency issue with python when i try to do it in synaptic. 

borzwazie - Did u installed it from the image package and compile it from source or did u install it from synaptic?

---

### Post by kfc on 2005-05-08
ok.
now i got the driconf to work.
changing to TCL software mode can solve the problem i had with flickering in 3d.
Now.... i have another problem is, everytime i launch Alias Maya. It's immediately freeze after a couple of clicks.
what's wrong?

---

### Post by kfc on 2005-05-08
btw,
i really got to add this. now my glxgear running steadily at 3430fps at 1024x768.
that's quite a great boost in performance.

---

### Post by kfc on 2005-05-12
[QUOTE=kfc]ok.
now i got the driconf to work.
changing to TCL software mode can solve the problem i had with flickering in 3d.
Now.... i have another problem is, everytime i launch Alias Maya. It's immediately freeze after a couple of clicks.
what's wrong?[/QUOTE]

now... i've got the flickering problem fixxed. changing the TCL from hardware to software helps. and I've checked on the option for improve performance in driconf.
I can comfirm that it runs steadily at 3350 fps in glxgears.

Tuxracer works perfectly for me (surprisingly).
But Alias Maya and Wings3d doesn't work for me at all.
Maya freezes after 10 sec of running the app, it can launch perfectly tho. while wings3d can't be started at all.

oh well... let's hope the later release of the dri drivers can be much more stable than it does now.

---

### Post by bathala on 2005-05-13
I too have given up on this.

After jumping through the hoops just to get DRI working ... the 3D application that I am using kept crashing with a segmentation fault. 

I have long since reinstalled ubuntu without messing with DRI/GL.

---

### Post by benplaut on 2005-05-13
it seems that there are some problems with installing, for some people... can anyone explain it in layman's terms, please?


for the reference, i have a T40 2373-7CU that is stock except for more ram...

the GPU section of my xorg.conf looks like:

```

        Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "True"
        Option          "EnablePageFlip" "True"
```

pretty much stock  :neutral: 

my glxgears is 720fps... not too great  ](*,) 

the last time i tried to install dri, it fried my X, so i want a human saying "OK", rather than just relying on google this time  :???:

---

### Post by gotmonkey on 2005-05-17
[QUOTE=borzwazie]So I just found Ubuntu, and I'm installing it on every piece of hardware I own.

I ran into trouble on Hoary, and I hope I can save someone else some trouble.

Hoary reported that my laptop display chipset was:

ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)

This led me to believe that I could use the ATI fglrx drivers. This is incorrect.

What this really should have been was:

ATI Technologies, Inc. Radeon 7500 Mobility (M7 LW)

This chipset uses the DRI project "radeon" driver. Big difference! I spent some time chasing this problem.

I got the latest snapshot from the DRI website:

[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

and used the following in my xorg.conf (device section):

```

Section "Device"
        Identifier      "Radeon Mobility M7 LW"
        Driver          "radeon"
        VendorName      "ATI Technologies Inc."
        BoardName       "Radeon Mobility M7 LW"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"        "true"
EndSection

```

be sure to add:
     Option "omit xfree86-dga"

to a subsection in Section "Module" as well.

EDIT:

By the way, if you've done all this successfully, by *all* means, download and install DRIConf - I went from about 970 frames/sec in glxgears to 2100 frames/sec!

[http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)

If you are using the latest snapshots from the DRI website, and you're using DriConf to tweak things, be sure to change the TCL mode to "Use software TCL pipeline" - it's much, much faster than the hardware TCL. Also, the hardware TCL displays weird lighting on quads (3d objects flicker and are lighted badly).

Choosing Software TCL gives you by far the biggest performance boost.

Also, be sure to run DriConf as the user that's actually logged in (not just as root!) - it doesn't seem to affect all applications (like screensavers) otherwise.

hope this helps someone![/QUOTE]

Hey question, I did the dri driver install & driconf, but when I try running driconf it returns "libGL is too old"

any idea how I can resolve this?

thanks

---

### Post by Arthemys on 2005-05-18
[QUOTE=gotmonkey]Hey question, I did the dri driver install & driconf, but when I try running driconf it returns "libGL is too old"

any idea how I can resolve this?

thanks[/QUOTE]

I'm getting the exact same thing. That and I can compile the ATi DRI drivers but not the common. Has that happened to anyone in that order?

---

### Post by gotmonkey on 2005-05-18
[QUOTE=Arthemys]I'm getting the exact same thing. That and I can compile the ATi DRI drivers but not the common. Has that happened to anyone in that order?[/QUOTE]


Originally, I tried the Radeon snapshot & it didn't work. 

I just tried to install the DRI common package for 5-17 and it now seems to work. Direct rendering is "on" in glxinfo & driconf is running.

hope that this helps

---

### Post by Arthemys on 2005-05-19
Unfortunately that didn't help ;)

I'll just have to putz with it some more I guess.

---

### Post by Kenny-HUN on 2005-06-10
Hi!
I searched Google, but I can't find the answer I need. Please help me!
I use SuSE 9.3, and I'd like to install DRI Savage driver to my Twister K integrated VGA.
But I get this error message in dri.log at last step: "Makefile:163: *** Cannot find a kernel config file.  Stop."
I don't know, what should I do. Can anybody help me?
Thanks!

---

