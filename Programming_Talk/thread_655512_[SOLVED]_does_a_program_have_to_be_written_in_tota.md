---
title: "[SOLVED] does a program have to be written in totally one language?"
date: 2008-01-01
forum: Programming Talk
---

### Post by -grubby on 2008-01-01
so basically what I'm asking is does a program have to be written in 1 language or can different components be different languages? I heard that openoffice is written in C and C++

---

### Post by Peyton on 2008-01-01
Yes, a program can be written in more than one language.

---

### Post by Wybiral on 2008-01-01
People do it all the time, when you use a library in a language like C++ or even something higher like Python, it may very well be written in something lower like C. AJAX-based web applications often have Javascript communicating back and for with Python/Ruby/PHP so the application is a combination of Javascript and a server language. Speaking of Python, it's very common for larger applications to use small chunks of C or PyRex code to increase runtime efficiency.

---

### Post by -grubby on 2008-01-01
ok thanks guys!

---

### Post by Sporkman on 2008-01-01
> **nathangrubb said:**
> C and C++

Those are the same language, C++ just has extra fuctionality added.

---

### Post by LaRoza on 2008-01-01
> **Sporkman said:**
> Those are the same language, C++ just has extra fuctionality added.

They are not the same language at all.

C and C++, besides a common syntax, are not the same. In fact, the best way to be a poor C++ programmer is to think it is C.

By "extra functionality" add an entirely different way of programming.

---

### Post by slavik on 2008-01-01
even though you can write different pieces of a program in different languages, getting them to work together might be a PITA.

---

### Post by Sporkman on 2008-01-01
> **LaRoza said:**
> They are not the same language at all.

C and C++, besides a common syntax, are not the same. In fact, the best way to be a poor C++ programmer is to think it is C.

By "extra functionality" add an entirely different way of programming.

Meh - same syntax + compiles in the same compiler = same language in my book. The "way of programming" is the way you use the language, not the language itself. The extra functionality in C++ allows you to use the the Jedi OO way, but the underlying language is the same, IMO.

Semantics. My programs use OO to a degree, but I also use printf, fopen, etc. The compiler doesn't care. I guess my language is "C/C++".

---

### Post by Wybiral on 2008-01-01
> **Sporkman said:**
> Meh - same syntax + compiles in the same compiler = same language in my book. The "way of programming" is the way you use the language, not the language itself. The extra functionality in C++ allows you to use the the Jedi OO way, but the underlying language is the same, IMO.

Semantics. My programs use OO to a degree, but I also use printf, fopen, etc. The compiler doesn't care. I guess my language is "C/C++".

OO is not the only difference (but even if it were, that's a big enough difference to justify completely different design strategies). Don't forget about templates, passing by reference, memory allocation being built-in (not functions in a library like C), OO streams, safe strings, and the STL (that's a big one), function+operator overloading, RAII design pattern?

You can use the C++ compiler to compile C code, but that doesn't mean you're programming in C++. In a real C++ project, you'll get shot for using printf/fopen, there are streams for that kind of stuff!

---

### Post by LaRoza on 2008-01-01
> **Sporkman said:**
> Meh - same syntax + compiles in the same compiler = same language in my book. The "way of programming" is the way you use the language, not the language itself. The extra functionality in C++ allows you to use the the Jedi OO way, but the underlying language is the same, IMO.

Semantics. My programs use OO to a degree, but I also use printf, fopen, etc. The compiler doesn't care. I guess my language is "C/C++".

I use gcc to compile Fortran 77 programs....

You can write OO code in C, [http://www.cs.rit.edu/~ats/books/ooc.pdf](http://www.cs.rit.edu/~ats/books/ooc.pdf)

If you get to the core of it, all languages are the same, but superficially, C, Fortran and C++ are different langauges.

---

### Post by Sporkman on 2008-01-01
> **Wybiral said:**
> OO is not the only difference (but even if it were, that's a big enough difference to justify completely different design strategies). Don't forget about templates, passing by reference, memory allocation being built-in (not functions in a library like C), OO streams, safe strings, and the STL (that's a big one), function+operator overloading, RAII design pattern?


Yeah that's true, there is a lot more. For me, at least in my personal programming, my programs are relatively small, so I just do stuff & don't worry about whether it's C or C++. For the big stuff at work, I'm doing mostly what you'd call C++, and the IO stuff is hidden behind various APIs, though reading through the code I or others have written, you might occasionally find some stuff you'd call "C".

When I learned the language(s), the books I used referred to it (them) as "C/C++", so I never really made the distinction, In fact, I've never heard of anybody considering them as different languages until this forum.

---

### Post by CptPicard on 2008-01-01
> **Sporkman said:**
> In fact, I've never heard of anybody considering them as different languages until this forum.

They have their own separate standards and definitions, grammars, compilers... try writing C++ with a C compiler and it's not going to work. A C++ compiler is going to like C more, but it will still complain at points as C is not a pure subset of C++.

---

