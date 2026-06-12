---
title: "linking to FTGL libraries help"
date: 2007-06-08
forum: Programming Talk
---

### Post by moshy on 2007-06-08
I'm trying to compile a demo C++ program which uses OpenGL and FTGL for fonts. (It also uses Glut but normally I would use SDL).
I've installed FTGL on my computer after downloading it from the internet. There's also an ftgl-dev package in the repositories but that only contains header files. Anyway when compiling I don't know how to now link the demo file to the FTGL library.

Currently it can find the header files, but then I get this error
```

ftgl_demo.cpp: In function ‘void my_init(const char*)’:
ftgl_demo.cpp:22: error: no matching function for call to ‘FTGLOutlineFont::FTGLOutlineFont()’
/usr/include/FTGL/FTGLOutlineFont.h:33: note: candidates are: FTGLOutlineFont::FTGLOutlineFont(const unsigned char*, size_t)
/usr/include/FTGL/FTGLOutlineFont.h:25: note:                 FTGLOutlineFont::FTGLOutlineFont(const char*)
/usr/include/FTGL/FTGLOutlineFont.h:18: note:                 FTGLOutlineFont::FTGLOutlineFont(const FTGLOutlineFont&)

```
I know where the library is, it's in
/usr/local/lib/libftgl.a
which contains the object files, and
/usr/local/lib/libftgl.la
I have no idea what this file is, as I know nothing about libraries and how to link to them. This is my Makefile which I hacked together.
```

make : ftgl_demo.o
	g++ -L/usr/local/lib/libftgl.a ftgl_demo.o -o ftgl_demo

ftgl_demo.o : ftgl_demo.cpp
	 g++ -c -I/usr/include/FTGL ftgl_demo.cpp

```
Could somebody please tell me what I'm doing wrong, or some sites which completely explain how this works, or even better how to set it up so I don't have to specify actual paths, like when I do -lGL -lGLU -lSDL_image etc.

---

### Post by moshy on 2007-06-08
after discovering some readme's and actually installing FTGL properly so it has a pkg-config file, I've got this

Makefile:
```

FTGL_CPPFLAGS := $(shell pkg-config --cflags ftgl)
FTGL_LDFLAGS  := $(shell pkg-config --libs-only-L ftgl)
FTGL_LIBS     := $(shell pkg-config --libs-only-l ftgl)

CFLAGS = -c $(FTGL_CPPFLAGS)
LFLAGS = $(FTGL_LDFLAGS) $(FTGL_LIBS) -lglut

make : ftgl_demo.o
	g++ $(LFLAGS) ftgl_demo.o -o ftgl_demo

ftgl_demo.o : ftgl_demo.cpp
	 g++ $(CFLAGS) ftgl_demo.cpp

```

but it still gets this error
```

g++ -L/usr/local/lib   -lGLU -lGL -lfreetype -lz -lftgl   -lglut ftgl_demo.o -o ftgl_demo
ftgl_demo.o: In function `my_init(char const*)':
ftgl_demo.cpp:(.text+0x619): undefined reference to `FTGLOutlineFont::FTGLOutlineFont(char const*)'
ftgl_demo.cpp:(.text+0x643): undefined reference to `FTGLPolygonFont::FTGLPolygonFont(char const*)'
ftgl_demo.cpp:(.text+0x68e): undefined reference to `FTGLTextureFont::FTGLTextureFont(char const*)'
ftgl_demo.cpp:(.text+0x6d9): undefined reference to `FTGLBitmapFont::FTGLBitmapFont(char const*)'
ftgl_demo.cpp:(.text+0x724): undefined reference to `FTGLPixmapFont::FTGLPixmapFont(char const*)'
collect2: ld returned 1 exit status
make: *** [make] Error 1

```

even though now it should work

---

### Post by WW on 2007-06-08
Try putting ftgl_demo.o before the -l options in the command line:
```

g++ ftgl_demo.o -L/usr/local/lib   -lGLU -lGL -lfreetype -lz -lftgl   -lglut  -o ftgl_demo

```
The order matters when linking.

---

### Post by moshy on 2007-06-08
thankyou

---

