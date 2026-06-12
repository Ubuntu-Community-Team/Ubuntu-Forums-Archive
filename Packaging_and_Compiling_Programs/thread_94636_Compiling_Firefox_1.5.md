---
title: "Compiling Firefox 1.5"
date: 2005-11-24
forum: Packaging and Compiling Programs
---

### Post by Single on 2005-11-24
I keep getting some errors while compiling firefox 1.5rc3. I don't know how to solve it. Stucked at XRemoteClient.cpp

```

[LEFT]make[3]: Leaving directory `/home/jenfoong/mozilla/firefox/toolkit/components'
make[3]: Entering directory `/home/jenfoong/mozilla/firefox/widget/src/xremotecl ient'
c++ -o mozilla-xremote-client -O3 -march=pentium-m -pipe -fomit-frame-pointer -m sse2 -mmmx -mfpmath=sse -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-a rith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-v irtual-dtor -Wno-long-long -pedantic -O3 -march=pentium-m -pipe -fomit-frame-poi nter -msse2 -mmmx -mfpmath=sse -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -Os -freorder-blocks -march=pentium-m -fno-reorder-functions -gstabs+ -msse2 -mm mx -mfpmath=sse  mozilla-xremote-client.o XRemoteClient_standalone.o       -L../ ../../dist/bin -L../../../dist/lib -L../../../dist/lib -lplds4 -lplc4 -lnspr4 -l pthread -ldl   -ldl -lm
XRemoteClient_standalone.o: In function `XRemoteClient::Init()':
XRemoteClient.cpp:(.text+0x9f): undefined reference to `XOpenDisplay'
XRemoteClient.cpp:(.text+0xd4): undefined reference to `XInternAtoms'
XRemoteClient_standalone.o: In function `XRemoteClient::Shutdown()':
XRemoteClient.cpp:(.text+0x15c): undefined reference to `XCloseDisplay'
XRemoteClient_standalone.o: In function `XRemoteClient::CheckChildren(unsigned l ong)':
XRemoteClient.cpp:(.text+0x1cf): undefined reference to `XQueryTree'
XRemoteClient.cpp:(.text+0x252): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x265): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0x288): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::CheckWindow(unsigned lon g)':
XRemoteClient.cpp:(.text+0x342): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x354): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::GetLock(unsigned long, i nt*)':
XRemoteClient.cpp:(.text+0x46d): undefined reference to `XGrabServer'
XRemoteClient.cpp:(.text+0x4c3): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x4e6): undefined reference to `XUngrabServer'
XRemoteClient.cpp:(.text+0x4fa): undefined reference to `XSync'
XRemoteClient.cpp:(.text+0x588): undefined reference to `XNextEvent'
XRemoteClient.cpp:(.text+0x5dd): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0x646): undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::FreeLock(unsigned long)' :
XRemoteClient.cpp:(.text+0x70b): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x745): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::WaitForResponse(unsigned  long, char**, int*, unsigned long)':
XRemoteClient.cpp:(.text+0x785): undefined reference to `XNextEvent'
XRemoteClient.cpp:(.text+0x821): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x866): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommand(unsigned l ong, char const*, char**, int*)':
XRemoteClient.cpp:(.text+0x9cb): undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommandLine(unsign ed long, int, char**, char**, int*)':
XRemoteClient.cpp:(.text+0xbaf): undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::~XRemoteClient()':
XRemoteClient.cpp:(.text+0xc47): undefined reference to `XCloseDisplay'
XRemoteClient_standalone.o: In function `XRemoteClient::~XRemoteClient()':
XRemoteClient.cpp:(.text+0xca7): undefined reference to `XCloseDisplay'
XRemoteClient_standalone.o: In function `XRemoteClient::FindBestWindow(char cons t*, char const*, char const*, int)':
XRemoteClient.cpp:(.text+0xd2c): undefined reference to `XQueryTree'
XRemoteClient.cpp:(.text+0xde1): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0xdf7): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0xe51): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0xe76): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0xf85): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0xfab): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0x1010): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x1032): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0x104f): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0x1065): undefined reference to `XFree'
XRemoteClient.cpp:(.text+0x10cc): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x10f6): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommand(char const*,  char const*, char const*, char const*, char**, int*)':
XRemoteClient.cpp:(.text+0x118d): undefined reference to `XSelectInput'
XRemoteClient.cpp:(.text+0x11f6): undefined reference to `XChangeProperty'
XRemoteClient.cpp:(.text+0x128d): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x12c8): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommandLine(char con st*, char const*, char const*, int, char**, char**, int*)':
XRemoteClient.cpp:(.text+0x135d): undefined reference to `XSelectInput'
XRemoteClient.cpp:(.text+0x140b): undefined reference to `XGetWindowProperty'
XRemoteClient.cpp:(.text+0x1446): undefined reference to `XFree'
collect2: ld returned 1 exit status
make[3]: *** [mozilla-xremote-client] Error 1
make[3]: Leaving directory `/home/jenfoong/mozilla/firefox/widget/src/xremotecli ent'
make[2]: *** [tier_50] Error 2
make[2]: Leaving directory `/home/jenfoong/mozilla/firefox'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/jenfoong/mozilla/firefox'
make: *** [build] Error 2
jenfoong@u053691m:~/mozilla$
[/LEFT]

