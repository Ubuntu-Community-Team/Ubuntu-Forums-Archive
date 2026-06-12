---
title: "Resonable performance from an ATI Radeon 7000VE"
date: 2006-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by scott on 2006-07-23
Run  glxgears -printfps
I initially got 250fps and Google Earth was totally unusable.

Starting with a basic Dapper install download the latest radeon snapshot from here:
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)
Extract to a folder in your home directory, eg: /home/???/radeon-20060403-linux.386/

Open synaptec package manager and enable the universe repository and install:

   Linux Kernel Headers
   linux-headers-x86
   make
   gcc
   driconf


Open up a terminal and cd to the radeon directory above. Then run sudo ./install.sh
If all goes well type:
 sudo gedit /etc/X11/xorg.conf and change the Device section to look like the following:
```

Section "Device"
	Identifier	"Radeon"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option	        "EnablePageFlip" "True"
	Option	        "UseInternalAGPGART" "no"
	Option	        "backingstore" "true"
	Option	        "AllowGLXWithComposite" "true"
	Option          "RenderAccel" "true"
EndSection

```

Ensure that you use the same identifier in the screen section if you change it in this section, leave it be is probably best.

Save and exit.

Now run driconf. Do not run this as sudo, some user space applications will not pickup the changes if you do. In my case google earth would not run properly until I ran it as a regular user. (had to sudo rm .drirc before running as a regular user after I had run it as root.)

Change the TCL mode to "Use Software TCL Pipeline" and Use HyperZ to Yes. Save and quit.

Reboot and run glxgears -printfps. Mine went up from around 250fps to 850fps and I nolonger have funny artifacts all over preventing me from using Google Earth.

Please post if this works or if you have any tweaks to improve it.

Scott

---

### Post by louistan3 on 2006-08-07
8243 frames in 5.0 seconds = 1648.496 FPS
7913 frames in 5.0 seconds = 1582.543 FPS
8421 frames in 5.0 seconds = 1684.034 FPS
8387 frames in 5.0 seconds = 1677.380 FPS
8389 frames in 5.0 seconds = 1677.794 FPS

wow.. great howto.... improved my fps by a lot.. lol.. i had 700 fps at first.. now i got 1600 fps.. thanks!!! :-D

but my google earth still wont work.. when i run it.. the earth is kinda blurry and the stars go liney and stuf.. its just unusable.. eh.. any help?

---

### Post by TSMJ on 2006-08-08
Yo
Is it possible for you to condense the synaptic package list into an apt-get command? I had to install synaptic especially and couldn't find 'linux-headers-x86'.

My attempt failed at this last night, complaining of some kind of kernel problem, but I was 1/2 way though recompiling it anyway, so will try again. Great news to find something relating to the 7000 card btw, I've been looking for ages. 

Cheers

---

### Post by theProf on 2006-08-08
Wow.  This is great.  I went from ~430 FPS to about 1450 FPS.  Thanks for the info.

---

### Post by NerdyShinobi on 2006-08-08
For some reason, this didn't work for me.  I am using a custom compiled kernel, which is probably it.  I'm willing to recompile to make this work.  It tells me that it cannot find my current kernel modules, and compilation fails.

Here are the contents of dri.log:  

