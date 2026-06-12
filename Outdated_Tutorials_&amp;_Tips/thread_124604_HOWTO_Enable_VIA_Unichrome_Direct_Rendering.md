---
title: "HOWTO Enable VIA Unichrome Direct Rendering"
date: 2006-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-02-01
This is based on the Hoary instructions at:  [http://ubuntuforums.org/showthread.php?t=39349](http://ubuntuforums.org/showthread.php?t=39349)

but mainly on the info at: [http://www.ubuntulinux.se/node/164](http://www.ubuntulinux.se/node/164)

I found it needed a few changes to make it work (and the current Breezy VIA drivers don't seem to need the Unichrome project stuff).

It seemed to work fine on my system (**which already worked with the VIA drivers**), but if any other VIA UNICHROME users would like to try it and report back, I will make any necessary modifications.

Use "glxinfo" and "glxgears -printfps" to test if the hardware acceleration is actually working afterwards!

**Modify** and save the script under whatever name you like, and 'chown root' & 'chmod 744' it so it will run only under root.

```
 #!/bin/sh
 #
 # Unichrome 3d-HOWTO for Ubuntu 5.10 (Breezy)
 #
 # This script is a modification of the Hoary one at: http://www.ubuntulinux.se/node/164
 # The current Breezy kernel and VIA drivers seem to make the latter part of that script redundant.
 #
 # These instructions are based on the Unichrome 3d-HOWTO posted here:  http://sourceforge.net/docman/?group_id=102048
 #
 # This script must be run as root. Maybe you can "sudo" it but I have a root login and do not use sudo.
 #
 # Make sure the linux kernel headers for your current kernel are installed!!!!
 # You must also have the following packages installed (all of this is best done using Synaptic):
 # gcc-3.4 build-essential
 #
 # Before running this script, download and extract this file into a "install" directory under your Home directory:
 #
 # The latest via-YYYYMMDD-linux.i386.tar.bz2
 # (where YYYYMMDD is the date part of the filename!) can be found here:
 # http://dri.freedesktop.org/snapshots/
 #
 # STEP 1. Set the directory where the install files have been  extracted
 #         (from the file browser I right-clicked on the file  and clicked on "extract here")
 #         (this extracts the files to a subdirectory  fileName_FILES)
 # *** edit these two lines and then run the script:
 #
 # Example: dir=/home/dc/install (my user login is "dc")
 dir=/home/your-directory-name/install
 #
 # Edit this with the actual date data of your downloaded file!
 # Example: file=20060131
 file=YYYYMMDD
 #
 # This gets your current kernel running version,
 # (and you have installed the kernel headers for this exact version, haven't you?.....):
 ver=`uname -a | cut -f3 -d" "`
 # exit
 #
 # STEP 2. Create drm.ko and via.ko
 #
 cd $dir/via-$file-linux.i386/drm/linux-core
 make DRM_MODULES="via"
 echo "drm.ko and via.ko created"
 #
 # STEP 3. Copy drm.ko and via.ko to proper directory
 #
 cd $dir/via-$file-linux.i386/drm/linux-core
 cp -f drm.ko via.ko /lib/modules/$ver/kernel/drivers/char/drm/
 echo "via.ko and drm.ko copied"
 #
 # STEP 4. Add via DRM module to the kernel
 #
 depmod -ae
 modprobe via
 echo "via DRM module added to kernel"
 #
 #
 # end of script
 #
 # LAST STEP: edit xorg.conf and reboot
 echo "you now need to edit /etc/X11/xorg.conf and then reboot"
 #
 # change the "Device" section to look something like this:
 # Section "Device"
 #        Identifier      "VIA Technologies, Inc. VT8378 S3  UniChrome Integrated Video"
 #        Driver          "via"
 #         BusID           "PCI:1:0:0"
 #        Option          "EnableAGPDMA"
 # EndSection"
```

---

### Post by dcstar on 2006-02-18
[QUOTE=dcstar]This is based on the Hoary instructions at:  [http://ubuntuforums.org/showthread.php?t=39349](http://ubuntuforums.org/showthread.php?t=39349)

but mainly on the info at: [http://www.ubuntulinux.se/node/164](http://www.ubuntulinux.se/node/164)

I found it needed a few changes to make it work (and the current Breezy VIA drivers don't seem to need the Unichrome project stuff).
......[/QUOTE]
Warning: **After the latest kernel upgrade to 2.6.12-10.28 my Via Direct Rendering stopped working!** (with lots of "disagrees about version of symbol" errors in my dmesg output).

I found I had to now **remove** the Via module created by the above script with:

sudo modprobe -r via

And after a reboot all was well again!

It looks like the Via DRM code is now included in this kernel - people with Via Unichrome hardware may now want to check if Direct Rendering works.

---

### Post by fergus.b on 2006-02-28
Thanks, same thing happened to me about a month back when I upgraded my kernel. Only got it working again now, thanks to you :)

---

### Post by dcstar on 2006-02-28
[QUOTE=fergus.b]Thanks, same thing happened to me about a month back when I upgraded my kernel. Only got it working again now, thanks to you :)[/QUOTE]
Let's all hope it all works "automagically" for us when Dapper comes out!

---

### Post by dcstar on 2006-03-14
And since the new kernel with the bug fix came out today, I had to re-run the script to compile a new DRM module to get Direct Rendering working again.....

---

### Post by mr_niceguy on 2006-03-24
I got the following error when I tried to compile:

```
CONFIG_X86_CMPXCHG needs to be enabled in the kernel.
```

Any ideas?

---

### Post by dcstar on 2006-04-13
[QUOTE=mr_niceguy]I got the following error when I tried to compile:

```
CONFIG_X86_CMPXCHG needs to be enabled in the kernel.
```

Any ideas?[/QUOTE]
Not really, but one thing I have discovered when I compiled myself a **new 2.6.16 kernel** is that I could select the option to include Via Unichrome as built-in:

[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

This meant my new (and faster, BTW) kernel had direct rendering working 100% with my hardware without any of the custom module compiling listed at the start of this thread!

If people have the time, I'd recommend that they try the new kernel, and set these up in the "make xconfig" phase:

**Device Drivers-Character Drivers-/dev/agpart** (Via chipset support) & also
**Device Drivers-Character Drivers-Direct Rendering Manager** (Via unichrome video cards)

---

### Post by lijiang on 2006-07-24
I did as the script says step by step.
And then when I run my little test program of OpenGL, it says:
 OpenGL GLX extension not supported by display ':0.0'
and nothing went out.
How can I solve this?
thanks

---

### Post by ryan76 on 2007-01-08
I compiled the new kernel like in the thread [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560) but I'm still getting this:

```
ryan@ubuntu:$ glxinfo
name of display: :0.0
__driCreateNewScreen_20050727 - succeeded
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 -1  0 r  y  . -1 -1  8  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 -1  0 r  .  . -1 -1  8  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 -1  0 r  y  . -1 -1  8  0  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 -1  0 r  .  . -1 -1  8  0  0  0  0 16 16 16 16  0 0 Slow


```

I have also posted about this in the AMD64 forum with no response. 

Any help would be appreciated. Thanks

---

### Post by vxxzy on 2008-01-17
I get the same message as the one above. I but i actually found that [www.viaarena.com](www.viaarena.com) has the proper drivers for 7.10 i386. It worked fine from a fresh install. however 3d performance with games sucks. 

I think the problem lies with the Mesa Libraries. I'm only using 6.5.1 when 7.0.2 is available.

any ideas??

---

