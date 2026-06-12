---
title: "Weird IOCTL behavior?"
date: 2010-07-18
forum: Programming Talk
---

### Post by ruckuus on 2010-07-18
Hello Folks,

I am writing a char driver with IOCTL support just to pass a parameter from user, as follow:

```
static int device_ioctl(struct inode *inode, struct file *filp,
                       unsigned int ctl_num, unsigned long param)
{
       char *tmp = kmalloc(sizeof(*tmp), GFP_KERNEL);
       // check kmalloc result

       switch (ctl_num) {
       case IOCTL_SET_MSG:
               tmp = (char *)param;
               printk(KERN_INFO "message: %s\n", tmp);
               break;
       :
       :

       }
}
```

I assume that above code is just plain printk of "param", but when I executed it the output varied wildly. I take an argument from user if any then pass it to the kernel otherwise passing a string "Foo".

When I put any argument, the output of dmesg is:

message: TERM=xterm

When "Foo" is passed to kernel, the output is:

message:/dev/io_test

FYI, io_test is the device name. Have anyone had the same problem or just me missing anything?

Thanks in advance,
Dwi

---

### Post by seungwon on 2010-07-20
You are trying to directly dereference user-space pointer in kernel code. That's impossible.

---

### Post by Sporkman on 2010-07-21
Look into the copy_from_user() function...

---

