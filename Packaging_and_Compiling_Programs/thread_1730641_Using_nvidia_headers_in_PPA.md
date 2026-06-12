---
title: "Using nvidia headers in PPA"
date: 2011-04-16
forum: Packaging and Compiling Programs
---

### Post by Yellow Pasque on 2011-04-16
I'm trying to push vdpau-video to my catalysthacks PPA. I can get the package to debuild locally, but that is because it is using mesa's headers. In the PPA, it isn't finding the nvidia headers (even though I build depend on nvidia-current-dev) so it doesn't build all of the necessary files.

```
checking for GL/gl.h... no
checking for GL/glext.h... no
checking for GL/glx.h... no
checking for glXCreateContext in -lGL... no
```
..and it dies with this error:
```
dh_install: vdpau-video missing files (debian/tmp/usr/lib/dri/*.so), aborting
make: *** [binary-install/vdpau-video] Error 2
dpkg-buildpackage: error: /usr/bin/fakeroot debian/rules binary-arch gave error exit status 2
```

Full build log: [https://launchpadlibrarian.net/69568064/buildlog_ubuntu-natty-amd64.vdpau-video_0.7.3-1ubuntu2~catalysthacks2_FAILEDTOBUILD.txt.gz](https://launchpadlibrarian.net/69568064/buildlog_ubuntu-natty-amd64.vdpau-video_0.7.3-1ubuntu2~catalysthacks2_FAILEDTOBUILD.txt.gz)

---

### Post by SevenMachines on 2011-04-16
if your using mesa then <GL/gl.h> will work whereas in your ppa, since your specifying the nvidia headers, it wont since it stores its headers in  the subdirectory /usr/include/nvidia-current. Maybe try adding
CFLAGS+=-I/usr/include/nvidia-current 
to debian rules. Or use the mesa headers if you dont really need nvidias

---

### Post by Yellow Pasque on 2011-04-16
I found out that the nvidia-dev wasn't what was causing the issue. The issue was with the custom version of libva using a different install path than the Ubuntu one.

Thanks, anyway.

---

