---
title: "Logitech Quickcam Express"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Nedimm on 2008-10-09
I am new to Linux and my English is bad :)
My web cam is Logitech Quickcam Express
O.S. Ubuntu 8.04 x64
Picture of camera [http://www.logitech.com/index.cfm/435/254&cl=us,en](http://www.logitech.com/index.cfm/435/254&cl=us,en)
My question is how to install this web cam? With Xawtv works great but cant save video or take picture.
On camorama picture is blue even when I adjust brightness...
Also I tried with this tutorial [http://www.linuxjournal.com/video/get-your-webcam-working-gspca](http://www.linuxjournal.com/video/get-your-webcam-working-gspca) but get this error when try to compile spcagui20060127:

make: sdl-config: Command not found
cc -DUSE_SDL -O2 -DLINUX  -DHAVE_LIBJPEG=1   -c -o spcagui.o spcagui.c
In file included from spcagui.c:23:
gui.h:11:21: error: SDL/SDL.h: No such file or directory
gui.h:12:23: error: SDL_image.h: No such file or directory
In file included from spcagui.c:23:
gui.h:41: error: expected specifier-qualifier-list before &#8216;SDL_Surface&#8217;
gui.h:51: error: expected specifier-qualifier-list before &#8216;SDL_Surface&#8217;
gui.h:63: error: expected specifier-qualifier-list before &#8216;SDL_Surface&#8217;
gui.h:76: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
gui.h:79: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
gui.h:87: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
gui.h:90: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
gui.h:99: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
gui.h:102: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
gui.h:105: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
In file included from spcagui.c:26:
utils.h:22:21: error: jpeglib.h: No such file or directory
spcagui.c:224: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
spcagui.c: In function &#8216;refresh_screen&#8217;:
spcagui.c:238: error: &#8216;Screen&#8217; undeclared (first use in this function)
spcagui.c:238: error: (Each undeclared identifier is reported only once
spcagui.c:238: error: for each function it appears in.)
spcagui.c: In function &#8216;telecom&#8217;:
spcagui.c:289: error: &#8216;SDL_Surface&#8217; undeclared (first use in this function)
spcagui.c:289: error: &#8216;screen&#8217; undeclared (first use in this function)
spcagui.c:291: error: &#8216;Uint32&#8217; undeclared (first use in this function)
spcagui.c:291: error: expected &#8216;;&#8217; before &#8216;video_flags&#8217;
spcagui.c:292: error: &#8216;SDL_Event&#8217; undeclared (first use in this function)
spcagui.c:292: error: expected &#8216;;&#8217; before &#8216;event&#8217;
spcagui.c:295: error: &#8216;lib_flags&#8217; undeclared (first use in this function)
spcagui.c:295: error: &#8216;SDL_INIT_VIDEO&#8217; undeclared (first use in this function)
spcagui.c:297: error: &#8216;video_flags&#8217; undeclared (first use in this function)
spcagui.c:297: error: &#8216;SDL_HWPALETTE&#8217; undeclared (first use in this function)
spcagui.c:297: error: &#8216;SDL_DOUBLEBUF&#8217; undeclared (first use in this function)
spcagui.c:315: error: too many arguments to function &#8216;draw_button&#8217;
spcagui.c:316: error: too many arguments to function &#8216;draw_button&#8217;
spcagui.c:317: error: too many arguments to function &#8216;draw_button&#8217;
spcagui.c:318: error: too many arguments to function &#8216;draw_button&#8217;
spcagui.c:319: error: too many arguments to function &#8216;draw_button&#8217;
spcagui.c:320: error: too many arguments to function &#8216;draw_button&#8217;
spcagui.c:321: error: too many arguments to function &#8216;draw_potentiometre&#8217;
spcagui.c:322: error: too many arguments to function &#8216;draw_potentiometre&#8217;
spcagui.c:323: error: too many arguments to function &#8216;draw_potentiometre&#8217;
spcagui.c:324: error: too many arguments to function &#8216;draw_control&#8217;
spcagui.c:325: error: too many arguments to function &#8216;draw_control&#8217;
spcagui.c:329: error: &#8216;event&#8217; undeclared (first use in this function)
spcagui.c:332: error: &#8216;SDL_MOUSEMOTION&#8217; undeclared (first use in this function)
spcagui.c:343: error: too many arguments to function &#8216;process_potentiometre&#8217;
spcagui.c:352: error: too many arguments to function &#8216;process_potentiometre&#8217;
spcagui.c:360: error: too many arguments to function &#8216;process_potentiometre&#8217;
spcagui.c:368: error: &#8216;SDL_MOUSEBUTTONUP&#8217; undeclared (first use in this function)
spcagui.c:376: error: &#8216;SDL_MOUSEBUTTONDOWN&#8217; undeclared (first use in this function)
spcagui.c:404: error: too many arguments to function &#8216;process_control&#8217;
spcagui.c:411: error: too many arguments to function &#8216;refresh_control&#8217;
spcagui.c:414: error: too many arguments to function &#8216;refresh_control&#8217;
spcagui.c:422: error: too many arguments to function &#8216;process_control&#8217;
spcagui.c:431: error: too many arguments to function &#8216;process_potentiometre&#8217;
spcagui.c:439: error: too many arguments to function &#8216;process_potentiometre&#8217;
spcagui.c:446: error: too many arguments to function &#8216;process_potentiometre&#8217;
spcagui.c:461: error: too many arguments to function &#8216;process_button&#8217;
spcagui.c:473: error: too many arguments to function &#8216;process_button&#8217;
spcagui.c:477: error: too many arguments to function &#8216;process_button&#8217;
spcagui.c:482: error: too many arguments to function &#8216;process_button&#8217;
spcagui.c:488: error: too many arguments to function &#8216;process_button&#8217;
spcagui.c: In function &#8216;processvideo&#8217;:
spcagui.c:504: error: &#8216;SDL_Surface&#8217; undeclared (first use in this function)
spcagui.c:504: error: &#8216;screen&#8217; undeclared (first use in this function)
spcagui.c:505: error: &#8216;Uint32&#8217; undeclared (first use in this function)
spcagui.c:505: error: expected &#8216;;&#8217; before &#8216;video_flags&#8217;
spcagui.c:506: error: &#8216;SDL_Event&#8217; undeclared (first use in this function)
spcagui.c:506: error: expected &#8216;;&#8217; before &#8216;event&#8217;
spcagui.c:508: error: &#8216;lib_flags&#8217; undeclared (first use in this function)
spcagui.c:508: error: &#8216;SDL_INIT_VIDEO&#8217; undeclared (first use in this function)
spcagui.c:509: error: &#8216;video_flags&#8217; undeclared (first use in this function)
spcagui.c:509: error: &#8216;SDL_HWPALETTE&#8217; undeclared (first use in this function)
spcagui.c:509: error: &#8216;SDL_DOUBLEBUF&#8217; undeclared (first use in this function)
spcagui.c:583: error: too many arguments to function &#8216;refresh_screen&#8217;
make: *** [spcagui.o] Error 1

---

### Post by quibbler on 2008-10-10
Try this:

[http://sourceforge.net/project/showfiles.php?group_id=200261&package_id=237741&release_id=619131](http://sourceforge.net/project/showfiles.php?group_id=200261&package_id=237741&release_id=619131)

It works for me.

Regards quibbler

---

### Post by Nedimm on 2008-10-10
Error I get:

checking for WXCAM... configure: error: Package requirements (gtk+-2.0 libglade-2.0 mjpegtools) were not met:

No package 'mjpegtools' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables WXCAM_CFLAGS
and WXCAM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I have already installed mjpegtools but wxcam cant find package.
What to do

---

### Post by hyper_ch on 2008-10-10
I found that the uvc drivers here: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) now make my QC Fusion work :)

---

### Post by Nedimm on 2008-10-10
My camera is non-UVC web cam.
[http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams)

---

### Post by hyper_ch on 2008-10-10
that sux :( the drivers from berlios really helped me :( good luck with your cam.

---

### Post by Nedimm on 2008-10-11
After I reinstall my Ubuntu webcam works fine with Cheese (before reinstall picture was dark) but on camorama picture is still blue.

UPDATE:I have installed wxcam and works great!

---

