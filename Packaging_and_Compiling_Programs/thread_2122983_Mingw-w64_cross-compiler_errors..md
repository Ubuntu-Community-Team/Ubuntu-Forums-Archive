---
title: "Mingw-w64 cross-compiler errors."
date: 2013-03-06
forum: Packaging and Compiling Programs
---

### Post by SuperSeijin on 2013-03-06
Hi,

I am experiencing a problem with the Mingw-w64 cross compiler while attempting to cross compile to a Win64 host.  My system is Ubuntu Precise AMD64 with Mingw-w64 installed from the Ubuntu repositories.  During ./configure --host=x86_64-w64-mingw32, configure spits out the following info related to the python compilation environment:

```

checking for a Python interpreter with version =2.7... done
checking for python2.7... /usr/bin/python2.7
checking for python2.7 version... done
checking for python2.7 platform... done
checking for python2.7 script directory... done
checking for python2.7 extension module directory... done
checking for  include directory... /usr/include/python2.7
checking for python2.7 C libraries directory... /usr/lib/python2.7/config
checking for python2.7 link flags... -L/usr/lib/python2.7/config -lpython2.7
checking python includes in /usr/include/python2.7
checking Python.h usability... no
checking Python.h presence... no
checking for Python.h... no
checking for Python libraries... yes
configure: WARNING: No python compilation environment for =2.7

```

and the relative lines from the config.log are:

```
configure:19760: checking for a Python interpreter with version =2.7
configure:19799: python2.7 -c import sys, string if '=2.7' == '': sys.exit(0) spec = string.replace('=2.7', ' ', '') if spec[:2] == '<=': version_string = spec[2:] elif spec[:2] == '>=': version_string = spec[2:] elif spec[:1] == '=': version_string = spec[1:] elif spec[:1] == '>': version_string = spec[1:] elif spec[:1] == '<': version_string = spec[1:] ver = map(int, string.split(version_string, '.')) syshexversion = sys.hexversion >> (8 ABOUT-NLS AGPLv3 AUTHORS COPYING ChangeLog GPLv3 HACKING HOWTO-install-from-sources INSTALL LICENSE Makefile Makefile.am Makefile.in NEWS NIHPHOBIA README aclocal.m4 autom4te.cache conf confdefs.h config config.log config.status configure configure.ac database debian examples libtool po poker-client-specs.odp poker-network.pc poker-network.pc.in pokerclient2d pokernetwork pokerprizes pokerstats pokerui pokerweb tests twisted upgrade upgrades (4 - len(ver))) verhex = 0 for i in xrange(0, len(ver)): verhex = (verhex << 8) + ver[i] print 'sys.hexversion = 0x%08x, verhex = 0x%08x' % (syshexversion, verhex) if spec[:2] == '<=': status = syshexversion <= verhex elif spec[:2] == '>=': status = syshexversion >= verhex elif spec[:1] == '=': status = syshexversion == verhex elif spec[:1] == '>': status = syshexversion > verhex elif spec[:1] == '<': status = syshexversion < verhex else: status = syshexversion >= verhex if status: sys.exit(0) else: sys.exit(1)
sys.hexversion = 0x00000207, verhex = 0x00000207
configure:19802: $? = 0
configure:19807: result: done
configure:19816: checking for python2.7
configure:19834: found /usr/bin/python2.7
configure:19846: result: /usr/bin/python2.7
configure:19864: checking for python2.7 version
configure:19867: result: done
configure:19879: checking for python2.7 platform
configure:19882: result: done
configure:19889: checking for python2.7 script directory
configure:19893: result: done
configure:19902: checking for python2.7 extension module directory
configure:19906: result: done
configure:19933: checking for  include directory
configure:19941: result: /usr/include/python2.7
configure:19946: checking for python2.7 C libraries directory
configure:19954: result: /usr/lib/python2.7/config
configure:19959: checking for python2.7 link flags
configure:19969: result: -L/usr/lib/python2.7/config -lpython2.7
configure:19983: checking Python.h usability
configure:19983: x86_64-w64-mingw32-gcc -c -pipe -O3 -Wall -W  -I/usr/include/python2.7 conftest.c >&5
In file included from /usr/include/python2.7/Python.h:58:0,
                 from conftest.c:61:
/usr/include/python2.7/pyport.h:338:24: fatal error: sys/select.h: No such file or directory
compilation terminated.
configure:19983: $? = 1
```

It seems that this may be a PATH issue but my gut says its not as easy as that.  Can anyone give me some idea what the problem is and a possible solution?

---

### Post by peng6662001 on 2013-03-12
mark

---

### Post by schragge on 2013-03-13
Try this
```
sudo apt-get install {libc6,python}-dev
```

---

