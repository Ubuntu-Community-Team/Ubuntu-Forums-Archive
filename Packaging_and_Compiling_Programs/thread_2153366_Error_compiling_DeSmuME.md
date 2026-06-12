---
title: "Error compiling DeSmuME"
date: 2013-06-10
forum: Packaging and Compiling Programs
---

### Post by JamesTheAwesomeDude on 2013-06-10
I've been trying to get DeSmuME installed, and the versions in the official repos are incredibly stale, so I decided to compile it myself. Sadly, it's not working.

After installing the packages build-essential autoconf automake libgtk2.0-dev libglu1-mesa-dev libsdl1.2-dev libglade2-dev gettext zlib1g-dev libosmesa6-dev intltool libagg-dev libasound2-dev, as per the official instructions, I then extracted the source tarball, cd'ed into it, and ran ./configure. All well so far.

Unfortunately, make throws some errors...
```
james@james-OptiPlex-GX620:~/desmume-0.9.9$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.14.2
checking for XML::Parser... ok
checking for gzopen in -lz... yes
checking for zzip_open in -lzzip... no
checking for sdl-config... /usr/bin/sdl-config
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking for main in -ldl... yes
checking for main in -lGL... no
checking for main in -lOSMesa... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GTK... yes
checking for GTHREAD... yes
checking for update-desktop-database... /usr/bin/update-desktop-database
checking for LUA... no 
checking for LUA... yes
checking for ALSA... yes
checking for LIBAGG... yes
checking for LIBSOUNDTOUCH... no
configure: WARNING: SoundTouch library not found, pcsx2 resampler will be disabled
checking whether to enable maintainer-specific portions of Makefiles... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/cli/Makefile
config.status: creating src/cli/doc/Makefile
config.status: creating src/gtk/Makefile
config.status: creating src/gtk/doc/Makefile
config.status: creating src/gtk-glade/Makefile
config.status: creating src/gtk-glade/doc/Makefile
config.status: creating src/wx/Makefile
config.status: creating src/gdbstub/Makefile
config.status: creating autopackage/default.apspec
config.status: executing depfiles commands
config.status: executing po/stamp-it commands
james@james-OptiPlex-GX620:~/desmume-0.9.9$ make
Making all in po
make[1]: Entering directory `/home/james/desmume-0.9.9/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/james/desmume-0.9.9/po'
Making all in src
make[1]: Entering directory `/home/james/desmume-0.9.9/src'
Making all in .
make[2]: Entering directory `/home/james/desmume-0.9.9/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/james/desmume-0.9.9/src'
Making all in gtk
make[2]: Entering directory `/home/james/desmume-0.9.9/src/gtk'
Making all in doc
make[3]: Entering directory `/home/james/desmume-0.9.9/src/gtk/doc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/james/desmume-0.9.9/src/gtk/doc'
make[3]: Entering directory `/home/james/desmume-0.9.9/src/gtk'
g++  -g -O2   -o desmume desmume.o dToolsList.o ioregsView.o sndsdl.o ctrlssdl.o driver.o osmesa_3Demu.o cheatsGTK.o hq2x.o hq4x.o 2xsai.o bilinear.o epx.o lq2x.o scanline.o videofilter.o main.o ../libdesmume.a -L/usr/lib/x86_64-linux-gnu -lSDL -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0   -pthread -lgthread-2.0 -lrt -lglib-2.0   -lasound   -lagg_pic     -lOSMesa -ldl -lz  -lGLU
../libdesmume.a(OGLRender.o): In function `OGLLoadEntryPoints_Legacy':
/home/james/desmume-0.9.9/src/OGLRender.cpp:161: undefined reference to `glXGetProcAddress'
/home/james/desmume-0.9.9/src/OGLRender.cpp:162: undefined reference to `glXGetProcAddress'
/home/james/desmume-0.9.9/src/OGLRender.cpp:164: undefined reference to `glXGetProcAddress'
/home/james/desmume-0.9.9/src/OGLRender.cpp:165: undefined reference to `glXGetProcAddress'
/home/james/desmume-0.9.9/src/OGLRender.cpp:168: undefined reference to `glXGetProcAddress'
../libdesmume.a(OGLRender.o):/home/james/desmume-0.9.9/src/OGLRender.cpp:169: more undefined references to `glXGetProcAddress' follow
collect2: ld returned 1 exit status
make[3]: *** [desmume] Error 1
make[3]: Leaving directory `/home/james/desmume-0.9.9/src/gtk'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/james/desmume-0.9.9/src/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/james/desmume-0.9.9/src'
make: *** [all-recursive] Error 1
james@james-OptiPlex-GX620:~/desmume-0.9.9$
```

What's the problem, and how do I fix it?

---

