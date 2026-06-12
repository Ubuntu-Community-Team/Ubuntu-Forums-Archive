---
title: "First Time Installing a Library"
date: 2010-02-28
forum: Packaging and Compiling Programs
---

### Post by nirvana21 on 2010-02-28
This is the first time I have ever tried to install a library for c++ and I am running into trouble. I need to use the [[COLOR="Blue"]GMP library[/COLOR]]("http://gnulib.org/"). Anyway, I followed the instructions and installed the library for c++. 

My problem is that when I try to do
```
cout << somevar;
```
it compiles fine, but when I try to run a.out I get an error: ./a.out: error while loading shared libraries: libgmpxx.so.4: cannot open shared object file: No such file or directory

I found libgmpxx.so.4 in /usr/local/lib/
How can I make my compiler or whatever find the file?

I hope I am clear enough. If you need a better explanation or more information let me know. 

Thank you very much for your help in advance.:popcorn:

---

### Post by lloyd_b on 2010-02-28
> **nirvana21 said:**
> This is the first time I have ever tried to install a library for c++ and I am running into trouble. I need to use the [[COLOR="Blue"]GMP library[/COLOR]]("http://gnulib.org/"). Anyway, I followed the instructions and installed the library for c++. 

My problem is that when I try to do
```
cout << somevar;
```
it compiles fine, but when I try to run a.out I get an error: ./a.out: error while loading shared libraries: libgmpxx.so.4: cannot open shared object file: No such file or directory

I found libgmpxx.so.4 in /usr/local/lib/
How can I make my compiler or whatever find the file?

I hope I am clear enough. If you need a better explanation or more information let me know. 

Thank you very much for your help in advance.:popcorn:

Try running "sudo ldconfig" in a terminal window, and see if this resolves the issue.

The problem is that while you've compiled the library and have it installed in a standard location, you haven't told the system's library loader routine (ld) that it's there.  'ldconfig' scans all the standard locations for libraries, and adds any that are found to the index that 'ld' uses.

(ideally, the final state of the installation *should* have run 'ldconfig' for you, but it appears that it didn't).

Lloyd B.

---

### Post by nirvana21 on 2010-02-28
Excellent! Thank you very much.

---

