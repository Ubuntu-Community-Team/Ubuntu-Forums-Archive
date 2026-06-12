---
title: "Error Messages -- Graphics Driver Confusion -- Need Help"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by ellen3 on 2014-05-12
[FONT=Times New Roman][COLOR=#000000]Greetings;[/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000]Total noob here.  Please forgive posting mistakes,  and please know that any help is much appreciated. [/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000]Ubuntu12.04.4 recently installed on older HP Pavilion desktop (a1540n) having graphics processor "NVidia GeForce 6150 LE." Certain behaviors lead me to conclude graphic driver problems, including flickering screen and frequent freezing of mouse and/or keyboard within GUI. (Though symptoms are much reduced if Ubuntu is booted through the Recovery Mode, using "Resume normal boot.") [/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000]Also:[/COLOR][/FONT]
[FONT=Times New Roman][COLOR=#000000]Checking graphics driver thru GUI: "System>Details>Graphics" says installed driver is  called"VESA:Crush50Board -c51pvg0" (whatever that is!) (Incidentally, GUI "Hardware>Displays" incorrectly identifies my computer as a laptop even though the computer model is correctly identified in computer's name..."...EX276AA-ABA-a1540n".) [/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000]Also:[/COLOR][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]Running: (sudo lshw -C display) gives the following:[/FONT][/COLOR][/SIZE]
```

[SIZE=3][COLOR=#000000][FONT=Times New Roman]*-display UNCLAIMED 
   
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       description: VGAcompatible controller
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       product: C51[GeForce 6150 LE]
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       vendor: NVIDIACorporation
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       physical id: 5
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       bus info:pci@0000:00:05.0
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       version: a2
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       width: 64 bits
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       clock: 66MHz
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       capabilities: pmmsi vga_controller bus_master cap_list
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       configuration:latency=0
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       resources:memory:fc000000-fcffffff memory:e0000000-efffffff memory:fb000000-fbffffffmemory:80000000-8001ffff
[/FONT][/COLOR][/SIZE]

```

[SIZE=3][COLOR=#000000][FONT=Times New Roman]Shouldn't some driver be stated after"configuration"[/FONT][/COLOR][/SIZE]

[FONT=Times New Roman][COLOR=#000000]Also:[/COLOR][/FONT]
[FONT=Times New Roman][COLOR=#000000]If booted directly from GRUB, the following lines flash briefly before Ubuntuloads.[/COLOR][/FONT]
```

[FONT=Times New Roman][COLOR=#000000] [14.272793] [drm:drm_crtc_helper_set_config]*ERROR* failed to set mode on [CRTC:10][/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000] [14.272796] fbcon_init: detected unhandledfb_set_par error, error code -22[/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000] [14.272855] [drm:drm_crtc_helper_set_config]*ERROR* failed to set mode on [CRTC:10][/COLOR][/FONT]

```

[FONT=Times New Roman][COLOR=#000000]So, does the above indicate that the graphics driver is an issue, or is there something more important going on? I have read a bewildering array of posts regarding dealing with NVidia driver issues, and as a newcomer to Ubuntu/Linux I am feeling pretty much lost. I would prefer to use an OSS driver. Questions would include: Is there a specific Nouveau driver that I need? Would I need to somehow remove the existing driver? And what's all this about installing Linux sources and headers? What next?[/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000]Any advice to get a beginner on the right track would be much appreciated. A brief explanation along with any specific suggestions would be MUCH appreciated.[/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000]Ellen[/COLOR][/FONT]

[FONT=Times New Roman][COLOR=#000000]PS- Also, the monitor remains black on waking from "suspension" or sleep-mode. I am assuming this is another graphics-related issue. If not, will be another problem to be dealt with later. [/COLOR][/FONT]

---

### Post by buzzingrobot on 2014-05-12
Ellen, welcome to Ubuntu.  I don't have any definitive advice to offer, so please wait on someone else to show up with actually useful advice.

I do remember, though (refreshed with a quick Google) that the 6150 cards had problems with the open-source driver (Nouveau) about two years ago. Nouveau is the driver Ubuntu should try to use if it detects an active Nvidia card when it boots.  The fact that you are having a range of video isues probably points to those sorts of problems.

While I'd recommend waiting for someone to show up who can offer real help on using Nouveau, if you ever do want to try a proprietary Nvida driver, use the Additional Drivers tool, which will list the drivers it thinks are appropriate for you card. One of those should be Nouveau. The rest should be drivers from Nvidia.  Because the 6150 is showing its age, the 173 driver, if listed, is probably your best bet. 

But... don't mess with proprietary drivers until the underlying video issue is identified and fixed.  They are very often a first-class pain, frequently problematic after a kernel update, and one Nvidia driver needs to be entirely removed -- annoyingly difficult -- before installing another one.

(And, yes, as you noticed, there's a lot of less-than-useful stuff spread around about using Nvidia cards:  The cards differ, the drivers differ, and explanations explaining how to get one card working on one Linux distribution may or may not work anywhere else.)

Here's an Nvidia page from the Ubuntu wiki: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

---

### Post by ellen3 on 2014-05-13
[FONT=Arial][COLOR=#000000]Thanks much buzzingrobot for taking the time to respond. Your answer gave me the nudge to do the following, which seemed to solve immediate problems. I will state my steps very simply for the benefit of any other beginners with similar issues. [/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]Again, mine is an old HP Pavilion (a1540n) with graphics processor NVidia GeForce 6150LE.[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]And, again, the problem was that the graphics driver that installed with Ubuntu12.04.4 was not working.[/COLOR][/FONT]
> 
[FONT=Arial][COLOR=#000000]**1) **Went to Ubuntu Software Center and downloaded file called "NVidia binary X.org driver (version 173)" --( note: I had downloaded NO proprietary drivers when installing Ubuntu)[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]**2) **Opened System Settings>Hardware>Additional Drivers. There were three options listed:[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]-NVIDIA accelerated graphics driver (version 173)[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]-NVIDIA accelerated graphics driver (version 304)[Recommended][/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]-NVIDIA accelerated graphics driver (post-release updates)(version 304-updates)[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]To actually install a driver it needs to be "activated" then the computer needs to be restarted. I tried the first option and it caused a lot ofproblems. I then activated and installed (version 304). Voila![/COLOR][/FONT]


[FONT=Arial][COLOR=#000000]I can now boot normally with no pre-boot error messages. Have not noticed any unstable screen-image issues. Hardware>Displays now correctly identifies my monitor. (There still seem to be problems with sleep-mode, both entering and emerging, but solving those will be a new quest for another day.) [/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]I will happily call this thread closed and solved if someone could first explain just what one should do (if anything) with the "(post-releaseupdates)(version 304-updates)" option. [/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]Thank you.[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]Ellen[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]PS-- Proud that I could add one more solution to the NVidia collection![/COLOR][/FONT]

---

### Post by grahammechanical on 2014-05-13
Ubuntu comes with the open source video driver. When we run a Ubuntu live session Ubuntu will be using the open source video driver which is called Nouveau when we have an Nvidia graphic adapter and Radeon if the graphic adapter is by AMD/ATI.

When we install Ubuntu if we tick the box labelled "Install Third Party Software" we get as part of the installation not just video and audio codecs but also the proprietary video driver. I am not sure if this was true for 12.04 as it was originally released but it certainly is true for the releases that followed and it may be true for 12.04.4 which is the latest version of 12.04.

As has been noticed there are slightly different versions of proprietary video drivers. The recommended version is considered the most stable or tested version. In fact in Ubuntu 14.04 the designation "recommended" has been replaced with the designation "tested."

The "updates" version is a later release of the driver that has not been tested. Some people may want to install it if they think it might solve some problems that they are having.

We cannot have two video drivers installed or activated at the same time. When we install one driver any other driver that was being used gets de-activated. So, we do not need to do anything about video drivers that are listed but have not been activated. In fact it is most likely that they have not even been downloaded. Once we install a proprietary video driver then it is not removed from the hard disk even if we change to another video driver. 

This is nothing to worry about but it is possible to remove/delete the driver and we do need to be very specific about what we are removing. But there is no real need. There is especially no need to remove the open source video driver because that is now being used in Ubuntu when we use the Recovery mode Resume option.

Regards.

---

### Post by buzzingrobot on 2014-05-13
> **ellen3 said:**
> 
[FONT=Arial][COLOR=#000000]I will happily call this thread closed and solved if someone could first explain just what one should do (if anything) with the "(post-releaseupdates)(version 304-updates)" option. [/COLOR][/FONT]

[FONT=Arial][COLOR=#000000][/COLOR][/FONT]

If something works for me, I don't change it. I'm running "nvidia-331-updates" which a look at the repos shows is Ubuntu-speak for the driver Nvidia released as 331.38. Meanwhile, "nvidia-331", presumably minus updates, is also shown as  Nvidia's 331.38 release. I don't know the difference, if any.

---

### Post by ellen3 on 2014-05-14
[FONT=Arial][COLOR=#000000]Grahammechanical, thank you for explaining those points. [/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]If it's not stretching this thread too far, I am still curious about several things:[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]Buzzingrobot implies that within "Additional Drivers" I should be able to choose (activate/install) Nouveau. But, apparently, Nouveau was never downloaded when I installed Ubuntu. It has never been listed in "Additional Drivers",and has never shown up through any terminal inquiry that I've tried. [/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]So,question: is it possible to download Nouveau in any easy way, similar to how I downloaded the Nvidia drivers, so that it will show up in the "AdditionalDrivers" list? And, if it is in that list, could I then activate and install it as I did the NVidia drivers? (And then switch back to NVidia when it doesn't work!)[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]Buzzingrobot, I understand about not fixing things when they're not broken. This has long been my strategy using MS Windows -- legacy works for me... at least as long as MS will allow it. Mainly trying to learn something about Linux/Ubuntu here.  [/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]By the way, to update my experience with NVidia (version 304) driver, everything seems to be working well, even the sleep/wake process. It's a two-step process to wake up: a tap on the ctrl key wakes up the CPU and a jiggle of the mouse wakes up the monitor. Has worked without a hitch all day. All seems very stable![/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]Thanks again. 

Ellen[/COLOR][/FONT]

---

### Post by ellen3 on 2014-05-16
[FONT=Arial][COLOR=#000000]Thanks to those taking the time to help. My immediate problem is fixed, so I will label this thread solved if I can figure out how.[/COLOR][/FONT]

---