### Post by searchfgold6789 on 2013-06-10
It feels like a bug in the source code, since line numbers are given. Perhaps you could try 0.9.8 instead. But you may end up actually going into the source code to fix this. Try opening the desmume-0.9.9/src/OGLRender.cpp file, scrolling down to the lines mentioned (161, 162, 164, 165, 168) and seeing if there's anything there that might make it work if you commented it out. 
[Here]("http://forums.vega-strike.org/viewtopic.php?f=5&t=1563#p12369")'s a post that might contain a hint.

---

### Post by JamesTheAwesomeDude on 2013-06-11
I couldn't get anything out of that thread, but I did look into OGLRender.cpp and here's a snippet of the code:

```
static void OGLLoadEntryPoints_Legacy(){ // THIS IS LINE 152
    // Textures
    #if !defined(GLX_H)
    INITOGLEXT(PFNGLACTIVETEXTUREPROC, glActiveTexture) // Core in v1.3
    INITOGLEXT(PFNGLACTIVETEXTUREARBPROC, glActiveTextureARB)
    #endif


    // Blending THIS IS LINE 160
    INITOGLEXT(PFNGLBLENDFUNCSEPARATEPROC, glBlendFuncSeparate) // Core in v1.4
    INITOGLEXT(PFNGLBLENDEQUATIONSEPARATEPROC, glBlendEquationSeparate) // Core in v2.0


    INITOGLEXT(PFNGLBLENDFUNCSEPARATEEXTPROC, glBlendFuncSeparateEXT)
    INITOGLEXT(PFNGLBLENDEQUATIONSEPARATEEXTPROC, glBlendEquationSeparateEXT)


    // Shaders
    INITOGLEXT(PFNGLCREATESHADERPROC, glCreateShader) // Core in v2.0 
    INITOGLEXT(PFNGLSHADERSOURCEPROC, glShaderSource) // Core in v2.0
    INITOGLEXT(PFNGLCOMPILESHADERPROC, glCompileShader) // Core in v2.0
    INITOGLEXT(PFNGLCREATEPROGRAMPROC, glCreateProgram) // Core in v2.0
    INITOGLEXT(PFNGLATTACHSHADERPROC, glAttachShader) // Core in v2.0
    INITOGLEXT(PFNGLDETACHSHADERPROC, glDetachShader) // Core in v2.0
    INITOGLEXT(PFNGLLINKPROGRAMPROC, glLinkProgram) // Core in v2.0
    INITOGLEXT(PFNGLUSEPROGRAMPROC, glUseProgram) // Core in v2.0
    INITOGLEXT(PFNGLGETSHADERIVPROC, glGetShaderiv) // Core in v2.0
    INITOGLEXT(PFNGLGETSHADERINFOLOGPROC, glGetShaderInfoLog) // Core in v2.0
    INITOGLEXT(PFNGLDELETESHADERPROC, glDeleteShader) // Core in v2.0
    INITOGLEXT(PFNGLDELETEPROGRAMPROC, glDeleteProgram) // Core in v2.0
    INITOGLEXT(PFNGLGETPROGRAMIVPROC, glGetProgramiv) // Core in v2.0
    INITOGLEXT(PFNGLGETPROGRAMINFOLOGPROC, glGetProgramInfoLog) // Core in v2.0
    INITOGLEXT(PFNGLVALIDATEPROGRAMPROC, glValidateProgram) // Core in v2.0
    INITOGLEXT(PFNGLGETUNIFORMLOCATIONPROC, glGetUniformLocation) // Core in v2.0
    INITOGLEXT(PFNGLUNIFORM1IPROC, glUniform1i) // Core in v2.0
    INITOGLEXT(PFNGLUNIFORM1IVPROC, glUniform1iv) // Core in v2.0
    INITOGLEXT(PFNGLUNIFORM1FPROC, glUniform1f) // Core in v2.0
    INITOGLEXT(PFNGLUNIFORM2FPROC, glUniform2f) // Core in v2.0
    INITOGLEXT(PFNGLDRAWBUFFERSPROC, glDrawBuffers) // Core in v2.0
    INITOGLEXT(PFNGLBINDATTRIBLOCATIONPROC, glBindAttribLocation) // Core in v2.0
    INITOGLEXT(PFNGLENABLEVERTEXATTRIBARRAYPROC, glEnableVertexAttribArray) // Core in v2.0
    INITOGLEXT(PFNGLDISABLEVERTEXATTRIBARRAYPROC, glDisableVertexAttribArray) // Core in v2.0
    INITOGLEXT(PFNGLVERTEXATTRIBPOINTERPROC, glVertexAttribPointer) // Core in v2.0


    // VAO
    INITOGLEXT(PFNGLGENVERTEXARRAYSPROC, glGenVertexArrays)
    INITOGLEXT(PFNGLDELETEVERTEXARRAYSPROC, glDeleteVertexArrays)
    INITOGLEXT(PFNGLBINDVERTEXARRAYPROC, glBindVertexArray)


    // Buffer Objects
    INITOGLEXT(PFNGLGENBUFFERSARBPROC, glGenBuffersARB)
    INITOGLEXT(PFNGLDELETEBUFFERSARBPROC, glDeleteBuffersARB)
    INITOGLEXT(PFNGLBINDBUFFERARBPROC, glBindBufferARB)
    INITOGLEXT(PFNGLBUFFERDATAARBPROC, glBufferDataARB)
    INITOGLEXT(PFNGLBUFFERSUBDATAARBPROC, glBufferSubDataARB)
    INITOGLEXT(PFNGLMAPBUFFERARBPROC, glMapBufferARB)
    INITOGLEXT(PFNGLUNMAPBUFFERARBPROC, glUnmapBufferARB)


    INITOGLEXT(PFNGLGENBUFFERSPROC, glGenBuffers) // Core in v1.5
    INITOGLEXT(PFNGLDELETEBUFFERSPROC, glDeleteBuffers) // Core in v1.5
    INITOGLEXT(PFNGLBINDBUFFERPROC, glBindBuffer) // Core in v1.5
    INITOGLEXT(PFNGLBUFFERDATAPROC, glBufferData) // Core in v1.5
    INITOGLEXT(PFNGLBUFFERSUBDATAPROC, glBufferSubData) // Core in v1.5
    INITOGLEXT(PFNGLMAPBUFFERPROC, glMapBuffer) // Core in v1.5
    INITOGLEXT(PFNGLUNMAPBUFFERPROC, glUnmapBuffer) // Core in v1.5


    // FBO
    INITOGLEXT(PFNGLGENFRAMEBUFFERSEXTPROC, glGenFramebuffersEXT)
    INITOGLEXT(PFNGLBINDFRAMEBUFFEREXTPROC, glBindFramebufferEXT)
    INITOGLEXT(PFNGLFRAMEBUFFERRENDERBUFFEREXTPROC, glFramebufferRenderbufferEXT)
    INITOGLEXT(PFNGLFRAMEBUFFERTEXTURE2DEXTPROC, glFramebufferTexture2DEXT)
    INITOGLEXT(PFNGLCHECKFRAMEBUFFERSTATUSEXTPROC, glCheckFramebufferStatusEXT)
    INITOGLEXT(PFNGLDELETEFRAMEBUFFERSEXTPROC, glDeleteFramebuffersEXT)
    INITOGLEXT(PFNGLBLITFRAMEBUFFEREXTPROC, glBlitFramebufferEXT)
    INITOGLEXT(PFNGLGENRENDERBUFFERSEXTPROC, glGenRenderbuffersEXT)
    INITOGLEXT(PFNGLBINDRENDERBUFFEREXTPROC, glBindRenderbufferEXT)
    INITOGLEXT(PFNGLRENDERBUFFERSTORAGEEXTPROC, glRenderbufferStorageEXT)
    INITOGLEXT(PFNGLRENDERBUFFERSTORAGEMULTISAMPLEEXTPROC, glRenderbufferStorageMultisampleEXT)
    INITOGLEXT(PFNGLDELETERENDERBUFFERSEXTPROC, glDeleteRenderbuffersEXT)
}
```

