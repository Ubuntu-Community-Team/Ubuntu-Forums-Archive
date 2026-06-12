---
title: "dpkg-gencontrol: error: package linux-image* not in control info"
date: 2011-10-26
forum: Packaging and Compiling Programs
---

### Post by ufuser01 on 2011-10-26
Hi,

I am trying to patch a vanilla kernel with an RTAI patch and I get this error. I compiled older kernels successfully (2.6.32.11, .20 etc).  Any suggestions.

I found a similar post, but this didn't help:
[http://ubuntuforums.org/showpost.php?p=9638461&postcount=1488](http://ubuntuforums.org/showpost.php?p=9638461&postcount=1488)

Thanks.

     ./debian/templates.l10n   > ./debian/templates.master
install -p    -o root -g root  -m  644 ./debian/templates.master /usr/src/linux-2.6.35.9/debian/linux-image-2.6.35.9-custom/DEBIAN/templates
dpkg-gencontrol -DArchitecture=i386 -isp         \
            -plinux-image-2.6.35.9-custom -P/usr/src/linux-2.6.35.9/debian/linux-image-2.6.35.9-custom/
dpkg-gencontrol: error: package linux-image-2.6.35.9-custom not in control info
make[2]: *** [debian/stamp/binary/linux-image-2.6.35.9-custom] Error 255
make[2]: Leaving directory `/usr/src/linux-2.6.35.9'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.35.9-custom] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.35.9'
make: *** [kernel_image] Error 2

---

