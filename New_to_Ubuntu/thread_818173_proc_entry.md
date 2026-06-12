---
title: "/proc entry"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by makyramallo_22 on 2008-06-04
Hi everyone! Hope somebody can help me with the following...
 
I've done the following to create a /proc entry:

#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/proc_fs.h>
#include <linux/string.h>
#include <linux/vmalloc.h>
#include <asm/uaccess.h>

static struct proc_dir_entry *proc_entry;

ssize_t fortune_write( struct file *filp, const char __user *buff,
                        unsigned long len, void *data )

{
   printk("Soy write\n");
}

int fortune_read( char *page, char **start, off_t off,
                   int count, int *eof, void *data )
{
   printk("Soy read\n");
}

int minit_module(void)
{
   printk("Hola\n");

    proc_entry = create_proc_entry( "pepe", 0644, NULL );
    if (proc_entry == NULL) {
      printk(KERN_INFO "fortune: Couldn't create proc entry\n");
    }
    else {
      proc_entry->read_proc = fortune_read;
      proc_entry->write_proc = fortune_write;

      proc_entry->owner = THIS_MODULE;
      printk(KERN_INFO "fortune: Module loaded.\n");
    }
   return 1;
}

void mcleanup_module(void)
{
   printk("Chau\n");
   return;
}

module_init(minit_module);
module_exit(mcleanup_module);
MODULE_LICENSE("GPL");



But now I want to see on the terminal what has been written, how can I do so? 

Thanks for ure help!


Maky.-

---

### Post by Vadi on 2008-06-04
"cd /proc && ls" ?

---

### Post by aquavitae on 2008-06-04
Should this really be under Absolute Beginner?

---

