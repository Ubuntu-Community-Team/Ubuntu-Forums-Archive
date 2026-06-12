---
title: "can a function be an element of a structure"
date: 2010-09-26
forum: Programming Talk
---

### Post by jamesbon on 2010-09-26
Following structure which is a defined in linux/fs.h

```
struct file_operations {
        struct module *owner;
        loff_t (*llseek) (struct file *, loff_t, int);
        ssize_t (*read) (struct file *, char __user *, size_t, loff_t *);
        ssize_t (*write) (struct file *, const char __user *, size_t, loff_t *);
        ssize_t (*aio_read) (struct kiocb *, const struct iovec *, unsigned long, loff_t);
        ssize_t (*aio_write) (struct kiocb *, const struct iovec *, unsigned long, loff_t);
        int (*readdir) (struct file *, void *, filldir_t);
        unsigned int (*poll) (struct file *, struct poll_table_struct *);
        long (*unlocked_ioctl) (struct file *, unsigned int, unsigned long);
        long (*compat_ioctl) (struct file *, unsigned int, unsigned long);
        int (*mmap) (struct file *, struct vm_area_struct *);
        int (*open) (struct inode *, struct file *);
        int (*flush) (struct file *, fl_owner_t id);
        int (*release) (struct inode *, struct file *);
        int (*fsync) (struct file *, int datasync);
        int (*aio_fsync) (struct kiocb *, int datasync);
        int (*fasync) (int, struct file *, int);
        int (*lock) (struct file *, int, struct file_lock *);
        ssize_t (*sendpage) (struct file *, struct page *, int, size_t, loff_t *, int);
        unsigned long (*get_unmapped_area)(struct file *, unsigned long, unsigned long, unsigned long, unsigned long);
        int (*check_flags)(int);
        int (*flock) (struct file *, int, struct file_lock *);
        ssize_t (*splice_write)(struct pipe_inode_info *, struct file *, loff_t *, size_t, unsigned int);
        ssize_t (*splice_read)(struct file *, loff_t *, struct pipe_inode_info *, size_t, unsigned int);
        int (*setlease)(struct file *, long, struct file_lock **);
};

```
I want to know with respect to above llseek,read,write what are they are they pointers to functions.
I wrote a device driver of mine with help of some search from internet defining my file_operations but the above type of use of structure is new to me.

---

### Post by GeneralZod on 2010-09-26
> **jamesbon said:**
> 
I want to know with respect to above llseek,read,write what are they are they pointers to functions.

Yes :)

---

### Post by jamesbon on 2010-09-26
Hmmm thanks for pointing that out.
So now if some or you can tell I am trying to understand how is read implemented in fs.h can you give some link or file or where should I be looking at.

---

### Post by dwhitney67 on 2010-09-26
It's a pointer to a function.

Try compiling and running this silly C program:
```

#include <stdio.h>

void myFunction(int value)
{
   printf("value = %d\n", value);
}

struct Foo
{
   void (*f)(int);
};

int main()
{
   struct Foo foo;

   foo.f = myFunction;

   foo.f(5);

   return 0;
}

```
Are you enlightened yet?

---

### Post by jamesbon on 2010-09-28
Sorry for the late reply I just noticed it today I was busy with that binary tree problem.
Have a question then how does struct file_operations declaration in  a device driver access the function.
For example

in my device driver I write 
```

struct file_operations bond_fops {
.owner = THIS MODULE;
.read  = bond_read();
.write = bond_write();
}

```
We did not included any statement like 
```

foo.b  = some_function();

```
as you did in your example above.
> **dwhitney67 said:**
> 
Are you enlightened yet?
Thanks for the enlightment :)

---

### Post by Bachstelze on 2010-09-28
This does not look right, what's your entire code?

---

### Post by dwhitney67 on 2010-09-28
> **jamesbon said:**
> 
We did not included any statement like...


That's because I'm an old-school C programmer, thus I personally do not do "fancy" initialization like you see in that kernel driver.  However, the following is legal in C:
```

#include <stdio.h>

struct Foo
{
   void (*owner)(void);
   void (*read)(int);
   void (*write)(int);
};


void myOwner(void)
{
   printf("myOwner() called.\n");
}

void myRead(int value)
{
   printf("myRead() called with value = %d.\n", value);
}

void myWrite(int value)
{
   printf("myWrite() called with value = %d.\n", value);
}

struct Foo foo =
{
   .read  = myRead,
   .owner = myOwner,   /* notice how the order is not important; however syntax is! */
   .write = myWrite
};

int main()
{
   foo.owner();
   foo.read(10);
   foo.write(20);

   return 0;
}

```

---

### Post by nvteighen on 2010-09-29
Hey, I didn't know you can do that kind of initialization... and it's available already since C89! It seems handy.

---

