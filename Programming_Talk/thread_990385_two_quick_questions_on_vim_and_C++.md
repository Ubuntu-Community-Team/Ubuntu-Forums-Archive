---
title: "two quick questions on vim and C++"
date: 2008-11-22
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-22
is there a way to collapse code in vim like an IDE

and also...if i make my own header file do i need to add it to my make files?

---

### Post by conehead77 on 2008-11-22
:set foldmethod=syntax

then fold with zm and unfold with zr.
:help folding should help too.

---

### Post by jimi_hendrix on 2008-11-22
ok...also in the .vimrc is there a way i can put that so i dont have to do the set thing everytime?

---

### Post by dexter on 2008-11-22
Sure, just add "set foldmethod=syntax" (without quotes) to your .vimrc file.

---

### Post by jimi_hendrix on 2008-11-22
how do i test a header file for errors?

---

