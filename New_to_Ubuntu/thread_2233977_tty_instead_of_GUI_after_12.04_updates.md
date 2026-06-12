---
title: "tty instead of GUI after 12.04 updates"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by stm146 on 2014-07-11
Just run update manager & rebooted, but instead of the GUI I now get tty. Can anyone tell me how I get the GUI back?

---

### Post by Vladlenin5000 on 2014-07-11
What happens / error messages after you login and try *starx* to bring in the desktop environment? Any related to graphics card drivers?

---

### Post by claracc on 2014-07-12
More information is needed in order to help.

What are your hardware specs.?, did your system use a specific driver for your card graphics, before the update?, what is your card graphics?, did you receive a new kernel in the update?.

---

### Post by stm146 on 2014-07-20
Vladlenin5000 - When I run startx I get "NVIDIA: API mismatch: the NVIDIA kernel module has version 173.14.39, but this NVIDIA driver component has version 304.116. Please make sure that the kernel module and all NVIDIA driver components have the same version".
Is this why my GUI isn't running? What do I need to do?

---

### Post by stm146 on 2014-07-21
@claracc - The PC has a GeForce 7900 GS and I assume it used an NVIDIA driver before the update, but I don't know how to find out what it was or whether I got a new kernel in the update. Happy to investigate further if you can tell me how.

---

### Post by kansasnoob on 2014-07-21
Run the command:

```
uname -r
```

Then tell us what version kernel that shows. I'm curious if you might have been hit with the HWE update.

---

### Post by stm146 on 2014-07-22
3.2.0-65-generic

---

### Post by kansasnoob on 2014-07-23
> **stm146 said:**
> 3.2.0-65-generic

That rules out a failed HWE update which is a good thing.

Have you tried booting a prior kernel from the grub menu?

---

### Post by stm146 on 2014-07-23
> **kansasnoob said:**
> That rules out a failed HWE update which is a good thing.

Have you tried booting a prior kernel from the grub menu?

I tried with 3.2.0-58 and it just hangs - no tty - just a few spurious characters on the screen

3.2.0-56 boots, as do 53,39 and 37, but in each case I get:

"Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes
Trying modes for CRTC72
CRTC72: trying mode 640x480@0Hz with output at1024X768@0Hz (Pass 1)
CRTC72: trying mode 640x480@0Hz with output at1024X768@0Hz (Pass 2)"

The the screen resolution is wrong - huge icons - and I can't change it.

Hope this makes sense to you!

---

