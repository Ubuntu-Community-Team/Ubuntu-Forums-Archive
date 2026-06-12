---
title: "error: gtk/gtk.h: No such file or directory"
date: 2009-10-08
forum: Programming Talk
---

### Post by kboy on 2009-10-08
Hello, I've tried to compile a simple gtk+ program, using "code blocks", I always get the error:gtk/gtk.h: No such file or directory.
I installed the "libgtk2.0-dev" package, but still the problem continues,

need help
thanks.

---

### Post by dwhitney67 on 2009-10-08
You need to specify to the compiler where it can find the gtk directory that contains gtk.h.

Something like:
```

g++ -I/usr/include/gtk-2.0 MySource.cpp

# or

gcc -I/usr/include/gtk-2.0 MySource.c

```
I haven't a clue how to use code-blocks, much less any desire to.  So you will need to investigate on your own how to specify additional header file paths.  If the gtk-2.0 libraries are not in /usr/lib, then you will also need to specify the path where these are located at.  From the command line, the "-L" option is used to specify the path, and the "-l" (lowercase ell) is used to specify the library.

---

### Post by snova on 2009-10-08
Add the **/usr/include/gtk-2.0** directory to the include search when compiling (Code::Blocks should have a place to put this somewhere).

On the command line, it would be done like this:

```
gcc -c -o program.o program.c -I/usr/include/gtk-2.0
```

---

### Post by myromance123 on 2009-10-09
This may be silly of me but are you selecting GTK+ project from the new project menu?

 I haven't had to install anything but I am able to compile straight away the gtk+ application from codeblocks (the example they provide on choosing gtk+ project).
 Have you tried this? If this works it could be a mistype you made?
Sorry if this doesn't help.

---

