---
title: "Flash 11 no vdpau support?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by beew on 2011-10-09
Just upgraded to flash 11.0.152 (32bit) and I noticed that cpu usage on Youtube has jumped up sharply, I clicked on the video, from the setting it says "software rendering" so it is not using vdpau. Am I missing something? Flash 10 has been working very nicely with hardware acceleration on my machine.

---

### Post by Linuxisfast on 2011-10-09
Do you have vdpau requisite files installed?

---

### Post by beew on 2011-10-09
Of course I do. Flash 10.x was using vdpau.

---

### Post by fooman on 2011-10-09
how did you do the upgrade?

might want to give "flash-aid" a go if you have not tried it already.  it will give you the option of installing the latest, stable flash release...or the latest beta version.  it will also remove any prior/conflicting flash as well as adding some performance tweaks:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by beew on 2011-10-09
I upgraded with flash-aid.

---

### Post by philinux on 2011-10-09
> **beew said:**
> I upgraded with flash-aid.

I think on mine when I right click on a video and look in Settings, it shows the Enable Hardware Acceleration ticked. I think that is the default.

---

### Post by beew on 2011-10-09
Yes hardware accelearation is  enabled in settings, but it doesn't mean that it is actually used. It is checked by default even if you watch youtube on a machine that doesn't support hardware acceleration with flash (no Nvidia card e.g) But if you click "show video info"  it will tell you what actually happens, on mine it says "software rendering accelerated decoding"

---

### Post by stmiller on 2011-10-09
flash has never used vdpau. It had some kind of hardware acceleration under linux which always ended up using more cpu. :/

---

### Post by papibe on 2011-10-09
> **stmiller said:**
> flash has never used vdpau. It had some kind of hardware acceleration under linux which always ended up using more cpu. :/
I'm pretty sure it has vdpau support:
```
$ strings /usr/lib/firefox/plugins/flashplugin-alternative.so  | grep -i vdpau

H264 - VDPAU - CPU
H264 - VDPAU - VDPAU
libvdpau.so
libvdpau.so.1
GL_NV_vdpau_interop
glVDPAUInitNV
glVDPAUFiniNV
glVDPAUUnregisterSurfaceNV
glVDPAUSurfaceAccessNV
glVDPAUMapSurfacesNV
glVDPAUUnmapSurfacesNV
glVDPAURegisterOutputSurfaceNV
```
I'm able to see smooth full HD flash video (with medium to low CPU usage), using method described [here]("http://ubuntuforums.org/showpost.php?p=11255771&postcount=23"). I have a flash update pending though (10.4). I will update this info if the new plugin has some issues.

@stmiller, could you test that in your system?

Regards.

EDIT: I updated to the latest. The 'strings' changed a little bit, but the plug-in still supports acceleration.

---

### Post by beew on 2011-10-10
This is my output

> strings /usr/lib/firefox/plugins/flashplugin-alternative.so  |grep -i vdpau
VDPAU,H264,
VDPAU,Device 
VDPAU,
libvdpau.so
libvdpau.so.1
glVDPAUInitNV
glVDPAUFiniNV
glVDPAUUnregisterSurfaceNV
glVDPAUSurfaceAccessNV
glVDPAUMapSurfacesNV
glVDPAUUnmapSurfacesNV
glVDPAURegisterOutputSurfaceNV
However, I am pretty sure that it doesn't support vdpau or very poorly on my machine by comparing cpu usage before  and after updating to flash 11.01 on the same youtube clips. Some 1080p clips used to take about 10% cpu now it shoots up to 70-80% (mplayer is still working well with vdpau so flash is the only factor that has changed)

---

### Post by papibe on 2011-10-10
I tested again, and you are right, the new version does not support acceleration as well as the previous version.

I can play the full HD videos, but my CPU jumped to around 70% (used to be around 15%).

:( Not good.

EDIT: I wonder how one goes to report this.. launchpad?

---

### Post by beew on 2011-10-10
> **papibe said:**
> I tested again, and you are right, the new version does not support acceleration as well as the previous version.

I can play the full HD videos, but my CPU jumped to around 70% (used to be around 15%).

:( Not good.

EDIT: I wonder how one goes to report this.. launchpad?

Thanks for confirming that I am not the only one having issues. I am sure it is an Asobe problem rather than Ubuntu's. I have tried installing various versions of flash11 beta using flash-aid and it always has the same problem,  I thought they would have sorted it out before they release the  stable version..

---

### Post by LowSky on 2011-10-10
Flash DOES support VDPAU, unfortunately on my PC using the 64bit version it sometimes freezes the PC into a state where I need to reboot.

But no need for VDPAU when you have a 4 core processor at 3.5Ghz, lol

---

### Post by alexcckll on 2011-10-10
From memory, while it appears to support VDPAU enough to call hardware decoding (which definitely helps my netbook along), I think they ripped out the experimental Stage Video logic (possibly where the "software|accelerated rendering" came in) which was experimental in 10.x.

Means of course that the CPU usage is still a bit high - but hopefully full Stage Video support is on the maint list...

But at least it isn't rendering as a slideshow as it was before Flash 10... 

Comments based on a Lenovo Ideapad S12...

---

### Post by philinux on 2011-10-10
> **papibe said:**
> I tested again, and you are right, the new version does not support acceleration as well as the previous version.

I can play the full HD videos, but my CPU jumped to around 70% (used to be around 15%).

:( Not good.

EDIT: I wonder how one goes to report this.. launchpad?

According to this post #25 has an explanation.
[https://bbs.archlinux.org/viewtopic.php?pid=961476#p961476](https://bbs.archlinux.org/viewtopic.php?pid=961476#p961476)
I'm no expert on this either and your test vid runs smooth but 2 cores go to 80%. To report to launchpad:-
```
ubuntu-bug *packagename*
```

---

