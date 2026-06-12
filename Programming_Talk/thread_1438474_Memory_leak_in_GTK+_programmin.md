---
title: "Memory leak in GTK+ programmin"
date: 2010-03-25
forum: Programming Talk
---

### Post by supravat on 2010-03-25
I am using Ubuntu 9.10. I have created some GUI using Gtk+ and from that GUI I'm calling some executable file( which was created using c). After successful compilation when I'm running the main executable file then it shows memory leak. How should I solve this? What type of precautions should I take during programming? Please help me....

---

### Post by abraxas334 on 2010-03-25
did you write the c-code that has these memory leaks?
Generally when programming using pointers and memalloc or new depening which language you use make sure you assert your allocation or deallocation.
That is the only way of getting rid of memory leaks too. I don't know how complex your program is but in my very simple programms valgrind has been very good at telling me exactly where these leaks are happening, these can then easily be fixed.
[http://www.yolinux.com/TUTORIALS/C++MemoryCorruptionAndMemoryLeaks.html]("http://www.yolinux.com/TUTORIALS/C++MemoryCorruptionAndMemoryLeaks.html")
Google is you friend!

---

### Post by nvteighen on 2010-03-25
Ugh... if you mean the lots of memory leaks shown by valgrind when using GTK+, don't worry, those are all "false" positives.

If I am not wrong, what happens is that GTK+ uses shared memory and therefore, there's a lot of memory that your application is using shared with other ones... so, when your application closes, the memory isn't freed because the other applications still need it.

(I can't find now where I read this from... ugh... having a source would make this post much nicer)

---

