---
title: "linking to debug libs for use with valgrind"
date: 2009-05-20
forum: Packaging and Compiling Programs
---

### Post by jonim8or on 2009-05-20
I am developing a 3D library which uses OpenGL and has multiple threads. To find race hazards and memory leaks in this program, I hope to use valgrind's tools. However, the output from valgrind is quite useless when using the release OpenGL libraries:
```

==10421== Possible data race during write of size 2 at 0x95be158 by thread #8
==10421==    at 0x8E91C44: (within /usr/lib/libGLcore.so.180.44)
==10421==    by 0x9A2EB77: ???
==10421==    by 0xB99D02F: ???
==10421==  This conflicts with a previous read of size 2 by thread #1
==10421==    at 0x632B104: (within /usr/lib/libGL.so.180.44)
==10421==    by 0x9A3361F: ???
==10421==    by 0x98317A7: ???
==10421==    by 0x9A3361F: ???
==10421==    by 0xA1A63FF: ???
==10421==    by 0xA1A6417: ???
==10421==    by 0x9A3361F: ???
==10421==    by 0x9A2FB27: ???

```

Now I also installed the debug version of libGL (libgl1-mesa-glx-dbg, libgl1-mesa-dri-dbg), but how do I make sure that the program is runned using the debug versions?

When linking to the debug version of libGL, it misses some drm functions. It seems to be statically linked, while the normal version has dynamic links to other libraries. 
```

$ ldd /usr/lib/libGL.so
	linux-vdso.so.1 =>  (0x00007fff2ddff000)
	libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0x00007fcb247d3000)
	libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0x00007fcb246d1000)
	libm.so.6 => /lib/libm.so.6 (0x00007fcb2444b000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007fcb24239000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007fcb23f32000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fcb23d2d000)
	libc.so.6 => /lib/libc.so.6 (0x00007fcb239bb000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007fcb237b8000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007fcb2359b000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fcb25ccd000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007fcb23396000)
$ ldd /usr/lib/debug/usr/lib/libGL.so.1.2 
	statically linked

```

My question is: how should I approach creating a debug build that I can use to get useful output from tools like valgrind?

---