make DRM_MODULES=radeon.o modules
make[1]: Entering directory `/home/robb/source/radeon-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.17-beyond3/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-2.6.17'
  CC [M]  /home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.o
/home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.c: In function ‘drm_ati_free_pcigart_table’:
/home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.c:87: error: ‘struct page’ has no member named ‘count’
make[3]: *** [/home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.o] Error 1
make[2]: *** [_module_/home/robb/source/radeon-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.17'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/robb/source/radeon-20060403-linux.i386/drm/linux-core'
make: *** [radeon.o] Error 2

Can anyone tell me what I'm doing wrong, or what needs to change?

---

### Post by yoyoned on 2006-08-08
I have the PCI version.  I went from 150 to 380 fps.  Not as fast s some of the other reports, but still a good increase.  A note to anyone elsewith the PCI version who wants to try this.  I changed the "BUSID line to match the above post and X would not start until I restored it to its orginal state:```
BusID		"PCI:0:8:0"
```  Thanks for the great howto.

---

### Post by virgee on 2006-08-09
I am getting arror about inserting drm module - Cannot allocate memory. I have Radeon 9600 M, but I suppose it should be the same ase with 9700VE.
Anyone met this? thx

---

### Post by barbarian on 2006-08-09
Scott, thank you very much! I have poor Radeon 9200SE. And because of driconf i've achieved 1068 fps. And i had 750 fps before.

Though if i put Options:		
        Option          "AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option	        "EnablePageFlip" "True"
	Option	        "UseInternalAGPGART" "no"
	Option	        "backingstore" "true"
	Option	        "AllowGLXWithComposite" "true"
	Option          "RenderAccel" "true"

my X stuck from boot..

But anyway thanx, i will play with those options tomorrow.

---

### Post by chadk on 2006-08-09
This just for the 7000VE?  How about x800?

---

### Post by barbarian on 2006-08-11
And with:

> Option	        "EnablePageFlip" "True"

2000fps! -even more then with fglrx!

sweet, thak you again!

---

### Post by drewsimon on 2006-08-11
I've had such trouble getting my ATI card to work. 

lspci says this:
```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

```

Would this howto work for me?

---

### Post by barbarian on 2006-08-11
Hello,
try this [guide]("https://help.ubuntu.com/community/RadeonDriver"), radeon driver probably will work with your card. Dunno if r7500 mobility = r7500, though..

Good luck!

---

### Post by Moonunit2008 on 2006-08-11
ive got an ati radeon 7000 and when i ran gears it came out in the 50fps range, i really could use this if i could get it to work, but i get a problem with compiling.  it says to check dri.log for what went wrong, here is the output, Makefile:173: *** Cannot find a kernel config file.  Stop.

if you guys could help me out with this, i would be very glad. thanks.

---

### Post by claypole on 2006-08-13
Make sure you're in Terminal mode (with xserver stopped) before compiling.  I think <ctrl><alt><f1> should get you in the mode, <ctrl><alt><f7> gets you back and <ctrl><alt><backspace> resets xserver based on xorg.conf.

Beware, if there are any problems with xorg.conf you will be dumped back in the terminal mode.  Read the errors and then edit xorg.conf.  I use **sudo vi /etc/X11/xorg.conf** instead of gedit as the text editor (get familiar with vi quickly while everything is working).

Once everything is working, reboot for good measure :)

Hope this helps!

---

### Post by asherwoo on 2006-08-16
I get the same error without a custom compiled kernel.  I have the latest edgy packages.

---

### Post by asherwoo on 2006-08-16
> **NerdyShinobi said:**
> For some reason, this didn't work for me.  I am using a custom compiled kernel, which is probably it.  I'm willing to recompile to make this work.  It tells me that it cannot find my current kernel modules, and compilation fails.

Here are the contents of dri.log:  

make DRM_MODULES=radeon.o modules
make[1]: Entering directory `/home/robb/source/radeon-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.17-beyond3/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-2.6.17'
  CC [M]  /home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.o
