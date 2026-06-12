---
title: "Decompilation of a DOS C program"
date: 2013-04-07
forum: Programming Talk
---

### Post by createdcreature on 2013-04-07
Hi, I need a good decompiler for a 16-bit command-line program written in C/assembly language, and written for MS-DOS (it is not a .com, it is a .exe). The decompiler can run on 32 or 64 bit, any Linux distro, or any version of Windows (not a Mac), CLI or GUI (preferably GUI), closed source or open source, I don't care. The code will be recompiled again. I am doing this because I want the program compiled for 32/64 bit, as 16-bit can only run on 64 bit with an emulator such as DOSbox, which is a nightmare to use on an everyday basis. Don't worry, I have permission to decompile the program, and the whole operation will be fully legal. Thanks!

---

### Post by conradin on 2013-04-07
Softice prolly the best there is. (windows)
I bet there is something good in gnu for a decompiler. GDB perhaps?

---

### Post by trent.josephsen on 2013-04-07
> **conradin said:**
> I bet there is something good in gnu for a decompiler. GDB perhaps?

GDB doesn't decompile, no; at least I'm not aware of any such feature. I guess it does disassemble after a fashion, but I've always used objdump for that and I don't even know if objdump can handle PEs.

[Here is a list of decompilers](http://www.backerstreet.com/decompiler/decompilers.htm) made by the author of REC Studio. I've never used any of these, link provided only for informational purposes. Good luck.

---

