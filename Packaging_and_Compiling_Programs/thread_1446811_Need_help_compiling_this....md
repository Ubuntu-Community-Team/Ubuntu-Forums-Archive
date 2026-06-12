---
title: "Need help compiling this..."
date: 2010-04-04
forum: Packaging and Compiling Programs
---

### Post by dirbaio on 2010-04-04
Could someone help me compile this: [http://www.woodmann.net/fravia/rpat-en.html](http://www.woodmann.net/fravia/rpat-en.html)?

I have followed the instructions there, but i had no luck. This is what I did:

I downloaded the binutils 2.20 source package, and then executed configure, make and sudo make install. The three commands completed without errors.

I edited that makefile and set the BFD_ROOT variable to the directory i just extracted and compiled binutils.

I ran make and i got this:

```

gcc -I /home/dario/Desktop/binutils-2.20 -I /home/dario/Desktop/binutils-2.20/bfd -I /home/dario/Desktop/binutils-2.20/include -I /home/dario/Desktop/binutils-2.20/binutils -c rpat.c
In file included from rpat.c:10:
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:36: error: expected declaration specifiers or ‘...’ before ‘va_list’
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:46: error: expected declaration specifiers or ‘...’ before ‘FILE’
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:48: error: expected declaration specifiers or ‘...’ before ‘FILE’
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:52: error: expected ‘)’ before ‘*’ token
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_file_size’
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:75: warning: parameter names (without types) in function declaration
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:77: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /home/dario/Desktop/binutils-2.20/include/demangle.h:33,
                 from rpat.c:13:
/home/dario/Desktop/binutils-2.20/include/libiberty.h:292: error: conflicting types for ‘xrealloc’
/home/dario/Desktop/binutils-2.20/binutils/bucomm.h:77: note: previous declaration of ‘xrealloc’ was here
rpat.c: In function ‘print_name’:
rpat.c:79: warning: incompatible implicit declaration of built-in function ‘strlen’
rpat.c:87: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c: In function ‘find_section’:
rpat.c:95: error: dereferencing pointer to incomplete type
rpat.c:95: error: dereferencing pointer to incomplete type
rpat.c:96: error: dereferencing pointer to incomplete type
rpat.c:96: error: dereferencing pointer to incomplete type
rpat.c: In function ‘apply_section’:
rpat.c:111: warning: incompatible implicit declaration of built-in function ‘malloc’
rpat.c:116: warning: passing argument 2 of ‘bfd_get_section_contents’ from incompatible pointer type
/home/dario/Desktop/binutils-2.20/bfd/bfd.h:1720: note: expected ‘struct asection *’ but argument is of type ‘struct sec *’
rpat.c:121: error: dereferencing pointer to incomplete type
rpat.c:121: error: dereferencing pointer to incomplete type
rpat.c:122: error: dereferencing pointer to incomplete type
rpat.c:122: error: dereferencing pointer to incomplete type
rpat.c:129: warning: incompatible implicit declaration of built-in function ‘malloc’
rpat.c:135: warning: passing argument 2 of ‘bfd_get_section_contents’ from incompatible pointer type
/home/dario/Desktop/binutils-2.20/bfd/bfd.h:1720: note: expected ‘struct asection *’ but argument is of type ‘struct sec *’
rpat.c: In function ‘free_reloc’:
rpat.c:147: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c: In function ‘kill_functions’:
rpat.c:168: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c: In function ‘kill_sections’:
rpat.c:183: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c: In function ‘insert_function’:
rpat.c:202: warning: incompatible implicit declaration of built-in function ‘malloc’
rpat.c: In function ‘add_reloc’:
rpat.c:240: warning: incompatible implicit declaration of built-in function ‘strdup’
rpat.c: In function ‘assign_sizes’:
rpat.c:297: error: dereferencing pointer to incomplete type
rpat.c: In function ‘process_file’:
rpat.c:352: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c:371: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c:378: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c:397: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘int’
rpat.c:403: warning: passing argument 3 of ‘apply_section’ from incompatible pointer type
rpat.c:105: note: expected ‘struct sec *’ but argument is of type ‘struct bfd_section *’
rpat.c:429: warning: passing argument 2 of ‘find_section’ from incompatible pointer type
rpat.c:91: note: expected ‘struct sec *’ but argument is of type ‘struct asection *’
rpat.c:438: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c:460: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c:468: error: dereferencing pointer to incomplete type
rpat.c:468: error: dereferencing pointer to incomplete type
rpat.c:469: error: dereferencing pointer to incomplete type
rpat.c:494: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘bfd_vma’
rpat.c:494: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 5 has type ‘flagword’
rpat.c:494: warning: format ‘%0lx’ expects type ‘long unsigned int’, but argument 6 has type ‘int’
rpat.c:500: warning: format ‘%0lx’ expects type ‘long unsigned int’, but argument 4 has type ‘int’
rpat.c:500: warning: format ‘%0lx’ expects type ‘long unsigned int’, but argument 5 has type ‘int’
rpat.c:608: warning: incompatible implicit declaration of built-in function ‘free’
rpat.c: In function ‘process_filez’:
rpat.c:624: error: ‘true’ undeclared (first use in this function)
rpat.c:624: error: (Each undeclared identifier is reported only once
rpat.c:624: error: for each function it appears in.)
rpat.c: In function ‘usage’:
rpat.c:676: warning: incompatible implicit declaration of built-in function ‘exit’
rpat.c: In function ‘main’:
rpat.c:742: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [rpat.o] Error 1

```

I also tried compiling older versions of binutils (2.9 and 2.9.1 because the webpage says it works with those) to see if they were compatible with rpat.c but no luck... they don't want to compile.

So, rpat is not compatible with newer binutils, but older binutils are not compatible with my ubuntu (9.10)

What can I do?
I really need to compile that...
Thanks in advance.

---

### Post by Compyx on 2010-04-04
You really shouldn't have compiled and installed binutils from source on your system, it is likely to break a few things. What you should do is install the package 'binutils-dev'.
```

sudo apt-get install binutils-dev

```
That should pull in the headers required for building stuff against binutils and keep your system clean.

You should only install packages from source if you have a good reason to do so. And some website instructing you to install binutils from source just to build some of their code is not a good reason. The *-dev packages are there for that.

But you do realize that the code is 10 years old and horribly written?

---

