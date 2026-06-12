---
title: "HOWTO: Compile Avidemux from SVN/CVS"
date: 2006-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by SadaraX on 2006-06-26
EDIT: PLEASE NOTE -- This tutorial may become out of date with time. Please check the official Avidemux Wiki documentation where more current tutorial(s) are maintained.

[URL="http://www.avidemux.org/admWiki/index.php?title=Main_Page"]
http://www.avidemux.org/admWiki/index.php?title=Main_Page
[/URL]

For most users, if you just want the program (and you don't care about compiling it yourself), [you can usually just install it.]("http://www.avidemux.org/admWiki/index.php?title=Install_Ubuntu")

The current stable version of Avidemux is 2.5, [which has a tutorial for compiling here which I just updated]("http://www.avidemux.org/admWiki/index.php?title=Install_2.5#Manually_Getting_Dependencies_.28Linux_Only.29") ([http://www.avidemux.org/admWiki/index.php?title=Install_2.5#Manually_Getting_Dependencies_.28Linux_Only.29](http://www.avidemux.org/admWiki/index.php?title=Install_2.5#Manually_Getting_Dependencies_.28Linux_Only.29)).

---

### Post by boywondr16 on 2006-07-25
Sadara, I've followed the instructions and have avidemux compiled, but it doesn't have Win32 support.  I removed and recompiled and it still doesn't show Win32.  

Any ideas how to overcome this?

---

### Post by SadaraX on 2006-07-25
> **boywondr16 said:**
> Sadara, I've followed the instructions and have avidemux compiled, but it doesn't have Win32 support.  I removed and recompiled and it still doesn't show Win32.  

Any ideas how to overcome this?

Hi there. 

1st) My name is SadaraX, that's with an 'x'. I'm not a girl. :) I get that a lot unfortunately. 

2nd) About your troubles, I'm not sure what to say. I have to ask why do you need Win32 support? Whenever I have compiled this program under linux, I have never had it detect Win32 because I was indeed not compiling under Win32. This guide is not designed to help compile the Avidemux source code under a Win32 system, just under Ubuntu (though it generally works for most Debian linux systems). 

3rd) If you want to compile Avidemux for Win32, you probably need a different guide than this. Also, is there some reason the pre-compiled win32 binaries will not work for you? If you can tell me what you are trying to do, I will do my best to find a way to help you. While I have never compiled under Win32 per se, I am sure I can find out what the necessary steps are.

---

