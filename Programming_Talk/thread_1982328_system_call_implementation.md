---
title: "system call implementation"
date: 2012-05-18
forum: Programming Talk
---

### Post by s3lcuk on 2012-05-18
hi guys,
i had an assignment about implementing a new system call. Whole day, i searched it in google, but i couldn't find out any solution. There are lots of pdfs but they  really  made me confuse. 
My ubuntu distribution is 12.04, any help would be great..

---

### Post by roelforg on 2012-05-18
Now you're asking a lot!
You'll have to write a kernel module.
[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html)
This one will also tell you about syscalls.

---

### Post by Bachstelze on 2012-05-18
> **roelforg said:**
> Now you're asking a lot!
You'll have to write a kernel module.


That's not really true, you can implement your syscall directly in the kernel. Also, it depends what the syscall is supposed to do. A 'hello world' one is very simple to do.

---

