---
title: "Finding path of currently loaded modules?"
date: 2010-04-08
forum: Programming Talk
---

### Post by sdaau on 2010-04-08
Hi all, 

When we issue **lsmod**, we obtain a list of currently loaded modules, referred to by name. 
Is there any way that we can also find the path (to the corresponding .ko object) of each loaded module?

This is my problem: I am trying to start with building modules, and I am starting with snd-dummy ([http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.28.y.git;a=blob_plain;f=sound/drivers/dummy.c](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.28.y.git;a=blob_plain;f=sound/drivers/dummy.c)) .. It compiles fine and then I try to load it with
```

sudo insmod ./snd-dummy.ko

```and it seems to load fine; however, snd-dummy is already a kernel module, which exists in /lib/modules/(2.6.28-18-generic/kernel/sound/drivers/snd-dummy.ko). So if I instead issue:
```

sudo modprobe snd-dummy

```then I'm pretty sure the one from /lib/modules gets loaded. 

And, both of these modules will have the name of "snd_dummy" when listed by lsmod. Which is why I would also like to know the path of the currently loaded module. Is that somehow possible? 

Thanks in advance for any answers,

Cheers!

---

### Post by psusi on 2010-04-08
No, it isn't possible.

---

### Post by sdaau on 2010-04-08
Thanks for your reply psusi - good to have that confirmed.. 

Cheers!

---

