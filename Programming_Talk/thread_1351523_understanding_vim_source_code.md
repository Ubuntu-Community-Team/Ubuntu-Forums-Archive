---
title: "understanding vim source code"
date: 2009-12-10
forum: Programming Talk
---

### Post by bhargava470 on 2009-12-10
Hi all,

I'm trying to write a simple text editor just for fun. I want to have the vim style commands in it like in the command mode we give :w, :q and other stuff. I'm trying to get this feature. I'm not able to find info regarding this in the vim source code. Can someone help me. Which files in the source code are to be "grepped". This is my first major coding project, so any suggestions in browsing the source code will also be helpful.

Thanks.

---

### Post by MadCow108 on 2009-12-10
compiling vim with debugging information (-g flag) and attaching gdb to a running vim (gdb executable pid) can be helpful to understand the flow of things.

---

### Post by bhargava470 on 2009-12-10
> **MadCow108 said:**
> compiling vim with debugging information (-g flag) and attaching gdb to a running vim (gdb executable pid) can be helpful to understand the flow of things.

I'av installed vim from the repositories. Is this compiled with the debug information enabled?

Thanks.

---

### Post by dwhitney67 on 2009-12-10
You need to get the vim _source_ code... then configure and make it with debugging enabled.

vim is not performing any "magic" with respect to reading using inputs of :w, :q, etc. I almost bet that it relies on the ncurses library for obtaining user inputs, cursor placement, etc.  You should research this library to see how it can meet your needs.

You should also consider researching how to obtain raw input from a terminal, not the cooked stuff that most people are familiar with.  Look into tcgetattr() and tcsetattr().  If you use ncurses, then you will not need to worry about these low-level functions, but still it is nice to know about them.

---

