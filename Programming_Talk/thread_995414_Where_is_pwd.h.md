---
title: "Where is pwd.h"
date: 2008-11-27
forum: Programming Talk
---

### Post by supermoose on 2008-11-27
Hey everyone,

I'm trying to include pwd.h in some kernel code I'm writing. I am able to do #include <pwd.h> in programs outside the kernel but when I do that inside the kernel and do a make bzImage I get a file not found error.

I've been trying to find the full path to pwd.h by searching the file system but I have had no luck.

Any ideas?

-Thanks in advance
supermoose

---

### Post by jpkotta on 2008-11-27
```
locate pwd.h
```

You can't include userspace stuff in the kernel.  It is completely standalone.  Things like strcmp() and printf() (printk()) are totally re-implemented in the kernel.  You will have to re-implement the functions declared in pwd.h if you want to use them, but I don't think the kernel has the concept of users, so I don't think that would be very easy.

---

### Post by supermoose on 2008-11-28
Thanks for the reply, I found a different way of doing what I wanted. But it's good to know why i can't use certain headers.

---

