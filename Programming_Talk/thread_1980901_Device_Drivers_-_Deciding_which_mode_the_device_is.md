---
title: "Device Drivers - Deciding which mode the device is opened"
date: 2012-05-16
forum: Programming Talk
---

### Post by AlGorism on 2012-05-16
Here is the prototype of open method in my device driver:

[PHP]static int myd_open(struct inode *inode, struct file *filp)[/PHP]

In my sample code, the device is opened with argument "rw" like this:

[PHP]FILE* fd = fopen("/dev/dene","rw");[/PHP]

So, in open method, I want to decide the opening argument. In other words, I want to do different things on "w", "r", and "rw" modes.

---

### Post by codemaniac on 2012-05-16
> **AlGorism said:**
> Here is the prototype of open method in my device driver:

[PHP]static int myd_open(struct inode *inode, struct file *filp)[/PHP]

In my sample code, the device is opened with argument "rw" like this:

[PHP]FILE* fd = fopen("/dev/dene","rw");[/PHP]

So, in open method, I want to decide the opening argument. In other words, I want to do different things on "w", "r", and "rw" modes.
The allowed modes for fopen are as follows:
> r  - open for reading
w  - open for writing (file need not exist)
a  - open for appending (file need not exist)
r+ - open for reading and writing, start at beginning
w+ - open for reading and writing (overwrite file)
a+ - open for reading and writing (append if file exists)

---

