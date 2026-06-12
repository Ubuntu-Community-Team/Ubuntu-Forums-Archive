---
title: "quick question:  raw_input format (python)"
date: 2008-06-26
forum: Programming Talk
---

### Post by bigdidz on 2008-06-26
I just want to make a simple terminal keyboard speed test program.  I'll ask to my user to enter numbers but I do not want them to press enter after it.  I know that the users will enter 8 digits number.  How do I do that?

if I use 'input()' or 'raw_input' command they need to press enter after each number.

If you can help me I would be appreciated

BigDidz

P.-S.: Euler hack in Python

---

### Post by pmasiar on 2008-06-26
raw_input always waits for enter. Do do tricky input like you want, you may want ncurses or something with direct terminal input/output of every key pressed. Check core modules, something like that should be there

---

### Post by LaRoza on 2008-06-26
> **pmasiar said:**
> raw_input always waits for enter. Do do tricky input like you want, you may want ncurses or something with direct terminal input/output of every key pressed. Check core modules, something like that should be there

curses is there (curses.getch() is the function for it).

---