### Post by OrganicPanda on 2006-07-26
edit.. (removed), sorry stupid question i needed automake1.x (even though i'm on 6.06) installed, you might want to mention more about that in your guide for us less knowlegable ones

---

### Post by SadaraX on 2006-07-26
> **OrganicPanda said:**
> edit.. (removed), sorry stupid question i needed automake1.x (even though i'm on 6.06) installed, you might want to mention more about that in your guide for us less knowlegable ones

I have added automake1.9 to the apt-get install list in the original post.

---

### Post by Jeffery Mewtamer on 2006-08-13
I don't know if this effects Dapper and below, but I followed this guide in Edgy and had to manually edit my sources.list to enable multiverse repositories in order to get all of the dependencies.

---

### Post by telperion on 2006-08-14
ADM_x264.cpp:203: error: 'struct x264_param_t::<anonymous>' has no member named 'b_cbr'

Any idea?

edit - solved

With last x264, Ubuntu 6.06.1 
work:

svn co svn://svn.berlios.de/avidemux/branches/avidemux_2.3_branch/

---

### Post by bodah on 2006-08-19
got new version of avidemux2 then got this error when "make"

make[2]: Entering directory `/home/lt/avidemux_2.3_branch'
make[2]: Leaving directory `/home/lt/avidemux_2.3_branch'
*** Creating list of subdirectories
make[2]: Entering directory `/home/lt/avidemux_2.3_branch'
cd . && make -f admin/Makefile.common subdirs
make[3]: Entering directory `/home/lt/avidemux_2.3_branch'
make[3]: Leaving directory `/home/lt/avidemux_2.3_branch'
make[2]: Leaving directory `/home/lt/avidemux_2.3_branch'
*** Creating configure.files
*** Creating configure.in
make[2]: Entering directory `/home/lt/avidemux_2.3_branch'
cd . && make -f admin/Makefile.common configure.in ;
make[3]: Entering directory `/home/lt/avidemux_2.3_branch'
make[3]: Leaving directory `/home/lt/avidemux_2.3_branch'
make[2]: Leaving directory `/home/lt/avidemux_2.3_branch'
*** Creating aclocal.m4
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
make[1]: *** [cvs] Error 1
make: *** [all] Error 2

i was searching but couldnt find out why. anyone know why?

---

### Post by telperion on 2006-08-19
For me, this work:

svn co svn://svn.berlios.de/avidemux/branches/avidemux_2.3_branch/
cd avidemux_2.3_branch/
make -f Makefile.dist
./configure --with-jsapi-include=/usr/include/smjs/ --with-newfaad
sudo checkinstall 

(or make install)

---

### Post by bodah on 2006-08-21
> **telperion said:**
> For me, this work:

svn co svn://svn.berlios.de/avidemux/branches/avidemux_2.3_branch/
cd avidemux_2.3_branch/
make -f Makefile.dist
./configure --with-jsapi-include=/usr/include/smjs/ --with-newfaad
sudo checkinstall 

(or make install)

Thnx for reply telperion. I am sorry I was not clear in the beginning. I got the error message when I ran the "make -f Makefile.dist" command. This is before any configure. I am running on Fedora 4. Today I updated svn and still got same error. I tried altering aclocal.m4 but no change.

---

### Post by SadaraX on 2006-08-21
You are using Fedora? What versions of make, and automake are you using? Have you tried using newer or older versions than you currently have?

I have never compiled Avidemux on anything other than Debian systems, so I am not sure what to tell you.

---

### Post by telperion on 2006-08-21
> **bodah said:**
> Thnx for reply telperion. I am sorry I was not clear in the beginning. I got the error message when I ran the "make -f Makefile.dist" command. This is before any configure. I am running on Fedora 4. Today I updated svn and still got same error. I tried altering aclocal.m4 but no change.

[http://avidemux.org/wki/index.php?title=Compiling_Avidemux#Ubuntu.2FKubuntu_.28Dapper_6.06.2C_Breezy_5.10_.26_Hoary_5.04.29](http://avidemux.org/wki/index.php?title=Compiling_Avidemux#Ubuntu.2FKubuntu_.28Dapper_6.06.2C_Breezy_5.10_.26_Hoary_5.04.29)

ubuntu purge automake 1.4 and install new automake 1.9



fedora delete some line in configure.in and configure.in.in
read:
[http://www.avidemux.org/pun/viewtopic.php?id=2251](http://www.avidemux.org/pun/viewtopic.php?id=2251)

could be the solution

---

### Post by sup on 2006-09-23
I had to remove automake 1.6 and install automake 1.9, otherwise it is compiling nicely so far

---

### Post by ceenvee703 on 2006-09-28
I just found this thread after finding the same HOWTO on the Avidemux documentation wiki. I'm using the AMD64 version of 6.06 and am trying to get Avidemux 2.3 so I can enable multiprocessing on my AMD X2.

When I tried to apt-get install the required items, one failed:

```
 sudo apt-get install libsdl-console-dev

The following packages have unmet dependencies:
  libsdl-console-dev: Depends: libsdl-image1.2-dev but it is not going to be installed
E: Broken packages


```

I went through all the other steps just to see what would happen and things appeared to compile and install correctly. I guess I won't know for sure until I get home and try it. Any ideas how to resolve the dependencies, or if I've messed things up by ignoring it?

---

### Post by PRDR on 2006-10-01
Hi.

I went trough the described steps for compiling avidemux_2.3_branch, and everything went fine up to the *sudo checkinstall* one (the same thing happens if I try with sudo make install, of course).
That command finishes with the following error:

```
/bin/sh ../libtool --silent --tag=CXX --mode=link g++ -g -I.. -I../ADM_lavutil -IADM_library -I../ADM_library  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -O2 -falign-loops=16  -lpthread -lX11 -lXext -L/usr/X11R6/lib -o avidemux2   -L/usr/lib -lSDL -lpthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0   -pthread -lgthread-2.0 -lglib-2.0   -lfreetype -lz    -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lxml2 -lz -lm  guiplay.o gui_savenew.o gui_navigate.o gtk_gui.o callbacks.o avilist.o main.o prefs.o ADM_guiBitrate.o ADM_pp.o ADM_memsupport.o gui_autodrive.o GUI_jobs.o ADM_dialog/DIA_quota.o ADM_lavcodec/libavcodec.a ADM_lavcodec/libpostproc/libpostproc.a ./ADM_script/libADM_script.a ./ADM_editor/libADM_editor.a ./ADM_library/libADM_library.a ./ADM_openDML/libADM_openDML.a ./oplug_ogm/liboplug_ogm.a ./ADM_audiocodec/libADM_audiocodec.a ./ADM_audio/libADM_audio.a ./oplug_avi/liboplug_avi.a ./oplug_mp4/liboplug_mp4.a ./oplug_mpeg/liboplug_mpeg.a ./oplug_mpegFF/liboplug_mpegFF.a ./ADM_mplex/libADM_mplex.a ./ADM_lavformat/libADM_lavformat.a ./ADM_lavutil/libADM_lavutil.a ./ADM_lvemux/libADM_lvemux.a ./ADM_filter/libADM_filter.a ./ADM_video/libADM_video.a   ./ADM_encoder/libADM_encoder.a ./ADM_codecs/libADM_codecs.a ./ADM_vp32/libADM_vp32.a ./ADM_audiofilter/libADM_audiofilter.a ./libtoolame/liblibtoolame.a ./ADM_gui2/libADM_gui2.a ./MPlayer_pp/libMPlayer_pp.a ./mpeg2enc/libmpeg2enc.a ./ADM_liba52/libADM_liba52.a ./ADM_libMad/libADM_mad.a ./ADM_inpics/libADM_inpics.a  ./ADM_3gp/libADM_3gp.a ./ADM_avsproxy/libADM_avsproxy.a ./ADM_matroska/libADM_matroska.a ./ADM_asf/libADM_asf.a ./ADM_h263/libADM_h263.a ./ADM_nuv/libADM_nuv.a  ./ADM_ogm/libADM_ogm.a ./ADM_audiodevice/libADM_audiodevice.a ./ADM_xvidratectl/libADM_xvidratectl.a ./ADM_requant/libADM_requant.a ./ADM_ocr/libADM_ocr.a ./ADM_mpegdemuxer/libADM_mpegdemuxer.a ./ADM_audio/libADM_audio.a ./ADM_toolkit/libADM_toolkit.a ./ADM_dialog/libADM_dialog.a ./libMpeg2Dec/liblibMpeg2Dec.a ./ADM_tray/libADM_tray.a ./ADM_colorspace/libADM_colorspace.a ADM_lavcodec/libavcodec.a ./ADM_lavutil/libADM_lavutil.a ./ADM_lavcodec/libpostproc/libpostproc.a ./ADM_library/libADM_library.a ./ADM_toolkit/libADM_toolkit.a ./libass/libass.a   -lXv -lsmjs -lfontconfig -lmp3lame -lvorbis -lvorbisenc -lvorbis -lfaac -lfaad -lasound -lesd -lxvidcore -lxvidcore -lpng -lx264
libtool: link: cannot find the library `/usr/lib/libXrender.la'
make[2]: *** [avidemux2] Error 1
make[2]: Leaving directory `/usr/local/Packages/avidemux_2.3_branch/avidemux'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/local/Packages/avidemux_2.3_branch/avidemux'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye
```

My system is dapper with all the updates up to today.

Any ideas of what could be going wrong?

Thanx a million.

P.

---

### Post by PRDR on 2006-10-04
Problem solved:
[http://ubuntuforums.org/showthread.php?t=238449]("http://ubuntuforums.org/showthread.php?t=238449")

Of course, it had nothing to do with avidemux... Sorry for bothering you all with this...

P.

---

### Post by loko on 2006-10-27
this howto does not work for edgy at the moment, because it is not possible to install libsmjs-dev (libsmjs-dev depends on libmozjs-dev which depends on libnspr4-dev which cannot be installed because of conflicts).

i tried to compile spidermonkey from source, but i get an error:

```
...
jscpucfg.c:376: internal compiler error: in dwarf2out_finish, at dwarf2out.c:14129
Please submit a full bug report,
with preprocessed source if appropriate.
```

so it is not possible to build smjs at the moment, therefor it is not possible to compile avidemux.

if somebody knows a solution, let us know please.


EDIT: you can also take a look at this bug-report:
[https://launchpad.net/distros/ubuntu/+source/xulrunner/+bug/57161]("https://launchpad.net/distros/ubuntu/+source/xulrunner/+bug/57161")

---

### Post by sup on 2006-10-29
It is a [bug]("http://gcc.gnu.org/bugzilla/show_bug.cgi?id=26881") in gcc, but there is a workaround: ```
export BUILD_OPT=1
```, but I im stuck with another error:
```
make[1]: Circular Linux_All_OPT.OBJ/jsautocfg.h <- Linux_All_OPT.OBJ/jsautocfg.h dependency dropped.
gcc -o Linux_All_OPT.OBJ/jsapi.o -c -Wall -Wno-format -DGCC_OPT_BUG -O -DXP_UNIX -DSVR4 -DSYSV -D_BSD_SOURCE -DPOSIX_SOURCE -DHAVE_LOCALTIME_R -DX86_LINUX  -UDEBUG -DNDEBUG -UDEBUG_tom -DJS_THREADSAFE -DEDITLINE -I../../dist/Linux_All_OPT.OBJ/include -ILinux_All_OPT.OBJ  jsapi.c
In file included from jsatom.h:53,
                 from jsapi.c:56:
jslock.h:45:20: error: pratom.h: No such file or directory
jslock.h:46:20: error: prlock.h: No such file or directory
jslock.h:47:20: error: prcvar.h: No such file or directory
In file included from jsatom.h:53,
                 from jsapi.c:56:
jslock.h:60: error: expected specifier-qualifier-list before &#8216;PRLock&#8217;
jslock.h:71: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;JSLock&#8217;
In file included from jsapi.c:58:
jscntxt.h:154: error: expected specifier-qualifier-list before &#8216;PRLock&#8217;
jsapi.c: In function &#8216;JS_Init&#8217;:
jsapi.c:681: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:681: warning: implicit declaration of function &#8216;PR_NewLock&#8217;
jsapi.c:682: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:684: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcDone&#8217;
jsapi.c:684: warning: implicit declaration of function &#8216;PR_NewCondVar&#8217;
jsapi.c:684: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:685: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcDone&#8217;
jsapi.c:687: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestDone&#8217;
jsapi.c:687: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:688: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestDone&#8217;
jsapi.c:691: error: &#8216;JSRuntime&#8217; has no member named &#8216;rtLock&#8217;
jsapi.c:692: error: &#8216;JSRuntime&#8217; has no member named &#8216;rtLock&#8217;
jsapi.c:694: error: &#8216;JSRuntime&#8217; has no member named &#8216;stateChange&#8217;
jsapi.c:694: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:695: error: &#8216;JSRuntime&#8217; has no member named &#8216;stateChange&#8217;
jsapi.c:697: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotLock&#8217;
jsapi.c:698: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotLock&#8217;
jsapi.c:700: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotDone&#8217;
jsapi.c:700: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotLock&#8217;
jsapi.c:701: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotDone&#8217;
jsapi.c:703: error: &#8216;JSRuntime&#8217; has no member named &#8216;scopeSharingDone&#8217;
jsapi.c:703: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:704: error: &#8216;JSRuntime&#8217; has no member named &#8216;scopeSharingDone&#8217;
jsapi.c:706: error: &#8216;JSRuntime&#8217; has no member named &#8216;scopeSharingTodo&#8217;
jsapi.c: In function &#8216;JS_Finish&#8217;:
jsapi.c:737: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:738: warning: implicit declaration of function &#8216;PR_DestroyLock&#8217;
jsapi.c:738: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:739: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcDone&#8217;
jsapi.c:740: warning: implicit declaration of function &#8216;PR_DestroyCondVar&#8217;
jsapi.c:740: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcDone&#8217;
jsapi.c:741: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestDone&#8217;
jsapi.c:742: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestDone&#8217;
jsapi.c:743: error: &#8216;JSRuntime&#8217; has no member named &#8216;rtLock&#8217;
jsapi.c:744: error: &#8216;JSRuntime&#8217; has no member named &#8216;rtLock&#8217;
jsapi.c:745: error: &#8216;JSRuntime&#8217; has no member named &#8216;stateChange&#8217;
jsapi.c:746: error: &#8216;JSRuntime&#8217; has no member named &#8216;stateChange&#8217;
jsapi.c:747: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotLock&#8217;
jsapi.c:748: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotLock&#8217;
jsapi.c:749: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotDone&#8217;
jsapi.c:750: error: &#8216;JSRuntime&#8217; has no member named &#8216;setSlotDone&#8217;
jsapi.c:751: error: &#8216;JSRuntime&#8217; has no member named &#8216;scopeSharingDone&#8217;
jsapi.c:752: error: &#8216;JSRuntime&#8217; has no member named &#8216;scopeSharingDone&#8217;
jsapi.c: In function &#8216;JS_BeginRequest&#8217;:
jsapi.c:792: warning: implicit declaration of function &#8216;PR_Lock&#8217;
jsapi.c:792: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:795: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcThread&#8217;
jsapi.c:797: warning: implicit declaration of function &#8216;PR_WaitCondVar&#8217;
jsapi.c:797: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcDone&#8217;
jsapi.c:797: error: &#8216;PR_INTERVAL_NO_TIMEOUT&#8217; undeclared (first use in this function)
jsapi.c:797: error: (Each undeclared identifier is reported only once
jsapi.c:797: error: for each function it appears in.)
jsapi.c:801: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestCount&#8217;
jsapi.c:803: warning: implicit declaration of function &#8216;PR_Unlock&#8217;
jsapi.c:803: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c: In function &#8216;JS_EndRequest&#8217;:
jsapi.c:821: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:825: error: &#8216;JSRuntime&#8217; has no member named &#8216;scopeSharingTodo&#8217;
jsapi.c:850: warning: implicit declaration of function &#8216;PR_NotifyAllCondVar&#8217;
jsapi.c:850: error: &#8216;JSRuntime&#8217; has no member named &#8216;scopeSharingDone&#8217;
jsapi.c:854: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestCount&#8217;
jsapi.c:855: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestCount&#8217;
jsapi.c:856: warning: implicit declaration of function &#8216;PR_NotifyCondVar&#8217;
jsapi.c:856: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestDone&#8217;
jsapi.c:858: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c: In function &#8216;JS_YieldRequest&#8217;:
jsapi.c:875: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:877: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestCount&#8217;
jsapi.c:878: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestCount&#8217;
jsapi.c:879: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestDone&#8217;
jsapi.c:880: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:883: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:884: error: &#8216;JSRuntime&#8217; has no member named &#8216;requestCount&#8217;
jsapi.c:885: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c: In function &#8216;JS_MapGCRoots&#8217;:
jsapi.c:1659: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c:1661: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcLock&#8217;
jsapi.c: In function &#8216;JS_GetClass&#8217;:
jsapi.c:1985: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcThread&#8217;
jsapi.c: In function &#8216;JS_GetPrivate&#8217;:
jsapi.c:2021: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcThread&#8217;
jsapi.c: In function &#8216;JS_GetPrototype&#8217;:
jsapi.c:2050: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcThread&#8217;
jsapi.c: In function &#8216;JS_GetParent&#8217;:
jsapi.c:2071: error: &#8216;JSRuntime&#8217; has no member named &#8216;gcThread&#8217;
jsapi.c: In function &#8216;JS_SetCheckObjectAccessCallback&#8217;:
jsapi.c:2935: error: &#8216;JSRuntime&#8217; has no member named &#8216;checkObjectAccess&#8217;
jsapi.c:2936: error: &#8216;JSRuntime&#8217; has no member named &#8216;checkObjectAccess&#8217;
jsapi.c: In function &#8216;JS_HoldPrincipals&#8217;:
jsapi.c:2990: warning: implicit declaration of function &#8216;PR_AtomicIncrement&#8217;
jsapi.c:2990: error: &#8216;PRInt32&#8217; undeclared (first use in this function)
jsapi.c:2990: error: expected expression before &#8216;)&#8217; token
jsapi.c: In function &#8216;JS_DropPrincipals&#8217;:
jsapi.c:2996: warning: implicit declaration of function &#8216;PR_AtomicDecrement&#8217;
jsapi.c:2996: error: &#8216;PRInt32&#8217; undeclared (first use in this function)
jsapi.c:2996: error: expected expression before &#8216;)&#8217; token
jsapi.c: In function &#8216;JS_SetPrincipalsTranscoder&#8217;:
jsapi.c:3008: error: &#8216;JSRuntime&#8217; has no member named &#8216;principalsTranscoder&#8217;
jsapi.c:3009: error: &#8216;JSRuntime&#8217; has no member named &#8216;principalsTranscoder&#8217;
make[1]: *** [Linux_All_OPT.OBJ/jsapi.o] Error 1
make[1]: Leaving directory `/home/tom/Desktop/js/src'
make: *** [all] Error 2

```

another useful link for this is a guide how to compile spidermonkey for avidemux: [http://www.avidemux.org/pun/viewtopic.php?id=2527]("http://www.avidemux.org/pun/viewtopic.php?id=2527")

---

### Post by sup on 2006-10-29
ok, so I needed to install libnspr-dev libnspr4 packages and then change ```
INCLUDES += -I../../dist/$(OBJDIR)/include
```
```
INCLUDES += -I/usr/include/firefox/nspr
```
in order to get safe threading working, as stated on avidemux forum page I linked in the post above... but I am struggling in letting avidemux know where spidermoneky has been installed now:-/

---

### Post by sup on 2006-10-29
humph, so it seems all this hussle was not needed - one just needs to have guts.

Anyway, just install libnspr4-dev - it will remove awful lot of important stuff but it does not matter, everything should work until you restart (but I do recommend closing gnome-terminal either) and before that you will install it back.
Than install ibmozjs-dev libsmjs-dev and configure avidemux with  ./configure --with-jsapi-include=/usr/include/smjs --with-newfaad (I do not know what newfaad is exactly for, but it is on avidedemux wiki, so I do not question it) and make and install it as usual (it should work, I have not tried it yet because I need to get support for 264 first). Then install evrything back (and remove installed packages).
I think the original howto should be updated about this, because if I understand the bugreport mentioned above, it will not be fixed unitl Feisty.

I will update avidemux wiki.

---

### Post by sup on 2006-10-29
so the same process was needed for libxine (or gxine) as well.
 just for your need, this is what you are likely to install after you succesfully compiled avidemux
```
sudo apt-get install bug-buddy contact-lookup-applet deskbar-applet ekiga epiphany-browser evolution evolution-data-server evolution-exchange evolution-plugins firefox firefox-gnome-support gnome-app-install gnome-applets gnome-control-center gnome-panel gnome-session gnome-terminal libebook1.2-9 libedata-book1.2-2 libedataserverui1.2-8 libnspr-dev libnspr4 nautilus nautilus-cd-burner nautilus-sendto yelp

```

and do not spend too long without gnome-panel etc. installed, after several hours my desktop crashed and I had to reinstall it from command line, thank god I remembered most of the important packages...

---

### Post by SadaraX on 2006-10-29
> **sup said:**
> h./configure --with-jsapi-include=/usr/include/smjs --with-newfaad (I do not know what newfaad is exactly for, but it is on avidemux wiki, so I do not question it)

The --with-newfaad option is because there are two versions of faac/faad floating around in linux. One options must be dealt with one way while the other needs something slightly different. The --with-newfaad tells Avidemux configure what version to expect.

---

