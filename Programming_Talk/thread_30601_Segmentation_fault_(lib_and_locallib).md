---
title: "Segmentation fault (lib and local/lib)"
date: 2005-04-29
forum: Programming Talk
---

### Post by lgoss007 on 2005-04-29
I am trying to have both an installed ubuntu library and a development library (cvs) installed at the same time so that I can do tests on the cvs version but still work with the released version. However when I try to run a program I get a "Segmentation fault".

Here are the steps I follow:

1> I download the cvs version and compile.
2> Make my program based off library (using -L/usr/local/lib and -I/usr/local/include)
3> Run program.

The program runs fine as I expect.

Then:

4> Go to synaptic and install (library is libopenscenegraph)
5> Run program.

The program gives "Segmentation fault".

I have "/usr/local/lib" in my ld.so.conf, I've run ldconfig, and when I run ldd on my application it gives:
```

        libosg.so => /usr/local/lib/libosg.so (0xb7e1e000)
        libosgDB.so => /usr/local/lib/libosgDB.so (0xb7dc1000)
        libosgGA.so => /usr/local/lib/libosgGA.so (0xb7d7e000)
        libosgUtil.so => /usr/local/lib/libosgUtil.so (0xb7c92000)
        libosgText.so => /usr/local/lib/libosgText.so (0xb7c68000)
        libosgProducer.so => /usr/local/lib/libosgProducer.so (0xb7c29000)
        libProducer.so => /usr/local/lib/libProducer.so (0xb7bdd000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7b23000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b02000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7af6000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb79c9000)
        libGLU.so.1 => /usr/X11R6/lib/libGLU.so.1 (0xb7953000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb78db000)
        libOpenThreads.so => /usr/local/lib/libOpenThreads.so (0xb78d5000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb78d2000)
        libXmu.so.6 => /usr/X11R6/lib/libXmu.so.6 (0xb78bc000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0xb77f7000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb77e7000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0xb7feb000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0xb77da000)
        libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb7089000)
        libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0xb7086000)
        libXt.so.6 => /usr/X11R6/lib/libXt.so.6 (0xb7037000)
        libSM.so.6 => /usr/X11R6/lib/libSM.so.6 (0xb702e000)
        libICE.so.6 => /usr/X11R6/lib/libICE.so.6 (0xb7016000)

```

So can anyone give me a clue about why I get a seg fault when I have both libraries installed? How do others deal with release and development versions?

lucas

---

### Post by zeroK on 2005-04-29
If you're only testing the program then perhaps changing the ld.so.conf is probably a little bit too much. I think changing the LD_LIBRARY_PATH enviroment variable for example testing session could also do the job without affecting other programs :-)

---

### Post by lgoss007 on 2005-04-29
Well I deleted the "/usr/local/lib" from ld.so.conf and tried LD_LIBRARY_PATH and for some odd reason it worked. So it appears that something is going wrong with ld.so.

So is this possibly a bug? I don't really want to use LD_LIBRARY_PATH as the majority of my work is with the cvs version and I only occasionally use the other.

lucas

---

### Post by mendicant on 2005-04-29
It would be extremely odd for the linker to have a problem.  I would suspect something I did before something provided by the system.  Try running things under valgrind (if you can--valgrind is a bit slow for 3D stuff) to see if you have a problem in your own code.

---

