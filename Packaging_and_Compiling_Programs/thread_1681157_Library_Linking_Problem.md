---
title: "Library Linking Problem"
date: 2011-02-03
forum: Packaging and Compiling Programs
---

### Post by jeffrich4 on 2011-02-03
I'm trying to compile an OpenGL C program that uses 3 libraries, GL, GLU, and glut. For some reason when I compile with:

gcc lesson1.c -lGL -lGLU -lglut

I get an error message:

/usr/bin/ld: cannot find -lGL

I have verified that libGL.so is in usr/lib/mesa as well as usr/lib64/mesa, so I'm not sure why this is happening.

The other 2 link properly and they are in usr/lib. I think I could probably just copy GL there but it seems like this shouldn't be happening and I wanted to try to fix it the right way. Can anyone help?

---

### Post by MadCow108 on 2011-02-03
have you installed libGL from a package? if yes which one?
there should be a link in /usr/lib created by e.g. libgl1-mesa-dev

otherwise either create one yourself (man ln) or compile like this:
gcc lesson1.c -L/usr/lib/mesa -lGL -lGLU -lglut

-L adds a path for the linker to search in

the actual library used by your program at runtime is determined by
 /etc/ld.so.conf.d/GL.conf
this on ubuntu systems links to /etc/alternatives/gl_conf which again links to a file provided by packages providing a libGL.so e.g. nvidia, flgrx or mesa
it contains something like this for nvidia libGL.so:
/usr/lib/nvidia-current
/usr/lib32/nvidia-current

---

### Post by jeffrich4 on 2011-02-03
I have installed libgl-mesa-dev but there was no libGL file in usr/lib, only in usr/lib/mesa. I thought that the linker would search subdirectories of usr/lib and maybe it does. But the only way I was able to make it work was by copying libGL.so out to usr/lib.

Would it be possible to edit the GL.conf file to specify the mesa folder or does that even make sense?

---

### Post by MadCow108 on 2011-02-03
which os version are you using?
maverick package has that link:
[http://packages.ubuntu.com/maverick/amd64/libgl1-mesa-dev/filelist](http://packages.ubuntu.com/maverick/amd64/libgl1-mesa-dev/filelist)

GL.conf is only for runtime and should not be changed manually, that is done by packages.
If one wants to change it then only using the update-alternatives command.

For compiling use the -L flag

---

