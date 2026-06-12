---
title: "Kernel fflush? (+printk)"
date: 2013-10-10
forum: Programming Talk
---

### Post by azzamite on 2013-10-10
Hello guys

I have a lot of statements of this king in a module I'm debugging:
```
printk("%s:%s\n", __funct__, __line__);
bogus_pointer->may_crash = 0xf00;
```

If that pointer crashes the machine, I never get to see the line previous to it (specially if I don't add a \n),
nor in the dmesg salvaged from the crash dump, and not in the hypervisor console...

So... is there an equivalent to fflush() for the kernel?


BTW, I found this: [http://permalink.gmane.org/gmane.linux.kernel.commits.head/326275](http://permalink.gmane.org/gmane.linux.kernel.commits.head/326275)
but I don't see how to enable it and I'm running 2.6.39.

Thanks in advance

---

