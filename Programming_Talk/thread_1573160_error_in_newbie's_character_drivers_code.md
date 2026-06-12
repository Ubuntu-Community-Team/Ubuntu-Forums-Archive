---
title: "error in newbie's character drivers code"
date: 2010-09-12
forum: Programming Talk
---

### Post by jamesbon on 2010-09-12
[COLOR=#000000][FONT=Times New Roman][FONT=arial]From this link[http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0,0](http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0,0)


I wrote following program




It is to have a character device driver with Major number 60 and do read write 
```

[COLOR=#000000][FONT=Times New Roman][FONT=arial]/* Necessary includes for device drivers */
#include <linux/init.h>
#include <linux/config.h>
#include <linux/module.h>
#include <linux/kernel.h> /* printk() */
#include <linux/slab.h> /* kmalloc() */
#include <linux/fs.h> /* everything... */
#include <linux/errno.h> /* error codes */
#include <linux/types.h> /* size_t */
#include <linux/proc_fs.h>
#include <linux/fcntl.h> /* O_ACCMODE */
#include <asm/system.h> /* cli(), *_flags */
#include <asm/uaccess.h> /* copy_from/to_user */




/* Declaration of memory.c functions */
int bond_open(struct inode *inode, struct file *filp) { return 0;};
int bond_release(struct inode *inode, struct file *filp){ return 0;};
ssize_t bond_read(struct file *filp, char *buf, size_t count, loff_t *f_pos)
{ 
 
  /* Transfering data to user space */ 
  copy_to_user(buf,bond_buffer,1);


  /* Changing reading position as best suits */ 
  if (*f_pos == 0) { 
    *f_pos+=1; 
    return 1; 
  } else { 
    return 0; 
  }
};




ssize_t bond_write(struct file *filp, char *buf, size_t count, loff_t *f_pos)
 {


  char *tmp;


  tmp=buf+count-1;
  copy_from_user(bond_buffer,tmp,1);
  return 1;
} ;
void bond_exit(void);
int bond_init(void);


/* Structure that declares the usual file */
/* access functions */
struct file_operations bond_fops = {
  read: bond_read,
  write: bond_write,
  open: bond_open,
  release: bond_release
};


/* Global variables of the driver */
/* Major number */
int bond_major = 60;
/* Buffer to store data */
char *bond_buffer;


static int bond_init(void) {
  printk("<1> Hello bond new driver!\n");
     int result;


      /* Registering device */
      result = register_chrdev(bond_major, "bond", &bond_fops);
      if (result < 0) {
        printk(
          "<1>memory: cannot obtain major number %d\n", bond_major);
        return result;
      }


      /* Allocating memory for the buffer */
      bond_buffer = kmalloc(1, GFP_KERNEL); 
      if (!bond_buffer) { 
        result = -ENOMEM;
        goto fail; 
      } 
      memset(bond_buffer, 0, 1);


      printk("<1>Inserting bond module\n"); 
      return 0;


      fail: 
        bond_exit(); 
        return result;
      return 0;
 }


static void bond_exit(void) {
  printk("<1> Bye, bond world\n");
/* Freeing the major number */
  unregister_chrdev(bond_major, "bond");


  /* Freeing buffer memory */
  if (bond_buffer) {
    kfree(bond_buffer);
  }


  printk("<1>Removing bond module\n");




}


module_init(bond_init);
module_exit(bond_exit);


MODULE_AUTHOR("Bond");
MODULE_LICENSE("GPL");


[/FONT][/FONT][/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=arial]But when I compiled above[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][FONT=arial]I got following errors
```


/home/bond/driver/bond.c:5:26: error: linux/config.h: No such file or directory
/home/bond/driver/bond.c: In function &#8216;bond_read&#8217;:
/home/bond/driver/bond.c:25: error: &#8216;bond_buffer&#8217; undeclared (first use in this function)
/home/bond/driver/bond.c:25: error: (Each undeclared identifier is reported only once
/home/bond/driver/bond.c:25: error: for each function it appears in.)
/home/bond/driver/bond.c: In function &#8216;bond_write&#8217;:
/home/bond/driver/bond.c:43: error: &#8216;bond_buffer&#8217; undeclared (first use in this function)
/home/bond/driver/bond.c: At top level:
/home/bond/driver/bond.c:53: warning: initialization from incompatible pointer type
/home/bond/driver/bond.c:64: error: static declaration of &#8216;bond_init&#8217; follows non-static declaration
/home/bond/driver/bond.c:47: note: previous declaration of &#8216;bond_init&#8217; was here
/home/bond/driver/bond.c: In function &#8216;bond_init&#8217;:
/home/bond/driver/bond.c:66: warning: ISO C90 forbids mixed declarations and code
/home/bond/driver/bond.c: At top level:
/home/bond/driver/bond.c:93: error: static declaration of &#8216;bond_exit&#8217; follows non-static declaration
/home/bond/driver/bond.c:46: note: previous declaration of &#8216;bond_exit&#8217; was here
make[2]: *** [/home/bond/driver/bond.o] Error 1
make[1]: *** [_module_/home/bond/driver] Error 2
make: *** [build] Error 2


```[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=arial]What is the error in above code any idea?




Here is the corresponding Makefile
[/FONT][/FONT][/COLOR]```

[COLOR=#000000][FONT=Times New Roman][FONT=arial]ifeq ($(KERNELRELEASE),)
KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
.PHONY: build clean
build:
    $(MAKE) -C $(KERNELDIR) M=$(PWD) modules
clean:
    rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c
    rm -rf modules.order Module.symvers
else
$(info Building with KERNELRELEASE =${KERNELRELEASE})
obj-m := bond.o


endif
[/FONT][/FONT][/COLOR]
```[/FONT][/FONT][/COLOR]

---

### Post by worseisworser on 2010-09-12
I think you're missing the Linux kernel headers:

```

sudo aptitude search linux-headers

```

..so something like this, based on your installed kernel, perhaps:

```

sudo aptitude install linux-headers-`uname -r`

```

---

### Post by jamesbon on 2010-09-12
Ok by now I have been able to fix this problem.

1) config.h has been dropped from 2.6.19 series of kernels so that was one error

2) the program was kept in a directory whose directory name had a blank space in between this was also giving me errors
3) I had tried the functions with my name rather than memory_open,memory_read,memory_release
I am not clear if this type of use is wrong.

 I had tried the functions with my name rather than memory_open,memory_read,memory_release
 I am not clear if this type of use is wrong.  

The driver is working but it if I do 

echo -n abcdefg > /dev/memory

then on doing cat /dev/memory
only last g is coming and all previous words which I gave abcdef  are dropped out 
any idea on what might be the error.

---

