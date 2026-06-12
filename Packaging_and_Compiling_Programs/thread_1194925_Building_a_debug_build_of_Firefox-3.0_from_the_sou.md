---
title: "Building a debug build of Firefox-3.0 from the source package"
date: 2009-06-23
forum: Packaging and Compiling Programs
---

### Post by jdb2 on 2009-06-23
In an attempt to diagnose what exactly is causing "Couldn't load XRE functions." in [this](http://ubuntuforums.org/showthread.php?p=7502957#post7502957) post, I am attempting to build a debug version of the Ubuntu firefox-3.0_3.0.11+build2+nobinonly source package. Since the Ubuntu Mozilla Team elected to use a tarball within a tarball method to package their source, the first thing that I had to do after 'apt-get source firefox' was 'cd firefox-3.0-3.0.11+build2+nobinonly/; DEB_TAR_SRCDIR=mozilla make -f /usr/share/cdbs/1/rules/tarball.mk pre-build
'  after which the source tree was accessible for tweaking. I went ahead and edited the 'build-tree/mozilla/browser/config/mozconfig' file and added the following : 

```

ac_add_options --disable-optimize
ac_add_options --enable-debug 
ac_add_options --enable-tests

```

I also added a reference to the above in 'build-tree/mozilla' consisting of a 1 line .mozconfig file : 

```

. $topsrcdir/browser/config/mozconfig

```

After that I built the debs using 'DEB_BUILD_OPTIONS="--enable-debug --disable-optimize --disable-strip --disable-strip-libs" fakeroot debian/rules binary' .

When the build finished I installed the debs ( firefox-3.0 and firefox-3.0-branding ) and ran 'firefox --debug' only to get the "no debugging symbols found" output from GDB.

Running 'file /usr/lib/firefox-3.0.11/firefox' produces :

```

/usr/lib/firefox-3.0.11/firefox: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

So, my question is what exactly am I doing wrong that results in a stripped, optimized build instead of a debug build? I've successfully compiled a debug build from the official Mozilla project tarball but strangely it doesn't error out with "Couldn't load XRE functions." 

Any help would be appreciated,

Thanks

jdb2

---

### Post by jdb2 on 2009-06-25
Well I "solved" the problem, although not as I had intended. The fact that the debug build from the official Mozilla Project tarball ran without error is that I did not indicate to the build system that I wanted the build to be dynamically linked against my system libxul. Adding 'ac_add_options --disable-libxul' to .mozconfig fixed that problem. I can now see that there is a buffer overflow in or associated with libxul.

Still, it would be nice to know how to do a debug build of the Ubuntu source package.

jdb2

---

