---
title: "compiling and linking multiple files using gcc"
date: 2011-03-13
forum: Programming Talk
---

### Post by masali on 2011-03-13
Hi,
I have a question about compiling and linking using gcc:

What does a file name with a suffix '.a' represent?

If I have multiple .c and .h files, how can I link them together?
How can I create the .a file?

The articles I read were broad and ddnt target the above questions.

Thanks.

---

### Post by wmcbrine on 2011-03-13
.a is a static library. You can create them (from .o object files) with the "ar" command.

If you're building an executable from source (.c), you probably don't want to build a library as an intermediate step, although you could do it that way. Just build each module:

gcc -c foo.c
gcc -c bar.c

then link:

gcc -o foobar foo.o bar.o

Generally this sort of thing is the domain of makefiles. It can get very complicated.

---

### Post by masali on 2011-03-13
Thank you.problem solved.

---

### Post by Vox754 on 2011-03-13
> **masali said:**
> Hi,
I have a question about compiling and linking using gcc:

What does a file name with a suffix '.a' represent?

If I have multiple .c and .h files, how can I link them together?
How can I create the .a file?

The articles I read were broad and ddnt target the above questions.

Thanks.

A longer explanation.

A file with a suffix ".a" is usually an "archive" of object files, which is used as a "statically linked library". That is, when you link it with your program, all of the code of the defined functions is included in the final executable. This is different from linking your program to an external "shared library". There are references to the external functions, but their code is not actually included in the final executable.

If you have several files with source code ".c", you can compile them together, or you can do it in intermediate steps by creating first the object files ".o", and then linking them together to produce the final executable.
```

gcc source_1.c source_2.c source_3.c -o final

```

```

gcc -c source_1.c
gcc -c source_2.c
gcc -c source_3.c

gcc source_1.o source_2.o source_3.o -o final

```

By the way, header files ".h" are not compiled. Or well, sort of. They are included by ".c" files to inform the compiler about functions. Once the compiler has cross-referenced everything, their information is essentially discarded, and does not affect the final executable size.

How do you create the archive? Normally you'd use a very simple archiving program, which in Linux is "ar". This is sort of like "tar", or "zip", but without the compression and other stuff.

Normally, there is no need to create an archive for your own code, unless you are explicitly writing reusable code, in which case it does make sense to have all these functions inside either a shared library or a statically linked library.

To create a shared library, you need to compile the object files as "position-independent code" or PIC.
```

gcc -fPIC -c source_1.c source_2.c
gcc -shared -o libtest.so source_1.o source_2.o

```

Then you can use the shared library like any other shared library. Provided it is in the correct directory:
```

gcc main.c -ltest -o final

```

To create a statically linked library, archive your object files, and use the resulting file with your main file.
```

gcc -c source_1.c
gcc -c source_2.c

ar -cvq libtest.a source_1.o source_2.o

gcc main.c libtest.a -o final

```

Or also
```

gcc main.c -ltest -o final

```

Note that the flag "-ltest" loads a library called "libtest.so" or "libtest.a". Some projects provide both a shared library and a statically linked library. It depends on the user to decide if he or she wants to use one or the other.

More info: [http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html](http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html)

Watch out for old sources, but this one seems good enough.

---

