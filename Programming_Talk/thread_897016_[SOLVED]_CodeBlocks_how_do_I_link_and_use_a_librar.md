---
title: "[SOLVED] CodeBlocks: how do I link and use a library?"
date: 2008-08-21
forum: Programming Talk
---

### Post by JohnnyBoy022 on 2008-08-21
I made a new "static library" project in CodeBlocks. It contained two files: storage.h, and storage.cpp. I compiled the project just fine.

I created a new project to use this library with, went to the build options, went to linker settings, went to add link libraries, and selected libStorage.a I included "storage.h" in the main file of my new project that I want to use the library with. When I try to compile and run my new project I receive the error message "storage.h": No such file or directory.

I don't understand why this isn't working. The library compiled, and I added it to the linker for my new project. Is there something I am missing? Any help is greatly appreciated!

*edit* Also if anyone doesn't know the answer specifically for CodeBlocks, if you could let my know of some more information about how linking works, or what I might be doing wrong, thanks

---

### Post by JohnnyBoy022 on 2008-08-21
Bump

---

### Post by JohnnyBoy022 on 2008-08-21
Alright well I figured it out.

I didn't realize you had to let the compiler know the location of the header files when using a library, I thought they were included in the library.

* SOLVED *

---

