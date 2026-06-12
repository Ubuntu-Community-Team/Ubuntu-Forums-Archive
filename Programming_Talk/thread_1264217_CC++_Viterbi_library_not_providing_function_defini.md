---
title: "C/C++: Viterbi library not providing function definitions?"
date: 2009-09-11
forum: Programming Talk
---

### Post by creekmax on 2009-09-11
Hi All,

I've been fussing over a library problem for most of the day, have searched forums, etc. and have not found anything helpful.  I'm working with the SIMD Viterbi Decoder library from [http://freshmeat.net/projects/simd-viterbi/](http://freshmeat.net/projects/simd-viterbi/).  Here's a little program that should do little more than verify the existence of the library:

[php]
#include "viterbi27.h"

using namespace std;

int main()
{
    void *v_ptr;
    int status;

    v_ptr = create_viterbi27(240);
    status = init_viterbi27(v_ptr, 0);
    delete_viterbi27(v_ptr);

    return(0);
}
[/php]My attempt to compile the program results in the following:
```
>> g++ -g -Wall -o viterbi -lviterbi main.cpp
/tmp/ccwC05Gs.o: In function `main':
/home/creekmax/sandbox/viterbi/main.cpp:11: undefined reference to `create_viterbi27(int)'
/home/creekmax/sandbox/viterbi/main.cpp:12: undefined reference to `init_viterbi27(void*, int)'
/home/creekmax/sandbox/viterbi/main.cpp:13: undefined reference to `delete_viterbi27(void*)'
collect2: ld returned 1 exit status
```All three library functions are not defined.  As you can see, there's no error regarding the header file, and there's no error regarding the "viterbi" library that I specified.  I'm not a career programmer, but as far as I know, this means that the compiler found both the header file and the library, found the function prototypes in the header file, but did not find definitions for the funcitons in the library.

Why wouldn't these functions be in the library?

When I build the library's source code, I see the proper source files being compiled and included:
```
>> make
gcc -c -g -O2 -I. -Wall -march=i686 -DSSE2=1 -o viterbi27sse2.o viterbi27.c
as   -o sse2bfly27.o sse2bfly27.s
gcc -c -g -O2 -I. -Wall -march=i686 -DSSE2=1 -o viterbi29sse2.o viterbi29.c
as   -o sse2bfly29.o sse2bfly29.s
as   -o cpu_features.o cpu_features.s
ar rv libviterbi_sse2.a viterbi27sse2.o sse2bfly27.o viterbi29sse2.o sse2bfly29.o cpu_features.o
ar: creating libviterbi_sse2.a
a - viterbi27sse2.o
a - sse2bfly27.o
a - viterbi29sse2.o
a - sse2bfly29.o
a - cpu_features.o
gcc -shared -Xlinker -soname=libviterbi.so.2 -o libviterbi.so.2.0.1 -Wl,-whole-archive libviterbi_sse2.a -Wl,-no-whole-archive -lc

```(NOTE: Yes, this output says the library name is "libviterbi_sse2.a", but the installation process creates a symbolic link to the library with the name "libviterbi.a".  I've tried linking to each.)

I've examined viterbi27.c, and it does define the functions I'm calling.  I've also searched my file system, and there are no other instances of these file names; I'm fairly certain the compiler is linking to the correct library.

I'm at a loss.  Any ideas?

Thanks.

---

### Post by lensman3 on 2009-09-11
It looks like the lib is not in a standard place.  If you do a "locate lib...."  is the viterbi library where you think it is.  (I think) if you at -L /location/of/vertlib/library/directory", the linker will search the directory for "libviterbi".

Hope this helps.

---

### Post by creekmax on 2009-09-12
I'm afraid not.  Besides, if the compiler/linker couldn't find the library, it would return an error indicating that.  For example, if I change -lviterbi to -lfoo, g++ says, "/usr/bin/ld: cannot find -lfoo".

---

### Post by jpkotta on 2009-09-12
OK, this library was not written for 64-bit machines, but I got it compiled anyway.  I got the same results as you with g++, but it built fine with gcc (but still crashes when I run it).  Anyway, maybe it's name-mangling?

```

$ objdump -t viterbi.o                                                                                                                                                         

viterbi.o:     file format elf64-x86-64

SYMBOL TABLE:
0000000000000000 l    df *ABS*  0000000000000000 main.c
0000000000000000 l    d  .text  0000000000000000 .text
0000000000000000 l    d  .data  0000000000000000 .data
0000000000000000 l    d  .bss   0000000000000000 .bss
0000000000000000 l    d  .debug_abbrev  0000000000000000 .debug_abbrev
0000000000000000 l    d  .debug_info    0000000000000000 .debug_info
0000000000000000 l    d  .debug_line    0000000000000000 .debug_line
0000000000000000 l    d  .debug_frame   0000000000000000 .debug_frame
0000000000000000 l    d  .eh_frame      0000000000000000 .eh_frame
0000000000000000 l    d  .debug_loc     0000000000000000 .debug_loc
0000000000000000 l    d  .debug_pubnames        0000000000000000 .debug_pubnames
0000000000000000 l    d  .debug_aranges 0000000000000000 .debug_aranges
0000000000000000 l    d  .debug_str     0000000000000000 .debug_str
0000000000000000 l    d  .note.GNU-stack        0000000000000000 .note.GNU-stack
0000000000000000 l    d  .comment       0000000000000000 .comment
0000000000000000 g     F .text  0000000000000037 main
0000000000000000         *UND*  0000000000000000 _Z16create_viterbi27i
0000000000000000         *UND*  0000000000000000 _Z14init_viterbi27Pvi
0000000000000000         *UND*  0000000000000000 _Z16delete_viterbi27Pv
0000000000000000         *UND*  0000000000000000 __gxx_personality_v0

```

---

### Post by jpkotta on 2009-09-12
Yep, a quick search provides the answer:
```

extern "C" {
#include "viterbi27.h"
}

```

I've often seen this wrapped in an #ifndef, now I know what it actually does.

---

### Post by creekmax on 2009-09-12
That did it.  Thanks!

For future onlookers who may not be familiar with name mangling, as I was not until just now, here's what happened:

First, go look at the Wikipedia article on name mangling.  This library is written in C and compiles with gcc.  I, on the other hand, was writing a program in C++ and compiling with g++.  While C++ is mostly backwards compatible with C, because of name mangling the function names generated by my compiler did not match the function names in the viterbi library, so g++ said, "I can't find these function definitions."

jpkotta's extern "C" statement tells the compiler not to mangle the function names declared inside the brackets because they were written in the C language.  If the library header file had encapsuled its contents with a preprocessor directive like this:

```
#ifdef __cplusplus
extern "C" {
#endif

.
.
.

#ifdef __cplusplus
}
#endif
```then the library would have already been suitable for both C and C++ programs.

---

