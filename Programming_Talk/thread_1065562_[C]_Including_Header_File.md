---
title: "[C] Including Header File"
date: 2009-02-10
forum: Programming Talk
---

### Post by suncoolsu on 2009-02-10
Hi All,

It may be a very noobish question.

I have coded in C but never coded a header file before.

I have to include fifo.h in a .c file. I have the this header file in my home directory

i wrote

#include <~/fifo.h>

this doesn't work

pls suggest how to include the header file ? 

thx

---

### Post by cb951303 on 2009-02-10
use relative path and double quotes like this: **#include "../../fifo.h"**

or add this to your gcc line **-I/home/myuser** and then include the file like this: **#include <fifo.h>**

---

### Post by Thesuperchang on 2009-02-10
You may also want to make sure you have multiple inclusion protection.

[PHP]
#ifndef _HEADERNAME_H_
#define _HEADERNAME_H_

/*
Include header files contents in here!
*/

#endif[/PHP]

---

