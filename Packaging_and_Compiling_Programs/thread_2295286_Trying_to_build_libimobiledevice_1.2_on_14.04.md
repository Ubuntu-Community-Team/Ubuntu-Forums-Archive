---
title: "Trying to build libimobiledevice 1.2 on 14.04"
date: 2015-09-17
forum: Packaging and Compiling Programs
---

### Post by xan3 on 2015-09-17
Hello all!

I'm running a virtualmachine of Ubuntu 14.04 currently, and was trying to build the libimobiledevice 1.2 package so that I could inspect an iOS 8 device using Google's [ios-webkit-debug-proxy]("https://github.com/google/ios-webkit-debug-proxy/")

I followed along with the answer in this post on askubuntu.com:

[http://askubuntu.com/questions/598940/libimobiledevice-1-2-ios-8-support-for-ubuntu-14-04-trusty/](http://askubuntu.com/questions/598940/libimobiledevice-1-2-ios-8-support-for-ubuntu-14-04-trusty/)

and everything seemed to be working properly up until the step:

```
[COLOR=#111111][FONT=Consolas]debuild -b -j$(getconf _NPROCESSORS_ONLN)[/FONT][/COLOR]
```

then this is the code that shows up in my terminal at the end...

```

[COLOR=#111111][FONT=Consolas]#define LT_OBJDIR ".libs/"[/FONT][/COLOR]
configure: exit 1
dh_auto_configure: ./configure --build=i686-linux-gnu --prefix=/usr --includedir=${prefix}/include 
--mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var 
--libdir=${prefix}/lib/i386-linux-gnu --libexecdir=${prefix}/lib/i386-linux-gnu --disable-maintainer-mode 
--disable-dependency-tracking --prefix=/usr --sysconfdir=/etc --enable-dev-tools --disable-openssl 
--disable-silent-rules returned exit code 1
make[1]: *** [override_dh_auto_configure] Error 255
make[1]: Leaving directory `/home/xan/libimobiledevice-1.2.0'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1364: [COLOR=#111111][FONT=Consolas]dpkg-buildpackage -rfakeroot -D -us -uc -b failed[/FONT][/COLOR]
```

If anyone has any guidance they could provide at all that'd be greatly appreciated. Determined to get iOS inspecting working in my Ubuntu.

---

