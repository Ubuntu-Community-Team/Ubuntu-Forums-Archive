---
title: "compile for x86 in my x86-64 distribution"
date: 2010-02-22
forum: Programming Talk
---

### Post by Vichfret on 2010-02-22
I need to compile my C source code to run in standard x86 machines but I have a very specific configuration in the distribution I use (I use USE flags, and march=native, etc) how do I compile a binary file for other architectures and maybe for windows?

---

### Post by ssam on 2010-02-22
you can use the gcc flag '-m32' to make a 32 bit binary. you will need to set march to the lowest CPU that you want to run it on (though you can mtune set to something higher). see [http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options](http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options)


most make files will let you do
```

make CFLAGS="-m32 -march=i686"
```

---

