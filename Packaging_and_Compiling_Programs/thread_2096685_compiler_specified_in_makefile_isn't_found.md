---
title: "compiler specified in makefile isn't found"
date: 2012-12-20
forum: Packaging and Compiling Programs
---

### Post by aPtRook on 2012-12-20
I'm going through homebrew GBA development and trying to compile some example roms using a makefile that specifies the compiler to be used (which is special, i.e. - not regular gcc). The compiler is called 'arm-none-eabi-gcc' and lives in

```
/opt/devkitpro/devkitARM/bin/
```

The makefile used to compile the source uses this line to specify where to find it.

```
PATH := /opt/devkitpro/devkitARM/bin:$(PATH)
```

The compiler very clearly exists in the specified location and everything is spelled correctly, yet when I run make, I get the following error:

```
make[1]: arm-none-eabi-gcc: Command not found
make[1]: *** [template.o] Error 127
make: *** [build] Error 2 
```

Where 'template.o' refers to the name of the source. I can compile and run regular c programs just fine, but this just can't be found. Any advice would be great, and if you need anything else to help you sniff out the problem, I'll post it as quickly as I can.

Thanks in advance.

---

### Post by MadCow108 on 2012-12-21
I doubt that will work:
```
PATH := /opt/devkitpro/devkitARM/bin:$(PATH)
```

PATH in a makefile is likely just a normal variable and nothing special. make is not a shell.

you normally have a CC variable which defines the compiler, e.g.:
```
CC ?= /opt/devkitpro/devkitARM/bin/arm-none-eabi-gcc
```

this CC is then used to compile everything or passed to submakes

you can also set PATH in the shell before you call make

---

