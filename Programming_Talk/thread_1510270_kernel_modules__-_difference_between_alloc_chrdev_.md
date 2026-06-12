---
title: "kernel modules  - difference between alloc_chrdev_region &amp; cdev_add"
date: 2010-06-15
forum: Programming Talk
---

### Post by bluedalmatian on 2010-06-15
Im working through the Oreilly book on writing device drivers for the 2.6 kernel but Im a little confused about registering dynamic device numbers.
Ive defined a global variable:

```

dev_t devicemajorminornum = MKDEV(0,0);  // will store the major & minor numbers allocated by the kernel

```
then in the initialisation function ive done

```


alloc_chrdev_region(&devicemajorminornum,0,1,"TXE2MDR");


```

This works OK and I can see in /proc/devices my module has been a given a major number of 251.

I then allocate a cdev structure and initalise its fops and owner attributes and then try to call
```
cdev_add(mycdev,devicemajorminornum, 1)
```
passing in the same dev_t I created earlier but this line fails.

Can anyone enlighten me as to what Im doing wrong please?

The complete code is as follows:

```


#include <linux/init.h>
#include <linux/module.h>
#include <linux/fs.h>
#include <linux/cdev.h>

MODULE_LICENSE("Dual BSD/GPL");
static int txe2_init(void);
static void txe2_exit(void);
int txe2mdr_open(struct inode* inode, struct file* filp);
int txe2mdr_release(struct inode* inode, struct file* filp);
void* buffer;



dev_t devicemajorminornum = MKDEV(0,0);  // will store the major & minor numbers allocated by the kernel
int opencount=0;
struct cdev* mycdev;



struct file_operations txe2mdr_fops =
{
	.owner = THIS_MODULE,
	.open = txe2mdr_open,
	.release = txe2mdr_release,
	//.read = txe2mdr_read,
};


static int txe2_init(void)
{
	alloc_chrdev_region(&devicemajorminornum,0,1,"TXE2MDR");
	mycdev=cdev_alloc();
	mycdev->ops= & txe2mdr_fops;
	mycdev->owner = THIS_MODULE;
	if ((buffer = kmalloc(12,GFP_KERNEL)))
	{
		//succeeded
	}
	else
	{
		printk(KERN_ALERT "TXE2 MDR driver NOT loaded. Memory kmalloc failed\n");
		return -1;
	}
	if (cdev_add(mycdev,devicemajorminornum, 1)) //this line returns error
	{
		printk(KERN_ALERT "TXE2 MDR driver loaded\n");
		return 0;
	}
	else
	{
		printk(KERN_ALERT "TXE2 MDR driver NOT loaded. cdev registration failed\n");
		kfree(buffer);
		return -1;
	}
}


```

---

### Post by rajkumar.kasirajan on 2011-08-01
Hi,

The cdev_add returns zero on success or a negative error code on failure.

so please change your code like this,

if (cdev_add(mycdev,devicemajorminornum, 1) == 0)
    {
        printk(KERN_ALERT "TXE2 MDR driver loaded\n");
        return 0;
    }


Thanks,
Rajkumar

---

### Post by EkuquoL on 2011-08-01
A kernel is the terminal handler / SU / SH / bash / csh 

The differences are not very wildly different.
Just some commands are more dynamic than others.
For instance... you could not run unity / Gnome without bash

---

