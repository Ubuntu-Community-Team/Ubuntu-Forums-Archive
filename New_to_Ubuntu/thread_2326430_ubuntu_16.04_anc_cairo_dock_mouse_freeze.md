---
title: "ubuntu 16.04 anc cairo dock mouse freeze"
date: 2016-06-01
forum: New to Ubuntu
---

### Post by petarivanov1985 on 2016-06-01
Hello,

I have installed ubuntu 16.04, gnome and cairo dock on my asus n551 laptop. sometimes when I`m closing applications cairo dock is causing random mouse freezes for a second. If I quit the cairo dock - this freeze is gone, that`s why i think the problem is some where between cairo and my video. Can you help me fix this annoying issue?

Thanks

---

### Post by RobGoss on 2016-06-01
Hello and welcome, What are the specs for this machine it will help others pinpoint your issues

---

### Post by petarivanov1985 on 2016-06-01
Intel Core i7-6700HQ, 16 GB RAM, 2 TB Plus 128 GB SSD, NVIDIA GTX960M, 2 GB Integrated Graphics

P.S. I was able to find out that this freeze occurs only when I close an application, and its icon is removed from the dock i.e. the animation used for removing icon from dock is causing this issue..

---

### Post by RobGoss on 2016-06-01
How did you install Cario dock from the terminal or Software center? I would recommend uninstalling it and install it again then reboot your machine and see if that helps

I use Cario dock on all my machines and never encountered this issue

---

### Post by RobGoss on 2016-06-01
I use the **Pulse** for my icon animation nothing more for reasons like this depending on what your system is like it may cause issues but after seeing your specs you should not have any problems.
Have you try choosing no  animation to see how it preforms?

---

### Post by petarivanov1985 on 2016-06-01
I`m installing everything from terminal. I will try reinstall cairo dock and will report back

Edit : tried - deinstall cairo dock, reboot, install again -> same issue

---

### Post by RobGoss on 2016-06-01
> If I [COLOR=#000000]quit the cairo dock - this freeze is gone,[/COLOR]

Are you saying if you don't use Cairo dock then your mouse does not freeze strange?

---

### Post by QDR06VV9 on 2016-06-01
maybe due to your drivers (e.g. your video drivers).

---

### Post by petarivanov1985 on 2016-06-01
> **RobGoss said:**
> Are you saying if you don't use Cairo dock then your mouse does not freeze strange?
Yes, if i remove cairo - everything is OK

---

### Post by petarivanov1985 on 2016-06-02
This is the info about my video controllers 

*-display               
       description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:133 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:129 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64)

---

### Post by petarivanov1985 on 2016-06-02
Smth,very strange - this behavior is only in Gnome. If i switch to unity - cairo dock works perfectly fine.
Also one another issue found - when starting Gnome session with second monitor attached - the system freezes and I can`t do anything, but to restart and boot without second monitor.

---

### Post by petarivanov1985 on 2016-06-04
Can some one help me - i think that the problem is in the video driver and gnome, but don`t know how to fix it.

---

### Post by howefield on 2016-06-04
Have you installed proprietary drivers as suggested by the Additional Drivers application ?

---

### Post by petarivanov1985 on 2016-06-04
Yes, I`ve installed these drivers. So let`s summarize:
- cairo dock with gnome - mouse frezees for 1 second when I close an application
- gnome without cairo - no problem with mouse freeze
- gnome with dual monitors - system freezes on start
- cairo dock with unity - no problem
- unity with dual monitor - no problem

I can use unity as work around for now, but I don`t like it at all.

---

### Post by howefield on 2016-06-04
You may have done so already, but I'd suggest posting to the cairo dock forums as well.

[http://www.glx-dock.org/bg_forumlist.php](http://www.glx-dock.org/bg_forumlist.php)

The developers appear helpful, friendly and active.

---

### Post by petarivanov1985 on 2016-06-04
Thanks, I`ve posted a thread there.
For now I switched to using Plank instead of Cairo Dock and everything seems to work just ok.
The other issue with second monitor attached and gnome is still unfixed - if somebody can help me, will be great

---

### Post by RobGoss on 2016-06-04
> [COLOR=#000000]The other issue with second monitor attached and gnome is still unfixed - if somebody can help me, will be great[/COLOR]

I would recommend starting another thread for your monitor problem

---

### Post by petarivanov1985 on 2016-08-16
Still do not have solution for that. Can any one help me?

---