/home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.c: In function ‘drm_ati_free_pcigart_table’:
/home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.c:87: error: ‘struct page’ has no member named ‘count’
make[3]: *** [/home/robb/source/radeon-20060403-linux.i386/drm/linux-core/ati_pcigart.o] Error 1
make[2]: *** [_module_/home/robb/source/radeon-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.17'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/robb/source/radeon-20060403-linux.i386/drm/linux-core'
make: *** [radeon.o] Error 2

Can anyone tell me what I'm doing wrong, or what needs to change?


BTW, my previous post was a replay to this one.

---

### Post by asherwoo on 2006-08-16
> **barbarian said:**
> Scott, thank you very much! I have poor Radeon 9200SE. And because of driconf i've achieved 1068 fps. And i had 750 fps before.

Though if i put Options:		
        Option          "AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option	        "EnablePageFlip" "True"
	Option	        "UseInternalAGPGART" "no"
	Option	        "backingstore" "true"
	Option	        "AllowGLXWithComposite" "true"
	Option          "RenderAccel" "true"

my X stuck from boot..

But anyway thanx, i will play with those options tomorrow.


How did you get X working again?  Mine just goes to a black screen

---

### Post by barbarian on 2006-08-16
Hi,

I've just excluded:
[I]Option "AGPFastWrite" "true"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
Option "RenderAccel" "true"[/I]

and changed:

*Option "AGPMode" "4"* to * Option "AGPMode" "8"*
since I have r9200SE.
btw, [ here]("http://dri.sourceforge.net/doc/DRIuserguide.html") is great howto.

---

### Post by art on 2006-08-16
This driver just compltely freezes my session. Have to hard reboot. It is a Radeon Mobility 7000 (M6) card. Anyone knows why, or how to fix?

---

### Post by TFrog on 2006-08-22
I tried this on my old Athlon desktop system with an ATI Radeon 7000VE.  Just got done with a clean install of Dapper thanks to the person uploading a bad xserver-xorg-core but that is another story.  I took the time to check glxgears -printfps before doing this and came up with 351FPS and after doing this trick I was impressed by a 4.25 times speed enhancement:D   I'm now seeing 1496FPS:D   Have you done any tinkering in the driconf other than what you've already posted?  Also, I noticed on that download site and later found out these are the very same drivers DRI is working cooperatively on with ATI.  I also noticed drivers for other Radeon cards here.  One actually supported my laptop's 200M chipset but I haven't gone into learning all the settings tidbits yet.  Would be nice to have 3D on my laptop.  It's just a bit faster than my desktop without acceleration and the card is on the PCI-e bus.  That is truly sad.  Plus, I can't use the onboard memory to have 3D.  ATI's proprietary driver only works with UMA memory.  What a waste.  Anyway, excellent how to and one that should be stickied cause there are some of use still running older gear.

---

### Post by soc on 2006-08-24
great!
i get with my radeon 9800:
```
21040 frames in 5.0 seconds = 4207.832 FPS
```
now i'll will try running xgl + compiz with these opensource drivers ...

---

### Post by edemark on 2006-08-25
Hi Scott

You really made my day with this how to (my day not really my year or actually my 3 years).
I have a HP Compaq NX9010 that comes with an ati igp 345 graphic chip. I could never get more than 300 fps and some 12-18 fps at full screen. With your howto it gone up to 1100 fps and 190 fps fullscreen.

Thanks again it is really cool

again just for the googlers 
works perfectly with this card:
 "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"

---

### Post by TFrog on 2006-10-14
For those testing or already working with Ubuntu 6.10 there is a twist to this.  You no longer need to load the DRI's driver as it's already in the distro.  Just go into System Settings/Monitor & Display, log into the administrator mode and set your hardware to:

graphics card - ATI Radeon
driver        - ati

monitor       - Plug-n-Play

After this you should restart your xorg server.  Your /etc/X11/xorg.conf should look similar to this:


Section "Device"
  identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
  boardname "ATI Radeon"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  vendorname "ATI"
  option "MergedFB" "off"
EndSection

This gave me the following report from glxgears -printfps:

frog@kubuntu:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
7665 frames in 5.0 seconds = 1532.919 FPS
7661 frames in 5.0 seconds = 1532.092 FPS
7668 frames in 5.0 seconds = 1533.562 FPS
7662 frames in 5.0 seconds = 1532.296 FPS
7658 frames in 5.0 seconds = 1531.544 FPS
7660 frames in 5.0 seconds = 1531.820 FPS
7656 frames in 5.0 seconds = 1531.175 FPS
7654 frames in 5.0 seconds = 1530.730 FPS
7651 frames in 5.0 seconds = 1530.042 FPS
7648 frames in 5.0 seconds = 1529.568 FPS
7648 frames in 5.0 seconds = 1529.407 FPS
7656 frames in 5.0 seconds = 1531.102 FPS
7662 frames in 5.0 seconds = 1532.295 FPS
7659 frames in 5.0 seconds = 1531.717 FPS
7663 frames in 5.0 seconds = 1532.420 FPS
7655 frames in 5.0 seconds = 1530.989 FPS
5854 frames in 5.0 seconds = 1170.650 FPS
5603 frames in 5.0 seconds = 1120.438 FPS
7400 frames in 5.0 seconds = 1479.834 FPS
7659 frames in 5.0 seconds = 1531.740 FPS
7657 frames in 5.0 seconds = 1531.346 FPS

ANY SETTINGS OTHER THAN THESE STATED WILL COST YOU SEVERAL HUNDRED FPS.
The difference between this and other settings on my system alone shows a move from around 330FPS to the report above.  This done on Kubuntu Edgy Eft Beta.

Your mileage with this will vary and I accept no responsibility for damages should there be any while you attempt to get more performance from your system.

---

### Post by Rob2687 on 2006-10-14
My radeon mobility m6 (radeon 7000 equivalent) went from 400 to 1600 fps. THe driconf changes gave the biggest increase.

---

### Post by arcorreia on 2006-10-18
Scott,

I've done everything you said, I had no errors but when I tried to use driconf it gave me these errors:

Driver "radeon" is not installed or does not support configuration.
/usr/lib/python2.4/site-packages/driconf.py:1424: DeprecationWarning:
  "priv", self.configTree.saveConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1427: DeprecationWarning:
  "priv", self.configTree.reloadConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1428: DeprecationWarning:
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf.py:1431: DeprecationWarning:
  "priv", self.configTree.newItem, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1434: DeprecationWarning:
  "priv", self.configTree.removeItem, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1437: DeprecationWarning:
  "priv", self.configTree.moveUp, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1440: DeprecationWarning:
  "priv", self.configTree.moveDown, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1443: DeprecationWarning:
  "priv", self.configTree.properties, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1444: DeprecationWarning:
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf.py:1453: DeprecationWarning:
  self.aboutHandler, None, -1)
