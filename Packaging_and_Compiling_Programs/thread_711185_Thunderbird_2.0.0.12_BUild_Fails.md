---
title: "Thunderbird 2.0.0.12 BUild Fails"
date: 2008-02-29
forum: Packaging and Compiling Programs
---

### Post by WoofGrrrr on 2008-02-29
Thunderbird 2.0.0.12 build fails in the final stages, creating thunderbird-bin.
Could someone please help me figure this out?

A couple of days ago, I got 2.0.0.9 to build without problem.  But they just released 2.0.0.12.


platform: Ubuntu 7.10 "Gutsy" on amd63, KDE

I Downloaded source for Thunderbird 2.0.0.12 and Firefox 2.0.0.12 today.
I Un-tar'ed them in the same directory.  The directory is *different* from the
one I used for thunderbird 2.0.0.9, just in case inter-mingling source for two
releases makes a difference.  (It shouldn't, but who knows?)



Here is my .mozconfig:
----------------------------------------------------------------------
```
MOZ_CO_PROJECT="mail"

. $topsrcdir/mail/config/mozconfig

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/tbird

mk_add_options MOZ_MAKE_FLAGS="-j2"
ac_add_options --enable-application="mail"
ac_add_options --disable-debug
ac_add_options --enable-optimize="-O2 -march=athlon64"
ac_add_options --disable-tests
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-system-cairo
ac_add_options --enable-xft
ac_add_options --disable-freetype2
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --enable-static
ac_add_options --disable-shared
ac_add_options --enable-update-packaging

```
----------------------------------------------------------------------
Most of this I got from the net...



When I try to build, I get the following:

```
> > make -f client.mk build
    .
    .
    .
    .
c++ -o thunderbird-bin  -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual
-Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG
-DTRIMMED -O2 -march=athlon64  nsMailApp.o nsStaticComponents.o      -L../../dist/bin -L../../dist/lib
-L../../dist/lib/components ../../dist/lib/libxulapp_s.a -L../../dist/bin -lmozjs  -L../../dist/bin -lxpcom -lxpcom_core
  -L../../dist/lib -lplds4 -lplc4 -lnspr4 -lpthread -ldl -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm
-lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0
-lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0     -lX11  -lgthread-2.0 -ldl -lm
../../dist/lib/components/libxpcom_compat_c.a ../../dist/lib/components/libxpconnect.a
../../dist/lib/components/libuconv.a ../../dist/lib/components/libi18n.a ../../dist/lib/components/libmork.a
../../dist/lib/components/libstoragecomps.a ../../dist/lib/components/libnecko.a ../../dist/lib/components/libnecko2.a
../../dist/lib/components/libpref.a ../../dist/lib/components/libcaps.a ../../dist/lib/components/librdf.a
../../dist/lib/components/libhtmlpars.a ../../dist/lib/components/libgfxps.a ../../dist/lib/components/libgfx_gtk.a
../../dist/lib/components/libimglib2.a ../../dist/lib/components/libwidget_gtk2.a
../../dist/lib/components/libgklayout.a ../../dist/lib/components/libdocshell.a
../../dist/lib/components/libembedcomponents.a ../../dist/lib/components/libwebbrwsr.a
../../dist/lib/components/libeditor.a ../../dist/lib/components/libtxmgr.a ../../dist/lib/components/libcomposer.a
../../dist/lib/components/libnsappshell.a ../../dist/lib/components/libaccessibility.a
../../dist/lib/components/libchrome.a ../../dist/lib/components/libmozfind.a ../../dist/lib/components/libfileview.a
../../dist/lib/components/libappcomps.a ../../dist/lib/components/libremoteservice.a
../../dist/lib/components/libcommandlines.a ../../dist/lib/components/libtoolkitcomps.a
../../dist/lib/components/libpipboot.a ../../dist/lib/components/libpipnss.a ../../dist/lib/components/libpippki.a
../../dist/lib/components/libmozldap.a ../../dist/lib/components/libimport.a ../../dist/lib/components/libmsgsmime.a
../../dist/lib/components/libmail.a ../../dist/lib/components/libwallet.a ../../dist/lib/components/libwalletviewers.a
../../dist/lib/components/libxmlextras.a ../../dist/lib/components/libtransformiix.a
../../dist/lib/components/libautoconfig.a ../../dist/lib/components/libsystem-pref.a
../../dist/lib/components/libwebsrvcs.a ../../dist/lib/components/libuniversalchardet.a
../../dist/lib/components/libauth.a ../../dist/lib/components/libmailcomps.a ../../dist/lib/libunicharutil_s.a
../../dist/lib/libucvutil_s.a ../../dist/lib/libgtkxtbin.a ../../dist/lib/libgfxshared_s.a ../../dist/lib/libgfxpsshar.a
../../dist/lib/libgkgfx.a ../../dist/lib/libxulapp_s.a ../../dist/lib/libmimecthglue_s.a  -L../../dist/lib -lmozpng
-L../../dist/lib -lmozjpeg -L../../dist/lib -lmozz  -L-L../../dist/bin -L../../dist/lib -lcrmf -lsmime3 -lssl3 -lnss3
-lsoftokn3  -L../../dist/bin -L../../dist/lib -lldap50 -llber50 -lprldap50   -lcairo    -lXt -lXft -lfontconfig
-L../../dist/lib -lxpcom_compat
../../dist/lib/components/libxpcom_compat_c.a(nsXPCOMObsolete.o):(.rodata+0x60): undefined reference to
`nsFileSpecImpl::Create(nsISupports*, nsID const&, void**)'
../../dist/lib/components/libxpcom_compat_c.a(nsXPCOMObsolete.o):(.rodata+0xc0): undefined reference to
`nsDirectoryIteratorImpl::Create(nsISupports*, nsID const&, void**)'
/usr/bin/ld: thunderbird-bin: hidden symbol `nsFileSpecImpl::Create(nsISupports*, nsID const&, void**)' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make[4]: *** [thunderbird-bin] Error 1
make[4]: Leaving directory `/home/markb/projects/mozilla/tbird/mail/app'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/markb/projects/mozilla/tbird/mail'
make[2]: *** [tier_99] Error 2
make[2]: Leaving directory `/home/markb/projects/mozilla/tbird'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/markb/projects/mozilla/tbird'
make: *** [build] Error 2

```

---

### Post by WoofGrrrr on 2008-02-29
I found the solution at:

[https://bugzilla.mozilla.org/show_bug.cgi?id=416463](https://bugzilla.mozilla.org/show_bug.cgi?id=416463)

---

