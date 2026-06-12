---
title: "Luvcview Wont Install!!??"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by skylinedna on 2008-06-30
Im downloading the luvciew package and can untar it but it wont install. 

Dont have the foggiest idea why so can someone please try help me sort this stuff out... i been trying to get my cam going for like 6 months. i know people out there have done it so cant understand for the life of me why i cant



[B]skylinedna@MISKNK:~$  wget [http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz)
--21:46:30--  [/B]



[http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz)
           => `luvcview-20060920.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.150
Connecting to mxhaard.free.fr|212.27.63.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 62,854 (61K) [application/x-gzip]

100%[====================================>] 62,854         9.42K/s    ETA 00:00

21:46:37 (9.41 KB/s) - `luvcview-20060920.tar.gz' saved [62854/62854]

[B]
skylinedna@MISKNK:~$ zcat luvcview-20060920.tar.gz |tar xvf -
[/B]

luvcview-20060920/
luvcview-20060920/ToDo
luvcview-20060920/Makefile
luvcview-20060920/gui.c
luvcview-20060920/gui.h
luvcview-20060920/README
luvcview-20060920/avilib.c
luvcview-20060920/avilib.h
luvcview-20060920/v4l2_enumfrmfmt.h
luvcview-20060920/frmfmtenum.c
luvcview-20060920/huffman.h
luvcview-20060920/v4l2uvc.c
luvcview-20060920/v4l2uvc.h
luvcview-20060920/utils.c
luvcview-20060920/utils.h
luvcview-20060920/luvcview.c
luvcview-20060920/uvcvideo.h
luvcview-20060920/button.h

[B]
skylinedna@MISKNK:~$  cd luvcview-20060920
skylinedna@MISKNK:~/luvcview-20060920$ make[/B]


