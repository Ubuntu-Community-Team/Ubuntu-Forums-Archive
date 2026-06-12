---
title: "Problem Installing podofobrowser"
date: 2016-01-11
forum: New to Ubuntu
---

### Post by Balbir_Kumar on 2016-01-11
While installing podofobrowser I am getting following error. Could you
please help me.

LIBFREETYPE headers: LIBFREETYPE_FT2BUILD_H-NOTFOUND
LIBFREETYPE_FTHEADER_H-NOTFOUND

CMake Error: The following variables are used in this project, but they are
set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake
files:
LIBFREETYPE_FT2BUILD_H
   used as include directory in directory
/home/mjc_in1/Desktop/podofobrowser/src
LIBFREETYPE_FTHEADER_H
   used as include directory in directory
/home/mjc_in1/Desktop/podofobrowser/src

---

### Post by steeldriver on 2016-01-11
Have you installed the libfreetype6-dev package?

```

libfreetype6-dev - FreeType 2 font engine, development files

```

---

### Post by Balbir_Kumar on 2016-01-11
Yes I had installed Freetype and PoDoFo is working fine with it.

Shall I need to make some changes into cmake file which is as follows?

FIND_PATH(LIBFREETYPE_FT2BUILD_H NAMES ft2build.h)

FIND_PATH(LIBFREETYPE_FTHEADER_H
    NAMES config/ftheader.h freetype/config/ftheader.h
    PATHS
    ${LIBFREETYPE_FT2BUILD_H}/freetype2
    ${LIBFREETYPE_FT2BUILD_H}/freetype
    )

FIND_LIBRARY(LIBFREETYPE_LIB NAMES freetype libfreetype)
MESSAGE("freetype lib: ${LIBFREETYPE_LIB}")

IF(LIBFREETYPE_FT2BUILD_H AND LIBFREETYPE_FTHEADER_H AND LIBFREETYPE_LIB)
    SET(LIBFREETYPE_FOUND TRUE CACHE BOOLEAN "Was libfreetype found")
ELSE(LIBFREETYPE_FT2BUILD_H AND LIBFREETYPE_FTHEADER_H AND LIBFREETYPE_LIB)
    SET(LIBFREETYPE_FOUND FALSE CACHE BOOLEAN "Was libfreetype found")
ENDIF(LIBFREETYPE_FT2BUILD_H AND LIBFREETYPE_FTHEADER_H AND LIBFREETYPE_LIB)

---

### Post by Balbir_Kumar on 2016-01-11
Thanks [**[COLOR=#DD4814][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500"). I am able to fix it by some changes in above cmake file.

---

### Post by salahuddin3 on 2016-08-16
Hi, what changes did you needed to do to cmake run without errors?

---

### Post by anteldan on 2017-03-21
As for me, I looked into the findFREETYPE.cmake file in podofo to see how it worked. I also located ft2build.h, it is in /usr/include/freetype2

$ cmake -DLIBFREETYPE_FT2BUILD_H=/usr/include/freetype2 -DLIBFREETYPE_FTHEADER_H=/usr/include/freetype2/freetype/config -DLIBPODOFO_DIR=/home/daniel/podofo/lib64 -DCMAKE_INCLUDE_PATH=/home/daniel/podofo/include DCMAKE_LIBRARY_PATH=/home/daniel/podofo/lib64 ../podofobrowser-0.5

and after that cmake is fine.

But then I have this problem on the make :
$ make
[  5%] Generating moc_pdfobjectmodel.cxx
moc: Cannot open options file specified with @
...
src/CMakeFiles/podofobrowser.dir/build.make:115: recipe for target 'src/moc_pdfobjectmodel.cxx' failed
make[2]: *** [src/moc_pdfobjectmodel.cxx] Error 1
CMakeFiles/Makefile2:85: recipe for target 'src/CMakeFiles/podofobrowser.dir/all' failed
make[1]: *** [src/CMakeFiles/podofobrowser.dir/all] Error 2
Makefile:127: recipe for target 'all' failed
make: *** [all] Error 2

---

