---
title: "Warnings at the end of ./configure"
date: 2011-05-18
forum: Programming Talk
---

### Post by abioticrhyme on 2011-05-18
I am trying to run ./configure for drivel 3.0.3 but at the end it gives me the following warnings. 

drivel-3.0.3:

    Prefix:                     /usr/local
    Source code location:        .
    Compiler:            gcc
    Warnings:             -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Werror -Wdeclaration-after-statement
    Using gtkspell:            yes
    Music player D-Bus interface:    yes
    Update MIME database:        yes
    Update desktop database:    yes

I am lost on how to fix this any help would be appreciated. :confused:

---

### Post by muteXe on 2011-05-18
They dont look like compiler warnings to me.

edit:  Look here:
[http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html)

They are just the compiler warning flags that are being used. You dont need to fix anything.

---

### Post by abioticrhyme on 2011-05-18
Thank you I am not a programmer and trying to understand what I am looking at is a little confusing. The link you gave is helping.

---

### Post by muteXe on 2011-05-18
You are welcome mate :)

---