---

### Post by steeldriver on 2013-06-11
It may be something to do with your specific graphics hardware / drivers and exactly what OpenGL version and features it supports, it looks like the ABI does not require implementations to export that function and it's bad practice to rely on it

[http://dri.freedesktop.org/wiki/glXGetProcAddressNeverReturnsNULL/](http://dri.freedesktop.org/wiki/glXGetProcAddressNeverReturnsNULL/)

There may be a workaround, it depends how much work you want to put into this

---

### Post by JamesTheAwesomeDude on 2013-06-11
I actually have no experience coding in C++ (I'm currently learning Python,) and I've never experimented with OpenGL, but after reading that article, I can't see why the reference to [COLOR=#000000][FONT=Ubuntu Mono]glXGetProcAddress[/FONT][/COLOR] would be undefined, since the function never returns null. Wouldn't any issues appear at runtime in that case? Why does it affect compilation?

---

### Post by steeldriver on 2013-06-11
sorry, I didn't mean that article specifically, just to point out that a particular vendor may chose not to define the function at all (or at least not externally) - which seems to be what you're experiencing

---

### Post by steeldriver on 2013-06-11
DISCLAIMER: THIS IS A COMPLETE SWAG, ABSOLUTELY NO WARRANTY EXPRESSED OR IMPLIED etc. etc.  - but if you don't get any better suggestions you could try this

```

make clean
sed -i'.bak' 's/glXGetProcAddress/glXGetProcAddressARB/' src/OGLRender.h
make

```

The above just replaces the macro definition of INITOGLEXT (which is the immediate cause of your reported errors) with a - hopefully equivalent - reference to glXGetProcAddressARB

---

