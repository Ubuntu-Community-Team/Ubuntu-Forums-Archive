---
title: "stroustrup + programming principles and practice using c++ - chapter 12"
date: 2009-12-14
forum: Programming Talk
---

### Post by vase on 2009-12-14
I am learning C++ from the book of stroustrup: programming practice and principles using C++. I program on ubuntu 8.10 using the gcc compiler with the g++ script to compile c++ code. I fail to run the first example program of chapter 12 of this book (section 12.3, page 411), is is freely available on the website: [www.stroustrup.com/Programming/](www.stroustrup.com/Programming/), also the libs needed are available there.
        
        I compile the programming using this command:
        g++ -lfltk -lfltk_images -o 12_3 12_3.cpp -I ../lib -L../lib -lbookgui
        
        Compling goes fine, but if I run the program I get into trouble:
        *** glibc detected *** ./12-3: free(): invalid size: 0x00007fffb4bb4b50 ***
        ======= Backtrace: =========
        /lib/libc.so.6[0x7f29aba2fa58]
        /lib/libc.so.6(cfree+0x76)[0x7f29aba320a6]
        
        and so on...
        
        I was a bit surprised because I ran exactly the example given in the book, I get the same problems with other examples of this chapter, but not of previous chapters. Anyone a clue how I can trace this the cause of this memory problem?

---

### Post by Zugzwang on 2009-12-14
Have you tried running valgrind on the the program? This is a useful tool for finding out what went wrong in such situations.

```

valgrind --tool=memcheck ./yourprogram

```

---

### Post by johnny3k on 2011-05-09
I can't find code examples on site. Unfortunately they talking of code by parts. Can you help me?

---

