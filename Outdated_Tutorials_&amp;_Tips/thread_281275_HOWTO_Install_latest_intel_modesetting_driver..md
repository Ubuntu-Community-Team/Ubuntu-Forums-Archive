---
title: "HOWTO: Install latest intel modesetting driver."
date: 2006-10-20
forum: Outdated Tutorials &amp; Tips
---

### Post by terrax on 2006-10-20
This howto, show you how to install the very latest sourcecode version of intels driver, with mode setting support, without using the video bios. It actually also fixes some performance issues etc.

And if you got this issue:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/61306](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/61306)
It solves that bug too.


1. First. Add this repositories (edgy users can ignore this step):
 
```

deb http://ubuntu.beryl-project.org/ dapper main aiglx

```

Then we have to update:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

If you have installed 915resolution before. Then remove it. You don't need it anymore.

```

sudo apt-get remove 915resolution

```

Now we have to install build and compiling tools.

```

sudo apt-get install build-essential m4 autoconf automake1.9 libtool gcc linux-headers-`uname -r` autoconf autotools-dev cvs git bison git-svn git-cvs xorg-build-macros xorg-dev mesa-common-dev libdrm-dev

```

And don't forget to:

```

sudo update-alternatives --set automake /usr/bin/automake-1.9
sudo update-alternatives --config git
select #2: git-scm

```

Ok, now we have to get some sourcecodes.

Make a directory, example:
```

sudo mkdir ~/src
cd ~/src

```

Check the latest driver out:

```

git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
cd xf86-video-intel

```

Now we have to change the Branch of the source, so we can get the newest modesetting driver:

```

git checkout modesetting

```

Now we are going to compile and install the driver
```

./autogen.sh --prefix=/usr
make
sudo make install

```

[COLOR="red"]NOTE:[/COLOR] If you get an compiling error containing i830_modes.c and M_T_PREFERRED,
then just:

```

nano src/i830_modes.c
[COLOR="red"]And add thiese lines, under the other defines:[/COLOR]
#define M_T_PREFERRED 0x08     /* preferred mode within a set */
#define M_T_DRIVER  0x40       /* Supplied by the driver (EDID, etc) */

```

Now try making it again. Its a common error, and you will probably get it.

When all this is done, the new driver is installed and ready. Now restart, and enjoy you don't have to use 915resolution anymore.

BTW several bugs have been fixed, but the driver is still in a very early development state. But I haven't seen any problems yet, only with glxgears. I get this error:

```

glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Afbrudt (SIGABRT)

```

But thats an error most peoples get with earlier drivers also (edgy). 

Anyway, plz post if you got any problems with this howto.  I wrote it at late night, and may have forgotten something.

Cheers, Terrax.:)

---

### Post by terrax on 2006-10-21
Can anybody confirm, that it works in Edgy or Dapper?

---

### Post by mrojas73 on 2006-10-21
I am willing to give it a try,  I will report back!

---

### Post by mrojas73 on 2006-10-22
I get this error:
```

The following packages have unmet dependencies:
  xorg-dev: Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxcursor-dev but it is not going to be installed
            Depends: libxdamage-dev but it is not going to be installed
            Depends: libxfixes-dev but it is not going to be installed
            Depends: xserver-xorg-dev but it is not going to be installed

```

---

### Post by terrax on 2006-10-23
Hmm have you enabled every dipositories avalible?

---

### Post by jambes on 2006-10-24
I got this error in Edgy:

In file included from i810.h:58,
                 from i810_accel.c:55:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from i810.h:58,
                 from i810_accel.c:55:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before 'GLboolean'
make[3]: *** [i810_accel.lo] Error 1
make[3]: Leaving directory `/home/jambes/source/intel-modesetting/xf86-video-intel/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jambes/source/intel-modesetting/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jambes/source/intel-modesetting/xf86-video-intel'
make: *** [all] Error 2

---

### Post by holzbit on 2006-10-24
> **terrax said:**
> Can anybody confirm, that it works in Edgy or Dapper?

config: Kubuntu 6.0.6 LTS 64bit, Mainboard Asus P5LD2-TVM, i945G onboard graphics

I installed following your howto, with two changes:

> sudo mkdir ~/src
cd ~/src

if created with sudo the ~/src is not writeable by the user, so I´d rather mkdir without sudo

> ./autogen.sh --prefix=/usr
make

make banged me with an error because gl.h was missing.
    sudo apt-get install mesa-common-dev
fixed that.


But alas, it doesn´t help for my problem. Kubuntu is still crashing whenever the X-Server is shut down. No matter if I use the original or the new driver discussed in this howto :confused:

---

### Post by mrojas73 on 2006-10-24
> **terrax said:**
> Hmm have you enabled every dipositories avalible?
I followed your instructions. I will be trying again with a fresh install.

---

### Post by mrojas73 on 2006-10-26
New clean installation now and I get this errors when I do make:
```

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -DI830_XV -g -O2 -MT i830_modes.lo -MD -MP -MF .deps/i830_modes.Tpo -c i830_modes.c  -fPIC -DPIC -o .libs/i830_modes.o
i830_modes.c: In function 'i830GetDDCModes':
i830_modes.c:294: error: 'M_T_PREFERRED' undeclared (first use in this function)i830_modes.c:294: error: (Each undeclared identifier is reported only once
i830_modes.c:294: error: for each function it appears in.)
i830_modes.c:296: error: 'M_T_DRIVER' undeclared (first use in this function)
i830_modes.c: In function 'i830FPNativeMode':
i830_modes.c:425: error: 'M_T_PREFERRED' undeclared (first use in this function)i830_modes.c: In function 'i830GetLVDSMonitor':
i830_modes.c:664: error: 'M_T_PREFERRED' undeclared (first use in this function)make[3]: *** [i830_modes.lo] Error 1
make[3]: Leaving directory `/home/mrojas/src/xf86-video-intel/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mrojas/src/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mrojas/src/xf86-video-intel'
make: *** [all] Error 2
mrojas@Aspire5601:~/src/xf86-video-intel$

```

---

### Post by jthirt on 2006-10-27
I use Dapper on a laptop. 

I followed the Howto and it did the job perfectly for me as far as compiling and installing. :D  I also had to edit src/i830_modes.c as indicated to fix the error. 

Unfortunately, once in place and after rebooting, X crashes. Here are the last few lines that look quite suspicious to me ... :-k 

```

(II) I810(0): Found panel of size 768x16384 in BIOS VBT tables
(II) I810(0): Panel mode h active 54 blank 0 rate 6451.851852 v active 0 blank 0 rate inf
(II) I810(0): Found BDB block type 42
(II) I810(0): Monitoring connected displays enabled
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x83e
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
Executing (ax == 0x5f01) BIOS call at i830_driver.c:500
(II) I810(0): BIOS Build: 2880
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(==) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 65368 kByte
(--) I810(0): Maximum space available for video modes: 8000 kByte
(WW) I810(0): Mode 1024x768 is out of range.
(WW) I810(0): Valid modes must be between 320x200-768x16384
(WW) I810(0): Mode 800x600 is out of range.
(WW) I810(0): Valid modes must be between 320x200-768x16384
(II) I810(0): Valid mode using panel fitting: 640x480x60
(II) I810(0): Total number of valid FP mode(s) found: 4
(II) I810(0): Printing probed modes for pipe 1
(II) I810(0): Not using default mode "640x480x60" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "720x400x60" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x400x60" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x350x60" (bad mode clock/interlace/doublescan)
(II) I810(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) I810(0): I2C device "CRTDDC_A:ddc2" removed.
(II) I810(0): Printing probed modes for pipe 0

Fatal server error:
No modes found on either pipe

```

When I read : "Found panel of size 768x16384" I am worried !

Before that, there are a few errors reported :

```

(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) I810(0): I2C bus "CRTDDC_A" initialized.
(II) I810(0): I2C bus "LVDSDDC_C" initialized.
(II) I810(0): I2C bus "DVOI2C_E" initialized.
(II) I810(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers/sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(EE) I810(0): detecting sil164
(EE) I810(0): Unable to read from DVOI2C_E Slave 112.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers/ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(EE) I810(0): detecting ch7xxx
(EE) I810(0): Unable to read from DVOI2C_E Slave 236.
(II) I810(0): I2C bus "DVOI2C_E" removed.
(II) I810(0): I2C bus "DVODDC_D" removed.
(II) I810(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) I810(0): I2C device "CRTDDC_A:ddc2" removed.
(EE) I810(0): DDC Analog 0, 00005010
(II) I810(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) I810(0): I2C device "LVDSDDC_C:ddc2" removed.
(EE) I810(0): DDC LVDS 1, 00005018

```

So I reverted back to the non modeline driver for now. 

BTW, the laptop I'm experimenting this on is an 'infamous' Gateway 400VTX with a 1024x768 pannel that wouldn't do better than 800x600 so far under ubuntu. ](*,) 

Looking forward to further improvements and fixes to hopefully get this working before Christmas ! :-D

I don't know if the driver is up for testing yet so I could participate and report such errors.

---

### Post by loko on 2006-10-27
hello,

i have Intel 945GM-chipset and tested this how-to.

i don't got any errors during compiling, after inserting the two lines in src/i830_modes.c.

after reboot X works well without any problem, but it seems that the driver doesn't do anything to my system, because i still get:

```
user@laptop:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x5b
3989 frames in 5.0 seconds = 797.624 FPS
```

---

