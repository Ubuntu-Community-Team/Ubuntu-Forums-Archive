---
title: "printk() problem"
date: 2010-04-24
forum: Programming Talk
---

### Post by vksingh on 2010-04-24
Hi,

I have put printk("some text"); in one kernel module file. Where will be the message printed. Where should i look for that file in system.

Thanks,

Vivek

---

### Post by the_unforgiven on 2010-04-24
/var/log/kern.log
or 
/var/log/messages

---

### Post by ibuclaw on 2010-04-24
Or at the tail of the command
```
dmesg
```

Regards

---

