---
title: "Help"
date: 2005-08-29
forum: Programming Talk
---

### Post by mczi on 2005-08-29
Hi all!!!
I just installed ubuntu on my computer and I'd like help on the command to compile c source code on ubuntu.
I tried using the same command as I used in mandrake(cc -o filename filename.c -lm) but ubuntu does not recognise it.

Does it matter which editor one is using, cause I'm using gedit. Talking about editors could someone help me on how to get and install emacs on ubuntu.
Thanks!!!!
mczi ](*,)

---

### Post by DJ_Max on 2005-08-29
```
sudo apt-get install build-essential
```

---

### Post by toojays on 2005-08-30
On Ubuntu, the easiest way to install programs is to use the Synaptic Package Manager, which is in the Administration submenu of the System menu at the top of your screen.

In Synaptic, "mark" the build-essential and [emacs21](http://www.dina.kvl.dk/~abraham/religion/)  packages for installation, then press the "Apply" button.

The build-essential package will install the compiler and a few other goodies you will want. Unfortunately it doesn't install much documentation; depending on what you're doing you may want to install packages like gcc-doc, glibc-doc, emacs-lisp-intro, etc.

By the way: next time you post, please try to set a more useful title; it will help the next person who comes along with the same problem.

---

### Post by intel17 on 2005-09-03
Thank you that has Helped me :D

---

