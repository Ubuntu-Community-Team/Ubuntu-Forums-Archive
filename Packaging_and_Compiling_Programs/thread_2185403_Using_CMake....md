---
title: "Using CMake..."
date: 2013-11-02
forum: Packaging and Compiling Programs
---

### Post by Jamie_Edwards on 2013-11-02
Hi guys,

I haven't got a clue with what to do with CMake.

Could anyone help by making an easy to adapt "template"?

I have the following workspace structure at the moment:

```

ceros /
         bin/
         docs/
         include/
         iso/
         src/
              arch/
                     boot/ 
                            boot.s # using nasm syntax
                     init/
                          main.c
                     obj/
                     utils/
                            ld/
                               linker.ld

```

I'd like to have a CMakeList.txt where it only looks in:
1. src/arch/boot/
2. src/arch/init/
3. src/obj/
4. src/utils/ld/
5. bin/
6. include/

Of those directories, 
I need 1 & 2 to be compiled.
3 is where I'd like the object files to be stored,
4 has the linker script I want to use to link everything together
5 is where I'd like the final binary ( named "kernel" )
6 is where I'll be storing the header files of my kernel.

If you could put comments telling me what is being done and if possible how I could add more directories/languages to the file(s) that would be amazing!

Thanks in advance.

Jamie.

---

### Post by Jamie_Edwards on 2013-11-03
bump

---

