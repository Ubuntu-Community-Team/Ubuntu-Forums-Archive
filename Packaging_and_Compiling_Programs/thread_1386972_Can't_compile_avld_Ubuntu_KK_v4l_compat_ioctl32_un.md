---
title: "Can't compile avld Ubuntu KK: v4l_compat_ioctl32 undeclared"
date: 2010-01-21
forum: Packaging and Compiling Programs
---

### Post by mzettik on 2010-01-21
Hi, I have problem with compile AVLD on Ubuntu KK 2.6.31-17-generic.

make:
make -C /lib/modules/2.6.31-17-generic/build M=/home/maso/Plocha/HG12605/avld_0.1.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/maso/Plocha/HG12605/avld_0.1.4/video_device.o
/home/maso/Plocha/HG12605/avld_0.1.4/video_device.c:627: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/maso/Plocha/HG12605/avld_0.1.4/video_device.c:637: warning: initialization from incompatible pointer type
make[2]: *** [/home/maso/Plocha/HG12605/avld_0.1.4/video_device.o] Error 1
make[1]: *** [_module_/home/maso/Plocha/HG12605/avld_0.1.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [all] Error 2

Where is defined function "v4l_compat_ioctl32"? On Debian 5 2.6.26 this work and is located in linux-headers-...-common/include/media/v4l2-dev.h

I need avld for showing video on LCD via parallel port and /dev/video0 (HG12605).

[http://allonlinux.free.fr/Projets/AVLD/](http://allonlinux.free.fr/Projets/AVLD/)

thanks for help

---

### Post by SevenMachines on 2010-01-21
hi there, i believe it was something to do with the v4l ioctl32 stuff being moved and should not be handled by the drivers themselves in newer kernels ( >2.6.29? ). its a little hazy but the fix attached works here, it simply ignores the compat_ioctl: v4l_compat_ioctl32 line on kernels >=2.6.29, which as far as i can remember is an ok thing to do.
as i say, seems to work fine but you should probably contact the author and get him to actively update the driver or find a more actively developed equivalent

---

### Post by mzettik on 2010-01-22
> **SevenMachines said:**
> hi there, i believe it was something to do with the v4l ioctl32 stuff being moved and should not be handled by the drivers themselves in newer kernels ( >2.6.29? ). its a little hazy but the fix attached works here, it simply ignores the compat_ioctl: v4l_compat_ioctl32 line on kernels >=2.6.29, which as far as i can remember is an ok thing to do.
as i say, seems to work fine but you should probably contact the author and get him to actively update the driver or find a more actively developed equivalent

big thanks for right way :-)
I tested before you wrote, comment a line with v4l_compat_ioctl32 and make and make install works and too
modprobe avld width=....
but if I can accessing to this with any program include hg12605, error is occured while opening device (/dev/video0):
Unknown error 515

rights of /dev/video0 are:
crw-rw----+ 1 root video 81, 0 2010-01-22 08:28 /dev/video0

I tested rw-rw-rw and rwxrwxrwx and not works (err 515)

---

### Post by SevenMachines on 2010-01-22
sounds like actual problems in the avld driver codes v4l stuff to me, though i could be wrong. Probably needs some fixing to work with newer kernel v4l stuff. i really dont know anything about v4l drivers though... if the authors still maintaining it you should probably contact them and see what they say

---

### Post by mzettik on 2010-01-22
> **SevenMachines said:**
> sounds like actual problems in the avld driver codes v4l stuff to me, though i could be wrong. Probably needs some fixing to work with newer kernel v4l stuff. i really dont know anything about v4l drivers though... if the authors still maintaining it you should probably contact them and see what they say

I emailed to author, see if will be any reaction from him...

Thanks for helping

---

### Post by Whoopie on 2010-01-22
Hi,

please find attached a patch to get the avld module working.

Best regards,
Whoopie

---

### Post by mzettik on 2010-01-23
> **Whoopie said:**
> Hi,

please find attached a patch to get the avld module working.

Best regards,
Whoopie

ooh, big thanks, it works! How do you it? :-)
It's great!

---

### Post by Whoopie on 2010-01-25
Hi,

great to know that it also works for you.

What I did is compare the latest changes to the vloopback module and do the same in the avld code.

Best regards,
Whoopie

---

### Post by LuciusMare on 2010-03-06
Hello, i have exactly the same problem, but i found both of the patches for the wrong version - so, please, could anyone make one for the newest version, or better, a .deb package that works?

---

### Post by pki on 2010-03-10
LuciusMare, you are wrong, the latest version is 0.1.4 and the patch is exactly for this version. Yesterday i compiled it without problems, now the device runs about 20 hours uninterrupted without problems.

Many many thanks to Whoopie for doing the patchfile.

For your ease i attach a patched version.

---

### Post by C4I0N4 on 2011-03-04
About almost one year later I just downloaded the patched version and installed with succes. Thank you guys!:)

---

