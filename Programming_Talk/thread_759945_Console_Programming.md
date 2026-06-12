---
title: "Console Programming"
date: 2008-04-19
forum: Programming Talk
---

### Post by zJerrik on 2008-04-19
Hi, I'm new to Ubuntu and also the terminal (I've used the windows command prompt, but not for much).

Is there a way (and if so a good guide or tutorial) to do output to a terminal in a specific way (defined below)?

In C if you use printf it adds to the terminal. I want to be able to print characters to a certain part of the terminal, not just the end of the last output. For instance:

.........................................
.................x......................
.........................................
........................................|

Here we have some output (denoted by periods) that has been made by printf. The pipe (|) denotes where the cursor currently is, and where printf would put its output. Is there some way I could overwrite the already place character at x?

It doesn't have to be language specific, I just used printf in C as an example.

Thanks for taking the time to read this! =)

---

### Post by LaRoza on 2008-04-19
Ncurses is what you seem to want.

(Works with C, but also most other languages including Python if you don't want to be using C)

[http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific)

---

### Post by zJerrik on 2008-04-19
> **LaRoza said:**
> Ncurses is what you seem to want.

(Works with C, but also most other languages including Python if you don't want to be using C)

[http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific)

Thank you, this is exactly what I was looking for =D

---

### Post by finferflu on 2008-04-19
It's already among the links provided on LaRoza's website, but I want to highlight it: [http://linuxcommand.org](http://linuxcommand.org)
It's not about ncruses, but it's an excellent introduction to shell commands, which you might find useful as well.

---

### Post by zJerrik on 2008-04-19
> **finferflu said:**
> It's already among the links provided on LaRoza's website, but I want to highlight it: [http://linuxcommand.org](http://linuxcommand.org)
It's not about ncruses, but it's an excellent introduction to shell commands, which you might find useful as well.

Thats great thank you as well ^_^

---

