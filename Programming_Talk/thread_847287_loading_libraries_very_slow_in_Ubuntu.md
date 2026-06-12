---
title: "loading libraries very slow in Ubuntu"
date: 2008-07-02
forum: Programming Talk
---

### Post by elmasto on 2008-07-02
Hi folks, I am a little stuck...

I am working with an application that is mainly written in C++
(thunderbird to be specific). Anyway, I added a couple of functions,
written in C, and having a few library calls (like libc malloc, sprintf, backtrace etc). The
problem I am having is that the first time those libc functions are
invoked, loading(or executing?) them is taking very long. (running it
under GDB and stepping through the code, on the libc function calls it
takes about 5-10 minutes to return on a dual core, 512 gig machine). However,
once a libc function is invoked and returned, it returns fast as
expected in subsquent invocations of the same function.

I tried to statically link libc, but still have same issues. Have any
ideas?
Thanks a lot

---

### Post by NathanB on 2008-07-02
> **elmasto said:**
> Hi folks, I am a little stuck...

I am working with an application that is mainly written in C++
(thunderbird to be specific). Anyway, I added a couple of functions,
written in C, and having a few library calls (like libc malloc, sprintf, backtrace etc). The
problem I am having is that the first time those libc functions are
invoked, loading(or executing?) them is taking very long. (running it
under GDB and stepping through the code, on the libc function calls it
takes about 5-10 minutes to return on a dual core, 512 gig machine). However,
once a libc function is invoked and returned, it returns fast as
expected in subsquent invocations of the same function.

I tried to statically link libc, but still have same issues. Have any
ideas?
Thanks a lot


It sounds to me like your Swap Partition is set too small ( <512 MB ).  You will get a much better user experience if you set the Swap size to at least 4x to 8x the size of installed RAM.

Nathan.

---

### Post by NathanB on 2008-07-02
Xubuntu is great for memory-constricted PCs:

[http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu)

But your best choice is to purchase more main memory (it is cheap these days).  Your current 512 MB is barely sufficient to handle Ubuntu smoothly.

Nathan.

---

### Post by elmasto on 2008-07-02
Thank you for the tip,
I am running Ubuntu using VMWare Fusion on a mac mini, hence the 512 megs assigned memory. I will try and increase the allocated memory. I don't know if I can change the swap partition tho. I will also try running it on a different machine that is running Ubuntu natively.
I just figured 5 minutes was way to slow even for a half gig machine...
Thanks,

---

