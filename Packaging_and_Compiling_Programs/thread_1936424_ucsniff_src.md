---
title: "ucsniff src"
date: 2012-03-06
forum: Packaging and Compiling Programs
---

### Post by Xenque on 2012-03-06
Hello everyone.

I downloaded src of this software, configure them, but i have an error:
```

checking for correct ltmain.sh version... grep: character class syntax is [[:space:]], not [:space:]
no

*** Gentoo sanity check failed! ***
*** libtool.m4 and ltmain.sh have a version mismatch! ***
*** (libtool.m4 = 1.5.18, ltmain.sh = ) ***

Please run:

  libtoolize --copy --force

if appropriate, please contact the maintainer of this
package (or your distribution) for help.

```


I run libtoolize but he didn't help me. Try to do this: autoreconf --force --install --symlink, helped. Running of "make", caused error:
```

Making all in man
make[1]: Entering directory `/home/josh/Downloads/ucsniff-3.10/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/josh/Downloads/ucsniff-3.10/man'
Making all in share
make[1]: Entering directory `/home/josh/Downloads/ucsniff-3.10/share'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/josh/Downloads/ucsniff-3.10/share'
Making all in include
make[1]: Entering directory `/home/josh/Downloads/ucsniff-3.10/include'
make  all-am
make[2]: Entering directory `/home/josh/Downloads/ucsniff-3.10/include'
make[2]: Leaving directory `/home/josh/Downloads/ucsniff-3.10/include'
make[1]: Leaving directory `/home/josh/Downloads/ucsniff-3.10/include'
Making all in include
make[1]: Entering directory `/home/josh/Downloads/ucsniff-3.10/include'
make  all-am
make[2]: Entering directory `/home/josh/Downloads/ucsniff-3.10/include'
make[2]: Leaving directory `/home/josh/Downloads/ucsniff-3.10/include'
make[1]: Leaving directory `/home/josh/Downloads/ucsniff-3.10/include'
Making all in src
make[1]: Entering directory `/home/josh/Downloads/ucsniff-3.10/src'
Makefile:3940: *** missing separator.  Stop.
make[1]: Leaving directory `/home/josh/Downloads/ucsniff-3.10/src'
make: *** [all-recursive] Error 1

```

Error string 3940:
```

.cpp.o:
_**@am__fastdepCXX_TRUE@   if $(CXXCOMPILE) -MT $@ -MD -MP -MF "$(DEPDIR)/$*.Tpo" -c -o $@ $<; \**_
@am__fastdepCXX_TRUE@   then mv -f "$(DEPDIR)/$*.Tpo" "$(DEPDIR)/$*.Po"; else rm -f "$(DEPDIR)/$*.Tpo"; exit 1; fi
@am__fastdepCXX_FALSE@  source='$<' object='$@' libtool=no \
@am__fastdepCXX_FALSE@  depfile='$(DEPDIR)/$*.Po' tmpdepfile='$(DEPDIR)/$*.TPo' \
@am__fastdepCXX_FALSE@  $(CXXDEPMODE) $(depcomp) \
@am__fastdepCXX_FALSE@  $(CXXCOMPILE) -c -o $@ $<

```

Any idea?
Sorry for my english :D Thx.

---

### Post by Xenque on 2012-03-06
Up! 
Anybody help me

---

### Post by oldos2er on 2012-03-07
Moved to Packaging and Compiling Programs.

---

### Post by SevenMachines on 2012-03-07
Try adding AC_PROG_CXX to configure.in, then running autoconf, should or might get rid of that problem. not a good sign though, i suspect there'll be more issues

---

### Post by Xenque on 2012-03-11
Hello!
Thank you for your reply!
After adding AC_PROG_CXX and running "autoconf", "make" being implemented.
Then it still left with these errors:
```

vc_plugins.c: In function 'plugin_filter':
vc_plugins.c:134.49: error: expected ')' before 'LTDL_SHLIB_EXT'
make[2]: *** [ucsniff-vc_plugins.o] Error 1
make[2]: Leaving directory '/home/xen/Dowloads/ucsniff-3.10/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/xen/Dowloads/ucsniff-3.10/src'
make: *** [all-recursive] Error 1

```

---

### Post by SevenMachines on 2012-03-13
Seems like LTDL_SHLIB_EXT is probably not being defined. This may be because autotools has been updated and so the program needs to be updated too. Or its being undefined for some reasonable reason, whatever that might be!. Looking in detail at the autotools setup and updating manually would probably be the 'proper' fix, and maybe long and boring too :)

As a temporary hack to see if that indeed is the problem you could try adding AC_LTDL_SHLIBEXT to configure.in and see if that helps. If its still not helping you could manually add it to vc_plugin.c:134. (or maybe add it as a CFLAGS). It should be defined as something like ".so", its the lib extension for ltdl, and if you have libltdl-dev installed then you'll have libltdl.so somewhere.
```

$ dpkg -L libltdl-dev |grep .so
/usr/lib/x86_64-linux-gnu/libltdl.so
```Anyway, you could try it to test the problem perhaps

src/vc_plugins.c:134
```
   if ( match_pattern(d->d_name, PLUGIN_PATTERN ".so") )
```

---

