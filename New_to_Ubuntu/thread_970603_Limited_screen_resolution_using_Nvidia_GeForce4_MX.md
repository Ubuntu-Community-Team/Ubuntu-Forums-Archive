---
title: "Limited screen resolution using Nvidia GeForce4 MX440 AGP8x"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by theorist on 2008-11-04
I've heard great things about Ubuntu and am excited to try it out, but unless I can get decent screen resolution and my printer to work, it may be a briefer visit than I hoped.

I can't get a decent screen resolution.  I've recently installed Hardy Heron 8.04.1.  My graphics card is an nvidia geforce4 mx440 agp8x.  Using the 8.10 and 8.04.1 liveCDs I was unable to select a resolution above 800x600.  I read about limited support for this graphics card under 8.10 so I installed 8.04.1.  At first, the basic install gave me at most 800x600 resolution.  I updated to the recommended 96.43.05+ nvidia driver and now I can't get more than 640x480 resolution.

I've read about others having similar difficulties using several releases of Ubuntu, but I didn't see any consensus on a solution as much as on shared frustration.

Any help would be appreciated.  Thank you.

---

### Post by Peter09 on 2008-11-04
Try booting into recovery mode and selecting reconfigure  X server.

To get to recovery mode hit ESC at the Grub prompt and select the second option down.

Also check if you have any drivers to enable in System->Administration->Hardware Drivers

---

### Post by sdowney717 on 2008-11-04
you must run the nvidia configuration settings before you will see any more resolutions

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/chapter-03.html#id2475512](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/chapter-03.html#id2475512)

I had a machine with that card and it will work with high resolutions.

---

### Post by theorist on 2008-11-04
Thanks for the promising lead.  I'm getting "ERROR: Unable to write to directory '/etc/X11'."  I was a regular unix user in the 90's but never an administrator.  Whatever I once knew about file permissions and superusers I've long forgotten.


eric@babitub:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first CorePointer in the config input list.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

eric@babitub:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NV18 [GeForce4 MX 440 AGP 8x]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
eric@babitub:~$ 

I also booted in recovery mode, ran xfix, and re-enabled the nvidia hardware driver.

---

### Post by Peter09 on 2008-11-04
to get to administrator mode put the command sudo in front of the normal command.

```
sudo <some command>
```

---

### Post by theorist on 2008-11-04
before reading your last pointer, i found that i could enter the root command shell in recover mode and run nvidia-xconfig from there.  I rebooted and my monitor said it was out of range, after waiting for a couple minutes, I hard rebooted and it came up in 1600x1200 resolution.  I was able to scale a bit to get a good refresh rate and then noticed that the title bars of the windows weren't there.  I restarted and still can't move windows.  I also can't use the terminal application now.

Up at the top bar Ubuntu asked me about updates and I said to install all of the recommended ones.  Did I install an update that creates the same incompatibility with this nvidia driver that is in Ibex?  Should I rerun xfix or nvidia-xconfig from the recovery mode root shell?  I'm afraid that I'm creating problems as quickly as I'm fixing them.  (The updates also seemed to wipe out my dvorak keyboard layout setting,  I've got it back for most things but not the login screen.)

---

### Post by Peter09 on 2008-11-04
Try moving the windows by holding down the ALT key as well as the mouse button. It may be that the window title bar is under the top panel.

---

### Post by theorist on 2008-11-04
restarting to recover mode and running xfix fixed the title bars.  now sudo nvidia-xconfig is reporting the following validation error.

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by Peter09 on 2008-11-04
Think it may be resolved, have you still got your original problems?

---

