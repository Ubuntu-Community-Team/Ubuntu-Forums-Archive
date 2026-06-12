---
title: "MATLAB installation"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by K3ITHK on 2012-11-12
I'm trying to install MATLAB. I got the installation started before, but had some errors that caused it to stop. Now when I try to run the installer, nothing happens. It says preparing files and then finished no more than a second apart. It's almost as if it thinks it's still installed and is just quitting? The first time the installer window opened, but it doesn't anymore. And note that I am running the installer as sudo.

```
Preparing installation files ...
->  DVD                 = /media/MATHWORKS_R2012A
->  ARCH                = glnxa64
->  DISPLAY             = :0
->  TESTONLY            = 0
->  JRE_LOC             = /tmp/mathworks_2931/sys/java/jre/glnxa64/jre
->  LD_LIBRARY_PATH     = /tmp/mathworks_2931/bin/glnxa64
 
Command to run:
/tmp/mathworks_2931/sys/java/jre/glnxa64/jre/bin/java  -splash:"/media/MATHWORKS_R2012A/java/splash.png" -Djava.ext.dirs=/tmp/mathworks_2931/sys/java/jre/glnxa64/jre/lib/ext:/tmp/mathworks_2931/java/jar:/tmp/mathworks_2931/java/jarext:/tmp/mathworks_2931/java/jarext/axis2/:/tmp/mathworks_2931/java/jarext/guice/:/tmp/mathworks_2931/java/jarext/webservices/ com/mathworks/professionalinstaller/Launcher -root "/media/MATHWORKS_R2012A" -tmpdir "/tmp/mathworks_2931" 
 
Installing ...
Finished

```

If anyone knows how to resolve this, please help!



EDIT!

I was able to get it to install. I think the problem in this case was that I had a space in the pathname where the disk image was located. What happened before and caused the initial installation failure was improper disk mounting or permissions or something. I really don't know.

How do I mark as solved?

---

