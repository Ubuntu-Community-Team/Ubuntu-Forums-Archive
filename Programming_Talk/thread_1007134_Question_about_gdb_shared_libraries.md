---
title: "Question about gdb shared libraries"
date: 2008-12-10
forum: Programming Talk
---

### Post by ooobooontooo on 2008-12-10
Hi,

So I'm starting to pick up gdb and c programming. However, something that's been blocking my progress is the shared library concept that gdb uses. According to the guide I'm using, when you start up gdb, you're supposed to get this line:
'Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1"'
I don't get that message... So every time, I run gdb it doesn't load any shared library files and that leads to bad things. When I did "show auto-solib-add" it showed it was on. When I had it "show solib-search-path", it only consisted of the current directory. So am I supposed to edit .gdbinit so that it sets the path every time to include that "libthread_db.so.1" file (by the way I do have that file, I'm not missing it) or is it supposed to do it automatically and I'm missing something? Thanks in advance.

---

### Post by Zugzwang on 2008-12-10
Can't understand why it makes problems if this message is missing. Messages might change in later versions of gdb and your book is probably a little bit old.

Additionally, I just tried debugging some test program ("gdb ./test"). If I then type "run", I get the following line: "[Thread debugging using libthread_db enabled]" - Looks like as if things are working fine.

---

### Post by ooobooontooo on 2008-12-10
It's not that it's causing problems. It's just that when I try to do symoblic debugging, like "break strcpy()", it doesn't work because the library is not loaded. (It's not that "break strcpy()" causes gdb to error, it just never stops at strcpy() because the definition is never loaded). So I was just wondering if it's supposed load libraries automatically or if I have to add that line in .gdbinit

Also, I never get this line: "[Thread debugging using libthread_db enabled]" when I type "run". The book was also published in 2008.

EDIT: I just found it it does load the library by default. It just won't break at strcpy. It will break at things like printf. Does anyone know why strcpy in C gets translated to memcpy in assembly? Thanks in advance.

---

