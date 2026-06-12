---
title: "GMA500 (Poulsbo) gma500_gfx"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by vojmary on 2014-04-06
Hey guys,
sorry to bother you, but I already installed Xubuntu 13.10, with xcfe 4.10 on my Eee PC 1101HA with Intel GMA 500. I am a total newbie in linux world, so I am writting this, to ask how to install Intel GMA 500 drivers. I have tried with Poulsbo, but after adding repository it just do not see any file, while trying to install the driver. Also, after using sudo apt-get update it shows, that repository is broken:

W: Failed to fetch [http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


So can you help me with this problem?


Next problem is that my backlight keys are broken. They work, and I can increase and decrease the brightness, but it seems like there are about five different scales, so when I push the FN + F5 to decrease brightness, it goes darker, suddenly there is max and so on for five times.

I also cannot change my resolution (1366x768) to lower like 1024x768. It does not show whole screen and it is cut in the middle.

Please. Help me to solve this problem.

---

### Post by oldfred on 2014-04-07
Moved post from this related but now old thread.
[http://ubuntuforums.org/showthread.php?t=1984236](http://ubuntuforums.org/showthread.php?t=1984236)

Your ppa is for saucy which may not work. 
Generally better not to use ppa unless that is the only alternative.
Old thread then said it should work out of the box?

Did you try various boot parameters in grub? Usually with Intel nomodeset is not correct, but the method for adding boot parameters is shown.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
        Older Intel video card:
 i915.modeset=1 or i915.modeset=0
 newer:
  i915.i915_enable_rc6=1

Also by original poster for 12.04.

 [http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)

---

### Post by vojmary on 2014-04-07
Mister, all I can know about linux for now is how to use sudo apt-get and nothing more, so I really do not know how to use GRUB settings and others.

---

### Post by Bashing-om on 2014-04-07
vojmary; Hi ! My Welcome to you.

If I may. let me see what I can do to nudge this along.

saucy is not supported by that Personal Package Archive, see:
[http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/](http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/)
To know this a true.

Remove that PPA from your Software sources lists. and then let's see what is:
post back the results - between code tags - of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo lshw -C display
lspci -nnk | grep -iA3 vga

``` so we also get a look at what your graphics situation overall is.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


If we are able to get the "problematic GMA500" driver situation under control, perhaps the other issues will also be resolved.

Not to know is not a sin; none of us were born knowing. Now that situation is correctable !

[INDENT][INDENT]just my little bit
[INDENT][INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vojmary on 2014-04-07
Alright. Runnin' the scripts.

#3. Result:

```
*-display               
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:22 memory:f3f80000-f3ffffff ioport:c880(size=8) memory:d0000000-dfffffff memory:f3f40000-f3f7ffff
```

As I understand, I have got this driver already? I was not installing this. Is it really on my computer, so why I cannot change resolution to lower?

Script #4.

```
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ce]
    Kernel driver in use: gma500
00:1b.0 Audio device [0403]: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller [8086:811b] (rev 07)

```

And how to repair baklight? I can switch it, but it likes to change suddenly and I cannot set it properly, cause the key for backlight are running out of the scale.

---

### Post by Bashing-om on 2014-04-07
vojmary; Umph,

Looking about, and the outlook does not look good:
see:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Maybe we can garner some focus to a better condition:
what results from terminal command: 
```

lsmod | grep gma

```

[INDENT][INDENT]maybe this is one of those times,
[INDENT][INDENT][INDENT]there just ain't
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vojmary on 2014-04-08
```
**gma500_gfx**            173701  2 
drm_kms_helper         46867  1 **gma500_gfx**
drm                   242400  3 drm_kms_helper,gma500_gfx
i2c_algo_bit           13197  1 **gma500_gfx**
video                  18777  2 [B]gma500_gfx,asus_wmi
[/B]

```

Some of these parameters are red, I bolded where the text was red.

---

### Post by Bashing-om on 2014-04-08
vojmary; Well,

That output indicates that the modules are loaded, and all "helper" files are enabled. It is now beyond my experience to advise any further. Others who are running the GMA500 driver will have to advise.

As to the red output, that "red" is a function of your terminal to indicate that the out put from "grep gma" is a match.

Wait and see what other advise others may offer.

[INDENT][INDENT]knowledge being the base of reason
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-08
Did you try the work arounds in the blog by bodhizazen? 

He says with the boot options it works.

---

### Post by vojmary on 2014-04-09
Bashing-om, thank you for sacrificing your valueable time.

I've tried some options at GRUB and it was succesful. Backlight is working properly without switching of the ACPI.

Unfortunately there is still problem with resolutions.

---

### Post by Bashing-om on 2014-04-09
vojmary; Hello,

That in and of it's self is 2 steps forward, and none back.

I have limited experience with setting resolutions. If one can not obtain the desired effect from the system settings, it is out of my field of experience. As bodhi.zazen's advise does not offer a solution, I can advise nothing further.

The one and only time I had similar problems, I changed the graphics card and monitor. For me was a welcome upgrade, not your desired course to a solution.

I hate to say I do not know
but ->
[INDENT][INDENT]if I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mikewhatever on 2014-04-11
> **vojmary said:**
> Hey guys,
sorry to bother you, but I already installed Xubuntu 13.10, with xcfe 4.10 on my Eee PC 1101HA with Intel GMA 500. I am a total newbie in linux world, so I am writting this, to ask how to install Intel GMA 500 drivers. I have tried with Poulsbo, but after adding repository it just do not see any file, while trying to install the driver. Also, after using sudo apt-get update it shows, that repository is broken:

Intel has had a host of linux drivers for gma500. Iironically, all of them suked badly, and most seem now abandoned.  GMA500_gfx is the only one that works on today distros, but has not seen much development feature wise. So, the only driver that works is installed - nothing to do here.
> 
W: Failed to fetch [http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


So can you help me with this problem?

That repository is not for 13.10. It contains packages for older releases, abandoned drivers that no longer work.

> Next problem is that my backlight keys are broken. They work, and I can increase and decrease the brightness, but it seems like there are about five different scales, so when I push the FN + F5 to decrease brightness, it goes darker, suddenly there is max and so on for five times.

I also cannot change my resolution (1366x768) to lower like 1024x768. It does not show whole screen and it is cut in the middle.

Please. Help me to solve this problem.

1366x768 seems to be the correct resolution for your netbook - no need to change it.

---

### Post by vojmary on 2014-04-11
> [COLOR=#000000]1366x768 seems to be the correct resolution for your netbook - no need to change it.[/COLOR]

Mister, I am using my netbook for presentations, and most of multimedia projectors are not compatibile with 1366x768 resolution, so I need to change it to 1024x768. 

I also need lower resolutions for running old programms in playonlinux or wine.

---

### Post by mikewhatever on 2014-04-11
So, are there other resolutions to switch to? If so, what happens when you choose the desired one? 
Can you post the output of **xrandr**, it should list the available modes.

---

### Post by vojmary on 2014-04-11
What is happening? Nah. Better ask, what isn't happening.

When I try to change to 1024x768 screen displays only half of the whole desktop, and changes refresh rate to 120,01 Hz.
When I try to change to 800x600 screen displays only one fourth of the whole desktop and starts to roll from left to right periodically.

Xrandr result.

```
S[FONT=arial]creen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096[/FONT]
[FONT=arial]LVDS-0 connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm[/FONT]
[FONT=arial]   1366x768       60.0*+[/FONT]
[FONT=arial]   1360x768       59.8     60.0  [/FONT]
[FONT=arial]   1024x768       60.0     60.0  [/FONT]
[FONT=arial]   960x720        60.0  [/FONT]
[FONT=arial]   928x696        60.1  [/FONT]
[FONT=arial]   896x672        60.0  [/FONT]
[FONT=arial]   960x600        60.0  [/FONT]
[FONT=arial]   960x540        60.0  [/FONT]
[FONT=arial]   800x600        60.0     60.3     56.2  [/FONT]
[FONT=arial]   840x525        60.0     59.9  [/FONT]
[FONT=arial]   800x512        60.2  [/FONT]
[FONT=arial]   700x525        60.0  [/FONT]
[FONT=arial]   640x512        60.0  [/FONT]
[FONT=arial]   720x450        59.9  [/FONT]
[FONT=arial]   640x480        60.0     59.9  [/FONT]
[FONT=arial]   680x384        59.8     60.0  [/FONT]
[FONT=arial]   576x432        60.1  [/FONT]
[FONT=arial]   512x384        60.0  [/FONT]
[FONT=arial]   400x300        60.3     56.3  [/FONT]
[FONT=arial]   320x240        60.1  [/FONT]
[FONT=arial]S-video-0 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=arial]S-video-1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=arial]VGA-0 disconnected (normal left inverted right x axis y axis)[/FONT]
```

---

### Post by mikewhatever on 2014-04-12
That's very odd, but I don't know the answer. ...sorry about that. We usually get gma500 users coplain of being stuck at a low resolution, not the other way around.

---

### Post by vojmary on 2014-04-12
Hah. Thanks for trying :)

---

### Post by vojmary on 2014-04-13
So? Anyone can help me?

---