### Post by terrax on 2006-10-28
> **mrojas73 said:**
> New clean installation now and I get this errors when I do make:
```

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -DI830_XV -g -O2 -MT i830_modes.lo -MD -MP -MF .deps/i830_modes.Tpo -c i830_modes.c  -fPIC -DPIC -o .libs/i830_modes.o
i830_modes.c: In function 'i830GetDDCModes':
i830_modes.c:294: error: 'M_T_PREFERRED' undeclared (first use in this function)i830_modes.c:294: error: (Each undeclared identifier is reported only once
i830_modes.c:294: error: for each function it appears in.)
i830_modes.c:296: error: 'M_T_DRIVER' undeclared (first use in this function)
i830_modes.c: In function 'i830FPNativeMode':
i830_modes.c:425: error: 'M_T_PREFERRED' undeclared (first use in this function)i830_modes.c: In function 'i830GetLVDSMonitor':
i830_modes.c:664: error: 'M_T_PREFERRED' undeclared (first use in this function)make[3]: *** [i830_modes.lo] Error 1
make[3]: Leaving directory `/home/mrojas/src/xf86-video-intel/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mrojas/src/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mrojas/src/xf86-video-intel'
make: *** [all] Error 2
mrojas@Aspire5601:~/src/xf86-video-intel$

```

Remember to edit the i830_modes.c file, as said in the howto :)

---

### Post by Snail Wins! on 2006-10-28
> **loko said:**
> hello,

i have Intel 945GM-chipset and tested this how-to.

i don't got any errors during compiling, after inserting the two lines in src/i830_modes.c.

after reboot X works well without any problem, but it seems that the driver doesn't do anything to my system, because i still get:

```
user@laptop:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x5b
3989 frames in 5.0 seconds = 797.624 FPS
```
I have this exact same problem, it doesn't seem like it did anything at all :(

---

### Post by terrax on 2006-10-28
The modsetting driver, doesn't fix that "warning", but it allows you to use your original screensettings, without 915resolution.

---

### Post by scannerdarkly on 2006-10-28
tried that but now my desktop doesn't seem to send a signal to the monitor.

---

### Post by jwl007 on 2006-10-28
I have a gateway m305crv laptop (same intel 8552 chipset as the gateway 400 mentioned earlier, and I tried following this howto.  I was able to compile the modesetting driver, but I got the following error when restarting X: (This is in dapper, mind you :D)

```

(II) I810(0): Printing probed modes for pipe 0

Fatal server error:
No modes found on either pipe

```

Any hints/suggestions?

Thanks.

---

### Post by Beggar Su on 2006-10-29
Tested this on edgy, no errors except for the make install which I had to add the 2 lines to the script. Reboot with no errors but same problem with it not changing anything after checking glxgears

---

### Post by Rumo on 2006-10-29
I get this error after running autogen on edgy:
> Requested 'libdrm >= 2.2' but version of libdrm is 2.0.2


Haven't found an update to libdrm yet.

---

### Post by terrax on 2006-10-29
If you got an error, that it cannot find any monitors. Then you have to find your old xorg.conf file in /etc/X11/.

I think the new driver sometimes install a new xorg.conf file and take a backup of the old xorg.conf file and back it up in xorg.conf~. But Im not sure, thats the case all the time.

But it worked for me.

---

### Post by terrax on 2006-10-29
> **Rumo said:**
> I get this error after running autogen on edgy:


Haven't found an update to libdrm yet.

Just install the latest librm from [www.mesa3d.org](www.mesa3d.org)
There is a guide, howto do it on their side. I used the cvs version.

---

### Post by loko on 2006-10-30
i have installed it on my laptop with 945GM.

The only problem that i have now is that if i boot into gnome, i can see the gdm-login-screen, i log in then and the display gets black.

i have then to switch to console with STRG+ALT+F1 and switch back with STRG+ALT+F7. then i have normal screen.

Is there a workaround for this?

---

### Post by extremecarver on 2006-10-31
> **loko said:**
> i have installed it on my laptop with 945GM.

The only problem that i have now is that if i boot into gnome, i can see the gdm-login-screen, i log in then and the display gets black.

i have then to switch to console with STRG+ALT+F1 and switch back with STRG+ALT+F7. then i have normal screen.

Is there a workaround for this?

Same Problem.

Furthermore external monitor won't go any bigger than 1280x800 my internal monitor resolution
And once in gnome FN+F8 doesn't work anymore.

---

### Post by terrax on 2006-10-31
Thats a common issue I also get. I think we have to wait for further updates.

You can type.

```

git pull

```

In a clean src directory (A dir, where you did not make the git branch selection).

Then you will get the newest git sources.

---

### Post by extremecarver on 2006-10-31
1. Could you please inert that git pull into perspective of the installation How-To? 
I don't know how to work with git - I thought the beginning was already using git???????
I did it 2 days ago as on the front page, should I compile again?

It doesn't allways happen. If it doesnt happen I get only 1024x768 resolution instead of bigger ones.

2. Howto switch back and forth between i810 driver via synaptic and the modesetting driver? Howto know which one is active?

---

### Post by terrax on 2006-11-03
1. Just using the git pull. before you are changing branch to modesetting. I have two different dirs. On for the original driver, and one for the modesetting driver. I always pull the original driver.

2. Just reinstall the packaged version with synaptic og adept. Then you got the repos driver back.

If you want the git version again, just make another make install in the source dir of the driver.

---

### Post by extremecarver on 2006-11-03
So I use Git-pull instead of git-clone??
WHEN DO I HAVE TO ENTER GIT-PULL - Thanks, but I'm really a noob concerning this

git-pull git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
cd xf86-video-intel

---

### Post by terrax on 2006-11-04
No. You have to use git pull, after you have used git-clone :-)

```

git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel

cd xf86-video-intel

git pull

```

---

### Post by jthirt on 2006-11-06
This git thing is kind of confusing as it's unclear what you're getting from it ...

As I don't know for sure, I've started from scratch again every time. I hate this as it's the kind of thing that leads to wasting bandwidth, if anyone still cares about that ! 

In any case, I pulled the latest modesetting sources this morning, compiled and installed the driver to see some progress as opposed to the last time I did it about 10 days ago. :) It doesn't crash as Xorg starts, but I don't get any usable video either ... :-k 

Xorg.o.log reports :

```
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 852GM
(--) I810(0): Chipset: "852GM/855GM"
```

Then Xorg.0.log ends like this :

```

