---
title: "[C] Linking shared library"
date: 2012-01-08
forum: Programming Talk
---

### Post by MG&amp;TL on 2012-01-08
I have a project in C, that I'd like to compile into a shared library.

Currently, I only have one file to compile/link, but that's going to expand shortly. So, here's the build process:

```
gcc -Wall -c -fPIC mylib.c
ld -shared -soname libmylib.so.1 -o libmylib.so.1.0 -lc libmylib.o
```

(I'm following [_this_]("http://www.ibm.com/developerworks/library/l-shobj/") tutorial, if it helps.)

problem:

```

<snip *clean, no errors* gcc compile>


mylib.c:(.text+0xa3): undefined reference to `__stack_chk_fail_local'
ld: libmylib.so.1.0: hidden symbol `__stack_chk_fail_local' isn't defined
ld: final link failed: Bad value
make: *** [link] Error 1
```

Any ideas? I'm not doing anything especially messy with the code, and I'm definitely not exporting, using, defining, or linking to (in my knowledge) __stack_chk_fail_local. All I can find on the web is some stuff about setting that flag on gcc, back around feisty, apparently. My code only links to stdio.h

Any ideas greatly appreciated, particularly as I have no idea what's happening, even that that existed.

PS It's not actually called mylib, but if I put the real name you'd all laugh at me. :P

---

### Post by Bachstelze on 2012-01-08
It works fine here; paste your code.

---

### Post by MG&amp;TL on 2012-01-08
I don't have the machine at present; but it's running 11.10, and here's the (approximate) code:

```

#include <stdio.h>

void BadFormatException(char subMsg[]) {
    char[50] stdMsg = "BMICS: Caught bad format exception:";
    printf("%s\n", stdMsg);
    printf("%s\n", subMsg);
}
```

I'm just echoing somebody else's code ('translating' C from Java.)

---

### Post by MadCow108 on 2012-01-08
you probably need to link against libgcc too.
but why are you using ld for this?
you should prefer gcc.
```
gcc -shared -Wl,-soname,libmylib.so.1 -o libmylib.so.1.0 libmylib.o -lc
```

that will link with all required low level libraries for you

if that does not work, make sure -lc is behind the object files on the commandline.

---

### Post by MG&amp;TL on 2012-01-09
> **MadCow108 said:**
> you probably need to link against libgcc too.
but why are you using ld for this?
you should prefer gcc.
```
gcc -shared -Wl,-soname,libmylib.so.1 -o libmylib.so.1.0 libmylib.o -lc
```

that will link with all required low level libraries for you

if that does not work, make sure -lc is behind the object files on the commandline.

Thanks, madcow & bachstelze, that did it!

Can I find an ebook around that will explain this? I am a little confused...

---

