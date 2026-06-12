---
title: "error in char device module compilation"
date: 2011-09-16
forum: Packaging and Compiling Programs
---

### Post by pawan_dear on 2011-09-16
**[SIZE=4]i am getting the following error------------------------------------------[/SIZE]**

/home/kk/module_programming/fileops.c:30: warning: initialization from incompatible pointer type
/home/kk/module_programming/fileops.c: In function ‘cleanup_module’:
/home/kk/module_programming/fileops.c:57: error: void value not ignored as it ought to be
/home/kk/module_programming/fileops.c: At top level:
/home/kk/module_programming/fileops.c:81: error: conflicting types for ‘device_release’
/home/kk/module_programming/fileops.c:10: note: previous declaration of ‘device_release’ was here
/home/kk/module_programming/fileops.c: In function ‘__inittest’:
/home/kk/module_programming/fileops.c:112: error: ‘start’ undeclared (first use in this function)
/home/kk/module_programming/fileops.c:112: error: (Each undeclared identifier is reported only once
/home/kk/module_programming/fileops.c:112: error: for each function it appears in.)
/home/kk/module_programming/fileops.c: At top level:
/home/kk/module_programming/fileops.c:112: error: redefinition of ‘init_module’
/home/kk/module_programming/fileops.c:32: note: previous definition of ‘init_module’ was here
/home/kk/module_programming/fileops.c: In function ‘__exittest’:
/home/kk/module_programming/fileops.c:113: error: ‘stop’ undeclared (first use in this function)
/home/kk/module_programming/fileops.c: At top level:
/home/kk/module_programming/fileops.c:113: error: redefinition of ‘cleanup_module’
/home/kk/module_programming/fileops.c:55: note: previous definition of ‘cleanup_module’ was here
/home/kk/module_programming/fileops.c:114: error: expected declaration specifiers or ‘...’ before string constant
/home/kk/module_programming/fileops.c:114: warning: data definition has no type or storage class
/home/kk/module_programming/fileops.c:114: warning: type defaults to ‘int’ in declaration of ‘MODULE_LICENCE’
/home/kk/module_programming/fileops.c:114: warning: function declaration isn’t a prototype
make[2]: *** [/home/kk/module_programming/fileops.o] Error 1
make[1]: *** [_module_/home/kk/module_programming] Error 2
make[1]: Leaving directory `/usr/src/kernels/2.6.32-71.el6.x86_64'
make: *** [modules] Error 2


**_[SIZE=4]my programe code [/SIZE]_**

#include<linux/kernel.h>
#include<linux/module.h>
#include<linux/fs.h>
#include<asm/uaccess.h>

int init_module(void);
void cleanup_module(void);

static int device_open(struct inode *, struct file *);
static int device_release(struct file *, struct file *);

static ssize_t device_read(struct file *, char *, size_t, loff_t *);
static ssize_t device_write(struct file *, const char *, size_t, loff_t *);

#define SUCCESS 0
#define DEVICE_NAME "chardev"
#define BUF_LEN 80

static int Major;
static int Device_Open = 0;

static char msg[BUF_LEN];
static char *msg_Ptr;

static struct file_operations fops = {
    .read     = device_read,
    .write    = device_write,
    .open    = device_open,
    .release=device_release
};

int init_module(void)
{
    Major = register_chrdev( 0, DEVICE_NAME, &fops);

    if ( Major < 0 )
    {
        printk("Registering char device failed with %d\n", Major);
        return Major;
    }
    



    printk("I was assinged major number %d. to talk \n",Major);
    printk("the driver create a dev file with \n");
    printk("mknod /dev/%s c %d 0 .\n", DEVICE_NAME, Major);
    
    return SUCCESS;
}




void    cleanup_module(void)
{
    int ret    = unregister_chrdev ( Major, DEVICE_NAME );
    
    if( ret < 0 )
        printk("Error in unregister_chardev : %d \n",ret);

}
    
static int device_open(struct inode *inode, struct file *file)
{
    static int counter = 0;
    
    if( Device_Open)
        return -EBUSY;

    Device_Open++;
    sprintf(msg, "I already told you %d times Hello World \n", counter++);
    
    msg_Ptr = msg ;
    try_module_get(THIS_MODULE);

    return SUCCESS;
}


static int device_release( struct inode *inode, struct file *file)
{
    Device_Open--;

    module_put (THIS_MODULE);
    return 0;
}

static ssize_t device_read( struct file *file, char *buffer, size_t length, loff_t *offset )
{
    int bytes_read = 0;
    
    if( *msg_Ptr == 0)
        return 0;

    while( length && *msg_Ptr )
    {
        put_user( *(msg_Ptr++), buffer++ );
        length--;
        bytes_read++;
    }
    
return bytes_read;
}

static ssize_t device_write( struct file *filp, const char *buff, size_t len, loff_t *off )
{    
    printk("sorry, this operation isn';t supported. \n");
    return -EINVAL;
}

module_init(start);
module_exit(stop);
MODULE_LICENCE("GPL");

---

### Post by SevenMachines on 2011-09-21
You have
```
static int device_release(struct file *, struct file *);
```which I'm guessing you meant
```
static int device_release(struct inode *, struct file *);
```unregister_chrdev returns void in newer kernels so dont use the return value, change 
```
int ret    = unregister_chrdev ( Major, DEVICE_NAME );
    
    if( ret < 0 )
        printk("Error in unregister_chardev : %d \n",ret);
```to simply
```
unregister_chrdev ( Major, DEVICE_NAME );
```You're using 
```
module_init(start);
module_exit(stop);
```to direct the kernel to two non-existent load and unload functions, you could implement them of course but you're using init_module and cleanup_module anyway so just remove those module_init/_exit calls

You have
```
MODULE_LICENCE("GPL");
```but, there must quite a few usa developers, the kernel uses the us english "license" spelling :)
```
MODULE_LICENSE("GPL");
```Should work after those changes

---

### Post by SevenMachines on 2011-09-21
Almost forgot, just for future reference, if you post code to the forum its a best to put it between CODE tags.

---

