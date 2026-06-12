---
title: "CodeBlocks and linking SDL"
date: 2012-11-08
forum: Programming Talk
---

### Post by Pendertuga on 2012-11-08
I'm having a hard time getting CodeBlocks to link SDL and it's libraries. There is no error in the code as I've compiled it on Windows but I can't seem to get the compile and links to work on Ubuntu. 
I've downloaded SDL through: apt-get install libsdl1.2-dev
as well as SDL Image through: apt-get install libsdl-image1.2-dev

Now my current settings for CodeBlocks are
Linker Settings >> Other linker options >> -lSDLmain -lSDL -lSDL_image

Search Directories >> Compiler >> /usr/include/SDL

When compiling I get:

-------------- Build: Debug in motion ---------------

Linking console executable: bin/Debug/motion
obj/Debug/main.o: file not recognized: File format not recognized
collect2: error: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings
 

Also: everytime I try to compile it prompts me as if I haven't attempted a compile before. 

Not sure what I'm doing wrong, would greatly appreciate some help c:

---

### Post by Pendertuga on 2012-11-08
SOLVED:

In case anyone else ends up having this error it is because of the main.o file in your debug folder.

This happened to me because I'm actually using a shared project with Windows through Google Drive. Deleting this file solves the problem and you should be able to compile successfully.

---

