---
title: "Simple C Program"
date: 2011-07-10
forum: Programming Talk
---

### Post by konsolelover on 2011-07-10
i just tried to compile simple C program(just to print hello world lol) in Ubuntu 11.04 n it gave me some error.....then i included stdio.h then it compiled successfully ....when i used to program under Windows , it'd compiled successfully without stdio.h....then why it is necessary in Linux?

---

### Post by schauerlich on 2011-07-10
Some compilers will automatically include things for you, and some won't. Don't rely on this behavior, as it's not portable. If you need something from stdio, include it.

---

### Post by dwhitney67 on 2011-07-10
GCC (gcc) does NOT require that you include stdio.h when using printf().  However, if you want to be assured that you are adhering to the function declaration, then you should.

If you fail to include stdio.h, then the following warning is produced:
```

warning: incompatible implicit declaration of built-in function ‘printf’

```
Note that this is not an error!  It is merely a warning indicating that gcc hasn't a clue what the printf() function is.

M$ compilers have been known to cut corners when it comes to generating compiler warnings.  I've seen many programmers who mistakenly thought that they were writing "good" code, when in fact they neglected to include the proper header file(s) to make their code portable.

---

### Post by lisati on 2011-07-10
Although it's OK to do things to make your programming tasks easier, it's generally not a good idea to cut corners. Short program might work well, but with longer programs it can be a real pain to track down the source of weird and obscure errors, particularly when you have cut corners.

---

### Post by konsolelover on 2011-07-10
Thank y'll for your replies now i won't cut corners and will play by the rules... :lolflag:
i've little curiosity about C Programming that is it worth to learn C programming (at deep levels not like dilettante ) in an environment where languages like Java , Python rule....But sometimes my eyes just gets dazzled by assembly language because of its closeness to machine language.....plz help me  out:(

---

### Post by OlyPerson on 2011-07-10
> **konsolelover said:**
> Thank y'll for your replies now i won't cut corners and will play by the rules... :lolflag:
i've little curiosity about C Programming that is it worth to learn C programming (at deep levels not like dilettante ) in an environment where languages like Java , Python rule....But sometimes my eyes just gets dazzled by assembly language because of its closeness to machine language.....plz help me  out:(

C is definitely worth learning as (pretty much) the whole Linux kernel as well as many programs are written in C.  Unless you have a job that requires it, it's probably not worth learning assembly of any sort, though.

---

### Post by Bachstelze on 2011-07-10
> **OlyPerson said:**
> C is definitely worth learning as (pretty much) the whole Linux kernel as well as many programs are written in C.  Unless you have a job that requires it, it's probably not worth learning assembly of any sort, though.

Disagreed.  When you do a lot of C, you *will* sometimes have a program that behaves counter-intuitively.  Knowing how to analyse the assembly code will give you the ability to figure out why, while if you don't you will bang your head on a wall for a while and ultimately ask someone who does (and who will probably be better paid than you).

---