make: sdl-config: Command not found
make: sdl-config: Command not found
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc   -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc    -c -o luvcview.o luvcview.c
luvcview.c:32:21: error: SDL/SDL.h: No such file or directory
luvcview.c:33:28: error: SDL/SDL_thread.h: No such file or directory
luvcview.c:34:27: error: SDL/SDL_audio.h: No such file or directory
luvcview.c:35:27: error: SDL/SDL_timer.h: No such file or directory
luvcview.c:45:27: error: SDL/SDL_syswm.h: No such file or directory
luvcview.c:106: error: expected specifier-qualifier-list before &#8216;SDLKey&#8217;
luvcview.c:111: error: &#8216;SDLK_n&#8217; undeclared here (not in a function)
luvcview.c:111: warning: excess elements in struct initializer
luvcview.c:111: warning: (near initialization for &#8216;keyaction[0]&#8217;)
luvcview.c:111: warning: excess elements in struct initializer
luvcview.c:111: warning: (near initialization for &#8216;keyaction[0]&#8217;)
luvcview.c:112: error: &#8216;SDLK_b&#8217; undeclared here (not in a function)
luvcview.c:112: warning: excess elements in struct initializer
luvcview.c:112: warning: (near initialization for &#8216;keyaction[1]&#8217;)
luvcview.c:112: warning: excess elements in struct initializer
luvcview.c:112: warning: (near initialization for &#8216;keyaction[1]&#8217;)
luvcview.c:113: error: &#8216;SDLK_x&#8217; undeclared here (not in a function)
luvcview.c:113: warning: excess elements in struct initializer
luvcview.c:113: warning: (near initialization for &#8216;keyaction[2]&#8217;)
luvcview.c:113: warning: excess elements in struct initializer
luvcview.c:113: warning: (near initialization for &#8216;keyaction[2]&#8217;)
luvcview.c:114: error: &#8216;SDLK_w&#8217; undeclared here (not in a function)
luvcview.c:114: warning: excess elements in struct initializer
luvcview.c:114: warning: (near initialization for &#8216;keyaction[3]&#8217;)
luvcview.c:114: warning: excess elements in struct initializer
luvcview.c:114: warning: (near initialization for &#8216;keyaction[3]&#8217;)
luvcview.c:115: error: &#8216;SDLK_c&#8217; undeclared here (not in a function)
luvcview.c:115: warning: excess elements in struct initializer
luvcview.c:115: warning: (near initialization for &#8216;keyaction[4]&#8217;)
luvcview.c:115: warning: excess elements in struct initializer
luvcview.c:115: warning: (near initialization for &#8216;keyaction[4]&#8217;)
luvcview.c:116: error: &#8216;SDLK_v&#8217; undeclared here (not in a function)
luvcview.c:116: warning: excess elements in struct initializer
luvcview.c:116: warning: (near initialization for &#8216;keyaction[5]&#8217;)
luvcview.c:116: warning: excess elements in struct initializer
luvcview.c:116: warning: (near initialization for &#8216;keyaction[5]&#8217;)
luvcview.c:117: error: &#8216;SDLK_z&#8217; undeclared here (not in a function)
luvcview.c:117: warning: excess elements in struct initializer
luvcview.c:117: warning: (near initialization for &#8216;keyaction[6]&#8217;)
luvcview.c:117: warning: excess elements in struct initializer
luvcview.c:117: warning: (near initialization for &#8216;keyaction[6]&#8217;)
luvcview.c:118: error: &#8216;SDLK_a&#8217; undeclared here (not in a function)
luvcview.c:118: warning: excess elements in struct initializer
luvcview.c:118: warning: (near initialization for &#8216;keyaction[7]&#8217;)
luvcview.c:118: warning: excess elements in struct initializer
luvcview.c:118: warning: (near initialization for &#8216;keyaction[7]&#8217;)
luvcview.c:119: error: &#8216;SDLK_r&#8217; undeclared here (not in a function)
luvcview.c:119: warning: excess elements in struct initializer
luvcview.c:119: warning: (near initialization for &#8216;keyaction[8]&#8217;)
luvcview.c:119: warning: excess elements in struct initializer
luvcview.c:119: warning: (near initialization for &#8216;keyaction[8]&#8217;)
luvcview.c:120: error: &#8216;SDLK_e&#8217; undeclared here (not in a function)
luvcview.c:120: warning: excess elements in struct initializer
luvcview.c:120: warning: (near initialization for &#8216;keyaction[9]&#8217;)
luvcview.c:120: warning: excess elements in struct initializer
luvcview.c:120: warning: (near initialization for &#8216;keyaction[9]&#8217;)
luvcview.c:121: error: &#8216;SDLK_y&#8217; undeclared here (not in a function)
luvcview.c:121: warning: excess elements in struct initializer
luvcview.c:121: warning: (near initialization for &#8216;keyaction[10]&#8217;)
luvcview.c:121: warning: excess elements in struct initializer
luvcview.c:121: warning: (near initialization for &#8216;keyaction[10]&#8217;)
luvcview.c:122: error: &#8216;SDLK_t&#8217; undeclared here (not in a function)
luvcview.c:122: warning: excess elements in struct initializer
luvcview.c:122: warning: (near initialization for &#8216;keyaction[11]&#8217;)
luvcview.c:122: warning: excess elements in struct initializer
luvcview.c:122: warning: (near initialization for &#8216;keyaction[11]&#8217;)
luvcview.c:123: error: &#8216;SDLK_s&#8217; undeclared here (not in a function)
luvcview.c:123: warning: excess elements in struct initializer
luvcview.c:123: warning: (near initialization for &#8216;keyaction[12]&#8217;)
luvcview.c:123: warning: excess elements in struct initializer
luvcview.c:123: warning: (near initialization for &#8216;keyaction[12]&#8217;)
luvcview.c:124: error: &#8216;SDLK_p&#8217; undeclared here (not in a function)
luvcview.c:124: warning: excess elements in struct initializer
luvcview.c:124: warning: (near initialization for &#8216;keyaction[13]&#8217;)
luvcview.c:124: warning: excess elements in struct initializer
luvcview.c:124: warning: (near initialization for &#8216;keyaction[13]&#8217;)
luvcview.c:125: error: &#8216;SDLK_f&#8217; undeclared here (not in a function)
luvcview.c:125: warning: excess elements in struct initializer
luvcview.c:125: warning: (near initialization for &#8216;keyaction[14]&#8217;)
luvcview.c:125: warning: excess elements in struct initializer
luvcview.c:125: warning: (near initialization for &#8216;keyaction[14]&#8217;)
luvcview.c:126: error: &#8216;SDLK_l&#8217; undeclared here (not in a function)
luvcview.c:126: warning: excess elements in struct initializer
luvcview.c:126: warning: (near initialization for &#8216;keyaction[15]&#8217;)
luvcview.c:126: warning: excess elements in struct initializer
luvcview.c:126: warning: (near initialization for &#8216;keyaction[15]&#8217;)
luvcview.c:127: error: &#8216;SDLK_q&#8217; undeclared here (not in a function)
luvcview.c:127: warning: excess elements in struct initializer
luvcview.c:127: warning: (near initialization for &#8216;keyaction[16]&#8217;)
luvcview.c:127: warning: excess elements in struct initializer
luvcview.c:127: warning: (near initialization for &#8216;keyaction[16]&#8217;)
luvcview.c:128: error: &#8216;SDLK_m&#8217; undeclared here (not in a function)
luvcview.c:128: warning: excess elements in struct initializer
luvcview.c:128: warning: (near initialization for &#8216;keyaction[17]&#8217;)
luvcview.c:128: warning: excess elements in struct initializer
luvcview.c:128: warning: (near initialization for &#8216;keyaction[17]&#8217;)
luvcview.c:129: warning: excess elements in struct initializer
luvcview.c:129: warning: (near initialization for &#8216;keyaction[18]&#8217;)
luvcview.c:129: warning: excess elements in struct initializer
luvcview.c:129: warning: (near initialization for &#8216;keyaction[18]&#8217;)
luvcview.c:130: error: &#8216;SDLK_i&#8217; undeclared here (not in a function)
luvcview.c:130: warning: excess elements in struct initializer
luvcview.c:130: warning: (near initialization for &#8216;keyaction[19]&#8217;)
luvcview.c:130: warning: excess elements in struct initializer
luvcview.c:130: warning: (near initialization for &#8216;keyaction[19]&#8217;)
luvcview.c:131: error: &#8216;SDLK_j&#8217; undeclared here (not in a function)
luvcview.c:131: warning: excess elements in struct initializer
luvcview.c:131: warning: (near initialization for &#8216;keyaction[20]&#8217;)
luvcview.c:131: warning: excess elements in struct initializer
luvcview.c:131: warning: (near initialization for &#8216;keyaction[20]&#8217;)
luvcview.c:179: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
luvcview.c:181: error: expected &#8216;)&#8217; before &#8216;key&#8217;
luvcview.c:184: error: expected specifier-qualifier-list before &#8216;SDL_Surface&#8217;
luvcview.c:193: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;SDL_VIDEO_Flags&#8217;
luvcview.c: In function &#8216;main&#8217;:
luvcview.c:199: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
luvcview.c:199: error: &#8216;info&#8217; undeclared (first use in this function)
luvcview.c:199: error: (Each undeclared identifier is reported only once
luvcview.c:199: error: for each function it appears in.)
luvcview.c:201: error: &#8216;SDL_Surface&#8217; undeclared (first use in this function)
luvcview.c:201: error: &#8216;pscreen&#8217; undeclared (first use in this function)
luvcview.c:202: error: &#8216;SDL_Overlay&#8217; undeclared (first use in this function)
luvcview.c:202: error: &#8216;overlay&#8217; undeclared (first use in this function)
luvcview.c:203: error: &#8216;SDL_Rect&#8217; undeclared (first use in this function)
luvcview.c:203: error: expected &#8216;;&#8217; before &#8216;drect&#8217;
luvcview.c:204: error: &#8216;SDL_Event&#8217; undeclared (first use in this function)
luvcview.c:204: error: expected &#8216;;&#8217; before &#8216;sdlevent&#8217;
luvcview.c:205: error: &#8216;SDL_Thread&#8217; undeclared (first use in this function)
luvcview.c:205: error: &#8216;mythread&#8217; undeclared (first use in this function)
luvcview.c:206: error: &#8216;SDL_mutex&#8217; undeclared (first use in this function)
luvcview.c:206: error: &#8216;affmutex&#8217; undeclared (first use in this function)
luvcview.c:209: error: &#8216;Uint32&#8217; undeclared (first use in this function)
luvcview.c:209: error: expected &#8216;;&#8217; before &#8216;currtime&#8217;
luvcview.c:210: error: expected &#8216;;&#8217; before &#8216;lasttime&#8217;
luvcview.c:334: error: &#8216;SDL_INIT_VIDEO&#8217; undeclared (first use in this function)
luvcview.c:356: error: &#8216;SDL_VIDEO_Flags&#8217; undeclared (first use in this function)
luvcview.c:356: error: &#8216;SDL_HWSURFACE&#8217; undeclared (first use in this function)
luvcview.c:360: error: &#8216;SDL_ASYNCBLIT&#8217; undeclared (first use in this function)
luvcview.c:386: error: &#8216;SDL_SWSURFACE&#8217; undeclared (first use in this function)
luvcview.c:412: error: &#8216;SDL_YUY2_OVERLAY&#8217; undeclared (first use in this function)
luvcview.c:414: error: &#8216;drect&#8217; undeclared (first use in this function)
luvcview.c:430: error: &#8216;lasttime&#8217; undeclared (first use in this function)
luvcview.c:437: error: &#8216;struct pt_data&#8217; has no member named &#8216;ptscreen&#8217;
luvcview.c:438: error: &#8216;struct pt_data&#8217; has no member named &#8216;ptvideoIn&#8217;
luvcview.c:439: error: &#8216;struct pt_data&#8217; has no member named &#8216;ptsdlevent&#8217;
luvcview.c:439: error: &#8216;sdlevent&#8217; undeclared (first use in this function)
luvcview.c:440: error: &#8216;struct pt_data&#8217; has no member named &#8216;drect&#8217;
luvcview.c:442: error: &#8216;struct pt_data&#8217; has no member named &#8216;affmutex&#8217;
luvcview.c:446: error: &#8216;currtime&#8217; undeclared (first use in this function)
luvcview.c:473: error: &#8216;struct pt_data&#8217; has no member named &#8216;frmrate&#8217;
luvcview.c: At top level:
luvcview.c:500: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SDL_Surface&#8217;
luvcview.c: In function &#8216;GUI_whichbutton&#8217;:
luvcview.c:503: error: &#8216;Sint32&#8217; undeclared (first use in this function)
luvcview.c:503: error: expected &#8216;;&#8217; before &#8216;scaleh&#8217;
luvcview.c:504: error: &#8216;scaleh&#8217; undeclared (first use in this function)
luvcview.c:509: error: &#8216;pscreen&#8217; undeclared (first use in this function)
luvcview.c: At top level:
luvcview.c:516: error: expected &#8216;)&#8217; before &#8216;key&#8217;
luvcview.c: In function &#8216;eventThread&#8217;:
luvcview.c:532: error: &#8216;SDL_Surface&#8217; undeclared (first use in this function)
luvcview.c:532: error: &#8216;pscreen&#8217; undeclared (first use in this function)
luvcview.c:532: error: &#8216;struct pt_data&#8217; has no member named &#8216;ptscreen&#8217;
luvcview.c:533: error: &#8216;struct pt_data&#8217; has no member named &#8216;ptvideoIn&#8217;
luvcview.c:534: error: &#8216;SDL_Event&#8217; undeclared (first use in this function)
luvcview.c:534: error: &#8216;sdlevent&#8217; undeclared (first use in this function)
luvcview.c:534: error: &#8216;struct pt_data&#8217; has no member named &#8216;ptsdlevent&#8217;
luvcview.c:535: error: &#8216;SDL_Rect&#8217; undeclared (first use in this function)
luvcview.c:535: error: &#8216;drect&#8217; undeclared (first use in this function)
luvcview.c:535: error: &#8216;struct pt_data&#8217; has no member named &#8216;drect&#8217;
luvcview.c:536: error: &#8216;SDL_mutex&#8217; undeclared (first use in this function)
luvcview.c:536: error: &#8216;affmutex&#8217; undeclared (first use in this function)
luvcview.c:536: error: &#8216;struct pt_data&#8217; has no member named &#8216;affmutex&#8217;
luvcview.c:547: error: &#8216;struct pt_data&#8217; has no member named &#8216;frmrate&#8217;
luvcview.c:550: error: &#8216;SDL_KEYUP&#8217; undeclared (first use in this function)
luvcview.c:551: error: &#8216;SDL_MOUSEBUTTONUP&#8217; undeclared (first use in this function)
luvcview.c:556: error: &#8216;SDL_MOUSEBUTTONDOWN&#8217; undeclared (first use in this function)
luvcview.c:558: error: &#8216;SDL_MOUSEMOTION&#8217; undeclared (first use in this function)
luvcview.c:560: error: too many arguments to function &#8216;GUI_whichbutton&#8217;
luvcview.c:562: error: &#8216;SDL_VIDEORESIZE&#8217; undeclared (first use in this function)
luvcview.c:566: error: &#8216;SDL_VIDEO_Flags&#8217; undeclared (first use in this function)
luvcview.c:570: error: &#8216;SDL_KEYDOWN&#8217; undeclared (first use in this function)
luvcview.c:575: error: &#8216;SDL_QUIT&#8217; undeclared (first use in this function)
make: *** [luvcview.o] Error 1

---

### Post by AtrejuT on 2008-06-30
I suppose you need to install something like libsdl-dev.
```

sudo apt-get install libsdl-dev

```
Hope that helps

atreju

---

### Post by skylinedna on 2008-06-30
Ok i installed that. installed fine. so i dont know what happened now... Sorry to be a pain its bugging me

**skylinedna@MISKNK:~/luvcview-20060920$ make**

gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o luvcview.o luvcview.c
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o utils.o utils.c
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o v4l2uvc.o v4l2uvc.c
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o gui.o gui.c
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o avilib.o avilib.c
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o frmfmtenum.o frmfmtenum.c
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:8: error: nested redefinition of ‘enum v4l2_frmsizetypes’
v4l2_enumfrmfmt.h:8: error: redeclaration of ‘enum v4l2_frmsizetypes’
v4l2_enumfrmfmt.h:9: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_DISCRETE’
/usr/include/linux/videodev2.h:335: error: previous definition of ‘V4L2_FRMSIZE_TYPE_DISCRETE’ was here
v4l2_enumfrmfmt.h:10: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_CONTINUOUS’
/usr/include/linux/videodev2.h:336: error: previous definition of ‘V4L2_FRMSIZE_TYPE_CONTINUOUS’ was here
v4l2_enumfrmfmt.h:11: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_STEPWISE’
/usr/include/linux/videodev2.h:337: error: previous definition of ‘V4L2_FRMSIZE_TYPE_STEPWISE’ was here
v4l2_enumfrmfmt.h:14: error: nested redefinition of ‘enum v4l2_frmivaltypes’
v4l2_enumfrmfmt.h:14: error: redeclaration of ‘enum v4l2_frmivaltypes’
v4l2_enumfrmfmt.h:15: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_DISCRETE’
/usr/include/linux/videodev2.h:375: error: previous definition of ‘V4L2_FRMIVAL_TYPE_DISCRETE’ was here
v4l2_enumfrmfmt.h:16: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_CONTINUOUS’
/usr/include/linux/videodev2.h:376: error: previous definition of ‘V4L2_FRMIVAL_TYPE_CONTINUOUS’ was here
v4l2_enumfrmfmt.h:17: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_STEPWISE’
/usr/include/linux/videodev2.h:377: error: previous definition of ‘V4L2_FRMIVAL_TYPE_STEPWISE’ was here
v4l2_enumfrmfmt.h:24: error: redefinition of ‘struct v4l2_frmsize_discrete’
v4l2_enumfrmfmt.h:32: error: redefinition of ‘struct v4l2_frmsize_stepwise’
v4l2_enumfrmfmt.h:52: error: redefinition of ‘struct v4l2_frmsizeenum’
v4l2_enumfrmfmt.h:73: error: redefinition of ‘struct v4l2_frmival_stepwise’
v4l2_enumfrmfmt.h:84: error: redefinition of ‘struct v4l2_frmivalenum’
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:116:1: warning: "VIDIOC_ENUM_FRAMESIZES" redefined
In file included from /usr/include/linux/videodev.h:15,
                 from frmfmtenum.c:34:
/usr/include/linux/videodev2.h:1378:1: warning: this is the location of the previous definition
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:117:1: warning: "VIDIOC_ENUM_FRAMEINTERVALS" redefined
In file included from /usr/include/linux/videodev.h:15,
                 from frmfmtenum.c:34:
/usr/include/linux/videodev2.h:1379:1: warning: this is the location of the previous definition
make: *** [frmfmtenum.o] Error 1
skylinedna@MISKNK:~/luvcview-20060920$ sudo make install


gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o frmfmtenum.o frmfmtenum.c
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:8: error: nested redefinition of ‘enum v4l2_frmsizetypes’
v4l2_enumfrmfmt.h:8: error: redeclaration of ‘enum v4l2_frmsizetypes’
v4l2_enumfrmfmt.h:9: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_DISCRETE’
/usr/include/linux/videodev2.h:335: error: previous definition of ‘V4L2_FRMSIZE_TYPE_DISCRETE’ was here
v4l2_enumfrmfmt.h:10: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_CONTINUOUS’
/usr/include/linux/videodev2.h:336: error: previous definition of ‘V4L2_FRMSIZE_TYPE_CONTINUOUS’ was here
v4l2_enumfrmfmt.h:11: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_STEPWISE’
/usr/include/linux/videodev2.h:337: error: previous definition of ‘V4L2_FRMSIZE_TYPE_STEPWISE’ was here
v4l2_enumfrmfmt.h:14: error: nested redefinition of ‘enum v4l2_frmivaltypes’
v4l2_enumfrmfmt.h:14: error: redeclaration of ‘enum v4l2_frmivaltypes’
v4l2_enumfrmfmt.h:15: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_DISCRETE’
/usr/include/linux/videodev2.h:375: error: previous definition of ‘V4L2_FRMIVAL_TYPE_DISCRETE’ was here
v4l2_enumfrmfmt.h:16: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_CONTINUOUS’
/usr/include/linux/videodev2.h:376: error: previous definition of ‘V4L2_FRMIVAL_TYPE_CONTINUOUS’ was here
v4l2_enumfrmfmt.h:17: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_STEPWISE’
/usr/include/linux/videodev2.h:377: error: previous definition of ‘V4L2_FRMIVAL_TYPE_STEPWISE’ was here
v4l2_enumfrmfmt.h:24: error: redefinition of ‘struct v4l2_frmsize_discrete’
v4l2_enumfrmfmt.h:32: error: redefinition of ‘struct v4l2_frmsize_stepwise’
v4l2_enumfrmfmt.h:52: error: redefinition of ‘struct v4l2_frmsizeenum’
v4l2_enumfrmfmt.h:73: error: redefinition of ‘struct v4l2_frmival_stepwise’
v4l2_enumfrmfmt.h:84: error: redefinition of ‘struct v4l2_frmivalenum’
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:116:1: warning: "VIDIOC_ENUM_FRAMESIZES" redefined
In file included from /usr/include/linux/videodev.h:15,
                 from frmfmtenum.c:34:
/usr/include/linux/videodev2.h:1378:1: warning: this is the location of the previous definition
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:117:1: warning: "VIDIOC_ENUM_FRAMEINTERVALS" redefined
In file included from /usr/include/linux/videodev.h:15,
                 from frmfmtenum.c:34:
/usr/include/linux/videodev2.h:1379:1: warning: this is the location of the previous definition
make: *** [frmfmtenum.o] Error 1

---

### Post by AtrejuT on 2008-06-30
I think you are using an old version of luvcview. Try using
[http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz)

that should work. (compiles here)

good luck

atreju

---

