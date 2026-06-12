---
title: "[C]  Problem with cdev interface"
date: 2008-06-18
forum: Programming Talk
---

### Post by doles2 on 2008-06-18
Hi all
I`m a brand-new kernel modules programmer. I have written simple char device
which can read and write. I can use "cat" and "echo" to my device. But i
wrote this using old mechanism - > register_chrdev() and
unregister_chrdev(). It was ok. I understand how it works and everything
was simple. But I`ve just read that there is more modern interface like a
cdev structure and some functions connected with this one. So I decided to
migrate on this cdev but now I have plenty of troubles either with working
or understading my new device. I used some sample source code from LDD 3. I
don`t know it was char device maybe about memory managment... But it seems
to be very simple and there was these lines: 
```
static void simple_setup_cdev(struct cdev *dev, int minor,
                struct file_operations *fops)
{
        int err, devno = MKDEV(simple_major, minor);
    
        cdev_init(dev, fops);
        dev->owner = THIS_MODULE;
        dev->ops = fops;
        err = cdev_add (dev, devno, 1);
        /* Fail gracefully if need be */
        if (err)
                printk (KERN_NOTICE "Error %d adding simple%d", err, minor);
}
/*******************************************/
static int simple_init(void)
{
	int result;
	dev_t dev = MKDEV(simple_major, 0);

	/* Figure out our device number. */
	if (simple_major)
		result = register_chrdev_region(dev, 2, "simple"winking smiley;
	else {
		result = alloc_chrdev_region(&dev, 0, 2, "simple"winking smiley;
		simple_major = MAJOR(dev);
	}
	if (result < 0) {
		printk(KERN_WARNING "simple: unable to get major %d\n", simple_major);
		return result;
	}
	if (simple_major == 0)
		simple_major = result;

	/* Now set up two cdevs. */
	simple_setup_cdev(SimpleDevs, 0, &simple_remap_ops);
	simple_setup_cdev(SimpleDevs + 1, 1, &simple_nopage_ops);
	return 0;
```

So I have taken some lines from this sample and I used it in my char device.
It looks like that: 
```
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/init.h>
#include <linux/fs.h>
#include <linux/cdev.h>
#include <asm/uaccess.h>

static int      FirstModuleInit(void);
static void     FirstModuleExit(void);
static  int     device_open(struct inode *, struct file *);
static  int     device_release(struct inode *, struct file *);
static  ssize_t device_read(struct file *, char *, size_t, loff_t *);
static  ssize_t device_write(struct file *, const char *, size_t, loff_t *);

#define DEV_LICENSE     "GPL"
#define SUCCESS         0
#define DEVICE_NAME     "chardev"
#define BUF_LEN         80

static int Major;
static int Device_Open = 0;

static  char    msg[BUF_LEN];
static  char    *msg_Ptr;

static struct cdev* my_cdev;

static  struct file_operations fops = {
        .read    = device_read,
        .write   = device_write,
        .open    = device_open,
        .release = device_release
};

static int FirstModuleInit(void)
{
        int result, err;
        dev_t devno;
        dev_t dev = MKDEV(Major,0);
        
        /*Figure out our device number */
        if (Major)
                result = register_chrdev_region(dev, 1, DEVICE_NAME);
        else{
                result = alloc_chrdev_region(&dev, 0, 1, DEVICE_NAME);
                Major = MAJOR(dev);
        }
        if (result < 0 ) {
                printk(KERN_WARNING "First: unable to get major
number-> %d",Major);
                return result;
        }
        if (Major == 0)
                Major = result;
        
        /*devno = MKDEV(Major,1); */
        cdev_init(my_cdev, &fops);
        my_cdev->owner = THIS_MODULE;
        my_cdev->ops   = &fops; 
        err = cdev_add(my_cdev, dev, 1);
        /* We have to tell that adding char devince has failed */
        if (err)
                printk(KERN_NOTICE "Error during adding %s device",
DEVICE_NAME);

        printk(KERN_INFO "I was assigned major number %d. To talk to\n",
Major);
        printk(KERN_INFO "My devno = %d", devno);
        printk(KERN_INFO "My dev   = %d", dev);
        printk(KERN_INFO "'mknod /dev/%s c %d 0'\n", DEVICE_NAME, Major);

        return SUCCESS;
}

static void FirstModuleExit(void)
{
        cdev_del(my_cdev);
}

static  int device_open(struct inode *inode, struct file *file)
{
        static int counter = 0;
        if(Device_Open)
                return -EBUSY;

        Device_Open++;
        sprintf(msg, "I`ve already told you %d times Hello World!\n",
counter++);
        msg_Ptr = msg;
        try_module_get(THIS_MODULE);

        return SUCCESS;
}

static  int device_release(struct inode *inode, struct file *file)
{
        Device_Open--;
        module_put(THIS_MODULE);
        return 0;
}

static ssize_t device_read(struct file *flip, char *buffer, size_t length,
loff_t *offset)
{
        int bytes_read = 0;
        if(*msg_Ptr == 0)
                return 0;

        while(length && *msg_Ptr){
                put_user( *(msg_Ptr++), buffer++);
                length--;
                bytes_read++;
        }
        return bytes_read;
}

static ssize_t  device_write(struct file *flip, const char *buffer, size_t
length, loff_t *off)
{
        int i;
        for(i=0; i< length && i < BUF_LEN; i++)
                get_user(msg[i],buffer+i);
        msg_Ptr = msg;
        printk(KERN_INFO "Your message from Userland is: %s",msg);
        return i;
}

/*licence of the module and other stuff */
module_init(FirstModuleInit);
module_exit(FirstModuleExit);

MODULE_LICENSE(DEV_LICENSE);
MODULE_AUTHOR("Bartosz Dolewski"winking smiley;
MODULE_DESCRIPTION("Simple char device "winking smiley;
MODULE_SUPPORTED_DEVICE("TestDevice"winking smiley;
```

Now I have two questions.
1) Why when i fire up my code i can see this lines ?

RIP: 0010:[<ffffffff803142e0>] [<ffffffff803142e0>] memset_c+0x20/0x30
RSP: 0018:ffff81002c019e20 EFLAGS: 00010212
RAX: 0000000000000000 RBX: 0000000000000000 RCX: 000000000000000d
RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
RBP: ffff81003506f240 R08: 0000000000000000 R09: 0000000000000000
R10: 0000000000200200 R11: 0000000000000001 R12: ffffffff88396c60
R13: 0000000000000011 R14: ffffc200004f5c18 R15: 0000000000000001
FS: 00002aba9a1886e0(0000) GS:ffff8100375f8ac0(0000) knlGS:0000000000000000
CS: 0010 DS: 0000 ES: 0000 CR0: 000000008005003b
CR2: 0000000000000000 CR3: 000000002c0a8000 CR4: 00000000000006e0
DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Process insmod (pid: 3502, threadinfo ffff81002c018000, task
ffff81002c012000)
Stack: ffffffff8029a6cf 0000000000000001 0000000000000000 ffffffff88396d80
ffffffff88396137 0000000000000011 0fa00000004f5c18 ffffffff88396d80
ffffffff80256c30 0000000000002c22 0000000000000000 0000000000000000
Call Trace:
[<ffffffff8029a6cf>] cdev_init+0x19/0x3e
[<ffffffff88396137>] :first:FirstModuleInit+0x96/0x129
[<ffffffff80256c30>] sys_init_module+0x16e3/0x1821
[<ffffffff8020be2e>] system_call+0x7e/0x83


Code: f3 48 ab 44 89 c1 f3 aa 4c 89 c8 c3 0f 1f 40 00 eb ce 66 66
RIP [<ffffffff803142e0>] memset_c+0x20/0x30
RSP <ffff81002c019e20>
CR2: 0000000000000000
---[ end trace d6a2467b49c798f8 ]---
Bartek-Debian:/home/bartek/Modu&#322;y/CharDev#

As far as I can see something wrong is doing inside or after the cdev_init.
But I completely don`t know what...
2) Why in sample code from LDD 3 was double MKDEV ? There was twice
invokation of this macro. I thought one MKDEV is enougth.
I`m totally confused with this new way to creating char device. I`m also
angry with [tldp.org] because there is
only the old method sad smiley Moreover plenty of people is learning from this site
so it could be up to date. If somebady is able to help me please do it smiling smiley I
think kernel module programming is to difficult for me.

Regards,
Bartek

---

