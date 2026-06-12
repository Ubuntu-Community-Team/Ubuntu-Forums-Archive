---
title: "GCC does not work anymore after upgrading to ubuntu 10.04"
date: 2010-05-08
forum: Programming Talk
---

### Post by alfa_80 on 2010-05-08
Hi everybody,

I would like to ask you, what is actually the problem with my GCC 4.4.3.. I guess it's something to to with incorrect path, but i don't how to reconfigure the path :-( Could anyone help me resolving this..I really need it to program something these days..huhu

Below is the error  i got and thanks in advance :-)

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
```

shah@shah-laptop:~/Desktop/try$ gcc --version
gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by HermanAB on 2010-05-08
Install the kernel source, compile and install it.  After that, GCC is guaranteed to work.

---

### Post by alfa_80 on 2010-05-09
I don't think so guy because when I saw in my synaptic manager, the linux-image-386 is already checked. And as an ubuntu beginner like me, i'm afraid to try to compile it myself as the following link suggested: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

What to do, anyone has any ideas?

-alfa-

---

### Post by alfa_80 on 2010-05-09
It's weird after upgrading ubuntu 9.10 to 10.04. My gcc doesn't work any longer and i don't know where to tweak after several attempts. Help me please. The error is as follows:

```


shah@shah-laptop:~/Desktop/try$ g++ try.cpp try
try: In function `_start':
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
/tmp/ccKMYRPA.o:try.cpp:(.text+0x0): first defined here
try: In function `_init':
(.init+0x0): multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o:(.init+0x0): first defined here
/usr/lib/gcc/i486-linux-gnu/4.4.3/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
try:(.dtors+0x4): first defined here
/usr/bin/ld: error in try(.eh_frame); no .eh_frame_hdr table will be created.
collect2: ld returned 1 exit status



```

---

### Post by GregBrannon on 2010-05-09
How do you know that the code, try.cpp, isn't the problem?

Rather than starting a new thread, you could have bumped the original one or given it more time.  This question may also receive a better response in the Programming Talk forum.

Welcome to the forums and good luck!

---

### Post by lisati on 2010-05-09
Threads merged.

---

### Post by alfa_80 on 2010-05-09
> **GregBrannon said:**
> How do you know that the code, try.cpp, isn't the problem?

Rather than starting a new thread, you could have bumped the original one or given it more time.  This question may also receive a better response in the Programming Talk forum.

Welcome to the forums and good luck!


try.cpp is just a hello world. Here is the code:
```

#include <iostream>                            


using namespace std;

int main()
{
    cout << "hello world" << endl;    

    return 0;
}



```


Thanks in advance..

---

### Post by alfa_80 on 2010-05-09
Thanks a lot [Compyx..]("http://ubuntuforums.org/member.php?u=76398")

Definitely, i'm too careless of the missing -o. It's resolved already :-)

Again thanks everybody especially Compyx..

-alfa_80-

---

