---
title: "how to put comments in kernel codes and see output"
date: 2010-05-02
forum: Programming Talk
---

### Post by nandan.amar on 2010-05-02
Hello,
I am trying to study kernel codes of wireless module for some enhancement.
I put some comments like  [COLOR="Purple"]printk(KERN_INFO " comments.1..");[/COLOR]  in functions to see in what order they are called .
But I got no response in [COLOR="Plum"][COLOR="Purple"]dmesg[/COLOR][/COLOR].
[COLOR="Purple"]I want to know how to get response of printk();
Is there any other way to study kernel codes.[/COLOR]

---

### Post by dwhitney67 on 2010-05-02
AFAIK, printk() outputs messages to /var/log/messages.

You did not indicate whether you recompiled the wireless driver kernel module after you modified it.  Also, you did not indicate whether this module is built into the kernel, or if it is a stand-alone module.

If it is built into the kernel, then you would need to remake the entire kernel.  If it is a stand-alone module, then you merely need to rebuild the module and then load it using modprobe.  Of course you would need to ensure that it is not currently loaded, or modprobe will issue a warning.

---

### Post by nandan.amar on 2010-05-02
Thnaks dwhitney67,

I have compiled the kernel after making previously mentioned changes
and those modules were part of kernel.

---

### Post by CptPicard on 2010-05-02
> **nandan.amar said:**
> 
what is syntax of  AFAIK and how it is used ?

**A**s **F**ar **A**s **I** **K**now... :)

Usage: Use when communicating that your opinion is limited to your current knowledge, and may thus be wrong in light of more complete information.

---

### Post by nandan.amar on 2010-05-02
:p:p:p:p
    :)

---

