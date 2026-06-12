---
title: "users default folder?"
date: 2010-11-03
forum: Programming Talk
---

### Post by Sexraider on 2010-11-03
Hello all!

I'm currently using gambas 2 and I'm having a bit of trouble.

How do I have my save dialog open a certain folder?

let's say this folder:

/home/%user%/.folder/saves

Any ideas? Thanks!

---

### Post by Tony Flury on 2010-11-03
can't you pass "~/.folder/saves" as an argument - or does it not support expansion of "~".

The only other options I would guess are to try to expand "$HOME" environment variable, or use a system call to get the current users home directory.

I am not a GAMBAS expert so i can't give any more detail - sorry.

---

### Post by kalaharix on 2010-11-03
Hi,

You can use a tilde(~) in Gambas.

You can also use the variable user.home as in:

user.home & "/.folder/saves"

Another useful variable is application.path

do a google search on "gambas user.home"

---

