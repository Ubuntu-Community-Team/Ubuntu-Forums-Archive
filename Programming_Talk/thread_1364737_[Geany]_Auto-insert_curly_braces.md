---
title: "[Geany] Auto-insert curly braces"
date: 2009-12-26
forum: Programming Talk
---

### Post by kahumba on 2009-12-26
Hi,
I have the options checked but geany doesn't generate the curly braces, neither with "if", nor with "for" (using .cpp files)
Anyone knows what's the matter, is it a bug?

---

### Post by Can+~ on 2009-12-26
Works with .c files though.

---

### Post by kahumba on 2009-12-26
After some testing: I think the implementation (of brace generation) is sloppy/buggy.
It doesn't work when the code is inside some other curly braces (which is almost all the time when doing C++) that is, when writing a "for" or "if" inside a class or a function, in this case Geany seems to think that the ending brace of the class/function is the ending brace of if/for and hence it doesn't bother inserting the ending brace. Pitty.

---

### Post by Queue29 on 2009-12-26
Monodevelop and Eclipse are the only IDE's I use personally. Everything else is too poorly made. Actually NetBeans is probably okay as well, but I don't have a use for it. If it's C/C++ stuff you're working on, Eclipse has a version for that in the repositories called eclipse-cdt .

---

### Post by Can+~ on 2009-12-26
Well, if you want "powerful" autocompletion, autoinsertion of things and whatnot, use [eclipse]("http://www.eclipse.org/downloads/"), for C/C++ programmers.

---

### Post by kahumba on 2009-12-26
Thanks,
looks like I'll have to move to Eclipse, but I really liked geany cause it's so easy to use, very fast startup and built-in terminal.

---

### Post by Can+~ on 2009-12-26
> **kahumba said:**
> Thanks,
looks like I'll have to move to Eclipse, but I really liked geany cause it's so easy to use, very fast startup and built-in terminal.

Use both. I have both eclipse and geany. One for medium-large projects, and the other for short snippets.

And I never use autocompletion for bracers, because I have a "mental macro" of automatically doing (), {}, or [], clicking one key right after the other. (Using spanish keyboard, I got all the parenthesis families right next to each other)

---

