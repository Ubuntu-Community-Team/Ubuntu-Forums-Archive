---
title: "my driver is dropping characters"
date: 2010-09-15
forum: Programming Talk
---

### Post by jamesbon on 2010-09-15
[COLOR=#000000][FONT=Times New Roman][FONT=arial][COLOR=#000000][FONT=Times New Roman][FONT=arial]I wrote  my hello world  type of character device driver.(First driver that I wrote)
I created a device as follows
```

mknod /dev/bond c 60 0 

```and then [/FONT][/FONT][/COLOR]tried to write something to that device as follows
```
echo -n abcde > /dev/bond
```[COLOR=#000000][FONT=Times New Roman][FONT=arial]


[/FONT][/FONT][/COLOR]```
cat /dev/bond
```[COLOR=#000000][FONT=Times New Roman][FONT=arial]
will show me the last
[/FONT][/FONT][/COLOR]```
e
```[COLOR=#000000][FONT=Times New Roman][FONT=arial] of  entered [/FONT][/FONT][/COLOR]```
abcde
```[COLOR=#000000][FONT=Times New Roman][FONT=arial]
above but will drop abcd.
I can see the last character which was passed on to as argument to echo but not the previous characters.

Any idea what improvement should I make.
Here is the code.
```

#include <linux/init.h>
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


```[/FONT][/FONT][/COLOR][/FONT][/FONT][/COLOR]

---

### Post by worseisworser on 2010-09-15
Hint: You're passing a 1 to copy_to_user.

---

### Post by jamesbon on 2010-09-18
Yes got your point.
I changed that value but still it did not worked.
Here is my new code
```



#include <linux/init.h>

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

MODULE_LICENSE("Dual BSD/GPL");


int bond_open(struct inode *inode, struct file *filp);
int bond_release(struct inode *inode, struct file *filp);
ssize_t bond_read(struct file *filp, char *buf, size_t count, loff_t *f_pos);
ssize_t bond_write(struct file *filp, char *buf, size_t count, loff_t *f_pos);
void bond_exit(void);
int bond_init(void);

struct file_operations bond_fops = {
  read: bond_read,
  write: bond_write,
  open: bond_open,
  release: bond_release
};

module_init(bond_init);
module_exit(bond_exit);

int bond_major = 60;

char *bond_buffer;

int bond_init(void) {
  int result;


  result = register_chrdev(bond_major, "bond", &bond_fops);
  if (result < 0) {
    printk(KERN_ALERT  "memory: cannot obtain major number %d\n", bond_major);
    return result;
  }


  bond_buffer = kmalloc(14, GFP_KERNEL); 
  if (!bond_buffer) { 
    result = -ENOMEM;
    goto fail; 
  } 
  memset(bond_buffer, 0, 14);

  printk(KERN_ALERT "Inserting bond module\n"); 
  return 0;

  fail: 
    bond_exit(); 
    return result;
}


void bond_exit(void) {

  unregister_chrdev(bond_major, "bond");


  if (bond_buffer) {
    kfree(bond_buffer);
  }

  printk( KERN_ALERT "Removing bond module\n");

}


int bond_open(struct inode *inode, struct file *filp) {


  return 0;
}


int bond_release(struct inode *inode, struct file *filp) {
 

  return 0;
}


ssize_t bond_read(struct file *filp, char *buf, 
                    size_t count, loff_t *f_pos) { 
 

  copy_to_user(buf,bond_buffer,count<14 ? count:14);


 /* if (*f_pos == 0) { 
    *f_pos+=1; 
    return 1; 
  } else { 
    return 0; 
  }*/
}

ssize_t bond_write( struct file *filp, char *buf,
                      size_t count, loff_t *f_pos) {

//  char *tmp;

  //tmp=buf+count-1;
  copy_from_user(bond_buffer,buf,count<14 ? count : 14);
  return 1;
}
```
running an strace on above segment showed me 
```


mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2a2f03b000
write(1, "abcde", 5)                    = 1
write(1, "bcde", 4)                     = 1
write(1, "cde", 3)                      = 1
write(1, "de", 2)                       = 1
write(1, "e", 1)                        = 1
close(1)                                = 0
munmap(0x7f2a2f03b000, 4096)            = 0
close(2)                                = 0
exit_group(0)                           = ?

```

---

### Post by dwhitney67 on 2010-09-25
Why do you always return 1 from bond_write()?  It seems to me that you should return the lesser of either 'count' or 14.

And in bond_read(), you don't return any value!  You should.

---

### Post by worksofcraft on 2010-09-25
Nice one :)

My first suspicion is that you are only allocating one byte here:
```

 bond_buffer = kmalloc(1, GFP_KERNEL);

```

but IDK because I never wrote a Linux driver myself and don't know how debug one.

p.s.
also I think this bit will only let you read one character when *f_pos is at the start of file and otherwise reads nothing:
```

  /* Changing reading position as best suits */ 
  if (*f_pos == 0) { 
    *f_pos+=1; 
    return 1; 
  } else { 
    return 0; 
  }

```

lol - and then in bond_write you are definitely only saving the last character written:
```

...
  tmp=buf+count-1; // see this is the last one in "buf"
  copy_from_user(bond_buffer,tmp,1); // and that's all you copy

```

So I think the whole thing is just designed to do one character. However it's very interesting... What command do I need to compile it? Also it just says I haven't got any of those header files either :shock:

---

### Post by worseisworser on 2010-09-25
> **worksofcraft said:**
> Also it just says I haven't got any of those header files either :shock:

You're looking for the *linux-headers* package.

---

### Post by dwhitney67 on 2010-09-25
> **worksofcraft said:**
> 
... What command do I need to compile it? Also it just says I haven't got any of those header files either :shock:

You need to create a Makefile.  Here's an example for compiling a kernel driver source file named "bond.c":
```

obj-m := bond.o

KDIR  := /lib/modules/$(shell uname -r)/build

all:
        $(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
        $(MAKE) -C $(KDIR) M=$(PWD) clean

```

To hop aboard the OP's train, then you will need to do the following:
```

1.  Create a character device

	# mknod /dev/bond c 60 0


2.  Build the kernel module

	$ make


3.  Load the kernel module

	# insmod bond.ko


4.  Write to the character device

	# echo -n hello > /dev/bond


5.  Verify write

	# cat /dev/bond


When all done:

1.  Remove the driver

	# rmmod bond


2.  Remove the character device

	# rm -f /dev/bond

```


P.S.  The errors you mentioned in the OP's opening post have been corrected (AFAIK).

Here's his code again, in (I hope) a working version:
```

#include <linux/init.h>

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

MODULE_LICENSE("Dual BSD/GPL");


int     bond_open(struct inode *inode, struct file *filp);
int     bond_release(struct inode *inode, struct file *filp);
ssize_t bond_read(struct file *filp, char *buf, size_t count, loff_t *f_pos);
ssize_t bond_write(struct file *filp, char *buf, size_t count, loff_t *f_pos);
void    bond_exit(void);
int     bond_init(void);

struct file_operations bond_fops =
{
  read:    bond_read,
  write:   bond_write,
  open:    bond_open,
  release: bond_release
};

module_init(bond_init);
module_exit(bond_exit);

int   bond_major  = 60;
char* bond_buffer = 0;


int bond_init(void)
{
   int result = register_chrdev(bond_major, "bond", &bond_fops);

   if (result < 0)
   {
      printk(KERN_ALERT  "memory: cannot obtain major number %d\n", bond_major);
      return result;
   }

   bond_buffer = kmalloc(14, GFP_KERNEL); 

   if (!bond_buffer)
   {
      result = -ENOMEM;
      bond_exit(); 
   }
   else
   {
      result = 0;
      memset(bond_buffer, 0, 14);
      printk(KERN_ALERT "Inserting bond module\n"); 
   }

   return result;
}


void bond_exit(void)
{
   unregister_chrdev(bond_major, "bond");

   if (bond_buffer)
   {
      kfree(bond_buffer);
   }

   printk(KERN_ALERT "Removing bond module\n");
}


int bond_open(struct inode *inode, struct file *filp)
{
   return 0;
}


int bond_release(struct inode *inode, struct file *filp)
{
   return 0;
}


ssize_t bond_read(struct file *filp, char *buf, size_t count, loff_t *f_pos)
{ 
   ssize_t bytes = count < 14 ? count : 14;
   copy_to_user(buf, bond_buffer, bytes);
   return bytes;
}


ssize_t bond_write( struct file *filp, char *buf, size_t count, loff_t *f_pos)
{
   ssize_t bytes = count < 14 ? count : 14;
   copy_from_user(bond_buffer, buf, bytes);
   return bytes;
}

```

---

### Post by jamesbon on 2010-09-26
> **worksofcraft said:**
> Nice one

My first suspicion is that you are only allocating one byte here:
```

 bond_buffer = kmalloc(1, GFP_KERNEL);

```
Correct> **worksofcraft said:**
> 
p.s.
also I think this bit will only let you read one character when *f_pos is at the start of file and otherwise reads nothing:
```


  /* Changing reading position as best suits */
  if (*f_pos == 0) {
    *f_pos+=1;
    return 1;
  } else {
    return 0;
  }

```lol - and then in bond_write you are definitely only saving the last character written:
```

...
  tmp=buf+count-1; // see this is the last one in "buf"
  copy_from_user(bond_buffer,tmp,1); // and that's all you copy

```So I think the whole thing is just designed to do one character.

Correct.

Also  dwhitney67 code suggestions work but with a modification
> **dwhitney67 said:**
> 
Here's his code again, in (I hope) a working version:
```

.........snip.....
ssize_t bond_read(struct file *filp, char *buf, size_t count, loff_t *f_pos)
{
   ssize_t bytes = count < 14 ? count : 14;
   copy_to_user(buf, bond_buffer, bytes);
   return bytes;
}

```
Here is what I implemented
in read function ```

    if (*f_pos > 0)
        return 0;
    if (count > strlen(memory_buffer))
        count = strlen(memory_buffer);
    copy_to_user(buf,memory_buffer,count);
    *f_pos = *f_pos + count;

    return count; 
```Following is reason some one explained me
> 
The first read comes in with a *f_pos of 0. If you dont update the  file pointer, the user space program will keep reading from f_pos 0  indefinitely. As file pointer is at offset 0 always because you dont  update *f_pos, every read(..) called by user space will succeed. So,  your command cat /dev/bond will never return. user space programs  generally look for a specific return code to know that it is the end of  the file.
 
 can any one help me to understand why do I need to update f_pos each time.
If I do not update *f_pos then the code goes to an infinite loop when you do 
```
cat /dev/bond
```

---

