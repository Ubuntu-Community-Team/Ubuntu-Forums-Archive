---
title: "New to linux drivers programmation"
date: 2008-02-04
forum: Programming Talk
---

### Post by Winterrage on 2008-02-04
Hello everyone,

                       We're having a class at the university where you have to program various basic Linux Drivers. Right now i'm trying to compile those drivers from home. I'm having this simple driver:
-------------------------------------------------------------
#include <linux/init.h>
#include <linux/module.h>

static int hello_init(void)
{
  printk(KERN_ALERT "Hello World!");
  return 0; 
}

static void hello_exit(void)
{
  printk(KERN ALERT "Goodbye Cruel World");
}

module_init(hello_init);
module_exit(hello_exit);
---------------------------------------------------------
However, i'm trying to compile using a standard gcc -O -c helloworld.c and i'm getting these errors:

linux/init.h is not found
linux/module.h is not found

Is there any pre-requisite for drivers programmation?

Thanks!

---

### Post by ruy_lopez on 2008-02-04
You need a built and configured kernel to build kernel modules. 

Download chapter two from [here]("http://lwn.net/Kernel/LDD3/")

Its a good idea to read all of the chapters.

Also, for compiling a kernel, see TSEliot's howto

[http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835")

---

### Post by Winterrage on 2008-02-04
Will do!

Thanks for your time :)

---

### Post by JamesUser on 2008-02-04
Read this thread [http://ubuntuforums.org/showthread.php?t=687226](http://ubuntuforums.org/showthread.php?t=687226)

You need kernel headers in order to compile any device driver.

---

