---
title: "Sunbird XRemoteClient building errors"
date: 2005-12-18
forum: Packaging and Compiling Programs
---

### Post by kushboy on 2005-12-18
I think the best way to describe the problem is just to show it all to you:

Error after make -f client.mk build
```

make[4]: Leaving directory `/mozilla/mozilla/toolkit/components'
make[4]: Entering directory `/mozilla/mozilla/widget/src/xremoteclient'
c++ -o mozilla-xremote-client  -fno-rtti -fno-exceptions -Wall -Wconversion -Wpo inter-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wn o-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DDEBU G -D_DEBUG -DDEBUG_root -DTRACING -g -fno-inline -O  mozilla-xremote-client.o XR emoteClient_standalone.o    -lpthread           -L../../../dist/bin -L../../../d ist/lib -L../../../dist/lib -lplds4 -lplc4 -lnspr4 -lpthread -ldl   -ldl -lm 
XRemoteClient_standalone.o: In function `XRemoteClient::Init()':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:124: undefined reference to `XOpenDisplay'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:129: undefined reference to `XInternAtoms'
XRemoteClient_standalone.o: In function `XRemoteClient::Shutdown()':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:156: undefined reference to `XCloseDisplay'
XRemoteClient_standalone.o: In function `XRemoteClient::CheckChildren(unsigned l ong)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:292: undefined reference to `XQueryTree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:301: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:303: undefined reference to `XFree'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:314: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::CheckWindow(unsigned lon g)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:263: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:266: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::GetLock(unsigned long, i nt*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:356: undefined reference to `XGrabServer'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:364: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:370: undefined reference to `XChangeProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:374: undefined reference to `XUngrabServer'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:375: undefined reference to `XSync'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:411: undefined reference to `XNextEvent'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:434: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::FreeLock(unsigned long)' :
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:610: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:632: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::FindBestWindow(char cons t*, char const*, char const*, int)':
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
XRemoteClient_standalone.o: In function `XRemoteClient::WaitForResponse(unsigned  long, char**, int*, unsigned long)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:740: undefined reference to `XNextEvent'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:766: undefined reference to `XGetWindowProperty'
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:828: undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommandLine(unsign ed long, int, char**, char**, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:723: undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommandLine(char con st*, char const*, char const*, int, char**, char**, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:228: undefined reference to `XSelectInput'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommand(unsigned l ong, char const*, char**, int*)':
/mozilla/widget/src/xremoteclient/XRemoteClient.cpp:648: undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommand(char const*,  char const*, char const*, char const*, char**, int*)':
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

My .mozconfig:
```

. $topsrcdir/calendar/sunbird/config/mozconfig

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/mozilla
mk_add_options MOZ_CO_PROJECT=calendar

ac_add_options --enable-application=calendar
 
ac_add_options --enable-debug 

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

I've just upgraded to a clean Breezy 5.10.

There are a few threads I've found on google describing a similar problem with the firefox build, but none of the errors matches mine entirely. I've tried patching to the way those problems were fixed, but it hasn't helped. 

Any help is appreciated! Thanks!

---