```[LEFT]

Does anyone know to get throught this? I tried many ways but still stucked at here. Any help will be appreciated.
[/LEFT]

---

### Post by harism on 2005-11-24
[QUOTE=Single]I keep getting some errors while compiling firefox 1.5rc3. I don't know how to solve it. Stucked at XRemoteClient.cpp[/QUOTE]
I had similar problem, got rid of link error by running 'make -f client.mk build' instead of configure + make. Not sure if that was the problem, but worth trying  :)

---

### Post by Single on 2005-11-24
I didn't know i can use configure+make. Only used 'make -f client.mk build', and that's where i'm stucked. Thanks for helping.

---

### Post by Single on 2005-11-25
Ok solved it. Thx to this thread in mozilazine.
[http://forums.mozillazine.org/viewtopic.php?t=339585]("http://forums.mozillazine.org/viewtopic.php?t=339585")

---

### Post by Single on 2005-11-25
Oh boy, it is blazingly fast! :KS

---

### Post by harism on 2005-11-25
[QUOTE=Single]Ok solved it. Thx to this thread in mozilazine.
[http://forums.mozillazine.org/viewtopic.php?t=339585]("http://forums.mozillazine.org/viewtopic.php?t=339585")[/QUOTE]
I resolved Xft problem with a little Makefile mod (mozilla/browser/app/Makefile);
```
line 89;
LIBS += $(XLDFLAGS) $(XLIBS)
-->
LIBS += $(XLDFLAGS) $(XLIBS) -lXft

```
And built static version. Suppose there is a typo somewhere since '-lXt' is used for linking, or is Xt a valid library?

Is there a way/option in mozconfig to build 'firefox' instead of 'deer park'?

---

### Post by jdong on 2005-11-25
Why not use ubp-build.py and build from Dapper sources? ;)

---

### Post by Single on 2005-11-25
> **harism]I resolved Xft problem with a little Makefile mod (mozilla/browser/app/Makefile) said:**
>  I did something similiar. I added $(MOZ_XFT_LIBS) according to [https://bugzilla.mozilla.org/show_bug.cgi?id=316065]("https://bugzilla.mozilla.org/show_bug.cgi?id=316065")
To build firefox, add "mk_add_options MOZ_CO_PROJECT=browser" and[FONT=monospace] "[/FONT]ac_add_options --enable-application=browser" to the mozconfig.
I referenced some third party builds to set my mozconfig.:smile:

[quote]Why not use ubp-build.py and build from Dapper sources? :wink: How do I get the "ubp-build.py"? Do I need to edit repository list? Or download a dapper iso? Isn't the ubuntu firefox heavily patched, making it some what slower?

---

### Post by jdong on 2005-11-26
Firefox 1.5 has been seriously de-patched, and its performance is great!

Add **deb-src** lines for Dapper, apt-get update. Download ubp-build.py, then run **python ubp-build.py firefox**.

When an editor pops up with the Debian changelog, find the version number in parentheses, add **~breezy0.1** to the end. Then, CTRL+X y to exit. The build will continue. Afterwards, look in ~/ubp-compile-temp/ for the debs, install the appropriate ones.

---

### Post by digitalgnome on 2005-12-02
[QUOTE=jdong]
Add **deb-src** lines for Dapper, apt-get update. Download ubp-build.py, then run **python ubp-build.py firefox**.
[/QUOTE]

Sorry if this is a complete newb question, but I'm still new to apt in general.  Could you elaborate the above step a bit more?  I know where my sources.list is but I'm unsure what I would need to add for dapper without breaking something.  If there is a post/wiki page (I searched but didn't find anything) that explains what you are suggesting above in more detail please point me there.  Thanks for any help!

---

### Post by jdong on 2005-12-03
Actually, [http://sourceforge.net/project/showfiles.php?group_id=125877](http://sourceforge.net/project/showfiles.php?group_id=125877) I've made experimental debs for Firefox 1.5, though they do break a number of packages depending on Firefox... Use at own risk.

---

### Post by kushboy on 2005-12-18
I was trying to build Mozilla's calendar on my new Ubuntu 5.10 and this happened:
```