(EE) I810(0): p1 out of range
(EE) I810(0): phase 0 out of range
(WW) I810(0): pipe A dot 192000 n 3 m1 16 m2 8 p1 1 p2 10
(EE) I810(0): p1 out of range
(EE) I810(0): phase 0 out of range
(WW) I810(0): pipe B dot 278400 n 2 m1 19 m2 9 p1 1 p2 10
(WW) I810(0): DumpRegsEnd
ProcXCloseDevice to close or not ?
Synaptics DeviceOff called
(II) I810(0): Comparing regs before/after X's VT usage
(WW) I810(0): Register 0x70030 (DSPARB) changed from 0x00015455 to 0x00002faf
(WW) I810(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0x4800000b
(WW) I810(0): Register 0x61234 (PFIT_PGM_RATIOS) changed from 0x00000000 to 0x10001000
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2

```

I used the CTRl+ALT+F1and CTRL+ALT+F7 keys to see if it would make a difference, but it doesn't. 

I also noticed that the log reports :

```

(II) I810(0): Found panel of size 768x16384 in BIOS VBT tables
(II) I810(0): Panel mode h active 54 blank 0 rate 6451.851852 v active 0 blank 0 rate inf

```

And 768x16384 doesn't look/sound right to me !

I'm not sure how to interpret the next line but it looks like it's related ...

I don't know if there is anything I should try to move forward from here. Just wait and see in a few days ???

---

### Post by terrax on 2006-11-06
Keep in mind, that the modesetting driver is far from complete. Try just use the master branch. Its the default branch when you download it. (Just skip the git checkout modesetting part of the howto). But you have to install 915resolution then.

---

### Post by jthirt on 2006-11-07
> Keep in mind, that the modesetting driver is far from complete.

Oh, I realise that, but I've reached the conclusion that there is no solution to my issue outside of the modesetting approach. That was after reading some threads at bugs.freedesktop.org that ended by :

> Closing this. Everyone here should try the modesetting branch from the git repository.

So here I am, as the title says "HOWTO: Install latest intel modesetting driver".;) 

I also tried the main branch, but it did nothing for me.

---

### Post by Sixer on 2006-11-09
Terrax, thanks a lot so far for your very informative post.
Without the modesetting driver, my Mac Mini couldn't retrieve any modes from my HDTV set.

However, I get the following errors during a startx:

(EE) I810(0): Unable to read from SDVOCTRL_E for SDVOC slave 114.

(EE) I810(0): phase 0 out of range
(EE) I810(0): phase 0 out of range

I don't know what either of them mean. Any pointers?

---

### Post by terrax on 2006-11-10
#jtshirt

I can't say how we fix your problem. Maybe you should make a bug report about your problem?

#Sixer
Im sorry, but I can't tell why that problem accour. But thanks for your positive input.

---

### Post by SonicTheHedgehog on 2006-11-15
How do I uninstall this and revert back to i810?

Because after I restarted, X wouldn't load.  I've included my Xorg.0.log file (in a zip file) just in case.

------------------

EDIT: I tried using "make uninstall", and now I get a different error (see second zip file).

```

(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
...
(II) Primary Device is: PCI 00:02:0
(EE) No devices detected.

Fatal server error:
no screens found

```


I've also included my xorg.conf file, in case there is a problem with it (xorg.conf file is after using "make uninstall").

---

### Post by SonicTheHedgehog on 2006-11-16
*bump, I need help

Please help me get the i810 driver working again...

---

### Post by loko on 2006-11-16
i think it will work this way:

If you see no X, you will have the console.

log in with your username and password.
change the directory, go to the xf86-video-intel-directory.
enter 'sudo make uninstall'

now you should enter:

'sudo apt-get install xserver-xorg-video-i810' (you need internet-connection to do this)

---

### Post by SonicTheHedgehog on 2006-11-16
When i run 'sudo apt-get install xserver-xorg-video-i810' it says its already installed.

And, again when I try to start X, i get this error
```

(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
...
(II) Primary Device is: PCI 00:02:0
(EE) No devices detected.

Fatal server error:
no screens found

```

What is wrong?  My xorg.conf is posted in my previous post if its needed.

---

### Post by SonicTheHedgehog on 2006-11-17
*bump

---

### Post by loko on 2006-11-17
you should enter:

'sudo apt-get install xserver-xorg-video-i810 --reinstall'

This should install the package again.

if you did not change your xorg.conf, everything should work.

If you changed it, then enter:

'sudo dpkg-reconfigure xserver-xorg'

this will configure your xserver

---

### Post by SonicTheHedgehog on 2006-11-17
Thank you so much!!  That fixed everything :) :) :)

---

### Post by Karbonik on 2006-11-19
Terrax:
just install the latest librm from [www.mesa3d.org]("http://www.mesa3d.org/")
 There is a guide, howto do it on their side. I used the cvs version.


sorry, but kind n00b at this also - I'm having a hard time getting the mesa 915 drivers installed.  I'm trying to follow the instructions here [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)
especially in step 1.4

First off I don't see the Mesa/configs anywhere...

and then where it says:

 Now you're ready to compile it. For x86 you would type:  
  make linux-dri-x86

I do that, which gives me the output 

karbonik@biosolar-laptop:~/drm$ sudo make linux-dri-x86
make: *** No rule to make target `linux-dri-x86'. Stop.

what gives?  I'm not sure what to do from here.

---

### Post by loko on 2006-11-19
i did a look in the changelog and the last date when things were changed was at 2006-05-01.

so should this be the latest version of the driver?

---

### Post by bean1975 on 2006-11-19
Ugh drivers from source, no thanks. [http://people.ubuntu.com/~rodarvus/packages/xserver-xorg-video-i810/](http://people.ubuntu.com/~rodarvus/packages/xserver-xorg-video-i810/) the deb from this location worked for me...

---

### Post by terrax on 2006-11-22
#Karbonik
Hmm weird. Try just type make linux-dri.

#loko
No, the git source changes in about every two weeks. What changelog are you reading?

#bean1975
Its quite up to you, if you want to use a fresh self compiled version, or a version others have compiled :-)

---

### Post by humphry on 2006-11-27
I'm having issues... I apparently don't have git?  

```
mdavidson@humphry:/$ sudo apt-get install build-essential m4 autoconf automake1.9 libtool gcc linux-headers-`uname -r` autoconf autotools-dev cvs git bison git-svn git-cvs xorg-build-macros xorg-dev mesa-common-dev libdrm-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gcc is already the newest version.
linux-headers-2.6.17-10-generic is already the newest version.
Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package git has no installation candidate

```

Earlier someone in the thread suggested this:
```
git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel

```

and here's what I got:
```
bash: git-clone: command not found

```

Help?

Thanks!!!

---

### Post by Karbonik on 2006-11-28
> **terrax said:**
> #Karbonik
Hmm weird. Try just type make linux-dri.

I'm not entirely sure what I did right, because I haven't touched it again till now, but about a week ago I started following the instructions that came with the driver, namely copying all the appropriate files into the appropriate lib folders - I got up to moving all the .h files and making symlinks and just now followed the instructions again from scratch in a clean /src.

I rebooted, and it works!

Thanks for the help!

---

### Post by jthirt on 2006-11-28
I just had another go at this, with the latest sources and I get :

```
checking whether to include DRI support... yes
checking for DRI... configure: error: Package requirements (libdrm >= 2.2 xf86dr iproto) were not met:

Requested 'libdrm >= 2.2' but version of libdrm is 2.0.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRI_CFLAGS
and DRI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Any sugestion how I should deal with this ?

I checked on an edgy system and it uses the same version of libdrm, so upgrading to edgy is not the solution ...

I don't know how to set the above variables and what effect that will have. 

Will that disable DRI ? 

Thanks for your assistance.

---

### Post by Karbonik on 2006-11-28
> **terrax said:**
> #Karbonik
Hmm weird. Try just type make linux-dri.
Any ideas how to now make this new driver work with dual-head?

I tried following the instructions and example provided by the intel documentation, but got a message that the modules were not supported.  Here's an output of my xorg.conf with the new driver installed, following the intel docs.  The commented out Devices and Server Layout is what worked previously.

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

###### With the new Intel Embedded Integrated Driver ##########
Section "Device"
    Identifier "IntelEGD-0"
    Driver "intel"
    BusID "0:2:0"
    Screen 0
    VideoRam 32768
EndSection

#################################################################################
#Section "Device"
#    Identifier    "Intel Corporation Mobile Integrated Graphics Controller"
#    Driver        "i810"
#    BusID        "PCI:0:2:0"
#    Screen 0
#    Option "MonitorLayout" "CRT,LFP"
#    Option "DevicePresence" "true"
#EndSection
#################################################################################

###### With the new Intel Embedded Integrated Driver ##########
Section "Device"
    Identifier "IntelEGD-1"
    Driver "intel"
    BusID "0:2:0"
    Screen 1
    VideoRam 32768
    Option "XVideo" "No"
EndSection

########################################
#Section "Device"
#    Identifier "Device1"
#    Driver "i810"
#    BusID "PCI:0:2:0"
#    Screen 1
#    Option "MonitorLayout" "CRT,LFP"
#    Option "DevicePresence" "true"
#EndSection
########################################


Section "Monitor"
    Identifier    "Laptop Monitor"
#    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection


Section "Monitor"
    Identifier    "External Monitor Crystalscan"
    ModelName      "Gateway CrystalScan 500"
    HorizSync       30.0 - 64.0
    VertRefresh     50.0 - 100.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
    ModeLine       "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Laptop Screen"
    Device        "IntelEGD-0"
    Monitor        "Laptop Monitor"
#    Identifier    "Default Screen"
#    Device        "Intel Corporation Mobile Integrated Graphics Controller"
#    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
EndSection


Section "Screen"
    Identifier "Secondary Screen"
    Device "IntelEGD-1"
    Monitor "External Monitor Crystalscan"
    DefaultDepth 24
    SubSection "Display"
        Depth 1
        Modes "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort 0 0
    EndSubSection
    SubSection "Display"
        Depth 4
        Modes "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort 0 0
    EndSubSection
    Subsection "Display"
        Depth 8
        Modes "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort 0 0
    EndSubsection
    Subsection "Display"
        Depth 16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort 0 0
    EndSubsection
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort 0 0
    EndSubsection
#Modes      "800x600@60" "832x624@75" "800x600@85" "1024x768@75" "800x600@75" "1024x768@70" "800x600@72" "1024x768@60" "800x600@56" "1024x768@43" "640x480@85" "1152x768@54" "640x480@75" "1280x854" "640x480@72" "1280x960@60" #"640x480@60" "1280x1024@60"
#    EndSubSection
EndSection


Section "ServerLayout"
    Identifier "Dual-monitor Layout"
    Screen 0 "Laptop Screen" 0 0
    Screen 1 "Secondary Screen" LeftOf "Laptop Screen"
#    Screen 0 "Laptop Screen" 0 0
#     Option "Clone" "On"
#    Option "Xinerama" "On"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    InputDevice "Synaptics Touchpad"
EndSection

##################################################
#Section "ServerLayout"
#    Identifier    "Default Layout"
#    Screen        "Default Screen"
#    InputDevice    "Generic Keyboard"
#    InputDevice    "Configured Mouse"
#    InputDevice     "stylus" "SendCoreEvents"
#    InputDevice     "cursor" "SendCoreEvents"
#    InputDevice     "eraser" "SendCoreEvents"
#    InputDevice    "Synaptics Touchpad"
#EndSection
##################################################


Section "ServerFlags"
    Option "Xinerama" "True"
EndSection

Section "DRI"
    Mode    0666
EndSection

---

### Post by terrax on 2006-11-29
> **Karbonik said:**
> Any ideas how to now make this new driver work with dual-head?

I tried following the instructions and example provided by the intel documentation, but got a message that the modules were not supported.  Here's an output of my xorg.conf with the new driver installed, following the intel docs.  The commented out Devices and Server Layout is what worked previously.


If you followed my guide, you actually have to use "driver i810" instead of the embedded intel driver.

---

### Post by terrax on 2006-11-29
> **jthirt said:**
> I just had another go at this, with the latest sources and I get :

```
checking whether to include DRI support... yes
checking for DRI... configure: error: Package requirements (libdrm >= 2.2 xf86dr iproto) were not met:

Requested 'libdrm >= 2.2' but version of libdrm is 2.0.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRI_CFLAGS
and DRI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

You have to compile the latest libdrm from [www.mesa3d.org](www.mesa3d.org)

[http://mesa3d.org/install.html](http://mesa3d.org/install.html)

Follow the instructions the DRI/accelerated section.
just use this configure command before compiling: 
```

./configure --prefix=/usr

```

---

### Post by psyke83 on 2006-12-05
terrax,

I've already compiled the latest driver (non-modesetting), and it solved a bug in which the mouse cursor disappeared after suspend/switching to a virtual terminal, however it has *not* solved the 3D performance regression from Dapper -> Edgy (1024x768@16bit, Dapper: 1400fps, Edgy: ~930fps). Can you please post some glxgears -printfps scores, specifying your screen resolution and depth? And disable any compositors (beryl/compiz/xcompmgr, etc.).


PS. The modesetting driver doesn't work on my laptop/chipset (Inspiron 510m, 82855GM), but the master branch should have most major bugfixes anyway...

Thanks,
psyke83

---

### Post by Monkus on 2006-12-05
I just install the binary listed above and it worked perfectly. I now have 1280x800. HOORAY!!!

---

### Post by terrax on 2006-12-05
> **psyke83 said:**
> terrax,

I've already compiled the latest driver (non-modesetting), and it solved a bug in which the mouse cursor disappeared after suspend/switching to a virtual terminal, however it has *not* solved the 3D performance regression from Dapper -> Edgy (1024x768@16bit, Dapper: 1400fps, Edgy: ~930fps). Can you please post some glxgears -printfps scores, specifying your screen resolution and depth? And disable any compositors (beryl/compiz/xcompmgr, etc.).


PS. The modesetting driver doesn't work on my laptop/chipset (Inspiron 510m, 82855GM), but the master branch should have most major bugfixes anyway...

Thanks,
psyke83

Hello psyke83

I can't tell how to make the performance hit working. I still got bad performance. But I think the problem have been solved in the new libdrm. I will try that later and reply back.

---

### Post by terrax on 2006-12-05
I can tell it did not help compiling and installing the newest mesa, drm and i810 driver. If we see on the Performance.

---

### Post by psyke83 on 2006-12-06
Hey,

I've opened a bug with multiple issues here: [https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-video-i810/+bug/74751](https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-video-i810/+bug/74751)

I encourage everyone who's watching this thread to check for these issues and see if there's a pattern to the regressions in the intel driver from Dapper -> Edgy.

---

### Post by Karbonik on 2006-12-09
> **terrax said:**
> If you followed my guide, you actually have to use "driver i810" instead of the embedded intel driver.What's the point, then, really?

915 works fine, why bother with all this if there's no real benefit to the newest driver - ie: better dual head support or better rendering.  Unless this fixes a WINE error I found listed here:
[http://ubuntuforums.org/showthread.php?p=1826422](http://ubuntuforums.org/showthread.php?p=1826422)
"libGL warning: 3D driver claims to not support visual 0x5b"

I don't see how going thru all the trouble here with the new intel driver makes any real difference.

---

### Post by djberndt on 2006-12-10
I get this error when compiling:

```
i830_xf86Crtc.c: In function 'xf86DefaultMode':
i830_xf86Crtc.c:146: error: 'M_T_PREFERRED' undeclared (first use in this function)
i830_xf86Crtc.c:146: error: (Each undeclared identifier is reported only once
i830_xf86Crtc.c:146: error: for each function it appears in.)
i830_xf86Crtc.c: In function 'xf86OutputHasPreferredMode':
i830_xf86Crtc.c:200: error: 'M_T_PREFERRED' undeclared (first use in this function)
make[3]: *** [i830_xf86Crtc.lo] Error 1
make[3]: Leaving directory `/home/djberndt/src2/xf86-video-intel/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/djberndt/src2/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/djberndt/src2/xf86-video-intel'
make: *** [all] Error 2

```
... even though i have edited the i830_modes.c. does it matter where i put the two new lines?
thanks in advance.

---

### Post by terrax on 2006-12-13
> **Karbonik said:**
> What's the point, then, really?

915 works fine, why bother with all this if there's no real benefit to the newest driver - ie: better dual head support or better rendering.  Unless this fixes a WINE error I found listed here:
[http://ubuntuforums.org/showthread.php?p=1826422](http://ubuntuforums.org/showthread.php?p=1826422)
"libGL warning: 3D driver claims to not support visual 0x5b"

I don't see how going thru all the trouble here with the new intel driver makes any real difference.

The point is, that is solves many problems connection to external devices. I can't get my plasma tv up and running proberly without this driver for an example. And other get their issue with hdtv fixed.
 
If you want the speed issue fixed. You should problable first install every mesa3d thing from this guide first: [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)

If you loose your direct rendering by that. You should proberly recompile you kernel with that driver.

But if you don't want to do all that "trouble", then just wait until it is fixed on the rep. Its up to you :-)

---

### Post by terrax on 2006-12-13
> **djberndt said:**
> I get this error when compiling:

```
i830_xf86Crtc.c: In function 'xf86DefaultMode':
i830_xf86Crtc.c:146: error: 'M_T_PREFERRED' undeclared (first use in this function)
i830_xf86Crtc.c:146: error: (Each undeclared identifier is reported only once
i830_xf86Crtc.c:146: error: for each function it appears in.)
i830_xf86Crtc.c: In function 'xf86OutputHasPreferredMode':
i830_xf86Crtc.c:200: error: 'M_T_PREFERRED' undeclared (first use in this function)
make[3]: *** [i830_xf86Crtc.lo] Error 1
make[3]: Leaving directory `/home/djberndt/src2/xf86-video-intel/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/djberndt/src2/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/djberndt/src2/xf86-video-intel'
make: *** [all] Error 2

```
... even though i have edited the i830_modes.c. does it matter where i put the two new lines?
thanks in advance.

What is the output to this command.
```

automake --version

```

---

### Post by djberndt on 2006-12-14
> **terrax said:**
> What is the output to this command.
```

automake --version

```

i succeded in compiling the modeset driver, after updating the kernel. but the compiling process was a lot faster than all the other efforts, and I never had to edit src/i830_modes.c. strange?
after rebooting the computer, the screen resolution wee set to 1200x1600 as default. i changed it back and beryl messed up, showing only half of the screen.
reboot.
now everything works fine, but there's absolutely no increase in fps. and glxgears still says "warning: 3D driver claims to not support visual 0x5b".. :-| 

maybe you don't need it anymore, but the output from "automake --version" (after  installing all the upgrades) is:
```
automake (GNU automake) 1.9.6

```

---

### Post by jrichardson on 2006-12-15
So close and yet....

[B]jerry@jerry-desktop:~/src/xf86-video-intel$ git checkout modesetting fatal: cannot open index.lock file.
jerry@jerry-desktop:~/src/xf86-video-intel$ sudo git checkout modesetting
git-checkout-index: modesetting is not in the cache
jerry@jerry-desktop:~/src/xf86-video-intel$[/B]

Tried git pull to no avail
[B]jerry@jerry-desktop:~/src/xf86-video-intel$ git pull
fatal: Needed a single revision
Pulling into a black hole?
jerry@jerry-desktop:~/src/xf86-video-intel$ sudo git pull
Password:
fatal: Needed a single revision
Pulling into a black hole?
jerry@jerry-desktop:~/src/xf86-video-intel$[/B]


Any ideas?

---

### Post by jrichardson on 2006-12-16
I have been trying to get this to work for quite a while.

Hope you can help me.

At Install Build and Compiling Tools:

jerry@jerry-desktop:~$ sudo apt-get install build-essential m4 autoconf automake1.9 libtool gcc linux-headers-`uname -r` autoconf autotools-dev cvs git bison git-svn git-cvs xorg-build-macros xorg-dev mesa-common-dev libdrm-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
gcc is already the newest version.
linux-headers-2.6.17-10-generic is already the newest version.
[COLOR="Red"]Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source[/COLOR]

There is a lack of info on git.

hope you can help

---

### Post by terrax on 2006-12-17
> **jrichardson said:**
> I have been trying to get this to work for quite a while.

Hope you can help me.

At Install Build and Compiling Tools:

jerry@jerry-desktop:~$ sudo apt-get install build-essential m4 autoconf automake1.9 libtool gcc linux-headers-`uname -r` autoconf autotools-dev cvs git bison git-svn git-cvs xorg-build-macros xorg-dev mesa-common-dev libdrm-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
gcc is already the newest version.
linux-headers-2.6.17-10-generic is already the newest version.
[COLOR="Red"]Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source[/COLOR]

There is a lack of info on git.

hope you can help

Sure you have universe and multiverse enabled?

---

### Post by jrichardson on 2006-12-17
Followed the How To's explicitly.  After 3 days, I finally gave up and got a standard 4:3 monitor.

Thanks

---

### Post by K.Mandla on 2006-12-18
(Moving to the Howtos, FAQs, Tips and Tricks area, since this is a very good howto and worthy of that special brand of immortality ... ;) )

---

### Post by jthirt on 2006-12-21
> You have to compile the latest libdrm from [www.mesa3d.org](www.mesa3d.org)

[http://mesa3d.org/install.html](http://mesa3d.org/install.html)

Follow the instructions the DRI/accelerated section.

Much to my regret, I have to give up with this as it is far too complicated for what I'm trying to acheive. ](*,) 

I am really sad now to acknowledge that linux can be overwelmingly complicated. 

I do not have the time to dig up and try to master all this complexity. 

It's not the first time I hit problems with video drivers but this time it lead me to spend far too much time trying to resolve what should be a trivial resolution issue. 

I will be more careful the next time I decide to convert a laptop to linux and if it doesn't look right with the live CD I'll forget about it. 

Still, I'm really frustrated and sad. I will not be able to return my mum's laptop in a decent condition. That's a shame. :( 

Thank you anyways for your efforts.

---

### Post by terrax on 2006-12-29
If its just a resolution problem, you could probably try 915resolution?

But I agree with you. I have never ever tried a linux dist, where the videodrivers just worked without working like a beta driver. Thats sad. Because linux really is a very good OS.

---

### Post by mrojas73 on 2006-12-30
Don't give up, do a search for 915resolution, install it and configure it.  It is much easier than this howto!

---

### Post by Praxicoide on 2007-01-06
I had to type sudo before a couple of commands but everything installed fine.

Thanks a buch!

---

### Post by DuGi on 2007-01-18
.

---

### Post by toaste on 2007-01-19
This is exactly what I need, but I cannot get it to compile!
```

In file included from ch7017.c:40:
../i830_xf86Crtc.h:261: error: expected declaration specifiers or '...' before 'RRPropertyValuePtr'

```
examining the file, we see that it's just a regular #include statement.
```

#include "../i830_xf86Crtc.h"

```
What gives?  Does the preprocessor not recognize ".."?

---

### Post by jthirt on 2007-01-20
> **mrojas73 said:**
> Don't give up, do a search for 915resolution, install it and configure it.  It is much easier than this howto!

Unfortunately, I had to try this howto because everything else failed and the only possible solution is using the modesetting driver. 915resolution did nothing for that video card. The issue is with the bios capability apparently. It doesn't make sense to me since I have managed to use the targeted resolution on an external CRT, but there you go. 

I no longer have the laptop in question and it's user (my mother) has not yet realised she's not using the laptops native resolution ! For what se does so far, it's not a big deal, but it would help it I could solve that issue one day. Maybe Feisty will include the latest driver and it will work out of the box !

But for now, the machine is 800kms away, so I will not touch it remotely with video consequences ...

---

### Post by j0sh0 on 2007-01-22
Hi, I am having the same compiling issues as toaste. after doing "sudo make", i get the following error:
<code>
In file included from ch7017.c:40:
../i830_xf86Crtc.h:261: error: expected declaration specifiers or '...' before 'RRPropertyValuePtr'
make[3]: *** [ch7017.lo] Error 1
make[3]: Leaving directory `/home/josh/src/xf86-video-intel/src/ch7017'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/josh/src/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josh/src/xf86-video-intel'
make: *** [all] Error 2
</code>

the output from "automake --version" is

<code>
automake (GNU automake) 1.9.6
Written by Tom Tromey <tromey@redhat.com>.

Copyright 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
</code>

Please any help to solve this would be greatly appreciated! I'm in much the same boat as jthirt: I've tried different drivers, 915resolution... nothing will allow me to open X in 1024x768 (a resolution that is actually reported by the vbios!!!). This is, I presume, my last option other than purchasing a new laptop...

Regards

j0sh0

---

### Post by Praxicoide on 2007-01-23
Hi,

I installed this previously, but then I broke my install trying to intall some unrelated driver and had to reinstall Ubuntu again (except for my home folder which I placed on a different partition).

Anyways, I'm trying to install this again. However:

```
:~/src/xf86-video-intel$ git checkout modesetting
fatal: unable to create new cachefile
fatal: unable to create new index file

```

apparently I "need to solve my current index first".

Can anybody help me?

---

### Post by j0sh0 on 2007-01-23
Praxicoide: Have you tried the command with sudo infront of it?

---

### Post by Praxicoide on 2007-01-25
Yes, it says that I need to solve my current index.

What does that mean, and how do I do that?

---

### Post by toaste on 2007-01-29
Praxicoide: I ended up deleting the folder for xf86-video-intel and re-cloning it using git.  I checked out the modesetting driver and it compiled without complaint.

Unfortunately, I got no video after installing and rebooting.  For the record, if this doesn't go so well you can undo the damage by (assuming you cloned the git repository from your home directory):

```
cd ~/xf86-video-intel
sudo make uninstall
sudo apt-get install --reinstall xserver-xorg-video-i810
```

---

### Post by Praxicoide on 2007-01-29
Thanks, I guess I'll have to do the same.

I hope it doesn't break the X.

---

### Post by toaste on 2007-01-30
Sooo close!  I pulled the git repos for the latest xf86-video-intel modesetting branch and libdrm, compiled, installed, and restarted the my machine.

I got my monitor's native 1680x1050 on the login screen.

Now, this resolution isn't in my xorg.conf file, but I really didn't question it much since I was so darn excited to see it.  Unfortunately, the refresh rate goes out of range (flat panel only accepts 60hz at this resolution) shortly after I log in.

What does this driver use to configure the resolution?  It completely ignored the sync ranges and resolutions I had specified in my xorg.conf, which bothers me just a little.


Edit: for recent commits and changes, the shortlog is here.  The trunk is under active development and bug fixes or changes were probably submitted mere hours ago:
[http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=shortlog;h=modesetting](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=shortlog;h=modesetting)

---

### Post by mankanit on 2007-02-03
Thanks!
I have a 22" Fujitsu-Siemens L22W-3.
It works perfect. No compiling error.

Regards!

---

### Post by micekiller on 2007-02-05
For anyone messing around with the git repositories I finally got it to run by doing:
> 
git-clone git://gitweb.freedesktop.org/git/xorg/driver/xf86-video-intel
cd xf86-video-intel
git checkout modesetting
git-pull -s ours
./autogen.sh --prefix=/usr
make
sudo make install


Works just fine on Samsung SyncMaster 215TW (running debian unstable).

---

### Post by twoseids on 2007-02-11
Just upgraded to Edgy and have an update (915resolution) that won't go through (subprocess new pre-removal script returned error exit status 127). So I tried this fix here, but have a problem not mentioned so far in this forum.

After typing:

```
sudo git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel

```

It hangs in limbo for a while, and then returns:

```
fatal: unable to connect a socket (Connection timed out)
fetch-pack from 'git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel' failed.
```

Any ideas?

---

### Post by twoseids on 2007-02-14
Bueller? Bueller?

---

### Post by kobewan on 2007-02-14
All I can think of is try again, and make sure you have internet access.

So is there any way of knowing which driver I'm running? I don't think that the install worked, but it might have. It doesn't really effect me, since I was already at my monitor's maximum resolution of 1024x786.

---

### Post by twoseids on 2007-02-15
> **kobewan said:**
> All I can think of is try again, and make sure you have internet access.

So is there any way of knowing which driver I'm running? I don't think that the install worked, but it might have. It doesn't really effect me, since I was already at my monitor's maximum resolution of 1024x786.
I do have internet access, but could it be that my company's IT department has somehow blocked the kind of download I'm attempting here? I have never used *git* before so I don't really know how it works.

---

### Post by sameersegal on 2007-02-19
> **jambes said:**
> I got this error in Edgy:

In file included from i810.h:58,
                 from i810_accel.c:55:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from i810.h:58,
                 from i810_accel.c:55:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before 'GLboolean'
make[3]: *** [i810_accel.lo] Error 1
make[3]: Leaving directory `/home/jambes/source/intel-modesetting/xf86-video-intel/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jambes/source/intel-modesetting/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jambes/source/intel-modesetting/xf86-video-intel'
make: *** [all] Error 2


I am facing the same problem....anyone any idea??
sameer

---

### Post by asantainnasa on 2007-02-20
i got this error
> a@weiPC:~/src/xf86-video-intel$ sudo make
make  all-recursive
make[1]: Entering directory `/home/asantainnasa/src/xf86-video-intel'
Making all in src
make[2]: Entering directory `/home/asantainnasa/src/xf86-video-intel/src'
Making all in xvmc
make[3]: Entering directory `/home/asantainnasa/src/xf86-video-intel/src/xvmc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/asantainnasa/src/xf86-video-intel/src/xvmc'
Making all in bios_reader
make[3]: Entering directory `/home/asantainnasa/src/xf86-video-intel/src/bios_reader'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/asantainnasa/src/xf86-video-intel/src/bios_reader'
Making all in ch7017
make[3]: Entering directory `/home/asantainnasa/src/xf86-video-intel/src/ch7017'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..    -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -I./.. -I./../modes -g -O2 -MT ch7017.lo -MD -MP -MF ".deps/ch7017.Tpo" -c -o ch7017.lo ch7017.c; \
        then mv -f ".deps/ch7017.Tpo" ".deps/ch7017.Plo"; else rm -f ".deps/ch7017.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -I./.. -I./../modes -g -O2 -MT ch7017.lo -MD -MP -MF .deps/ch7017.Tpo -c ch7017.c  -fPIC -DPIC -o .libs/ch7017.o
ch7017.c:40:22: error: xf86Crtc.h: No such file or directory
In file included from ch7017.c:44:
../i2c_vid.h:7: error: expected specifier-qualifier-list before 'xf86OutputStatus'
ch7017.c:130: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ch7017_detect'
ch7017.c:295: error: unknown field 'detect' specified in initializer
ch7017.c:295: error: 'ch7017_detect' undeclared here (not in a function)
ch7017.c:295: warning: excess elements in struct initializer
ch7017.c:295: warning: (near initialization for 'ch7017_methods')
ch7017.c:296: error: unknown field 'mode_valid' specified in initializer
ch7017.c:296: warning: excess elements in struct initializer
ch7017.c:296: warning: (near initialization for 'ch7017_methods')
ch7017.c:297: error: unknown field 'mode_set' specified in initializer
ch7017.c:297: warning: excess elements in struct initializer
ch7017.c:297: warning: (near initialization for 'ch7017_methods')
ch7017.c:298: error: unknown field 'dpms' specified in initializer
ch7017.c:298: warning: excess elements in struct initializer
ch7017.c:298: warning: (near initialization for 'ch7017_methods')
ch7017.c:299: error: unknown field 'dump_regs' specified in initializer
ch7017.c:299: warning: excess elements in struct initializer
ch7017.c:299: warning: (near initialization for 'ch7017_methods')
ch7017.c:300: error: unknown field 'save' specified in initializer
ch7017.c:300: warning: excess elements in struct initializer
ch7017.c:300: warning: (near initialization for 'ch7017_methods')
ch7017.c:301: error: unknown field 'restore' specified in initializer
ch7017.c:301: warning: excess elements in struct initializer
ch7017.c:301: warning: (near initialization for 'ch7017_methods')
make[3]: *** [ch7017.lo] Error 1
make[3]: Leaving directory `/home/asantainnasa/src/xf86-video-intel/src/ch7017'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/asantainnasa/src/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/asantainnasa/src/xf86-video-intel'
make: *** [all] Error 2


any help?

---

### Post by j0sh0 on 2007-02-21
Hi,
I'm trying again, however now I get this error with the "autogen" step:

**"configure: error: Must have X server >= 1.3 source tree for mode setting code. Please specify --with-xserver-source"**

I have no idea how to resolve this! Any help greatly appreciated!

---

### Post by twoseids on 2007-02-24
> **j0sh0 said:**
> Hi,
I'm trying again, however now I get this error with the "autogen" step:

**"configure: error: Must have X server >= 1.3 source tree for mode setting code. Please specify --with-xserver-source"**

I have no idea how to resolve this! Any help greatly appreciated!
Same problem here.

---

### Post by jbebel on 2007-02-26
This seems to be a recent change:
[recent change]("http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=5a1a04649c62aa4b1c0617560b813642ce0c67b5")
The modesetting driver requires the xserver 1.3, which ubuntu doesn't have, since it's still developmental.  You can probably build the xserver yourself, or you can check out an older version of the modesetting branch that doesn't depend on xserver 1.3.

---

### Post by bumbles on 2007-03-01
I've successfully compiled the driver WITHOUT the modesetting branch, having installed the list of packages in the original HOWTO.

Also, I installed libdrm 2.2 from source, which worked fine as long as you do ./configure --prefix=/usr before running make.

However, all this being done, I should now have a new i810 driver, right? Cause I'm still in the same position I was.

My setup (work PC) is Dell Optiplex 745 running Intel 965Q graphics, with a DVI extension running into a Dell 2407WFP monitor - native res is 1920x1200, but the best I've been able to get is 1600x1200.

The VGA port of the graphics setup is shown to be PCI:0:2:0, whereas the DVI extension card is PCI:0:2:1. When X starts I get a message in the log about not having a Device declaration for PCI:0:2:1. I added a declaration in xorg.conf but the message is still there.

/etc/X11/xorg.conf:

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "Device"
        Identifier      "Generic Video Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        131072
        Option          "UseFBDev"              "true"
EndSection

Section "Device"
        Identifier      "DVI"
        Driver          "i810"
        BusID           "PCI:0:2:1"
        VideoRam        131072
        Option          "UseFBDev"              "true"
EndSection

## Culled from a thread on some forum somewhere...
Section "Monitor"
 Identifier "DELL 2407WFP"
 HorizSync 30 - 81
 VertRefresh 56 - 76
 ModeLine "1920x1200" 154.1 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync
 ModeLine "1600x1200" 161.0 1600 1704 1880 2160 1200 1201 1204 1242 -hsync +vsync
 ModeLine "1280x1024" 138.5 1280 1368 1504 1728 1024 1025 1028 1069 -hsync +vsync
 ModeLine "1024x768" 81.8 1024 1080 1192 1360 768 769 772 802 -hsync +vsync
 ModeLine "800x600" 48.9 800 840 920 1040 600 601 604 627 -hsync +vsync
 ModeLine "640x480" 30.7 640 664 728 816 480 481 484 502 -hsync +vsync
 Option "DPMS"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-130
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "DELL 2407WFP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

If I do "grep WW /var/log/Xorg.0.log" I get:

(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Failed to set up write-combining range (0xc0000000,0x10000000)
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
(WW) I810(0): Option "UseFBDev" is not used
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

Also, grepping for "1920" in the log gets me:

(II) I810(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) I810(0): Not using mode "1920x1200" (no mode of this name)

Can anyone help me? I'm sure I'm almost there!

Thanks,

B.

---

### Post by toaste on 2007-03-01
To get most widescreen resolutions out of the intel 965 graphics, you will need either a modified version of 915resolution to modify your video bios or you need to compile the (still experimental, still very much being worked on, may have changes made less than 2 hours ago when you check out the code) modesetting driver.

Patching 915 resolution and temporarily replacing a video mode you won't use (they revert back at reboot) did work for me, and might be an option if you can't pull an older version of the source for the modesetting driver that will compile on edgy.  Here's to hoping modesetting becomes stable enough that an exception is made to shoehorn it into feisty -- on the upside, 3D acceleration and compiz are reported to be working out of the box.

[915 resolution homepage]("http://www.geocities.com/stomljen/")
[Link to the thread with the 965 patch]("http://lists.freedesktop.org/archives/xorg/2006-October/018926.html")

---

### Post by bumbles on 2007-03-01
Many thanks for your reply toaste.

You know what? When the hackers who are putting this together confess that it's a damn ugly hack, I know to wait for proper support! I'm probably going to try and get a new gfx card through work and stick it in this Dell. 

All the best,

Bumbles.

---

### Post by toaste on 2007-03-01
915 resolution worked well with my system until I got the modesetting driver to compile and install.  After the modesetting driver, I used [read-edid]("http://john.fremlin.de/programs/linux/read-edid/") to make a mode line to stick in my xorg.conf file from the monitor's plug and play data and life was good.

If you do go for a discrete graphics card, be aware that some systems have to have the "agp=off" option added to the boot command in the grub menu or the kernel will panic on boot.  And for God's sake, don't give yourself the headache of dealing with an ATI card under Linux!

---

### Post by Haizman on 2007-03-01
Using Teraxx's guide I successfully installed this Intel driver on a Dell Optiplex 745 (GMA 3000 965 chipset) on Kubuntu 6.1, but was not successful when I tried it with Ubuntu 6.1.  When it worked it was great, I didn't have to edit xorg.conf with a custom modeline (I'm using an Acer AL1916W widescreen 19" monitor_native resolution is 1440 x 900).  But I did something (not sure) that made it not work anymore.

Like a few others have posted, in Ubuntu 6.1 I get stopped with this error:

 **configure: error: Must have X server >= 1.3 source tree for mode setting code. Please specify --with-xserver-source**

Does anyone know if the latest Kubuntu has the 1.3 xserver or has the driver code actually changed since it was first distributed?

I really want to use this new Dell for my work Linux box, but perhaps the hardware is too immature at this point?  I don't want to give up the widescreen monitor either.  If anyone out there has any ideas that would be great!

Thanks!
Haizman

---

### Post by simianstyle on 2007-03-01
I've got the same error as Haizman:

[B]configure: error: Must have X server >= 1.3 source tree for mode setting code. Please specify --with-xserver-source
[/B]

I also tried to skip the step

```
git checkout modesetting
```

however, it keeps telling me 

[B]Requested 'libdrm >= 2.2' but version of libdrm is 2.0.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRI_CFLAGS
and DRI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

any suggestions?

PS: I've also installed version 2.2 of libdrm with "./configure --prefix=/usr", and yet for some reason it still won't work with the latest version of the drivers.

---

### Post by bumbles on 2007-03-02
> **toaste said:**
> 915 resolution worked well with my system until I got the modesetting driver to compile and install.  After the modesetting driver, I used [read-edid]("http://john.fremlin.de/programs/linux/read-edid/") to make a mode line to stick in my xorg.conf file from the monitor's plug and play data and life was good.

If you do go for a discrete graphics card, be aware that some systems have to have the "agp=off" option added to the boot command in the grub menu or the kernel will panic on boot.  And for God's sake, don't give yourself the headache of dealing with an ATI card under Linux!

Thanks for the ATI tip - just compiled read-edid and it works a treat, will try this on the work PC and see if it corresponds with my previously used modeline.

As far as I can see the agp=off flag isn't there on my Edgy system, and besides, these new Dells don't come with AGP, it's PCI-E or PCI for graphics. No ATA bus either, these really are next-gen boxes!

Edit: bugger, just tried to build read-edid and realised I've installed Edgy x64 at work! Thought I'd take advantage of the Core 2 Duo...anyway it's x86 only. Anyone out there got read-edid output for the Dell 2407WFP? (I'll Google and report back.)

Edit: FWIW I've switched to VGA output, just to discount any strangeness with the DVI port. The display seems to be crisper and a bit brighter, but the resolution is the same....

Edit: Found an old ATI X550 lying around the server room. Installed it, installed the ATI driver, reboot, now got 1920x1200 on VGA. Will try DVI next. Nice!

Edit: I know this is gloating but DVI also works, but I can't get XGL or Beryl with the official driver...there's always something else with Linux... :-)

---

### Post by bumbles on 2007-03-02
> **simianstyle said:**
> I've got the same error as Haizman:

[B]configure: error: Must have X server >= 1.3 source tree for mode setting code. Please specify --with-xserver-source
[/B]

I also tried to skip the step

```
git checkout modesetting
```

however, it keeps telling me 

[B]Requested 'libdrm >= 2.2' but version of libdrm is 2.0.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRI_CFLAGS
and DRI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

any suggestions?

PS: I've also installed version 2.2 of libdrm with "./configure --prefix=/usr", and yet for some reason it still won't work with the latest version of the drivers.

I also did not download the modesetting branch, and the driver compiled OK once I'd deleted and re-gitted the source, without the modesetting branch. Now I'm thinking I need to get that branch to get it going!

I downloaded a tar.gz of libdrm2.2, configured it as above and it seemed to install fine. It wouldn't hurt immensely to reconfigure and recompile libdrm2.2 so it's definitely in /usr/lib.

---

### Post by toaste on 2007-03-19
The default branch for the Intel repos will download the source to the latest version of their normal driver.  That is, it won't have any resolution-changing voodoo.

The modesetting driver now depends on the version of xserver included in xorg 7.2, which will come with Feisty in the future.  Essentially, the driver is still in development (I don't even know if they're yet two thirds of the way done with it, but there is code submitted on roughly a daily basis) and Intel chose to make use of some shiny new features in the latest xorg (that they wrote) in their driver -- _[you can read all about it at this link]("http://keithp.com/blog/randr_1.2_update.html")_.  However, it means that **the lastest versions of the modesetting driver won't compile for edgy**.

However, if you can use git more adeptly than I can (no huge feat), you might be able to download an old snapshot of the source code that will compile with edgy.  Poking around the git commits for one mentioning "distro check" iirc should get you what you need to pull before.  After that, you'd just need to keep rolling back commits until it compiles (as a result of the changes made on some days, it might not)

---

### Post by thatoneguy297 on 2007-04-02
One step closer!

The

```
./autogen.sh --prefix=/usr
```

was pointing to the wrong directory, as pointed out by an email between programmers [here]("http://lists.freedesktop.org/archives/xorg/2007-March/022215.html").

Instead, use

```
./configure --prefix=/usr --with-xserver-source=../xserver
```

and it should configure without complaining about not having version 1.3

Hooray! One more step closer to having widescreen support on my beautiful 32" LCD HDTV!

But!

I try to make it, and this spits out:

```
corey@Ubuntu:~/src/xf86-video-intel$ sudo make
make  all-recursive
make[1]: Entering directory `/home/corey/src/xf86-video-intel'
Making all in src
make[2]: Entering directory `/home/corey/src/xf86-video-intel/src'
Making all in xvmc
make[3]: Entering directory `/home/corey/src/xf86-video-intel/src/xvmc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/corey/src/xf86-video-intel/src/xvmc'
Making all in bios_reader
make[3]: Entering directory `/home/corey/src/xf86-video-intel/src/bios_reader'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/corey/src/xf86-video-intel/src/bios_reader'
Making all in ch7017
make[3]: Entering directory `/home/corey/src/xf86-video-intel/src/ch7017'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..    -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -I./.. -I./../modes -g -O2 -MT ch7017.lo -MD -MP -MF ".deps/ch7017.Tpo" -c -o ch7017.lo ch7017.c; \
        then mv -f ".deps/ch7017.Tpo" ".deps/ch7017.Plo"; else rm -f ".deps/ch7017.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -I./.. -I./../modes -g -O2 -MT ch7017.lo -MD -MP -MF .deps/ch7017.Tpo -c ch7017.c  -fPIC -DPIC -o .libs/ch7017.o
ch7017.c:40:22: error: xf86Crtc.h: No such file or directory
In file included from ch7017.c:44:
../i2c_vid.h:7: error: expected specifier-qualifier-list before 'xf86OutputStatus'
ch7017.c:130: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ch7017_detect'
ch7017.c:295: error: unknown field 'detect' specified in initializer
ch7017.c:295: error: 'ch7017_detect' undeclared here (not in a function)
ch7017.c:295: warning: excess elements in struct initializer
ch7017.c:295: warning: (near initialization for 'ch7017_methods')
ch7017.c:296: error: unknown field 'mode_valid' specified in initializer
ch7017.c:296: warning: excess elements in struct initializer
ch7017.c:296: warning: (near initialization for 'ch7017_methods')
ch7017.c:297: error: unknown field 'mode_set' specified in initializer
ch7017.c:297: warning: excess elements in struct initializer
ch7017.c:297: warning: (near initialization for 'ch7017_methods')
ch7017.c:298: error: unknown field 'dpms' specified in initializer
ch7017.c:298: warning: excess elements in struct initializer
ch7017.c:298: warning: (near initialization for 'ch7017_methods')
ch7017.c:299: error: unknown field 'dump_regs' specified in initializer
ch7017.c:299: warning: excess elements in struct initializer
ch7017.c:299: warning: (near initialization for 'ch7017_methods')
ch7017.c:300: error: unknown field 'save' specified in initializer
ch7017.c:300: warning: excess elements in struct initializer
ch7017.c:300: warning: (near initialization for 'ch7017_methods')
ch7017.c:301: error: unknown field 'restore' specified in initializer
ch7017.c:301: warning: excess elements in struct initializer
ch7017.c:301: warning: (near initialization for 'ch7017_methods')
make[3]: *** [ch7017.lo] Error 1
make[3]: Leaving directory `/home/corey/src/xf86-video-intel/src/ch7017'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/corey/src/xf86-video-intel/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/corey/src/xf86-video-intel'
make: *** [all] Error 2
corey@Ubuntu:~/src/xf86-video-intel$ 
```

So, uh... SOMETHING happened! So I tried to install anyways...

```
corey@Ubuntu:~/src/xf86-video-intel$ sudo make install
Making install in src
make[1]: Entering directory `/home/corey/src/xf86-video-intel/src'
Making install in xvmc
make[2]: Entering directory `/home/corey/src/xf86-video-intel/src/xvmc'
make[3]: Entering directory `/home/corey/src/xf86-video-intel/src/xvmc'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libI810XvMC.la' '/usr/lib/libI810XvMC.la'
/usr/bin/install -c .libs/libI810XvMC.so.1.0.0 /usr/lib/libI810XvMC.so.1.0.0
(cd /usr/lib && { ln -s -f libI810XvMC.so.1.0.0 libI810XvMC.so.1 || { rm -f libI810XvMC.so.1 && ln -s libI810XvMC.so.1.0.0 libI810XvMC.so.1; }; })
(cd /usr/lib && { ln -s -f libI810XvMC.so.1.0.0 libI810XvMC.so || { rm -f libI810XvMC.so && ln -s libI810XvMC.so.1.0.0 libI810XvMC.so; }; })
/usr/bin/install -c .libs/libI810XvMC.lai /usr/lib/libI810XvMC.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/corey/src/xf86-video-intel/src/xvmc'
make[2]: Leaving directory `/home/corey/src/xf86-video-intel/src/xvmc'
Making install in bios_reader
make[2]: Entering directory `/home/corey/src/xf86-video-intel/src/bios_reader'
make[3]: Entering directory `/home/corey/src/xf86-video-intel/src/bios_reader'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/corey/src/xf86-video-intel/src/bios_reader'
make[2]: Leaving directory `/home/corey/src/xf86-video-intel/src/bios_reader'
Making install in ch7017
make[2]: Entering directory `/home/corey/src/xf86-video-intel/src/ch7017'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..    -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -I./.. -I./../modes -g -O2 -MT ch7017.lo -MD -MP -MF ".deps/ch7017.Tpo" -c -o ch7017.lo ch7017.c; \
        then mv -f ".deps/ch7017.Tpo" ".deps/ch7017.Plo"; else rm -f ".deps/ch7017.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -I./.. -I./../modes -g -O2 -MT ch7017.lo -MD -MP -MF .deps/ch7017.Tpo -c ch7017.c  -fPIC -DPIC -o .libs/ch7017.o
ch7017.c:40:22: error: xf86Crtc.h: No such file or directory
In file included from ch7017.c:44:
../i2c_vid.h:7: error: expected specifier-qualifier-list before 'xf86OutputStatus'
ch7017.c:130: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ch7017_detect'
ch7017.c:295: error: unknown field 'detect' specified in initializer
ch7017.c:295: error: 'ch7017_detect' undeclared here (not in a function)
ch7017.c:295: warning: excess elements in struct initializer
ch7017.c:295: warning: (near initialization for 'ch7017_methods')
ch7017.c:296: error: unknown field 'mode_valid' specified in initializer
ch7017.c:296: warning: excess elements in struct initializer
ch7017.c:296: warning: (near initialization for 'ch7017_methods')
ch7017.c:297: error: unknown field 'mode_set' specified in initializer
ch7017.c:297: warning: excess elements in struct initializer
ch7017.c:297: warning: (near initialization for 'ch7017_methods')
ch7017.c:298: error: unknown field 'dpms' specified in initializer
ch7017.c:298: warning: excess elements in struct initializer
ch7017.c:298: warning: (near initialization for 'ch7017_methods')
ch7017.c:299: error: unknown field 'dump_regs' specified in initializer
ch7017.c:299: warning: excess elements in struct initializer
ch7017.c:299: warning: (near initialization for 'ch7017_methods')
ch7017.c:300: error: unknown field 'save' specified in initializer
ch7017.c:300: warning: excess elements in struct initializer
ch7017.c:300: warning: (near initialization for 'ch7017_methods')
ch7017.c:301: error: unknown field 'restore' specified in initializer
ch7017.c:301: warning: excess elements in struct initializer
ch7017.c:301: warning: (near initialization for 'ch7017_methods')
make[2]: *** [ch7017.lo] Error 1
make[2]: Leaving directory `/home/corey/src/xf86-video-intel/src/ch7017'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/corey/src/xf86-video-intel/src'
make: *** [install-recursive] Error 1
corey@Ubuntu:~/src/xf86-video-intel$ 
```

That's new!

I just started using Linux -this week-, so a vast majority of this is purely logarithmic -- blind following on my part. Anyone have a clue what is causing these errors, and how to fix it? I'd REALLY love to have widescreen on my bigscreen, otherwise I'm going to play around with Debian, which is... okay, that was a lie, Debian scares me. I'll stay with Ubuntu, but please, any ideas?

---

### Post by toaste on 2007-04-02
thatoneguy297,

This driver will probably be more relevant when Edgy is out, but for now you can scroll back through the comments in this thread to find where I linked a patch for i915res, which will allow you to alter one of the limited possible resolutions to the native resolution of your monitor.

The disadvantage to using i915 resolution is that the change won't survive a reboot, so you'll either need to put the commands in a script that runs on startup or just redo it every boot.  Intel's experimental modesetting driver doesn't suffer these drawbacks, but at the same time, it makes use of some features only available in xorg 7.2 so forcing the install around this requirement probably won't leave you with a functioning system.

---

### Post by thatoneguy297 on 2007-04-02
I've tried on multiple occasions to get the 915resolution hack to work, to no avail.

I'll go through it step by step one more time to see if I'm doing something wrong.

```
corey@Ubuntu:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $3de
Mode Table Entries: 18

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

So far so good. I'll change the Mode 38, just like in the example on the site.

```
corey@Ubuntu:~$ sudo 915resolution 38 1366 768
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $3de
Mode Table Entries: 18

Patch mode 38 to resolution 1366x768 complete
corey@Ubuntu:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $3de
Mode Table Entries: 18

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1366x768, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1366x768, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1366x768, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

No problem there - the resolution I want is inserted into the lines that I don't use.

So from there, I edit my xorg file...

```
corey@Ubuntu:~$ sudo gedit /etc/X11/xorg.conf
```

Which has the following:

```
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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"32MAA-H6A"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"32MAA-H6A"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1366x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Awesomesauce. Moving on, I add the startup script so I don't have to run this hack every time I start up X.

```
corey@Ubuntu:~$ sudo gedit /etc/init.d/boot.local
```

The file was blank, so the entire contents are what I copied and pasted from the [readme on the site]("http://www.geocities.com/stomljen/readme.html"), with the pertinent parts edited:

```
#! /bin/sh
#
# Copyright (c) 2002 SuSE Linux AG Nuernberg, Germany.  All rights reserved.
#
# Author: Werner Fink , 1996
#  Burchard Steinbild, 1996
#
# /etc/init.d/boot.local
#
# script with local commands to be executed from init on system startup
#
# Here you should add things, that should happen directly after booting
# before we're going to the first run level.
#

/usr/bin/915resolution 38 1366 768 24
```

Then CTRL+ALT+Backspace to restart X aaaaaand....

Input out of range.

I've edited the xorg file, 915resolution and the boot script to reflect every single listed resolution one at a time that my HDTV's manual says it supports:

1366x768
1280x768
1280x1024

I even tried 1368x768, since that's what my old Windows XP partition identified it as!

After every edit, I'd hit CTRL+ALT+Backspace, and it would be out of range. So I'd hit CTRL+ALT+F1 to go into the console, edit all three parts with nano, then hit CTRL+ALT+F7 to return to X, then CTRL+ALT+Backspace to reboot X once more. Every time it's set to higher than 1024x768, my monitor says it can't read the input. 

The manual says that all resolutions are 24 bits, 60Hz.

Would someone please tell me what else might be going wrong? The monitor has run at 1368x768 with Windows XP, so I know that it is capable. What's the matter?

---

### Post by T.E.N. on 2007-04-14
> **micekiller said:**
> For anyone messing around with the git repositories I finally got it to run by doing:
```
git-clone git://gitweb.freedesktop.org/git/xorg/driver/xf86-video-intel
cd xf86-video-intel
git checkout modesetting
git-pull -s ours
./autogen.sh --prefix=/usr
make
sudo make install
```
Works just fine on Samsung SyncMaster 215TW (running debian unstable).
Thanks for sharing your experience in getting this to work (cf. also [http://l4x.org/28171](http://l4x.org/28171)).

On Ubuntu 6.10 (where DDC over DVI for the standard i810 and intel drivers is broken without a doubt), however, at least the following seems to be required first:
```
apt-get install xorg-dev git-core cogito autogen automake1.9 build-essential libtool
update-alternatives --config git
```...then select git-scm.
Some of these requirements are listed on the first pages of thread (as things stood half a year ago), but since the dependencies are complex enough to take a while to figure out, they are probably worth mentioning for the next users growing grey hair over how to use resolutions such as 1680*1050 (one also might need to select all entries of "System/Administration/Synaptic Package Manager" under "Settings/Repositories" at the start).

Nonetheless, however, I do get stuck with the modesetting branch of recent weeks still not compiling, even when autogen has been invoked using "--with-xserver-source", due to a missing xf86Crtc.h - so the final step required seems to be to either[LIST=1]
[*]upgrade to "X server >= 1.3 source tree for mode setting code"
[*]downgrade to / checkout an earlier version of the modesetting branch from the git server (or as archived the last time someone actually got it to compile on current Ubuntu) - any "walk-through" instructions appreciated!
[/LIST]

---

### Post by NilsE on 2007-04-19
> **thatoneguy297 said:**
> 
```
#! /bin/sh
#
# Copyright (c) 2002 SuSE Linux AG Nuernberg, Germany.  All rights reserved.
#
# Author: Werner Fink , 1996
#  Burchard Steinbild, 1996
#
# /etc/init.d/boot.local
#
# script with local commands to be executed from init on system startup
#
# Here you should add things, that should happen directly after booting
# before we're going to the first run level.
#

/usr/bin/915resolution 38 1366 768 24
```

What's the matter?

Put SUDO in the script in front of the 915resolution command. It may not get executed since it requires root permissions. Also, you don't need the /usr/bin/ either.  

SUDO 915resolution 38 1366 768 24  

Should work

---

### Post by T.E.N. on 2007-05-06
> **T.E.N. said:**
> Thanks for sharing your experience in getting this to work (cf. also [http://l4x.org/28171](http://l4x.org/28171)).

On Ubuntu 6.10 (where DDC over DVI for the standard i810 and intel drivers is broken without a doubt), however, at least the following seems to be required first:
```
apt-get install xorg-dev git-core cogito autogen automake1.9 build-essential libtool
update-alternatives --config git
```...then select git-scm.

[...] the modesetting branch of recent weeks [is] still not compiling, even when autogen has been invoked using "--with-xserver-source", due to a missing xf86Crtc.h - so the final step required seems to be to either[LIST=1]
[*]upgrade to "X server >= 1.3 source tree for mode setting code"
[*]downgrade to / checkout an earlier version of the modesetting branch from the git server (or as archived the last time someone actually got it to compile on current Ubuntu) - any "walk-through" instructions appreciated!
[/LIST]
apt-get install xserver-xorg-video-intel
gets you a working intel driver (replacing i810) for 1680*1050 on Ubuntu 7.04 "Feisty Fawn",
cf. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/106552](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/106552)

---

### Post by JoSch on 2007-05-16
> **thatoneguy297 said:**
> I've tried on multiple occasions to get the 915resolution hack to work, to no avail.

[...]

Input out of range.

I've edited the xorg file, 915resolution and the boot script to reflect every single listed resolution one at a time that my HDTV's manual says it supports:

1366x768
1280x768
1280x1024

I even tried 1368x768, since that's what my old Windows XP partition identified it as!

After every edit, I'd hit CTRL+ALT+Backspace, and it would be out of range. So I'd hit CTRL+ALT+F1 to go into the console, edit all three parts with nano, then hit CTRL+ALT+F7 to return to X, then CTRL+ALT+Backspace to reboot X once more. Every time it's set to higher than 1024x768, my monitor says it can't read the input. 

The manual says that all resolutions are 24 bits, 60Hz.

Would someone please tell me what else might be going wrong? The monitor has run at 1368x768 with Windows XP, so I know that it is capable. What's the matter?

I tried the same with my 1366x768 tv set. Got the same problems... tried even more things but with edgy I was stuck to 1280x768. With feisty I'm unable to get more then 1024x768.
I followed every tutorial I found and still no luck.
btw: have a look at /etc/default/915resolution

---

### Post by toaste on 2007-05-19
Feisty includes a version of this driver in the repositories.  It's not the absolute bleeding edge many are searching for, but it did solve my resolution problems and will run Beryl.  If you still have a monitor that won't "take" then install the package "read-edid" and google (or read the man page) for some pretty straight forward instructions to get it to generate a mode line to stick in your xorg.conf file (after making a backup!).  Good luck. 

```

sudo apt-get install xserver-xorg-video-intel

```

---

### Post by gottferdamnt on 2007-08-02
Is this how-to can be used on feisty?

---

### Post by toaste on 2007-08-04
gottferdamnt:

No -- the process in the howto won't work anymore since Intel started writing their driver to take advantage of some new features in versions of the xserver too recent to be included in feisty.  

But you can still get a more recent version of Intel's driver.  It'll let you enable desktop-effects or display widescreen resolutions on your GMA-x3000 based card.

To install this driver, you will need to enable the Universe software repository.  If you need help with that, read the instructions here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Now, as in my post above, you can either install the package from Synaptic (it's named "xserver-xorg-video-intel"), or use the command below in a terminal to get the job done:

```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by shantanubhadoria on 2008-09-28
I used this site [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html) for getting the latest official intel drivers for my presario c770TU with intel 965 GM earlier.
currently trying out your way will post back

---

