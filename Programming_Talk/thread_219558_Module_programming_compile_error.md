---
title: "Module programming compile error"
date: 2006-07-20
forum: Programming Talk
---

### Post by tekrei on 2006-07-20
Hello,
I dont know if this is right topic, sorry if not.
I am trying to learn module programming, but i cant compile my example without errors. Here is my c code:
```

#define __KERNEL__
#define MODULE
#define LINUX

#include <linux/kernel.h>
#include <linux/module.h>

int init_module(void) /*Load a module in the kernel*/
{
	printk("Hello");
	return 0;
}

void cleanup_module(void) /*Removes module from kernel*/
{
	printk("Goodbye");
}
```

Here is errors: (to compile: gcc -c -Wall hello.c)
```
emre@emre:~/Desktop$ gcc -c -Wall hello.c
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from hello.c:6:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from hello.c:6:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
hello.c: In function ‘init_module’:
hello.c:10: warning: implicit declaration of function ‘printk’
```




I am using Anjuta for development and it shows a red line on #include <linux/module.h> line. Please help, or i am gonna crack my head :S
(gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5))
Thanks.

---

