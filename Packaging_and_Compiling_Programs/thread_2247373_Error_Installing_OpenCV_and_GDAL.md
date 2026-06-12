---
title: "Error Installing OpenCV and GDAL"
date: 2014-10-07
forum: Packaging and Compiling Programs
---

### Post by nick-steiner on 2014-10-07
Getting the following message installing OpenCV:

Linking CXX shared library ../../lib/libopencv_highgui.so
/usr/bin/ld: /usr/local/lib/libjpeg.a(jcparam.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libjpeg.a: error adding symbols: Bad value
collect2: error: ld returned 1 exit status
make[2]: *** [lib/libopencv_highgui.so.2.4.9] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2

And also with GDAL:

usr/bin/ld: /usr/local/lib/libjpeg.a(jctrans.o): relocation R_X86_64_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libjpeg.a: error adding symbols: Bad value
collect2: error: ld returned 1 exit status
make[1]: *** [libgdal.la] Error 1
make[1]: Leaving directory `/home/nsteiner/gdal-1.10.1+dfsg'
make: *** [check-lib] Error 2

Please help, cannot seem to fix.

Thanks in advance.

Nick

---

### Post by oldos2er on 2014-10-07
Moved to Packaging & Compiling Programs.

---

