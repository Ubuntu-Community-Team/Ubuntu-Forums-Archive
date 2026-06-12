---
title: "Intel GMA 4500M screen resolution problem"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iheartubuntu on 2011-09-08
Hello! I was previously running Ubuntu 10.10 on my Acer Aspire laptop. It has Intel GMA 4500M integrated graphics and worked just fine. Great display, sharp, crisp, etc.

I decided to do a fresh install of 11.10 Oneiric and now am having problems. Originally I was getting the dreaded blank screen where the brightness was turned almost completely off. Some searching pulled up several easy fixes (editing GRUB).

Right now I am still having one issue. The screen resolution is stuck at a max of 1024x768 giving me a distorted screen. Is there any way to fix this issue? Ive Googled, Ive searched Ask Ubuntu and also spent time on the forums looking for a solution. Thus far, nothing. Apparently, was and still is a concern in Natty?

Any help would be greatly appreciated, thanks!

---

### Post by JonM33 on 2011-09-08
Using 11.10B1 myself with GMA 950, should be using same driver. No issues at all. Does it limit you on the LiveCD?

---

### Post by immerohnegott on 2011-09-08
Also using the GMA4500M (in a Dell Inspiron), and have zero graphical issues on either Natty or Oneiric. I'd say to check that the Intel drivers are running:
```
$ glxinfo | grep vendor
```

It should list:
```

server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Tungsten Graphics, Inc

```

Though, if you can log into the standard Unity or Gnome-Shell sessions, the drivers should be running fine (need 'em to do compositing). If such is the case, it might be an issue with the panel in your laptop not being properly detected.

---

### Post by iheartubuntu on 2011-09-08
Strangely, I did not have these problems with 10.10. Here is my output:


> dave@dave-Aspire:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Mesa Project


---

### Post by JonM33 on 2011-09-08
> **immerohnegott said:**
> Also using the GMA4500M (in a Dell Inspiron), and have zero graphical issues on either Natty or Oneiric. I'd say to check that the Intel drivers are running:
```
$ glxinfo | grep vendor
```

It should list:
```

server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Tungsten Graphics, Inc

```

Though, if you can log into the standard Unity or Gnome-Shell sessions, the drivers should be running fine (need 'em to do compositing). If such is the case, it might be an issue with the panel in your laptop not being properly detected.

I get that myself.

---

### Post by immerohnegott on 2011-09-08
Hmmmm. Could you maybe post the output of

```
lspci -vvnn |grep Graphics
```

as well as your /var/log/xorg.0.log?

For reference, my system shows a pair of entries for Intel Mobile 4 Series Graphics Controller at revision 07 with PCI IDs of 8086:2a42 and 8086:2a43. This could very well be an upstream glitch with the Intel drivers not properly recognizing your particular revision of the chipset. I had a similar issue messing around with the Xorg-edgers PPA on Maverick. It just up and decided my chipset wasn't supported. Updated a few days later and it was fine.

---

### Post by iheartubuntu on 2011-09-08
> dave@dave-Aspire:~$ lspci -vvnn |grep Graphics
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09) (prog-if 00 [VGA controller])
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)

And also my xorg.0.log:

