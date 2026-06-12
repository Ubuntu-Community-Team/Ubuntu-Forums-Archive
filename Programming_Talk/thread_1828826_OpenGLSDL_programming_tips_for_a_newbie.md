---
title: "OpenGL/SDL programming tips for a newbie?"
date: 2011-08-19
forum: Programming Talk
---

### Post by Rhemat on 2011-08-19
Hello all,

I have been wanting to get into OpenGL programming for a while now, but I haven't been able to find a good guide for starting to program OpenGL applications.  I did find that OpenGL applications can be crafted from various programming languages (but C/C++ seems to be the most popular), and I've also heard a little bit about SDL.  I think I've found a guide for writing SDL applications, but I was wondering if SDL applications have to be compiled, and if so, how to do such (I image with g++, right)?

Just in case it is of any use, I'm pretty good with PERL, and I know a little bit of C++, and BASH.

Thanks in advance

---

### Post by JDShu on 2011-08-19
I don't know perl, but there appears to be a decently mature wrapper library as well as SDL bindings:

[http://en.wikipedia.org/wiki/Perl_OpenGL](http://en.wikipedia.org/wiki/Perl_OpenGL)

[http://sdl.perl.org/](http://sdl.perl.org/)

Whichever language you choose to use, you can expect to import the libraries in the standard way for that language.

For actual coding, if you want to use SDL, first figure out how to make an OGL drawing area and how to send OGL code to SDL. There should be plenty of tutorials online. Note that for now, people still teach OGL 2 while OGL 3 is conceptually very different. The advice I've heard is to learn OGL 2 first, because it will help you understand OGL 3 better.

---

### Post by Rhemat on 2011-08-20
Thanks.  I have looked at the links you provided, and will try to find time to study them soon.  I'll also keep the advice about OGL versions in mind.

---

