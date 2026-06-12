---
title: "gcc compiling help (windows.h)"
date: 2008-02-16
forum: Programming Talk
---

### Post by wnaBsd8d on 2008-02-16
hi everyone...

i just need to know how to compile c source code in ubuntu FOR a windows machine

lets clarify ..i do NOT want to run the compiled program on linux....i just want to compile it in linux then be able to run it on windows?

when i try and run gcc file.c -o file

i get a few errors saying things are not declared and windows.h is no such file or directory ...

any ideas?

thanks in advance

ps: build essentials are installed

---

### Post by amingv on 2008-02-16
windows.h is a windows only library as far as I know. You should compile it in a windows machine or a VM running windows at the least.

Even if you could successfully compile it, you'd get a linux binary, with no use in windows.

---

### Post by LaRoza on 2008-02-16
You can use Dev-C++ in Wine to compile it. It will be a Windows executable.

This works at least: [http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable)

---

### Post by wnaBsd8d on 2008-02-16
ill give it a go ..thanks for the replies

---

### Post by public_void on 2008-02-16
Maybe have a look at the mingw32 cross compiler.

---

### Post by MarkieB on 2008-08-14
no longer participating in ubuntuforums.org

---

