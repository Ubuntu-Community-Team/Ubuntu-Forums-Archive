---
title: "ELF file format question"
date: 2006-12-16
forum: Programming Talk
---

### Post by Wybiral on 2006-12-16
Hey, does anyone know enough about the ELF format to help me embed data into a file? Basically, I have a "stub" file that contains the program itself, and I want to attach data to it for the executable to read. Does the ELF format have a place to do this? Can it simply be attached to the end of the file? Or will that mess things up?

---

### Post by winch on 2006-12-17
Elf defiantly allows data sections as well as code. Since you are putting the data into a stub exe you will have to get your hands dirty and edit the elf yourself instead of relying on the linker to do it all for you.

Appending data is the easier approach, you can use simple file I/O functions to append the data and access it.
It shouldn't cause any problems as far as running the exe is concerned.
Problems can occur if the user modifies the exe. For instance running through strip or an exe compressor.
This has two potential problems.
1. The modifying program may truncate the appended data, obviously the exe will now not run.
2. The modifying program changes the size of the elf which changes the position the appended data starts. When the exe runs it jumps to the wrong position and doesn't get the data it expects. This can be solved by calculating the size of the elf at runtime instead of jumping to a hard coded position.

---

