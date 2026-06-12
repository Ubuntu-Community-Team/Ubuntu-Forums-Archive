---
title: "Errors making Synergy"
date: 2009-08-18
forum: Packaging and Compiling Programs
---

### Post by traffas on 2009-08-18
I've been using Ubuntu for a long time, but haven't yet grasped the concept of making packages. I found a patch for Synergy that claims to get it to not crash when using Flash and Opera. I was successful in patching the correct source file, but when I try to configure and make, I get errors. Here's exactly what I've done:

```
./configure -x-libraries /usr/lib -x-includes /usr/includes
```

...returns with no noticeable errors.

```
sudo make install
```

Here is the output:

```
Making install in lib
make[1]: Entering directory `/home/aaron/temp/synergy-1.3.1/lib'
Making install in common
make[2]: Entering directory `/home/aaron/temp/synergy-1.3.1/lib/common'
make[3]: Entering directory `/home/aaron/temp/synergy-1.3.1/lib/common'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/aaron/temp/synergy-1.3.1/lib/common'
make[2]: Leaving directory `/home/aaron/temp/synergy-1.3.1/lib/common'
Making install in arch
make[2]: Entering directory `/home/aaron/temp/synergy-1.3.1/lib/arch'
source='CArchDaemonUnix.cpp' object='CArchDaemonUnix.o' libtool=no \
	depfile='.deps/CArchDaemonUnix.Po' tmpdepfile='.deps/CArchDaemonUnix.TPo' \
	FOO=5 depmode=gcc3 /bin/bash ../../config/depcomp \
	g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../lib/common     -g -O2 -g -Wall -Wno-unknown-pragmas -Werror   -DSYSAPI_UNIX=1 -DWINAPI_XWINDOWS=1 -pthread  -I/usr/includes -c -o CArchDaemonUnix.o `test -f 'CArchDaemonUnix.cpp' || echo './'`CArchDaemonUnix.cpp
CArchDaemonUnix.cpp: In member function &#8216;virtual int CArchDaemonUnix::daemonize(const char*, int (*)(int, const char**))&#8217;:
CArchDaemonUnix.cpp:53: error: &#8216;exit&#8217; was not declared in this scope
cc1plus: warnings being treated as errors
CArchDaemonUnix.cpp:60: error: ignoring return value of &#8216;int chdir(const char*)&#8217;, declared with attribute warn_unused_result
CArchDaemonUnix.cpp:74: error: ignoring return value of &#8216;int dup(int)&#8217;, declared with attribute warn_unused_result
make[2]: *** [CArchDaemonUnix.o] Error 1
make[2]: Leaving directory `/home/aaron/temp/synergy-1.3.1/lib/arch'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/aaron/temp/synergy-1.3.1/lib'
make: *** [install-recursive] Error 1


```

Environment is Jaunty 64. Are the configure options to blame?

---

### Post by stroyan on 2009-08-18
The error is probably caused by a missing build dependency.
It is best to use apt-get and debuild to build a package.
Add this line to /etc/apt/sources.list, (if it is not already present.)
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
Then use
```

sudo apt-get install ubuntu-dev-tools
sudo apt-get build-dep synergy
mkdir synergy_source
cd synergy_source
apt-get source synergy
cd synergy-1.3.1
debuild -us -uc
# Apply the patch manually.  The patch doesn't exactly match the jaunty source line numbers.
# Edit debian/changelog and add lines like this at top-
synergy (1.3.1-5ubuntu3) jaunty; urgency=low
  * Recover after mouse warp loses events. (LP: #332628)
 -- Mike Stroyan <mike@stroyan.net>  Tue, 18 Aug 2009 12:01:30 -0600
# Note that the version number is incremented.
# That allows this to replace repository version without pinning.
debuild -us -uc
sudo dpkg -i ../synergy_1.3.1-5ubuntu3_amd64.deb

```

---