make[4]: Entering directory `/mozilla/mozilla/widget/src/xremoteclient'
XRemoteClient.cpp
c++ -o XRemoteClient.o -c -I../../../dist/include/system_wrappers -include /mozilla/config/gcc_hidden.h -DOSTYPE=\"Linux2.6\" -DOSARCH=\"Linux\" -DBUILD_ID=0000000000  -I../../../dist/include/xpcom -I../../../dist/include/xremoteclient -I../../../dist/include -I../../../dist/include/nspr    -I../../../dist/sdk/include    -fPIC   -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -O   -DMOZILLA_CLIENT -include ../../../mozilla-config.h -Wp,-MD,.deps/XRemoteClient.pp /mozilla/widget/src/xremoteclient/XRemoteClient.cpp
rm -f libxremote_client_s.a
ar cr libxremote_client_s.a XRemoteClient.o
ranlib libxremote_client_s.a
mozilla-xremote-client.cpp
c++ -o mozilla-xremote-client.o -c -I../../../dist/include/system_wrappers -include /mozilla/config/gcc_hidden.h -DOSTYPE=\"Linux2.6\" -DOSARCH=\"Linux\" -DBUILD_ID=0000000000  -I../../../dist/include/xpcom -I../../../dist/include/xremoteclient -I../../../dist/include -I../../../dist/include/nspr    -I../../../dist/sdk/include    -fPIC   -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -O   -DMOZILLA_CLIENT -include ../../../mozilla-config.h -Wp,-MD,.deps/mozilla-xremote-client.pp /mozilla/widget/src/xremoteclient/mozilla-xremote-client.cpp
c++ -o mozilla-xremote-client  -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -O  mozilla-xremote-client.o XRemoteClient_standalone.o    -lpthread    -L../../../dist/bin -L../../../dist/lib -L../../../dist/lib -lplds4 -lplc4 -lnspr4 -lpthread -ldl   -ldl -lm
XRemoteClient_standalone.o: In function `XRemoteClient::Init()':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:124: undefined reference to `XOpenDisplay'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:129: undefined reference to `XInternAtoms'
XRemoteClient_standalone.o: In function `XRemoteClient::Shutdown()':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:156: undefined reference to `XCloseDisplay'
XRemoteClient_standalone.o: In function `XRemoteClient::CheckChildren(unsigned long)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:292: undefined reference to `XQueryTree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:301: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:303: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:314: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::CheckWindow(unsigned long)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:263: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:266: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::GetLock(unsigned long, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:356: undefined reference to `XGrabServer'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:364: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:370: undefined reference to `XChangeProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:374: undefined reference to `XUngrabServer'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:375: undefined reference to `XSync'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:411: undefined reference to `XNextEvent'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:434: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::FreeLock(unsigned long)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:610: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:632: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::FindBestWindow(char const*, char const*, char const*, int)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:457: undefined reference to `XQueryTree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:485: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:491: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:510: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:516: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:521: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:545: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:551: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:555: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:567: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:573: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:577: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:590: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::WaitForResponse(unsigned long, char**, int*, unsigned long)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:740: undefined reference to `XNextEvent'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:766: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:828: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommandLine(unsigned long, int, char**, char**, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:723: undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommandLine(char const*, char const*, char const*, int, char**, char**, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:228: undefined reference to `XSelectInput'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommand(unsigned long, char const*, char**, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:648: undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommand(char const*, char const*, char const*, char const*, char**, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:184: undefined reference to `XSelectInput'
collect2: ld returned 1 exit status
make[4]: *** [mozilla-xremote-client] Error 1
make[4]: Leaving directory `/mozilla/mozilla/widget/src/xremoteclient'
make[3]: *** [libs_tier_50] Error 2
make[3]: Leaving directory `/mozilla/mozilla'
make[2]: *** [tier_50] Error 2
make[2]: Leaving directory `/mozilla/mozilla'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/mozilla/mozilla'
make: *** [build] Error 2

```

I found this thread and thought it seemed pretty similar to my error, and I tried to fix it accordingly. I still get the error, however. I'm not sure what I'm doing wrong, but if anyone has some helpful feedback, that'd be great!

Here's my mozconfig:

```
. $topsrcdir/calendar/sunbird/config/mozconfig

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/mozilla
mk_add_options MOZ_CO_PROJECT=calendar

ac_add_options --enable-application=calendar
 
ac_add_options --enable-plaintext-editor-only
ac_add_options --enable-necko-protocols=about,http,ftp,file,res
ac_add_options --enable-storage
ac_add_options --disable-accessibility
ac_add_options --disable-activex
ac_add_options --disable-activex-scripting
ac_add_options --disable-installer
ac_add_options --disable-jsd
ac_add_options --disable-mathml
ac_add_options --disable-necko-disk-cache
ac_add_options --disable-oji
ac_add_options --disable-view-source
ac_add_options --disable-logging
ac_add_options --disable-plugins
ac_add_options --disable-cookies

```
Thanks a lot!

---

### Post by sugarland2k on 2005-12-26
Checkout "FirefoxNewVersion - Ubuntu Wiki" 
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

use as needed.  
Peace and a good 2006 to all !
sugarland2k

---

