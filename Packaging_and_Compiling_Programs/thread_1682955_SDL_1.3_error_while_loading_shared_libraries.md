---
title: "SDL 1.3: error while loading shared libraries"
date: 2011-02-06
forum: Packaging and Compiling Programs
---

### Post by KillerSponge on 2011-02-06
I'm trying to create a c++ program using SDL 1.3 and OpenGL 3.2. I downloaded/compiled/installed SDL 1.3 to my homedir (to not screw up SDL 1.2), and created a new project in Eclipse. I added the /include en /lib directories from SDL 1.3 to the project, and told it to use the SDL and GL libs, and use the sample code from [here]("http://www.opengl.org/wiki/Tutorial1:_Creating_a_Cross_Platform_OpenGL_3.2_Context_in_SDL_(C_/_SDL)").

The project compiles, but when I try to run it I get this error message:

```
error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory
```

Does anyone know how I can fix this? :)

---

### Post by SevenMachines on 2011-02-07
If you use local library installations (as you often should for the reason you mention) then you need the -I option for compiling, the -L option for linking as you have done, but also the system needs to find the libraries at runtime. Since they arent on your system search path then you need to add them either,

* At the command line with
$ LD_LIBRARY_PATH=/local/library/directory/ ./myprogram

* Or add the /local/library/directory/ to a new or existing file in /etc/ld.so.conf.d

---

