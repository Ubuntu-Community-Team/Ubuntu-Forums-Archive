---
title: "Problem running program with a shared library I created"
date: 2007-10-06
forum: Programming Talk
---

### Post by foo-bar on 2007-10-06
Hello there,

I've created a simple 2D game engine using SDL, and it all builds fine into a shared library file 'libsdlboo.so'.  Now, I am trying to make a test / example program using this library, and it builds fine (and links fine to the library I have created).  The problem is that when I attempt to run the program, it says the following:

> ./sdlboo_pong: error while loading shared libraries: libsdlboo.so: cannot open shared object file: No such file or directory


The file is in the same directory as the executable, and the permissions look fine to me.

Any help would be appreciated.

Thanks,
Anthony

---

### Post by dwhitney67 on 2007-10-06
Try fidgeting with the LD_LIBRARY_PATH.  In other words, try setting it to the location where your shared-library resides.

If that doesn't work, then add an entry to /etc/ld.so.conf or create a file (with a .conf extension) within /etc/ld.so.conf.d that contains the path to your library.

Do you have other applications that will use this shared library?  If not, then why are you using a shared library?  Consider statically linking the library to your application.

---

