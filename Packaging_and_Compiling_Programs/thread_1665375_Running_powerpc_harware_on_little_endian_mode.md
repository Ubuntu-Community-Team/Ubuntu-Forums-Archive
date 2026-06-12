---
title: "Running powerpc harware on little endian mode"
date: 2011-01-12
forum: Packaging and Compiling Programs
---

### Post by subarajan on 2011-01-12
Hai,
I have compiled the boot code(where it changes the default big endian mode to little endian mode) using bigendian gcc and rest of the code using the little endian gcc(mixed mode). The code is working fine,i.e we can view disassembly of the code and execution of the code is as expected. But the source level debugging is not possible, Can anyone help me in getting the source debugging possible. :cry:

While loading the image file in gdb, it is showing an error that:
Dwarf Error: wrong version in compilation unit header (is 512, should be 2)
It seems that the header of the image file created using powerpclittle-elf-gcc is wrong, should I include any other options??? please help me.....


Regards,
Suba

---

