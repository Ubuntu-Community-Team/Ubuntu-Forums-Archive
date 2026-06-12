---
title: "Dynamic System Call in Ubuntu"
date: 2009-04-04
forum: Programming Talk
---

### Post by kunsheng on 2009-04-04
Hello everyone,

I got some issues on adding a system call dynamically through a kernel module.

I am using Kernel 2.6.29 and rebuild kernel with everything under 'arch/x86':

I added following two lines in 'arch/x86/kernel/x86_ksyms.c

> 
extern void *sys_call_table;
EXPORT_SYMBOL(sys_call_table);


(Of course, I recompile the kernel and reboot after it)

Then define a module to insert a system call:

> 

#include <linux/init.h>    /* For module_init and module_clea */
#include <linux/module.h>  /* Needed by all modules */
#include <linux/kernel.h>  /* Needed for KERN_ALERT */


void *sys_call_table[];
asmlinkage long sys_ni_syscall(void)
{
    return -ENOSYS;
}


asmlinkage long my_sys_call(int i)
{
    return i;
}

static int dynamic_init(void)
{

    printk(KERN_INFO "Starting dynamic sys call\n");
    sys_call_table[333] = sys_ni_syscall;
    return 0;
}

static void dynamic_exit(void)
{
    printk(KERN_INFO "Cleaning dynamic sys call\n");
    sys_call_table[333] = sys_ni_syscall;
} 

module_init(dynamic_init);
module_exit(dynamic_exit);


My test program is as below:
> 
#include <unistd.h>
#include <stdio.h>

#define __NR_mycall 333

long mycall(int i){

    return syscall(__NR_mycall, i);
};


int main()
{
   printf("%d\n", mycall(100));
   return 0;
}



The module could be inserted into kernel but just no effects there. Everything was smooth and no error or warning info encountered

I am wondering if anyone could give me some idea,


Thanks in advance,

-Kunsheng

---

