---
title: "how to compile module program when meet  linux/tqueue.h: No such file or directory"
date: 2014-07-23
forum: Programming Talk
---

### Post by zerop2 on 2014-07-23
make: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
make: Nothing to be done for `/home/wonder/layer/hello.c'.
  CC [M]  /home/wonder/layer/hello.o
/home/wonder/layer/hello.c:15:26: fatal error: linux/tqueue.h: No such file or directory
compilation terminated.
make[1]: *** [/home/wonder/layer/hello.o] Error 1
make: *** [_module_/home/wonder/layer] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'

```

#ifndef __KERNEL__
#  define __KERNEL__
#endif
#ifndef MODULE
#  define MODULE
#endif

#include <linux/module.h>

#include <linux/sched.h>
#include <linux/kernel.h>
#include <linux/fs.h>     /* everything... */
#include <linux/proc_fs.h>
#include <linux/errno.h>  /* error codes */
#include <linux/tqueue.h>
#include <linux/interrupt.h> /* intr_count */
//wonder@wonder-VirtualBox:~/layer$ sudo make -C /usr/src/linux-headers-3.8.0-29-generic hello.c M=/home/wonder/layer modules

MODULE_LICENSE("GPL");
struct tq_struct jiq_task;

void jiq_print_tq(void *ptr)
{
    printk("martin runnning\n");
    /*
    if (jiq_print (ptr))
    {
        struct clientdata *data = (struct clientdata *)ptr;
        if (data->queue)
            queue_task(&jiq_task, data->queue);
        if (data->queue == &tq_immediate)
            mark_bh(IMMEDIATE_BH); /* this one needs to be marked */
    }*/
}

static int __init hello_init(void)
{
  printk("Hello World!\n");
  /* these lines are in init_module() */
  jiq_task.routine = jiq_print_tq;
  jiq_task.data = (void*)0;
  //jiq_task.data = (void *)&jiq_data;

  return 0;
}
static void __exit hello_exit(void)
{
  printk("Unloading hello.\n");
  return;
}

module_init(hello_init);
module_exit(hello_exit);

```

---

