---
title: "struct tty_driver (kernel programming)"
date: 2007-10-17
forum: Programming Talk
---

### Post by edfredcoder on 2007-10-17
Hi,
I am writing a kernel module. I want to be able to locate the struct tty_driver for the pts/* and tty* devices. Does anyone know how to do this?

-Kevin

---

### Post by jpkotta on 2007-10-19
Looking at the struct tty_driver definition and the register function, all registered drivers are in a linked list.  There is a procfs function that looks through the list and sorts them out. 

[http://fxr.watson.org/fxr/source/include/linux/tty_driver.h?v=linux-2.6#L162](http://fxr.watson.org/fxr/source/include/linux/tty_driver.h?v=linux-2.6#L162)
[http://fxr.watson.org/fxr/source/drivers/char/tty_io.c?v=linux-2.6#L3794](http://fxr.watson.org/fxr/source/drivers/char/tty_io.c?v=linux-2.6#L3794)
[http://fxr.watson.org/fxr/source/fs/proc/proc_tty.c?v=linux-2.6#L70](http://fxr.watson.org/fxr/source/fs/proc/proc_tty.c?v=linux-2.6#L70)

---

