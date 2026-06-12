---
title: "Visual Bug on few apps (18.04)"
date: 2020-10-29
forum: New to Ubuntu
---

### Post by whoviancoder on 2020-10-29
Hello! Recently I got this problem on few programs when using Ubuntu 18.04 (minecraft, Atom, Chrome). I atached 2 photos ([https://imgur.com/a/NaUgWPx](https://imgur.com/a/NaUgWPx)), one with the problem itself and one that shows what video card driver I got.
[IMG]https://imgur.com/a/NaUgWPx[/IMG]

---

### Post by ajgreeny on 2020-10-29
It looks like a graphic card/driver problem but I see you have Intel graphics which normally are very well supported in Ubuntu and other Linux distros.
Are you using an xorg login or perhaps logging into a wayland session?

To show us what your other hardware is please show us the terminal output of command ```
inxi -Fzx
```
Do not add an image as you did last time for textual information but use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

