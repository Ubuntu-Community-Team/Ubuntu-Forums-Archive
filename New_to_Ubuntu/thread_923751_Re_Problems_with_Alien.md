---
title: "Re: Problems with Alien"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by org.ale on 2008-09-18
hey... I'm a linux freshman, I installed alien and I wanna to convert a rpm into a deb

alien -k cnijfilter-ip1800series-2.70-1.i386.rpm

but I've got some errors
____________________________________________________________________________________

Warning: Skipping conversion of scripts in package cnijfilter-ip1800series: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/cnijfilter-ip1800series
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libgmodule-1.2.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libXi.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libXext.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libX11.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libm.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libxml.so.1 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libcnbpcmcm312.so needed by debian/cnijfilter-ip1800series/usr/local/bin/cifip1800 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libcnbpess312.so needed by debian/cnijfilter-ip1800series/usr/local/bin/cifip1800 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: failure: couldn't find library libpng.so.3 needed by debian/cnijfilter-ip1800series/usr/local/bin/cifip1800 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: control directory has bad permissions 777 (must be >=0755 and <=0775)
dpkg-deb: building package `cnijfilter-ip1800series' in `../cnijfilter-ip1800series_2.70-1_i386.deb'.
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
find: cnijfilter-ip1800series-2.70: No such file or directory

____________________________________________________________________________________

like I said, I'm a newbie in linux and forums...  could you please help me, those are my printer drivers and I really need them...

thanks

---

### Post by Sef on 2008-09-18
Moved to Absolute Beginners.

---

