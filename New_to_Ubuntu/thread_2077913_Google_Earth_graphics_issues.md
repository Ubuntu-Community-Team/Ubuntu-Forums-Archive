---
title: "Google Earth/ graphics issues"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by Sherman530 on 2012-10-29
[FONT=Arial][SIZE=2]Hey all,

Pretty new at this ubuntu thing but I think I may have installed a non-compatible package... or my computer is just slowly collapsing into a black hole.  Certainly feels like the latter.  Basically my whole experience with Ubuntu has been troubleshooting for about 3 straight days... I'm sure [SIZE=2]this will be the first of many posts I'm making unfor[SIZE=2]tunately[SIZE=2].:mad:[/SIZE][/SIZE][/SIZE]

System Specs:
Ubuntu 12.04 x64 (partition)
Windows 7 x64 on other side
[/SIZE][/FONT][COLOR=#333333][FONT=arial][FONT=Book Antiqua][FONT=Arial][SIZE=2][COLOR=Black]3rd generation Intel(R) Core(TM) i7-3610QM Processor (2.3 GHz, 6MB L3 Cache)
NVIDIA(R) GeForce(R) GT 630M Graphics with 1GB GDDR3 memory [HDMI, VGA]
12GB DDR3 System Memory (2 Dim[SIZE=2]m)


[SIZE=2][SIZE=2][SIZE=2]When I launch google earth in terminal I get this error:
[SIZE=2]Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
[SIZE=2][SIZE=2]#(This is repea[SIZE=2]ted about [SIZE=2]50 times)[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR]
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:
[/SIZE][/FONT]
[SIZE=2]blahblahblah text file


[SIZE=2]So I'm pretty sure this is a graphics issue.  Amusingly this program was worki[SIZE=2]ng just fine [SIZE=2]ye[SIZE=2]sterday.  I tried to install the newest [SIZE=2]nvidia driver[SIZE=2] but was unable to figure out how to sh[SIZE=2]ut down [SIZE=2]x server.

[SIZE=2]Followed this guide:
[SIZE=2]http://ubuntuforums.org/showthread.php?t=1972901

[SIZE=2][SIZE=2][SIZE=2]The[SIZE=2] system j[SIZE=2]ust hangs in limbo and won't allow me to do anything but type commands with no response after I [SIZE=2]stop[SIZE=2] light[SIZE=2]dm[SIZE=2].[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]
[/FONT][/COLOR]
[SIZE=2]All of this may be ir[SIZE=2]relelvant because I[SIZE=2]'m about to be eaten by a hurrican[SIZE=2]e.

[SIZE=2]Thanks all!

[SIZE=2]-Sherm[/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by Sherman530 on 2012-10-29
Well its working again.  However clamped polygons are not supported which is unfortunate because I need to get some KMLs.  Apparently I have 2 graphics cards, an Intel Ivybridge+ the Nvidia I listed above.  I am now running on the Intel... odd problem. 

So if anyone knows about a "clamped polygon" problem solution feel free to enlighten me

Thanks

---

### Post by Tommy on 2012-11-02
> **Sherman530 said:**
> Well its working again.  However clamped polygons are not supported which is unfortunate because I need to get some KMLs.  Apparently I have 2 graphics cards, an Intel Ivybridge+ the Nvidia I listed above.  I am now running on the Intel... odd problem. 

So if anyone knows about a "clamped polygon" problem solution feel free to enlighten me

Thanks

I wish I knew what "clamped polygons" are, but I have been ignoring that message and have been drawing and loading all sorts of kml polygons as well as creating overlays and saving and loading the overlays as .kmz files. I THINK what the message means is that the polygons show as an empty shape instead of a filled shape, which for my purposes is just fine.

I was following a discussion today on the ubuntu-users mailing list and added the "official" Google repository. As it turns out TODAY (well, November 1st) there's a brand-new version of Google Earth out, version 7.0-something. It LOOKS slicker, but I can't get any of the earth image layers to display, so I uninstalled it and went back to the 6.0.3.2197 that I've been using. (I created the .deb using the googleearth-package script. Who knows what version that script would create if I run it tomorrow?)

---

