---
title: "Help with (g)vim compliers"
date: 2008-05-16
forum: Programming Talk
---

### Post by led3234 on 2008-05-16
How do I use them?

I have the normal 7.1 install.

There's a folder called "compiler" filled with familiar names (gcc, fortran_lf95).

How do I use them, i.e. directly from gvim?

Two things, I'm just learning vim (coming from using IDEs) and I'm also on Windows (Vista, and Iwill make the switch soon, just can't for the time being).

Any help would be appreciated.

Let me know if I'm being too general.

Thanks in advance.

---

### Post by Compyx on 2008-05-17
```
:help compiler
```
Should provide you with some info.

Anyway, I always use :make from (g)vim to compile my projects since my projects nearly always consist of multiple source files. (You'll need a Makefile for this to work, of course)
After running :mak(e), vim will automatically jump to the first error/warning (if any) in your source file(s). You can then jump to subsequent errors/warnings with :cn(ext).

Vim's built-in help is a great source of information, alternatively you can browse the docs online at [http://www.vim.org]("http://www.vim.org").


Cheers.

---

