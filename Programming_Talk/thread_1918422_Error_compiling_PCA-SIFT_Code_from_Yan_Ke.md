---
title: "Error compiling PCA-SIFT Code from Yan Ke"
date: 2012-01-31
forum: Programming Talk
---

### Post by bagussetya on 2012-01-31
Hi all, 

My name is Bagus Setya Rintyarna. I'm using PCA-SIFT for my  master  exercise. I'm newbie in programming as well as in ubuntu. I read some  reference that PCA-SIFT need keypoint  detector code and it should be  merged to PCA-SIFT source code (from Yan  Ke). Would anyone give me any  suggestion how to merge the code ? I try to  compile PCA-SIFT code in  ubuntu and got this error :

if g++ -DHAVE_CONFIG_H -I. -I. -I.    -Wall -O3  -DNDEBUG -g -O2 -MT   image.o -MD -MP -MF ".deps/image.Tpo" -c -o image.o image.cc; \
    then mv -f ".deps/image.Tpo" ".deps/image.Po"; else rm -f   ".deps/image.Tpo"; exit 1; fi
image.cc:18:22: error: pgm.h: No such file or directory
image.cc: In constructor ‘Image::Image(const char*)’:
image.cc:54: error: ‘gray’ was not declared in this scope
image.cc:54: error: expected ‘;’ before ‘maxval’
image.cc:55: error: ‘pixels’ was not declared in this scope
image.cc:57: error: ‘maxval’ was not declared in this scope
image.cc:57: error: ‘pgm_readpgm’ was not declared in this scope
image.cc:70: error: ‘pgm_freearray’ was not declared in this scope
image.cc: In member function ‘void Image::write(const char*)’:
image.cc:202: error: ‘gray’ was not declared in this scope
image.cc:202: error: ‘pixels’ was not declared in this scope
image.cc:202: error: ‘pgm_allocarray’ was not declared in this scope
image.cc:214: error: ‘pgm_writepgm’ was not declared in this scope
image.cc:216: error: ‘pgm_freearray’ was not declared in this scope
make[1]: *** [image.o] Error 1
make[1]: Leaving directory `/home/bagus/pcasift-0.91nd'
make: *** [all] Error 2

---

### Post by Bachstelze on 2012-01-31
> image.cc:18:22: error: pgm.h: No such file or directory

This file is in the package [font=monospace]libpgm-dev[/font].

---

### Post by bagussetya on 2012-02-02
I've installed libpgm-dev but the error still occur.

---

### Post by Zugzwang on 2012-02-02
> **bagussetya said:**
> I've installed libpgm-dev but the error still occur.

Look here: [http://packages.ubuntu.com/oneiric/amd64/libpgm-dev/filelist](http://packages.ubuntu.com/oneiric/amd64/libpgm-dev/filelist)

Apparently, the header files are in the directory /usr/include/pgm-5.1 - the preferred way to get this into your include directories when compiling is to use pkgconfig. You will need to add something like `pkg-config --cflags openpgm-5.1` at the end of your compilation command to get the right headers and add `pkg-config --libs openpgm-5.1` to your linking command.

---

