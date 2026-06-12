---
title: "Unknown symbol init_module &amp; cleanup_module"
date: 2007-12-18
forum: Packaging and Compiling Programs
---

### Post by bbackx on 2007-12-18
Strange stuff...
I'm trying to compile a device driver I've updated (was written for older kernel, I think 2.6.8 ). All compilation errors are gone, but when I try to insmod the module, I'm getting the following errors in dmesg:
Unknown symbol init_module
Unknown symbol cleanup_module

This is strange, since there are no functions like that defined and I used the more up-to-date module_init and module_exit.

Is there anyone with the same problem? Because I'm rather confused by this errors :confused:

---

### Post by geraldm on 2007-12-18
You have probably used kernel header include/linux/module.h, which
defines those two symbols as external. 
Look into that header, about line 63 where it states the options:

/* These are either module local, or the kernel's dummy ones. */
extern int init_module(void);
extern void cleanup_module(void);

Now you know you have to find a way to accomodate the symbols.

Gerald

---

### Post by bbackx on 2007-12-19
Indeed, I use module.h, but even without that header, I get the same errors and when I make my own module_init and module_cleanup function, I also get the Unknown symbol errors :confused:

---

### Post by wings-grow on 2010-10-03
you would probably try this kind of code.

#include<linux/module.h>
#include<linux/kernel.h> 
int init_module(void)
...

<linux/module.h> means - /usr/src/linux/include/linux/module.h

that's where extern init_module(void) is defined. 

so put linux source code into /usr/src/linux

without hard copying we can use this command 
: ln -s /usr/src/linux-2.6.32 linux

---

