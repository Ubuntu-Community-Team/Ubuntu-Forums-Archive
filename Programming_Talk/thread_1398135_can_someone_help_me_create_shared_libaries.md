---
title: "can someone help me create shared libaries"
date: 2010-02-04
forum: Programming Talk
---

### Post by mikejonesey on 2010-02-04
I have built dll's before but never .so (never needed to, but now i need to),

can someone confirm my logic:

I can build my wxfb project in c:b (with the -fPIC compile option),

I can then build the object object file into a shared libary (.so file) using;

```
gcc -shared -Wl,-soname, -o libMyChosenLibName.so  MyObjectBuiltFromCodeBlocks.o
```

thanks for any help.

mike

---

### Post by dwhitney67 on 2010-02-04
That's how it is done.  You compile each module with the -fPIC (Position Independent Code) option.  Then when you link, the -shared is used to indicate that you are creating a shared library.  I forget exactly what the -W1,soname are for, but I know they are optional.

The rest of the puzzle involves actually writing a test program that utilizes the library.

If you do not install your shared-object library in /usr/lib (or /usr/local/lib), then you will need to augment your LD_LIBRARY_PATH environment variable before you can attempt to run your program.

P.S.  There are other ways to make libraries available which are not in /usr/lib or /usr/local/lib.  This involves dealing with ldconfig.

P.S.  #2 To my disappointment, the Mac does not use shared-object libraries in the way Linux/Unix do.

---

### Post by mikejonesey on 2010-02-04
excelent thanks

---

