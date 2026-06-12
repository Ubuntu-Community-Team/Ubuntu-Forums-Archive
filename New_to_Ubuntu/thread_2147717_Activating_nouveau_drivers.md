---
title: "Activating nouveau drivers?"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by Athquiz on 2013-05-22
So I was recently trying to fix some minor video problems I was having on 12.04, and in the process I foolishly installed an NVIDIA driver. Previously I was using the nouveau driver, and loving every minute of it, but now I can't seem to turn it back on. It shows up in the additional drivers window, but it says "Active, but not in use." and I have no idea how to make it "in use".

Output of jockey-text -l | grep -i nvidia
```
[B]kmod:nouveau - nVidia Riva/TNT/GeForce (Free, Enabled, Not in use)
[/B]kmod:nvidia_304 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Free, Disabled, Not in use)
kmod:nvidia_313 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Free, Disabled, Not in use)
kmod:nvidia_319 - Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library (Free, Disabled, Not in use)
kmod:nvidia_current_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_experimental_304 - Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_experimental_310 - Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidiafb - Framebuffer driver for nVidia graphics chipset (Free, Disabled, Not in use)

```

How would I switch back to nouveau? I've reactivated/reinstalled to no avail.

---

### Post by bogan on 2013-05-23
Hi!!, [B]Athquiz,
[/B]
In installing an nvidia driver the Nouveau driver will probably have been Blacklisted in '/etc/modprobe.d'

Look for an entry in the 'blacklist.conf' file or a file called "nvidia-installer-disable-nouveau.conf" or similar, 'comment-out' the blacklist lines, save the file, and reboot.

Run:```
sudo apt-get install gksu  # install gksu if necessary to get 'gksudo'.
gksudo nautilus /etc/modprobe.d # edit & save.
sudo reboot
```If there are still problems, check that 'xserver-xorg-video-nouveau' is installed, you can do so in Synaptic Package Manager, or run:```
:~$ apt-cache policy xserver-xorg-video-nouveau # which should show this:
xserver-xorg-video-nouveau:
  Installed: 1:1.0.7-0ubuntu1
  Candidate: 1:1.0.7-0ubuntu1
  Version table:
 *** 1:1.0.7-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
        100 /var/lib/dpkg/status
:~$ 
``` Should there not be a blacklist entry, & the xserver **is **installed, then try removing it and reinstalling:```
sudo apt-get remove --purge xserver-xorg-video-nouveau
sudo apt-get install xserver-xorg-video-nouveau
sudo reboot
```

If you need more info please Post the output of:```
uname -ar
lspci | grep -iA3 vga
lsmod | grep -e nouveau -e nvidia
/usr/lib/nux/unity_support_test -p
```And is 12.04 is a direct install, wubi, or an update?

Chao!, **bogan**.

---

### Post by Athquiz on 2013-05-23
Thanks for your response! This was a direct install of 12.04. 

It doesn't seem to appear in the blacklist. Reinstalling didn't seem to do anything. And I'm not sure if this is related, but whenever I try to run something with glx, like glxspheres, I get this error:
```
 ../../../../../src/mesa/main/context.c:1545: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
```

As for the outputs from those commands.

uname -ar:
```
Linux Vera-Ubuntu 3.5.0-18-generic #29-Ubuntu SMP Thu Oct 25 07:26:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

lspci | grep -iA3 vga:
```
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
--
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd4 (rev ff)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)

```

There was no output for [COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep -e nouveau -e nvidia

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]The output for /usr/lib/nux/unity_support_text -p was the error from above.
[/FONT][/COLOR]```
Gen6+ requires Kernel 3.6 or later.
unity_support_test: ../../../../../src/mesa/main/context.c:1545: _mesa_make_current: Assertion `newCtx->Version > 0' failed.

```

---

### Post by deadflowr on 2013-05-23
What's the output for

```
sudo lshw -C display | grep driver
```

Whatever the output for this is will be the driver in use.

---

