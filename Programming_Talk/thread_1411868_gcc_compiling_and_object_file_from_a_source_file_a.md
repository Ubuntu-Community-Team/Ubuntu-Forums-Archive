---
title: "gcc: compiling and object file from a source file and a static library"
date: 2010-02-20
forum: Programming Talk
---

### Post by cybo on 2010-02-20
i used gcc before but everything i have done so far was very simple compilation. please forgive my inexperience i'm still learning, i bet this is easy to do.

here is the problem.

i need to make an object file from a .c file, the .c file uses a static library (.a file). is that even possible?

so i need to do something like:

gcc -o cfile.o cfile.c mylib.a

can anyone help?

---

### Post by SledgeHammer_999 on 2010-02-20
Your question is if you can link a static lib with gcc? If yes, then yes you can. You need to have the appropriate header included in your .c file and then point the linker to the appropriate location where the static lib lies.(gcc invokes the linker for you, unless told otherwise).

---

### Post by gmargo on 2010-02-20
From the gcc man page, the -static option:

 -static
           On systems that support dynamic linking, this prevents linking with the shared libraries.  On other systems, this option has no effect.

But that's entirely static.  What you said above (gcc -o cfile.o cfile.c mylib.a) should work.

---

### Post by dwhitney67 on 2010-02-20
> **gmargo said:**
> From the gcc man page, the -static option:

 -static
           On systems that support dynamic linking, this prevents linking with the shared libraries.  On other systems, this option has no effect.

But that's entirely static.  What you said above (gcc -o cfile.o cfile.c mylib.a) should work.

Actually, the OP appears to have no idea what he wants.

First of all, when generating an object file, that is a .o, no linking takes place; thus the library file is not needed.

If linking, then yes the library specification is required, but not in the form the OP has used.

In compu-speak....


For generating an object file:
```

gcc -c cfile.c

```

For linking with a static library, where possibly a shared object library with a similar name exists:
```

gcc cfile.o -static -lmylib -o myapp

```

Combining all into one statement, thus skipping the generation of the object file:
```

gcc cfile.c -static -lmylib -o myapp

```

If a shared-object library (eg. libmylib.so) does not exist, then the -static portion of the command can be dropped.

Lastly, if the libmylib.a is not within the same directory as the cfile.c, or within a path that can be determined using the 'gcc -print-search-dirs' command, then the -L option will need to be used to specify the location of the OP's proprietary library.  For example:
```

gcc cfile.c -L/home/OP/lib -lmylib -o myapp

```


P.S.  The OP may need to do something similar to the following to run the application:
```

LD_LIBRARY_PATH=/home/OP/lib ./myapp

```

---

### Post by cybo on 2010-02-25
thanks everybody. your suggestions helped.

---

