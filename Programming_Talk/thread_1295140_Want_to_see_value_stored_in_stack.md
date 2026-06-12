---
title: "Want to see value stored in stack"
date: 2009-10-19
forum: Programming Talk
---

### Post by ltwinner on 2009-10-19
Im learning assembly in linux and using the gdb debugger. I know I can see the address of the stack pointer using print/x $esp. But I want to see the value stored at this address.

Say the stack pointer (esp) value is 0xbf81da10
T then push the value 1 onto the stack - pushl $1
Now when I type print/x $esp I get 0xbf81da0c

But I want to see the value that is currenly in being stored in the stack, not address of the stack pointer. How can I do this?

---

### Post by Zugzwang on 2009-10-19
Code run on a 64-bit machine, therefore I'm not using "esp".

```

(gdb) print $sp
$9 = (void *) 0x7fffd8c19320
(gdb) x $sp
0x7fffd8c19320: 0x00000000

```

---

### Post by ltwinner on 2009-10-19
cheers mate

---

