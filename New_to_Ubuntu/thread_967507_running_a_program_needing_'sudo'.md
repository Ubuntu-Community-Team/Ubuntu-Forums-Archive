---
title: "running a program needing 'sudo'"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by rkakkar on 2008-11-02
hi,

i use a program which requires root permission so i have to type 'sudo <program_name>' in the terminal, every time i need to run it. how can i create a desktop shortcut for the same?

---

### Post by Sef on 2008-11-02
You should not need sudo to run a program every time.   What program are you running, and how did you install it?

---

### Post by billgoldberg on 2008-11-02
If it's a graphical applications (aka it opens in its own window, not the terminal) then start it with gksudo.

Right-click the desktop and "create launcher".

In the command box, just enter "gksudo application".

---

