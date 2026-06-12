---
title: "Tab Complete"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by JustAnotherWinblowzHater on 2008-06-23
Hi, I know about the tab completion in Ubuntu and I know what it does. But every time I try and tab complete something, my computer beeps (the little motherboard speaker beeps, not my speakers on my desk). Anyway, I have found out that if I hit tab twice quickly, it works...sometimes. For instance, i was trying to tab complete 'clear', and got to 'cle' and hit tab, it only added one letter, making 'clea'. Is 'clea' a command? Anyway, my main point is, why do I have to hit tab twice? Can't I just hit tab once? What can I do to fix this?

Thanks in advance

---

### Post by dracayr on 2008-06-23
no, clear isn't a command, but there are multiple commands that start with clea, so the terminal doesn't know which one you want. You can see all the options by hitting tab twice.

dracayr

---

### Post by the_doc on 2008-06-23
> **JustAnotherWinblowzHater said:**
> 
Is 'clea' a command?


No.

> **dracayr said:**
> no, clear isn't a command

clear is a command, it clears the terminal screen!

---

### Post by mister_pink on 2008-06-23
There is a way! I fixed this ages ago, but when I reinstalled I couldn't remember how to do it again. Very infuriating.

Anyway: In /etc/inputrc (I think it can also go in ~/.inputrc, but I haven't tried this) you need the line:
```
set show-all-if-ambiguous on
```
It should already be in there, but commented out, so you should just need to delete the #. Remember you need to do
```
gksudo gedit /etc/inputrc
```
to edit the file

---