/usr/lib/python2.4/site-packages/driconf.py:1454: DeprecationWarning:
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf.py:1457: DeprecationWarning:
  self.exitHandler, None, -1)

Just to be sure the radeon module was installed I issued a modprobe -i radeon and I have these lines:

radeon                 1
drm                    75672  2 radeon
agpgart                34888  2 drm,via_agp

I can't figure out what happened. Did any one had a similar experience?
Any suggestions would be appreciated.

Thanks,
Correia

---

### Post by lazyart on 2006-10-26
I tried this with my Radeon 7200 All-in-Wonder on Dapper.  When I started I was getting a miserable 19 fps (those gears werent turning, they were ticking).  I followed the steps here and they went up to 40, still a far cry from acceptable, and obviously software rendered.

Eventually I found a thread on the Kubuntu board that helped me out... [http://kubuntuforums.net/forums/index.php?topic=9200.new](http://kubuntuforums.net/forums/index.php?topic=9200.new)

I got up to 1229 fps, then did the driconf bit and got up to over 1900.  2D is a lot better now as well (I knew something had to be wrong as it was taking too long to render windows and web paged).

Hopefully a googler finds this. :)

---

### Post by osinghrathore on 2006-10-28
> **asherwoo said:**
> BTW, my previous post was a replay to this one.

Don't know if you're still trying on it.

I was facing same problem.
I fixed it by editing drm/linux-core/drm_compat.h
**changed at line 173 [COLOR="Red"]atomic_dec(&(p)->count) to atomic_dec(&(p)->_count)[/COLOR]**

