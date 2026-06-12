---
title: "beginning kernel programming and printk"
date: 2008-11-02
forum: Programming Talk
---

### Post by soudak on 2008-11-02
Hello,

I am trying to dig into the Linux kernel on 8.04, and I am trying to figure out what the best methods and tools are for debugging and examining it. 

I've been able to download and build a custom kernel.

However, when I insert a test printk(KERN_DEBUG "testing in the kernel"); line, perhaps in a function triggered by a system call I am seeing "testing in the kernel" all jumbled when I run dmesg after running a simple C program that does the call.

Is this the right approach?  

Also, do I just have to rebuild the kernel and install it and then reboot to see these changes?

Thanks.

---

### Post by LaRoza on 2008-11-02
I don't know about the programming, but you do have to reboot for testing changes. You are using a VM aren't you?

---

### Post by soudak on 2008-11-02
> **LaRoza said:**
> You are using a VM aren't you?

Yeah it's in a VM.

---