[http://paste.ubuntu.com/685530/](http://paste.ubuntu.com/685530/)

---

### Post by lucazade on 2011-09-08
> **iheartubuntu said:**
> And also my xorg.0.log:

[http://paste.ubuntu.com/685530/](http://paste.ubuntu.com/685530/)

your system is using a generic driver (vesa) but i don't get why from that log.

can you paste the output of:
```
lshw -c video
```

and look for the line with "configuration". The loaded driver is prefixed with "driver:".
it will probably look like this:
"configuration: driver=i915 latency=0"

then check if this driver (i915) really support your pciid numbers (8086:2a42 and 8086:2a43) by using:

```
modinfo i915
```

---

### Post by iheartubuntu on 2011-09-08
Here is an example of my screen stretched to 1024x768..

[http://imagebin.org/171623](http://imagebin.org/171623)

I havent tried any 3D games like supertuxkart, but Stellarium is quite slow.

glxgears looks very nice at 178 fps. glxinfo gives me this data: [http://paste.ubuntu.com/685537/](http://paste.ubuntu.com/685537/)

---

### Post by iheartubuntu on 2011-09-08
dave@dave-Aspire:~$ sudo lshw -c video
> 
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:90000000-903fffff memory:80000000-8fffffff ioport:50f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:93400000-934fffff


dave@dave-Aspire:~$ modinfo i915

> filename:       /lib/modules/3.0.0-10-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     D42D56AFDC1987DF3AADCDE
alias:          pci:v00008086d0000015Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000162sv*sd*bc03sc*i*
alias:          pci:v00008086d00000152sv*sd*bc03sc*i*
alias:          pci:v00008086d00000166sv*sd*bc03sc*i*
alias:          pci:v00008086d00000156sv*sd*bc03sc*i*
alias:          pci:v00008086d0000010Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000126sv*sd*bc03sc*i*
alias:          pci:v00008086d00000116sv*sd*bc03sc*i*
alias:          pci:v00008086d00000106sv*sd*bc03sc*i*
alias:          pci:v00008086d00000122sv*sd*bc03sc*i*
alias:          pci:v00008086d00000112sv*sd*bc03sc*i*
alias:          pci:v00008086d00000102sv*sd*bc03sc*i*
alias:          pci:v00008086d00000046sv*sd*bc03sc*i*
alias:          pci:v00008086d00000042sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A011sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A001sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E92sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E32sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E22sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E02sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A02sv*sd*bc03sc*i*
alias:          pci:v00008086d000029D2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029C2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029B2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002992sv*sd*bc03sc*i*
alias:          pci:v00008086d00002982sv*sd*bc03sc*i*
alias:          pci:v00008086d00002972sv*sd*bc03sc*i*
alias:          pci:v00008086d000027AEsv*sd*bc03sc*i*
alias:          pci:v00008086d000027A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002772sv*sd*bc03sc*i*
alias:          pci:v00008086d00002592sv*sd*bc03sc*i*
alias:          pci:v00008086d0000258Asv*sd*bc03sc*i*
alias:          pci:v00008086d00002582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002572sv*sd*bc03sc*i*
alias:          pci:v00008086d0000358Esv*sd*bc03sc*i*
alias:          pci:v00008086d00003582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002562sv*sd*bc03sc*i*
alias:          pci:v00008086d00003577sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,video,i2c-algo-bit
vermagic:       3.0.0-10-generic SMP mod_unload modversions 686 
parm:           modeset:int
parm:           fbpercrtc:int
parm:           panel_ignore_lid:int
parm:           powersave:int
parm:           semaphores:int
parm:           i915_enable_rc6:int
parm:           i915_enable_fbc:int
parm:           lvds_downclock:int
parm:           lvds_use_ssc:int
parm:           vbt_sdvo_panel_type:int
parm:           reset:bool


---

### Post by immerohnegott on 2011-09-08
> **lucazade said:**
> your system is using a generic driver (vesa) but i don't get why from that log.

can you paste the output of:
```
lshw -c video
```

and look for the line with "configuration". The loaded driver is prefixed with "driver:".
it will probably look like this:
"configuration: driver=i915 latency=0"

then check if this driver (i915) really support your pciid numbers (8086:2a42 and 8086:2a43) by using:

```
modinfo i915
```

It should support those PCI IDs (my system gives the same IDs, though my chipset is at revision 07).

---

### Post by iheartubuntu on 2011-09-08
Just want to thank both of you for help on this as I am hosting an Ubuntu Hour later today here in Los Angeles. Was up all night trying to solve this on my own.

---

### Post by immerohnegott on 2011-09-08
No problem. Although this is starting to get a bit above my pay grade, as the usual logs aren't showing any reason WHY your system isn't using the Intel driver. It knows it's there, but is skipping to a generic driver.

What options are you passing to the kernel in GRUB?

---

### Post by iheartubuntu on 2011-09-08
Im running this in my grub...
> 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash acpi_osi=Linux"

The only thing Ive changed is the last line. I could get rid of "acpi_osi=Linux" and theres no difference, but I basically need to have "i915.modeset=0" or else I will get a black screen on boot. I could replace it with "nomodeset" also to see my screen. But Ive read nomodeset is not a good solution.

---

### Post by immerohnegott on 2011-09-08
That explains why it's using the VESA driver. IIRC, the newer versions of the Intel driver require KMS to actually work. There seems to be a workaround [here]("http://forums.gentoo.org/viewtopic-t-892206-start-0.html") to fix the backlight issue at boot. I would guess that it's less to do with the chipset and more with Acer's implementation of it (the poster in that link is also on an Acer notebook).

---

### Post by iheartubuntu on 2011-09-08
Interesting, thanks. I wonder if I can regress to an earlier driver version? rev 07 maybe?

---

### Post by lucazade on 2011-09-08
> **immerohnegott said:**
> That explains why it's using the VESA driver. IIRC, the newer versions of the Intel driver require KMS to actually work. There seems to be a workaround [here]("http://forums.gentoo.org/viewtopic-t-892206-start-0.html") to fix the backlight issue at boot. I would guess that it's less to do with the chipset and more with Acer's implementation of it (the poster in that link is also on an Acer notebook).

Yep..nomodeset kills kms, maybe this is the issue. Otherwise take a look at dmesg

---

### Post by immerohnegott on 2011-09-08
Well, the revision numbers listed in the lspci are hardware revisions, not software. In theory, you could revert to an older version of the driver, but I don't really have any experience in that.

For now, it looks like you've got a couple options to at least have a semi-functional system for the Ubuntu Hour:

One) Try some of the stuff in that Gentoo link (in theory, removing the i915.modeset parameter and changing "acpi_osi=Linux" to just "acpi_osi=" would give you back the Intel driver and allow direct control over LCD brightness from the keyboard hotkeys)

Two) Scrounge up an external display and see if the driver will allow you to use that with KMS (also requires dumping that i915.modeset bit).

---

### Post by iheartubuntu on 2011-09-08
PROGRESS! Woohoo! It looks great now. Thanks for the tips.

> One) Try some of the stuff in that Gentoo link (in theory, removing the i915.modeset parameter and changing "acpi_osi=Linux" to just "acpi_osi=" would give you back the Intel driver and allow direct control over LCD brightness from the keyboard hotkeys)

So I did this. I got rid of linux so the command reads "acpi_osi=" and I removed the i915.modeset.

A new situation has come up. Upon reboot the screen was black. My function key along with the brightness key did nothing, but CTRL+brightness worked! I was able to now see the lightdm logon screen and log into the computer. From all my reading I think I can figure out a setting to add into grub to fix the screen brightness and then I should be good to go. Works great and nice to see Unity-3D.

MUCH APPRECIATED!

---

### Post by immerohnegott on 2011-09-08
Awesome! And you are most welcome. 

Also, I found a bug report on Launchpad describing this issue - so hopefully this will get fixed at some point.

---

