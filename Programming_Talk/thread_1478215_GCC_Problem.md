---
title: "GCC Problem"
date: 2010-05-09
forum: Programming Talk
---

### Post by alfa_80 on 2010-05-09
Hi everybody,

I would like to ask you, what is actually the problem with my GCC  4.4.3.. I guess it's something to to with incorrect path, but i don't  how to reconfigure the path :sad: Could anyone help me resolving  this..I really need it to program something these days..huhu

Below is the error  i got and thanks in advance :smile:

```

shah@shah-laptop:~/Desktop/try$ g++ try.cpp trytry: In function `_start':
(.text+0x0): multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o:(.text+0x0): first defined here
try:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
try: In function `_fini':
(.fini+0x0): multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o:(.fini+0x0): first defined here
try:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
try: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o:(.data+0x0): first defined here
try: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.4.3/crtbegin.o:(.data+0x0): first defined here
try: In function `main':
(.text+0xb4): multiple definition of `main'
/tmp/cckdsFOY.o:try.cpp:(.text+0x0): first defined here
try: In function `_init':
(.init+0x0): multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o:(.init+0x0): first defined here
/usr/lib/gcc/i486-linux-gnu/4.4.3/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
try:(.dtors+0x4): first defined here
/usr/bin/ld: error in try(.eh_frame); no .eh_frame_hdr table will be created.
collect2: ld returned 1 exit status

```

---

### Post by Daniel0108 on 2010-05-09
Seems like you defined some functions more than once..
You defined two or more main functions. May you include a header which has a main function too.
Hope I helped you,
Daniel

---

### Post by alfa_80 on 2010-05-09
> **Daniel0108 said:**
> Seems like you defined some functions more than once..
You defined two or more main functions. May you include a header which has a main function too.
Hope I helped you,
Daniel

Thanks Daniel. But it's still unresolved..BTW, the try.cpp code is just a "hello world" code. Here is the code:
```

#include <iostream>                            


using namespace std;

int main()
{
    cout << "hello world" << endl;    

    return 0;
}


```

---

### Post by Compyx on 2010-05-09
> **alfa_80 said:**
> Thanks Daniel. But it's still unresolved..BTW, the try.cpp code is just a "hello world" code. Here is the code:
```

#include <iostream>                            


using namespace std;

int main()
{
    cout << "hello world" << endl;    

    return 0;
}


```

If that's the code you're compiling then I think the error is in the way you invoke the compiler.
One of these will do:
```

g++ try.cpp

```
or
```

g++ try.cpp -o try

```
The first method creates an executable with the default 'a.out' name, the second method specifies a user-defined name for the program ('try'). Both of those methods combine compiling with linking. Here's the compiling and linking phases separated:
```

g++ -c try.cpp
g++ try.o -o try

```
The first command compiling the source file 'try.cpp' into an object file 'try.o'.
The second command links the object file 'try.o' into an executable file 'try'.

I'm guessing you tried something similar but somehow specified try.o twice to the linker, resulting in a boatload of linker errors.

---

### Post by lisati on 2010-05-09
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1477860](http://ubuntuforums.org/showthread.php?t=1477860)

---

