---
title: "build error, can't find jpeglib.h - but it's right there?"
date: 2007-05-17
forum: Programming Talk
---

### Post by Catfish81 on 2007-05-17
Hi developer forum.

I've posted this in here becuase people in here will probably know more about this than in beginner forums.

I want to compile the source code for quake2max under linux (ubuntu). I have obtained a few quake2max source packages. I say a few because the first one I got looked more like the straight quake2 source released from ID. That one didnt have a make file or anything so I assume it is just the straight source for you to develop off.

I then found another quake2max source file that had a Makefile and quake2max related source files. So I've firstly tried building that. When I did a 'make' it outputs some options:

> catfish@delta:~/downloads/q2max.src/Quake2maX$ make

Set to YES or NO at the top of the file the possible binaries to build
by the makefile.
By default, a make release will build QuDos with maX support, a glx
renderer the required game binary and some other features.

Possible targets:

>> make release         build the binary for a release.
>> make debug           build the binary for debuging mode.
>> make install         will install to your quake2 home dir.
>> make bz2             create a tar.bz2 compressed package.
>> make clean           clean every '.o' object files.
>> make distclean       clean objects, binaries and modified files.



So I now do 'make release' but it outputs an error complaining for jpeglib.h

> catfish@delta:~/downloads/q2max.src/Quake2maX$ make release
ref_gl/gl_image.c:21:21: error: jpeglib.h: No such file or directory
ref_gl/gl_image.c:825: error: expected ‘)’ before ‘cinfo’
ref_gl/gl_image.c:829: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jpg_fill_input_buffer’
ref_gl/gl_image.c:835: error: expected ‘)’ before ‘cinfo’
ref_gl/gl_image.c:845: error: expected ‘)’ before ‘cinfo’
ref_gl/gl_image.c: In function ‘LoadJPG’:
ref_gl/gl_image.c:864: error: storage size of ‘cinfo’ isn’t known
ref_gl/gl_image.c:865: error: storage size of ‘jerr’ isn’t known
make[1]: *** [releasei386/ref_gl/gl_image.o] Error 1
make[1]: Leaving directory `/home/catfish/downloads/q2max.src/Quake2maX'
make: *** [release] Error 2
[email]catfish@delta:~/downloads/q2max.src[/email]/Quake2maX$ 


I did a search around for jpeglib.h and found that it exists in the first quake2 source file i downloaded. So I copied all the files from the second source archive to the directory structure of the first one giving me a mix of the two. No files were asked to be over written, so I assume that nothing was.
When I do 'make release' now, it complains the same but the thing is, the jpeglib.h file is in the same directory as the file that calls for it (ref_gl/gl_image.c) so I don't understand where it is looking to find this jpeglib.h file.

Anyone able to help out?

---

### Post by Catfish81 on 2007-05-17
Ok I fixed that error by changing the include line from:

#include <jpeglib.h>
to
#include "jpeglib.h"

And now I get errors about lvalues:

> error: invalid lvalue in assignment




Anyone got pre-built quake2max binaries that work?
HAHAHAHAHA

---

