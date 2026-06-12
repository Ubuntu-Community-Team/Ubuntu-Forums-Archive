---
title: "win32 compiles on Ubuntu 64 bit"
date: 2012-02-09
forum: Programming Talk
---

### Post by lucasart on 2012-02-09
I've installes mingw-w64 and can compile for win64 w/o any issues my code. But when I try the -m32 switch, I get a ton of errors that don't make any sense. Is it a known bug of the package ? (which is supposed to allow win32 compiles according to what synaptic says) Is there anything else to install for that to work ?
```

lucas@lucas-desktop:~/Chess/DC254$ x86_64-w64-mingw32-gcc -o ./DC254_win32 -std=c99 -DNDEBUG -Wall -O3 -flto -m32 ./src/*.c
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/libgcc.a when searching for -lgcc
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/libgcc.a when searching for -lgcc
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/libgcc.a when searching for -lgcc
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lgcc
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libadvapi32.a when searching for -ladvapi32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libadvapi32.a when searching for -ladvapi32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libadvapi32.a when searching for -ladvapi32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libadvapi32.a when searching for -ladvapi32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libadvapi32.a when searching for -ladvapi32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libadvapi32.a when searching for -ladvapi32
/usr/bin/x86_64-w64-mingw32-ld: cannot find -ladvapi32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libshell32.a when searching for -lshell32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libshell32.a when searching for -lshell32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libshell32.a when searching for -lshell32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libshell32.a when searching for -lshell32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libshell32.a when searching for -lshell32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libshell32.a when searching for -lshell32
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lshell32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libuser32.a when searching for -luser32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libuser32.a when searching for -luser32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libuser32.a when searching for -luser32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libuser32.a when searching for -luser32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libuser32.a when searching for -luser32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libuser32.a when searching for -luser32
/usr/bin/x86_64-w64-mingw32-ld: cannot find -luser32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libkernel32.a when searching for -lkernel32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libkernel32.a when searching for -lkernel32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libkernel32.a when searching for -lkernel32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libkernel32.a when searching for -lkernel32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libkernel32.a when searching for -lkernel32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libkernel32.a when searching for -lkernel32
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lkernel32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingw32.a when searching for -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmingw32
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/libgcc.a when searching for -lgcc
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/libgcc.a when searching for -lgcc
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/libgcc.a when searching for -lgcc
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lgcc
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmoldname.a when searching for -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmoldname
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmingwex.a when searching for -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmingwex
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/lib/gcc/x86_64-w64-mingw32/4.6.1/../../../../x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: skipping incompatible /usr/x86_64-w64-mingw32/lib/libmsvcrt.a when searching for -lmsvcrt
/usr/bin/x86_64-w64-mingw32-ld: cannot find -lmsvcrt
collect2: ld returned 1 exit status

```

---

### Post by epicoder on 2012-02-09
The errors you are seeing are the compiler looking for 32-bit libraries, and skipping over the 64-bit ones you have installed. Try installing the package mingw32.

---

### Post by lucasart on 2012-02-09
> **sh228 said:**
> The errors you are seeing are the compiler looking for 32-bit libraries, and skipping over the 64-bit ones you have installed. Try installing the package mingw32.
installing mingw32 removes mingw64, which is exactly what I don't want. I need to compile my code for win32 and win64 (as well as linux 64).
according to the description of the package mingw-w64 it is supposed to be capable of doing 32 bit compiles, which is also what the --help says...

---

### Post by epicoder on 2012-02-09
[FONT=Verdana]Looking through the list of files that mingw-w64 includes, it does seem to have those libraries. However, it seems to be searching the wrong directories for them.
Try including these options on the compile line, before the source file that you're compiling: 
[/FONT]
-L/usr/i686-w64-mingw32/lib[FONT=Verdana] -I[/FONT]/usr/i686-w64-mingw32/include[FONT=Verdana]

That's a capital L and I respectively, case matters.
This should tell the compiler to search [/FONT]/usr/i686-w64-mingw32/lib[FONT=Verdana] for libraries and /[/FONT]usr/i686-w64-mingw32/include for header files.

Using the same options as your first compile, the executed line should look somewhat like this:
```
x86_64-w64-mingw32-gcc -o ./DC254_win32 -std=c99 -DNDEBUG -Wall -O3 -flto -m32 -L/usr/i686-w64-mingw32/lib -I/usr/i686-w64-mingw32/include ./src/*.c
```

---

