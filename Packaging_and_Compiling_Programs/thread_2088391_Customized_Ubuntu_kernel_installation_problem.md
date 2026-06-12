---
title: "Customized Ubuntu kernel installation problem"
date: 2012-11-26
forum: Packaging and Compiling Programs
---

### Post by john1313 on 2012-11-26
I have compiled kernel on 64 bit running ubuntu machine by using below command 
CONCURRENCY_LEVEL=5 nice fakeroot make-kpkg --initrd
--append-to-version=-32-plx --overlay-dir=$(pwd) kernel-image
kernel-headers

**After compilation it generated two files **

-linux-headers-3.6.0-rc3-32-plx_3.6.0-rc3-32-plx-10.00.Custom_amd64.deb
-linux-image-3.6.0-rc3-32-plx_3.6.0-rc3-32-plx-10.00.Custom_amd64.deb

but when i install this package by using this command
dpkg -i linux-image-3.6.0-rc3-32-plx_3.6.0-rc3-32-plx-10.00.Custom_amd64.deb
 on other machine running 64 bit ubuntu it gives me these errors

dpkg:error processing linux-image-3.6.0-rc3-32-plx_3.6.0-rc3-32-plx-10.00.Custom_amd64.deb (--install):
linux-image-3.6.0-rc3-32-plx:3.6.0-rc3-32-plx_3.6.0-rc3-32-plx-10.00.Custom (Multi-Arch: no) is not co-installable with linux-image-3.6.0-rc3-32-plx:i386 3.6.0-rc3-32-plx_3.6.0-rc3-32-plx-10.00.Custom (Multi-Arch:no) which is currently installed
Errors were encountered while processing:
linux-image-3.6.0-rc3-32-plx_3.6.0-rc3-32-plx-10.00.Custom_amd64.deb

**Please tell me wt to do.:(**

---

### Post by Elfy on 2012-11-30
*Thread moved to **Packaging and Compiling Programs**.*

---

### Post by Bachstelze on 2012-11-30
Post the *entire* error message...

---

