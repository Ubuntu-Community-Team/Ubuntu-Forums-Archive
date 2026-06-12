---
title: "(newbie) module build environment"
date: 2010-12-15
forum: Packaging and Compiling Programs
---

### Post by andyhi on 2010-12-15
Hi

Please excuse me if this has already been explained but I did not find  it. I am new to Linux, but with a background in other OSes. I found  example code and instructions for building a module and wrote hello.c  as:
#define MODULE
#include </usr/include/linux/module.h>

int init_module(void) {printk("<1>Hello, World\n"); return 0; }
void cleanup_module(void) {printk("<1>Bye Bye! \n"); }

I tried building this with:
gcc -c /home/andy/hello.c

but received the following message:
fatal error: linux/module.h: No such file or directory
compilation terminated.

I put my search engine to use. Following the tips, I first established the version of ubuntu I have:
uname -r
2.6.35-23-generic

Then I checked the cache for available versions:
sudo apt-cache search linux-image

... and chose a version to install:
sudo apt-get install linux-image-2.6.35.23

This proceeded without spewing any error messages, and I assumed it  would provide the support I needed to build a module - but unfortunately  I still encounter the same error.

Can someone point out where I am going wrong, please?
Thanks.

---

### Post by File_ on 2010-12-16
There are already many threads on this topic including this one: [http://ubuntuforums.org/showthread.php?t=471071](http://ubuntuforums.org/showthread.php?t=471071)

Make a search next time ;)

---