---

### Post by Chii on 2006-12-02
> **TFrog said:**
> For those testing or already working with Ubuntu 6.10 there is a twist to this.  You no longer need to load the DRI's driver as it's already in the distro.  Just go into System Settings/Monitor & Display, log into the administrator mode and set your hardware to:

graphics card - ATI Radeon
driver        - ati

monitor       - Plug-n-Play

After this you should restart your xorg server.  Your /etc/X11/xorg.conf should look similar to this:


Section "Device"
  identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
  boardname "ATI Radeon"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  vendorname "ATI"
  option "MergedFB" "off"
EndSection

This gave me the following report from glxgears -printfps:
*snip in order to decrease the length of the post*

ANY SETTINGS OTHER THAN THESE STATED WILL COST YOU SEVERAL HUNDRED FPS.
The difference between this and other settings on my system alone shows a move from around 330FPS to the report above.  This done on Kubuntu Edgy Eft Beta.

Your mileage with this will vary and I accept no responsibility for damages should there be any while you attempt to get more performance from your system.

Sorry to bother, but I recently installed 6.10/Edgy and have been trying to  get this to work.  And after getting the error + log. I decided to keep reading (should have done this first) and have come upon your response.  But I am wondering how do I get to "System Settings/Monitor & Display" ?  Ive been looking for it myself and asking in irc and I feel like I'm bashing my head into a concrete wall. >.<

Thank you ahead of time for any help!
(Yes I am quite new to this still if you cant tell >.<)

-Chii

---

### Post by nmincone on 2006-12-14
Chii, you can get to those settings with #sudo gedit /etc/X11/xorg.conf ...its the same thing.
Here are the changes I made and my results on a nx9010 below....

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"radeon"
	BusID		"PCI:1:5:0"
	boardname	"ATI Radeon"
	screen		0
	vendorname	"ATI"
	option "MergedFB" "off"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option	        "EnablePageFlip" "True"
	Option	        "UseInternalAGPGART" "no"
	Option	        "backingstore" "true"
	Option	        "AllowGLXWithComposite" "true"
	Option         	"RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Results;
After: 1000 frames in 5.0 seconds = 350.284 FPS
Before: 6491 frames in 5.0 seconds = 1298.184 FPS

---

### Post by CyberCod on 2006-12-16
I'm trying this on the 7000VE PCI ... and i'm getting only so far before I'm running into this...
```

Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```

I'm thinking that I'm not getting the proper components when I'm looking for 
> 
Linux Kernel Headers
linux-headers-x86


could someone please explain the steps for obtaining these?  I'm trying to find them in Synaptic, but there are a lot of files that come up in the search.

I'm trying to get 3d support working for cedega... the fps seems to be great for OpenGL, but in the 3d accelleration test it just fails.

Any help guys?

---

### Post by _axiom_ on 2007-01-01
Trying to follow this tuturial on Dapper, but I also am not getting the kernal headers right.

When I try to install them in adept, it says that the package it "broken", and will let me uninstall it, but I am not sure how to get it correctly.

---

### Post by _savior_ on 2007-03-10
Hi Scott,

thank you very much for this how-to! I also have a nx9010 with Radeon 345IGP, and I have been stuck in Edgy with infernal performance. But thanks to your help, the FPS has gone up to 1170 / 270! Kudos!!

I also tried to change the settings in KDE, but it messed up my xorg.conf. So I just added ```
option "MergedFB" "off"
``` to the file. I don't know, if it helped or not, though... maybe that was what increased the FPS further from 1000 / 250.

Strange, because if I remember correctly, there were no problems with this card under Dapper (or was it Breezy?). But I cannot say for sure, since I changed to Linux in Dapper's era, and I didn't use it that much before.

Unfortunately Beryl/Compiz exits under Edgy with "Another window manager is already running" (they have no problem killing kwin, though :)), so I cannot try it... :(

---

