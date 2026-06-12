---
title: "Help with warning"
date: 2010-02-06
forum: Programming Talk
---

### Post by swappo1 on 2010-02-06
I am getting a compiler warning on line 28 and I can't figure out what I am doing wrong.  Line 28 is in red.  Here is my code:
```
#include <linux/init.h>
#include <linux/module.h>
#include <linux/kernel.h>	/*printk()*/
#include <linux/slab.h>		/*kmalloc()*/
#include <linux/fs.h>		/*everything...*/
#include <linux/errno.h>	/*error coding*/
#include <linux/types.h>	/*size_t*/
#include <linux/proc_fs.h>
#include <linux/fcntl.h>	/*O_ACCMODE*/
#include <asm/system.h>		/*cli(), *_flags*/
#include <asm/uaccess.h>	/*copy_from/to_user*/

MODULE_LICENSE("Dual BSD/GPL");

/*Declaration of memory.c functions*/
int memory_open(struct inode *inode, struct file *filp);
int memory_release(struct inode *inode, struct file *filp);
ssize_t memory_read(struct file *filp, char *buf, size_t count, loff_t *f_pos);
ssize_t memory_write(struct file *filp, char *buf, size_t count, loff_t *f_pos);
void memory_exit(void);
int memory_init(void);

/*struct that declares the usual file*/
/*Access function*/
struct file_operations memory_fops =
{
	.read =		memory_read,
	[COLOR="Red"].write =	memory_write,[/COLOR]
	.open =		memory_open,
	.release =	memory_release,
};

/*Declaration of the init and exit functions*/
module_init(memory_init);
module_exit(memory_exit);

/*Global variables of the driver*/
/*Major number*/
int memory_major = 60;
/*Buffer to store data*/
char *memory_buffer;

int memory_init(void)
{
	int result;
	
	/*Registering device*/
	/*link the driver with the corresponding /dev file in kernel space*/
	result = register_chrdev(memory_major, "memory", &memory_fops);
	if(result < 0)
	{
		printk("<1>memory: cannot obtain major number %d\n", memory_major);
		return result;
	}
	
	/*Allocating memory for the buffer*/
	memory_buffer = kmalloc(1, GFP_KERNEL);
	if(!memory_buffer)
	{
		result = -ENOMEM;
		goto fail;
	}
	memset(memory_buffer, 0, 1);
	
	printk("<1>Inserting memory module\n");
	return 0;
	
	fail:
		memory_exit();
		return result;
}

void memory_exit(void)
{
	/*Freeing the majory number*/
	unregister_chrdev(memory_major, "memory");
	
	/*Freeing buffer memory*/
	if(memory_buffer)
		kfree(memory_buffer);
	
	printk("<1>Removing memory module\n");
}

int memory_open(struct inode *inode, struct file *filp)
{
	/*Success*/
	return 0;
}

int memory_release(struct inode *inode, struct file *filp)
{
	/*Success*/
	return 0;
}

```
The error:
```
hopchewer@hopchewer:~/Kernel_programming/memory$ make
make -C /lib/modules/`uname -r`/build M=/home/hopchewer/Kernel_programming/memory modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-2-amd64'
  CC [M]  /home/hopchewer/Kernel_programming/memory/memory.o
/home/hopchewer/Kernel_programming/memory/memory.c:28: warning: initialization from incompatible pointer type
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/hopchewer/Kernel_programming/memory/memory.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-2-amd64'
hopchewer@hopchewer:~/Kernel_programming/memory$ 

```

---

### Post by Zugzwang on 2010-02-07
Probably it is because "ssize_t memory_write(struct file *filp, char *buf, size_t count, loff_t *f_pos);" is not the right function prototype for the "write" operation? The information on the following site, found by quick googling, suffests that the "char *buf" part should rather be "const char *buf": [http://www.faqs.org/docs/kernel/x571.html](http://www.faqs.org/docs/kernel/x571.html)

---

