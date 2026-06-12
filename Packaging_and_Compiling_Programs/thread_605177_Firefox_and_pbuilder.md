---
title: "Firefox and pbuilder"
date: 2007-11-06
forum: Packaging and Compiling Programs
---

### Post by Kow on 2007-11-06
Has anyone tried building firefox debs in a 386 pbuilder environment from a native amd64 ubuntu install?

```

rm -f libxptcall.a
ar cr libxptcall.a xptcall.o  
ranlib libxptcall.a
/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/config/nsinstall -R -m 644 libxptcall.a ../../../../dist/lib
make[7]: Entering directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom/reflect/xptcall/src/md'
make[8]: Entering directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom/reflect/xptcall/src/md/unix'
xptcinvoke_x86_64_linux.cpp
g++-4.2 -o xptcinvoke_x86_64_linux.o -c -fvisibility=hidden -DMOZILLA_INTERNAL_API -DOSTYPE=\"Linux2.6\" -DOSARCH=\"Linux\" -DBUILD_ID=2007110700 -DEXPORT_XPTC_API   -I../../../../../../dist/include/xpcom -I../../../../../../dist/include -I/usr/include/nspr -I/usr/include  -I/usr/include -I./../..    -fPIC   -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -g -Wall -O2 -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -pipe -w -O2 -fno-strict-aliasing -g   -DMOZILLA_CLIENT -include ../../../../../../mozilla-config.h -Wp,-MD,.deps/xptcinvoke_x86_64_linux.pp xptcinvoke_x86_64_linux.cpp
xptcinvoke_x86_64_linux.cpp: In function 'nsresult XPTC_InvokeByIndex(nsISupports*, PRUint32, PRUint32, nsXPTCVariant*)':
xptcinvoke_x86_64_linux.cpp:82: note: 'value' was declared here
xptcinvoke_x86_64_linux.cpp:153: error: invalid register name for 'd0'
xptcinvoke_x86_64_linux.cpp:154: error: invalid register name for 'd1'
xptcinvoke_x86_64_linux.cpp:155: error: invalid register name for 'd2'
xptcinvoke_x86_64_linux.cpp:156: error: invalid register name for 'd3'
xptcinvoke_x86_64_linux.cpp:157: error: invalid register name for 'd4'
xptcinvoke_x86_64_linux.cpp:158: error: invalid register name for 'd5'
xptcinvoke_x86_64_linux.cpp:159: error: invalid register name for 'd6'
xptcinvoke_x86_64_linux.cpp:160: error: invalid register name for 'd7'
xptcinvoke_x86_64_linux.cpp:182: error: invalid register name for 'a4'
xptcinvoke_x86_64_linux.cpp:183: error: invalid register name for 'a5'
make[8]: *** [xptcinvoke_x86_64_linux.o] Error 1
make[8]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom/reflect/xptcall/src/md/unix'
make[7]: *** [libs] Error 2
make[7]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom/reflect/xptcall/src/md'
make[6]: *** [libs] Error 2
make[6]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom/reflect/xptcall/src'
make[5]: *** [libs] Error 2
make[5]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom/reflect/xptcall'
make[4]: *** [libs] Error 2
make[4]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom/reflect'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla/xpcom'
make[2]: *** [tier_2] Error 2
make[2]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/tmp/buildd/firefox-2.0.0.9+2nobinonly/build-tree/mozilla'
make: *** [debian/stamp-makefile-build] Error 2
pbuilder: Failed autobuilding of package
 -> Aborting with an error
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//12773 and its subdirectories

```

Looks like somewhere along the line the pbuilder environment is failing at entirely faking the 386 environment and the firefox source seems to come to the conclusion that it is an x86_64 environment.

EDIT: [http://forums.mozillazine.org/viewtopic.php?t=587188](http://forums.mozillazine.org/viewtopic.php?t=587188) seems to confirm my problem. I can apply the fix suggested in that forum post but its dirty and shouldn't need to be done.

EDIT: Confirmed firefox source determines arch type via uname. Looking at debian lists this is a known issue and I'm surprised it has not been fixed yet. The REAL fix would be on mozilla's end. Code that differs by architecture implies bad code to begin with.

---

### Post by Kow on 2007-11-06
So I guess my question is how are the ubuntu developers getting around this problem? I guess using the linux32 binary would be one way but according to the developer documentation even if it were to work and I created debs they could not be used by ubuntu because the debs were not created via an ubuntu-supported method. Or is it? I would be using pbuilder but inside linux32...

---

### Post by LaserJock on 2007-11-07
> **Kow said:**
> So I guess my question is how are the ubuntu developers getting around this problem? I guess using the linux32 binary would be one way but according to the developer documentation even if it were to work and I created debs they could not be used by ubuntu because the debs were not created via an ubuntu-supported method. Or is it? I would be using pbuilder but inside linux32...

What problem do developers have to get around? Firefox is built for amd64 on an amd64 machine and for i386 on an i386 machine, etc.

-LaserJock

---

