---
title: "How to cross-compile for windows?"
date: 2009-04-28
forum: Programming Talk
---

### Post by The Cog on 2009-04-28
I have a very simple .c source (150 lines) that I want to cross-compile for windows, to a .exe. I have installed pacakge mingw32 from the repositories. But I have no idea what arguments to give to gcc. It compiles to a Linux executable and works with **gcc -Wall -o foo foo.c**. 

man gcc suggests that maybe -b <something> is needed, but what? I am imagining something like
gcc -Wall -o foo.exe -b win386 foo.c but gcc says that -b is an un-recognised option.

---

### Post by Tibuda on 2009-04-28
You got to compile with i586-mingw32msvc-gcc

---

### Post by The Cog on 2009-04-28
That's done the trick. 
Thank you very much. I wouldn't have guessed that in a lifetime or two.

---

### Post by monkeyking on 2009-04-28
Thanks!

---