### Post by Athquiz on 2013-05-23
```
sudo lshw -C display | grep driver
       configuration: driver=i915 latency=0
```

---

### Post by deadflowr on 2013-05-23
i915 is for intel gpus.

Which I guess means your system is an optimus one?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://nouveau.freedesktop.org/wiki/Optimus/](http://nouveau.freedesktop.org/wiki/Optimus/)

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Though there might be a way of disabling the intel gpu and using the nvidia gpu.
If that's what you'd want, then it most likely be done in the BIOS.

---

### Post by Athquiz on 2013-05-23
Yes I'm aware it's an optimus system. An annoying one at that. Requires a workaround to get the nvidia card working with nvidia drivers. But until 2 days ago I had the nouveau drivers running without the workaround and without optimus. I wish to get that state again. At some point I did an update, which allowed compiz to run, and made optimus irrelevant, but the fact that it was an update and not my intervention means I don't really know why it "fixed" itself.

The fact that I'm using an intel driver means that I can't do anything that requires any 3d rendering at all. Including things like compiz. Nvidia drivers require optirun to get anything to run properly, and that requires me to have already logged into something that allows terminal input, which is far too late to load compiz properly (possibly because of another problem... it breaks all the borders around the windows so I can't really do much).

Also, there's a particular game I'd like to play that doesn't seem to work with optirun nvidia drivers, but works with nouveau.

---

### Post by grahammechanical on 2013-05-23
If I remember, "Active but not in use" was a bug that has been around since before 12.04. I guess it has been fixed because it does not appear in 12.10 or 13.04. That printout from Jockey is showing that it is the Nvidia drivers that are not in use. So, what driver is being used on your system.?No video driver = low screen resolution. Ubuntu defaults to Nouveau when we boot without a proprietary driver activated.

What does the details page of About this Computer say? Sometimes on 12.04 it will list the video card if a proprietary driver is being used. On 13.04 it says Gallium if Nouveau is in use. Another way of testing is to Open the Displays utility. That only works if we are using Nouveau. When we use the Nvidia driver we get an Nvidia settings utility in the Dash. What does that Nvidia Xserver settings utility say? I bet it says that you are not using an Nvidia driver.

Regards.

---

### Post by Athquiz on 2013-05-23
> **grahammechanical said:**
> If I remember, "Active but not in use" was a bug that has been around since before 12.04. I guess it has been fixed because it does not appear in 12.10 or 13.04. That printout from Jockey is showing that it is the Nvidia drivers that are not in use. So, what driver is being used on your system.?No video driver = low screen resolution. Ubuntu defaults to Nouveau when we boot without a proprietary driver activated.

What does the details page of About this Computer say? Sometimes on 12.04 it will list the video card if a proprietary driver is being used. On 13.04 it says Gallium if Nouveau is in use. Another way of testing is to Open the Displays utility. That only works if we are using Nouveau. When we use the Nvidia driver we get an Nvidia settings utility in the Dash. What does that Nvidia Xserver settings utility say? I bet it says that you are not using an Nvidia driver.

Regards.

Well the problem is that without any proprietary drivers I still have the intel drivers. This machine does indeed have 2 video cards, and there seems to be some automatic configuration for the intel drivers, so it no longer defaults to anything but intel.

What really throws me in a loop is that this worked before. With no proprietary drivers installed it would load compiz on boot, and allow me to run any 3d programs. Now compiz requires a manual open, and 3d programs give me this error:
```
Gen6+ requires Kernel 3.6 or later.glxgears: ../../../../../src/mesa/main/context.c:1545: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
Aborted (core dumped)

```

My kernel is only at 3.5, but there doesn't seem to be an update, so I'm not sure what this is on about.

---

### Post by Athquiz on 2013-05-23
Update! I upgrade to the 3.6 kernel and everything seems to work fine. I'm not sure why the driver would function perfectly with the older kernel for so long and then crap out as soon as I mess with things. Oh well.

---

