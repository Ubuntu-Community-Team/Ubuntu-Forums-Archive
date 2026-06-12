---
title: "Compiling Firfox from source"
date: 2007-01-27
forum: Packaging and Compiling Programs
---

### Post by tawlboy on 2007-01-27
Hi,

I am have downloaded the Firefox source code (ver. 1.5.0.9 from mozilla.org). I am having some problems compiling it though (I am using Dapper). I am using 'make -f client.mk build'm but compilation gets stuck here:

```
:XRemoteClient.cpp:(.text+0xa29): undefined reference to `XGetWindowProperty'
:XRemoteClient.cpp:(.text+0xa4b): undefined reference to `XFree'
:XRemoteClient.cpp:(.text+0xa59): undefined reference to `XFree'
:XRemoteClient.cpp:(.text+0xac2): undefined reference to `XGetWindowProperty'
:XRemoteClient.cpp:(.text+0xae4): undefined reference to `XFree'
:XRemoteClient.cpp:(.text+0xaee): undefined reference to `XFree'
:XRemoteClient.cpp:(.text+0xb26): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::WaitForResponse(unsigned long, char**, int*, unsigned long)':XRemoteClient.cpp:(.text+0xb8b): undefined reference to `XNextEvent'
:XRemoteClient.cpp:(.text+0xc42): undefined reference to `XGetWindowProperty'
:XRemoteClient.cpp:(.text+0xd56): undefined reference to `XFree'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommandLine(unsigned long, int, char**, char**, int*)':XRemoteClient.cpp:(.text+0xe94): undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommandLine(char const*, char const*, char const*, int, char**, char**, int*)':XRemoteClient.cpp:(.text+0xf3d): undefined reference to `XSelectInput'
XRemoteClient_standalone.o: In function `XRemoteClient::DoSendCommand(unsigned long, char const*, char**, int*)':XRemoteClient.cpp:(.text+0x100f): undefined reference to `XChangeProperty'
XRemoteClient_standalone.o: In function `XRemoteClient::SendCommand(char const*, char const*, char const*, char const*, char**, int*)':XRemoteClient.cpp:(.text+0x10a7): undefined reference to `XSelectInput'
collect2: ld returned 1 exit status
make[3]: *** [mozilla-xremote-client] Error 1
make[3]: Leaving directory `/home/dicer/mozilla/ff-opt-static/widget/src/xremoteclient'
make[2]: *** [tier_50] Error 2
make[2]: Leaving directory `/home/dicer/mozilla/ff-opt-static'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dicer/mozilla/ff-opt-static'
make: *** [build] Error 2
```

As far as I am aware, I have all dependencies installed (using apt-get build-dep mozilla-firefox), so I cannont see why this is happening. Here is my .mozconfig file:

. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/ff-opt-static
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --enable-static
ac_add_options --disable-shared
ac_add_options --disable-tests
mk_add_options MOZ_CO_PROJECT=browser

I actually found the same problem here: [http://ubuntuforums.org/showthread.php?t=94636](http://ubuntuforums.org/showthread.php?t=94636) and I have added '$(MOZ_XFT_LIBS)' to mozilla/browser/app/Makefile.in as detailed here: [https://bugzilla.mozilla.org/show_bug.cgi?id=316065](https://bugzilla.mozilla.org/show_bug.cgi?id=316065) but I still cannot get past this problem.

I would appreciate any help with this please.

---

### Post by DJ_Peng on 2007-01-27
Is there a reason you're building it rather than simply getting their Linux download? I got it and had no need to compile it, I just run the /firefox/firefox script that is provided and I'm off to the races.

---

### Post by tawlboy on 2007-01-27
No, I have no particular reason. I actually already have Firefox installed, but I am interested in compiling programs from source just out of interest in learning more.

---

### Post by tqft on 2007-02-16
Ask that question here (if you haven't already)
Mozillazine 3rd party build forums
[http://forums.mozillazine.org/viewforum.php?f=42](http://forums.mozillazine.org/viewforum.php?f=42)
Have your .mozconfig ready


It appears you are trying to do a static build - do you have a lot of memory (>500Mb?)  if not that could be part of the problem.


I assume you have reviewed the doco 
[http://developer.mozilla.org/en/docs/Build_Documentation](http://developer.mozilla.org/en/docs/Build_Documentation)
and
[http://developer.mozilla.org/en/docs/Mozilla_Source_Code_Via_CVS](http://developer.mozilla.org/en/docs/Mozilla_Source_Code_Via_CVS)

As I build ff3 almost everyday (from CVS) I know it can and does work.
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9a3pre) Gecko/20070216 Minefield/3.0a3pre ID:0000000000 [cairo]

---