### Post by sp40140 on 2014-07-24
Google is friend.
Try this : [http://ubuntuforums.org/showthread.php?t=2203615](http://ubuntuforums.org/showthread.php?t=2203615)

---

### Post by stm146 on 2014-07-31
> **sp40140 said:**
> Google is friend.
Try this : [http://ubuntuforums.org/showthread.php?t=2203615](http://ubuntuforums.org/showthread.php?t=2203615)

Sorry but the info this link leads to is too confusing for me (I am a complete beginner).

When I enter

$ sudo apt-get purge nvidia-* 

these packages are listed:

nvidia-173*
nvidia-173-updates*
nvidia-304*
nvidia-common*
nvidia-current*
nvidia-settings*
nvidia-settings-304-updates*
ubuntu-desktop*

I think I understand why the NVIDIA modues are listed but I don't understand why the ubuntu-desktop* package is listed. I didn't continue the operation as it didn't seem a good idea to remove the ubuntu-desktop* package. Should I run $ sudo apt-get purge nvidia-* again and remove ubuntu-desktop* along with the 7 nvidia packages?

The info at the link also mentions uninstalling NVIDIA drivers with the shell script they came with if downloaded from the NVIDIA site. When this problem first arose I booted XP and downloaded the driver that NVIDIA reccomemended but would this be relevant to Ubuntu? 

Apologies for the newbie questions and thanks for any advice you can offer.

---

### Post by Bashing-om on 2014-07-31
stm146; Hi !

Be aware there may be a cleaner way to remove the proprietary driver.
Find the .run file for the uninstall operation:
```

sudo find / -name "NVIDIA-Linux-*"

```
Will take some time to complete, wait !
If that file exist:
you have to run the .run file again with --uninstall: ; then we will get to that operation at that time ( IF that file exists).
//
As to the current "sudo apt-get purge nvidia-* " Well, like this:
The above command will also remove the nvidia-common package and the nvidia-common package has as a dependency the ubuntu-desktop package.
So after above command you should also give the installation command for ubuntu-desktop package: - if we take this route to remove drivers.

Also of consideration is that the Nvidia installer may have blacklisted any other drivers, will need to check what is blacklisted after the proprietary driver is removed.

I am all for doing things in the cleanest fashion,;
Else, roll our sleeves up and get dirty. Which is why it is best to avoid 3rd party software. When there are problems, can be a pain to cope with. 

The good news is
[INDENT][INDENT][INDENT]that it can be done
[/INDENT][/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-01
> **Bashing-om said:**
> stm146; Hi !

Be aware there may be a cleaner way to remove the proprietary driver.
Find the .run file for the uninstall operation:
```

sudo find / -name "NVIDIA-Linux-*"

```



Thanks Bashing-om, but this command didn't find anything.

What next? Should I now use "sudo apt-get purge nvidia-* "?

What is the installation command for  ubuntu-desktop package?

 And how do I find out if the Nvidia installer blacklisted  any other drivers?

---

### Post by Bashing-om on 2014-08-01
stm146; Well;

Not finding a .run file is not necessarily a bad thing.
Before proceeding, let's look and see what is installed that will require removing:
```

dpkg -l  | grep nvidia

```

and to see what is blacklisted:
```

ls -al /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf

```

With the end goal here to remove the Nvidia driver, and come up on the open source driver, then make any adjustments.

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-02
Here's what these commands produce:

steve@ubuntu:~$ dpkg -l  | grep nvidia
ii  nvidia-173                             173.14.39-0ubuntu0.0.1                  NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-173-updates                     173.14.39-0ubuntu0.0.1                  Transitional package for nvidia-173
ii  nvidia-304                             304.116-0ubuntu0.0.1                    NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-current                         304.116-0ubuntu0.0.1                    Transitional package for nvidia-current
ii  nvidia-settings                        331.20-0ubuntu0.0.1                     Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-304-updates            331.20-0ubuntu0.0.1                     Transitional package for nvidia-settings

-------------

steve@ubuntu:~$ ls -al /etc/modprobe.d
total 25
drwxr-xr-x   2 root root 1024 Jul 11 02:28 .
drwxr-xr-x 133 root root 8192 Aug  2 09:16 ..
-rw-r--r--   1 root root 2507 Feb 16  2012 alsa-base.conf
-rw-r--r--   1 root root  325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r--   1 root root 1603 Mar 18  2011 blacklist.conf
-rw-r--r--   1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r--   1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r--   1 root root  156 Feb 16  2012 blacklist-modem.conf
lrwxrwxrwx   1 root root   41 Apr  1  2013 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r--   1 root root 1077 Mar 18  2011 blacklist-watchdog.conf
-rw-r--r--   1 root root  127 Jan 13  2013 dkms.conf
-rw-r--r--   1 root root  153 Aug  9  2013 nvidia-304_hybrid.conf
-rw-r--r--   1 root root  157 Feb 27  2013 nvidia-current_hybrid.conf
lrwxrwxrwx   1 root root   49 Jul 11 02:28 nvidia-graphics-drivers.conf -> /etc/alternatives/x86_64-linux-gnu_nvidia_modconf
-rw-r--r--   1 root root   30 May 18  2012 vmwgfx-fbdev.conf

-----------------------

steve@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by Bashing-om on 2014-08-02
stm146; Hey;

With all those attempts to get a graphics driver install, I am all for that sledge hammer approach to remove all Nvidia.
However, I still have 1 remaining point of concern before we proceed on out way:
> 
-rw-r--r-- 1 root root 157 Feb 27 2013 nvidia-current_hybrid.conf


Are we indeed dealing with hybrid graphics ??

Post back the output - between code tags, please - of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

too get an idea of what we are going to restore with .

[INDENT][INDENT][INDENT]safety is no accident
[/INDENT][/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-03
Hi Bashing-om

No hybrid graphics as far as I know - it's an old Dell Dimension 9150 desktop machine.

Output from lspci -nnk | grep -iA3 vga:
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G71 [GeForce 7900 GS] [10de:0292] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:0370]
    Kernel modules: nouveau, nvidiafb
04:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a] (rev 01)
```

Output from sudo lshw -C display: 
 ```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: G71 [GeForce 7900 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fc000000-fcffffff memory:e0000000-efffffff memory:fd000000-fdffffff ioport:dc80(size=128) memory:fea00000-fea1ffff
```

---

### Post by Bashing-om on 2014-08-03
stm146; OK ;

Let's do this, right now you have no driver loaded... and I do not see the the open source driver ( we are going to install ) as blacklisted.
From the GUI, key combo ctl+alt+F1 to get a console:
This is assuming you are running ubuntu with a standard desk top, else make proper adjustments !
```

sudo service lightdm stop
sudo apt-get remove --purge nvidia-*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup ##may not exist, if not - no worry##
sudo apt-get update
sudo apt-get install linux-headers-generic ##  just to be safe##
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install xserver-xorg-video-nouveau

```
Now to restart - to have a clean slate, and you should come up on the open source graphics driver 'nouveau' :
```

sudo shutdown -r now

```

Upon that restart, what are you looking like, now ?

[INDENT][INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-04
Thanks Bashing-om - all working again now.

When I first re-booted I had horizontal lines across the screen so I re-booted in recovery mode and selected failsafe graphics. The system couldn't detect my screen etc but I selected the reconfigure option, ran  the troubleshooter and that fixed the remaining problems.

Thanks again for all your help - I also learned a few things in the process.

Thanks also to Vladlenin5000, claracc, kansasnoob and sp40140.

Cheers

Steve

---

### Post by Bashing-om on 2014-08-04
stm146; Outstanding !

You done good !
It will be instructive to know what graphics driver is now in use. IF all is good, leave well enough alone.
If it works, do not fix it.
```

sudo lshw -C display

```
the "configuration' line should list the driver, and latency should be '0'.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-06
Hi again

It seems I do still have a graphics problem - occasional horizontal lines and other strange graphics errors. 

sudo lshw -C display outputs:


  ```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: G71 [GeForce 7900 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fc000000-fcffffff memory:e0000000-efffffff memory:fd000000-fdffffff ioport:dc80(size=128) memory:fea00000-fea1ffff
```

Seems my graphics driver isn't being recognised.

---

### Post by Bashing-om on 2014-08-06
stm146; Strange !

Agreed, no driver is loaded. Should have, so the question is why is the driver not loaded ?

Before we go forcing things, let's look again and make sure nouveau isn't blacklisted:
```

ls -la /etc/modprobe.d/
cat /etc/modprobe.d/blacklist.conf

```
And make sure there are no residual Nvidia graphics files lying about:
```

sudo find / -name "nvidia*"

```

Then we see what do do, what to do .

[INDENT][INDENT]if it don't fit,
[INDENT][INDENT][INDENT]don't force it
[INDENT][INDENT][INDENT][INDENT][INDENT]get a bigger hammer
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-06
Thanks for staying with this Bashing-om.

Running each command in turn:

```


steve@ubuntu:~$ ls -la /etc/modprobe.d/
total 23
drwxr-xr-x   2 root root 1024 Aug  4 08:48 .
drwxr-xr-x 132 root root 8192 Aug  6 23:49 ..
-rw-r--r--   1 root root 2507 Feb 16  2012 alsa-base.conf
-rw-r--r--   1 root root  325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r--   1 root root 1603 Mar 18  2011 blacklist.conf
-rw-r--r--   1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r--   1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r--   1 root root  156 Feb 16  2012 blacklist-modem.conf
lrwxrwxrwx   1 root root   41 Apr  1  2013 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r--   1 root root 1077 Mar 18  2011 blacklist-watchdog.conf
-rw-r--r--   1 root root  127 Jan 13  2013 dkms.conf
-rw-r--r--   1 root root   30 May 18  2012 vmwgfx-fbdev.conf

```

```
steve@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

```
steve@ubuntu:~$ sudo find / -name "nvidia*"
[sudo] password for steve: 
/lib/modules/3.2.0-58-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-58-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-58-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-23-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-23-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-23-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-39-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-39-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-39-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-33-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-33-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-33-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-37-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-37-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-37-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-67-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-67-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-67-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-30-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-30-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-30-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-53-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-53-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-53-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-56-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-56-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-56-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-34-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-34-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-34-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-31-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-31-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-31-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-32-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-32-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-32-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-35-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-35-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-35-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-65-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-65-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-65-generic/kernel/drivers/net/ethernet/nvidia
/var/lib/nvidia-common
/var/lib/dpkg/info/nvidia-common.md5sums
/var/lib/dpkg/info/nvidia-common.conffiles
/var/lib/dpkg/info/nvidia-common.config
/var/lib/dpkg/info/nvidia-common.preinst
/var/lib/dpkg/info/nvidia-common.prerm
/var/lib/dpkg/info/nvidia-common.templates
/var/lib/dpkg/info/nvidia-common.list
/var/lib/dpkg/info/nvidia-common.postinst
/var/lib/dpkg/info/nvidia-common.postrm
/var/cache/apt/archives/nvidia-settings-304-updates_331.20-0ubuntu0.0.1_amd64.deb
/var/cache/apt/archives/nvidia-current_304.116-0ubuntu0.0.1_amd64.deb
/var/cache/apt/archives/nvidia-settings-updates_331.20-0ubuntu0.0.1_amd64.deb
/var/cache/apt/archives/nvidia-settings-304_331.20-0ubuntu0.0.1_amd64.deb
/var/cache/apt/archives/nvidia-304_304.116-0ubuntu0.0.1_amd64.deb
/var/cache/apt/archives/nvidia-common_1%3a0.2.44.2_amd64.deb
/var/cache/apt/archives/nvidia-settings_331.20-0ubuntu0.0.1_amd64.deb
/var/cache/jockey/nvidia-173-updates.oldconf
/var/cache/jockey/nvidia-173.noconf
/var/cache/jockey/nvidia-current.oldconf
/usr/lib32/nvidia-current
/usr/lib32/nvidia-173-updates
/usr/lib32/nvidia-173
/usr/lib/nvidia-current
/usr/lib/nvidia-173-updates
/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py
/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.pyc
/usr/lib/python2.7/dist-packages/nvidia_common-0.0.0.egg-info
/usr/lib/nvidia
/usr/lib/nvidia-173
/usr/src/linux-headers-3.2.0-31/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-31/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-65-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-65-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-65-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-53/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-53/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-32-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-32-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-32-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-31-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-31-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-31-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-30-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-30-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-30-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-37/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-37/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-58-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-58-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-58-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-34-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-34-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-34-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-67-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-67-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-67-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-65/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-65/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-56-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-56-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-56-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-56/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-56/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-39/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-39/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-37-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-37-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-37-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-67/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-67/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-23/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-23/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-34/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-34/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-35/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-35/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-35-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-35-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-35-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-33/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-33/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-33-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-33-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-33-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-30/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-30/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-32/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-32/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-23-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-23-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-23-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-58/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-58/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-39-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-39-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-39-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-53-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-53-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-53-generic/include/config/net/vendor/nvidia.h
/usr/bin/nvidia-detector
/usr/share/screen-resolution-extra/nvidia-prime.pyc
/usr/share/screen-resolution-extra/nvidia-polkit.py
/usr/share/screen-resolution-extra/nvidia-prime.py
/usr/share/screen-resolution-extra/nvidia-polkit.pyc
/usr/share/nvidia-common
/usr/share/app-install/desktop/nvidia-driver-185.desktop
/usr/share/app-install/desktop/nvidia-driver-96.desktop
/usr/share/app-install/desktop/nvidia-driver-173.desktop
/usr/share/pyshared/NvidiaDetector/nvidiadetector.py
/usr/share/pyshared/nvidia_common-0.0.0.egg-info
/usr/share/doc/nvidia-common
/usr/share/jockey/handlers/nvidia.py
/etc/apparmor.d/abstractions/nvidia

```

---

### Post by Bashing-om on 2014-08-06
stm146; Humm,

not real sure what to make of it:
You have, still:
> 
/var/lib/nvidia-common
/var/lib/dpkg/info/XXXXX
/usr/lib32/nvidia-current
/usr/lib32/nvidia-173-updates
/usr/lib32/nvidia-173
/usr/lib/nvidia-current
/usr/bin/nvidia-detector

## These are biggies ! How does - and how come-  nvidia-prime come into play here ?????????
/usr/share/screen-resolution-extra/nvidia-prime.pyc
/usr/share/screen-resolution-extra/nvidia-polkit.py
/usr/share/screen-resolution-extra/nvidia-prime.py
/usr/share/screen-resolution-extra/nvidia-polkit.pyc
/usr/share/nvidia-common
/usr/share/app-install/desktop/nvidia-driver-185.desktop
/usr/share/app-install/desktop/nvidia-driver-96.desktop
/usr/share/app-install/desktop/nvidia-driver-173.desktop


I will have to take a bit of time to think about - and do some research - how to proceed. That nvidia-prime throws a wrench into the works.

[INDENT][INDENT]I'll Be Baacckkkk
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-06
stm146; Meanwhile;

That I continue to cogitate;
Let's get this out of the way as a possible source of a problem:
post back the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT]still, though
[INDENT][INDENT][INDENT]what to do, what to do
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-07
12.04 is the only version of Ubuntu I've had and I'm pretty sure I haven't downloaded any nvidia drivers since I installed it. I have a dual-boot setup with XP and I may have downloaded nvidia modules when running XP, but I guess his isn't relevant.

```
steve@ubuntu:~$ cat -n /etc/apt/sources.list
     1    # /etc/apt/sources.list
     2    
     3    deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
     4    deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
     5    deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

```

```
steve@ubuntu:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

```

---

### Post by Bashing-om on 2014-08-07
stm146; Well, well .

Your "sources.list" file is - as you know - non-standard. [s]I see no provision for "precise-updates" that in all likely hood is 1 cause of not updating the system properly.[/s]

Let me get to where I can fully focus my attention to your "sources" and we see what to do. But, that has nothing to do with why the Nvidia graphics driver files remain on your system. I need to consider a proper means to remove these vestiges of the Nvidia graphics drivers .

It is always amazing to me, what I do not know !

EDIT: re-read for comprehension, and precise-updates is there -- How did I miss it !

All in all, still
[INDENT][INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-07
stm146; A bit of progress;


I see nothing really amiss in your "/etc/apt/sources.list" file, But may I suggest:
Edit sources.list file;
Current:
```

1    # /etc/apt/sources.list
     2    
     3    deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
     4    deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
     5    deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

```

Edit it to this ( add you own comments to the file for your future reference) :
As I do not know the relationship of the 3rd party PPAs and how the package manager relates, let's see if they talk to one another by enabling 1 other repository.
```

1    # /etc/apt/sources.list
     2    
     3    deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
     4    deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
     5    deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

             deb http://archive.canonical.com/ubuntu precise partner

```

Run the update/upgrade routines:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Then we go back to work on getting a graphics driver loaded.

EDIT:
Presently also, there is no provision to add the non-free software ( IE flash, MicroSoft fonts, DVD codecs, etc ). Just something to keep in mind - no hinderance to what we are presently engaged in - 

[INDENT][INDENT]progress, slowly
[/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-09
OK - all done - first time I've edited a file in Ubuntu.
Really appreciating your help with this and the learning is a bonus!

---

### Post by Bashing-om on 2014-08-09
stm146; Hey,


It is all a learning experience; glad you are taking in in so well. I relate to you my little secret -> each day I sit down at my terminal I ask " what can I learn today" , There is no day that goes by that I do not add to my store of knowledge.

OK, now with all updated, take another look at what driver is loaded ( maybe !) .
```

sudo lshw -C display

```
Meanwhile I will see what can be done to get the system to clean up those residual Nvidia graphics ( yes graphics, as we do not want to mess about with video and net components). I do have a thought in mind, soon as I have it solidified we will proceed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Jonathan Precise on 2014-08-09
Try this: Make a backup of each of the files you mentioned:
```
cp /var/lib/nvidia-common /var/lib/nvidia-common.old
cp /var/lib/dpkg/info/XXXXX /var/lib/dpkg/info/XXXXX.old
cp /usr/lib32/nvidia-current /usr/lib32/nvidia-current.old
cp /usr/lib32/nvidia-173-updates /usr/lib32/nvidia-173-updates.old
cp /usr/lib32/nvidia-173 /usr/lib32/nvidia-173,old
cp /usr/lib/nvidia-current /usr/lib/nvidia-current.old
cp /usr/bin/nvidia-detector /usr/bin/nvidia-detector.old
cp /usr/share/screen-resolution-extra/nvidia-prime.pyc /usr/share/screen-resolution-extra/nvidia-prime.pyc.old
cp /usr/share/screen-resolution-extra/nvidia-polkit.py /usr/share/screen-resolution-extra/nvidia-polkit.py.old
cp /usr/share/screen-resolution-extra/nvidia-prime.py /usr/share/screen-resolution-extra/nvidia-prime.py.old
cp /usr/share/screen-resolution-extra/nvidia-polkit.pyc /usr/share/screen-resolution-extra/nvidia-polkit.pyc.old
cp /usr/share/nvidia-common /usr/share/nvidia-common.old
cp /usr/share/app-install/desktop/nvidia-driver-185.desktop /usr/share/app-install/desktop/nvidia-driver-185.desktop.old
cp /usr/share/app-install/desktop/nvidia-driver-96.desktop /usr/share/app-install/desktop/nvidia-driver-96.desktop.old
cp /usr/share/app-install/desktop/nvidia-driver-173.desktop /usr/share/app-install/desktop/nvidia-driver-173.desktop.old
```

Hope it's of help!

---

### Post by Bashing-om on 2014-08-09
stm146; Hey,

Jonathon's advise ^ is apt.
It would be real nice if the .run files were still in existence to help in this endeavor ! Save us having to manually troll through things, looking and deleting files.
I expect that the 'find' command was thorough, but just for my piece of mind, anything from ? :
```

sudo ls -la /root/NVIDIA*
ls la /home/steve/NVIDIA*

```
See if these files are in existence ??
No ? Then we roll our sleeves up and painstakingly hunt up files and remove them - carefully . Be aware with the number of failed attempts and left behind rubbish, I do expect it to be a chore.
Let's hold onto the files in "/var/lib/dpkg/info/" to look to as a guide to what should also be removed. Make those the last to be removed. 

 Working real hard to get the system booting up with the open source graphics driver.

The good thing is
[INDENT][INDENT][INDENT]it can be done
[/INDENT][/INDENT][/INDENT]

---

### Post by Andy_Crowd on 2014-08-11
You need to enable desktop manager (mdm/gdm/....). And it use to run on tty7, you can try switch there with Ctrl+Alt+F7
Ttell if sometheing of it will work.

---

### Post by Bashing-om on 2014-08-11
@ Andy_Crowd; Hello;

We appreciate the input and participation; However, in this instance it is a matter of making sure all vestiges of the old drivers have been removed, and getting the open source driver properly installed. Then see what is to be done.

[INDENT][INDENT]making progress
[INDENT][INDENT][INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stm146 on 2014-08-11
Hmm - seems nouveau is now loading OK:
```
steve@ubuntu:~$ sudo lshw -C display l
[sudo] password for steve: 
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce 7900 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fc000000-fcffffff memory:e0000000-efffffff memory:fd000000-fdffffff ioport:dc80(size=128) memory:fea00000-fea1ffff

```

---

### Post by Bashing-om on 2014-08-11
stm146; Great,

That do make me feel better. I would at this time go ahead and "move" the cruft out of the way, reboot and if all is good then delete those old no-longer-needed files.
Then, maybe see what " Additional Drivers " offers for a proprietary driver IF performance is not what you want from the nouvea driver.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

