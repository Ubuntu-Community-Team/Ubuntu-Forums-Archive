---
title: "Linux Device Drivers 3rd Edition"
date: 2008-03-03
forum: Programming Talk
---

### Post by WernerLioen on 2008-03-03
Hi,

Does anyone know if someone translated the examples in this book from a "vanilla" kernel to Ubuntu. It would be a great help for me getting a copy from such in writing my own drivers.

Werner

---

### Post by rbprogrammer on 2008-03-03
i'm no expert in this area at all.  at least not as of yet.  but my opinion is that device drivers probably don't depend on the "flavor" :wink: of the distro, but rather the version of the kernel.

but, i dont have this book, nor do i know how to write a device driver.

---

### Post by WernerLioen on 2008-03-03
Thanks RBprogrammer for your comments.

---

### Post by rbprogrammer on 2008-03-03
is there a free online version that you know of?? it might be easier to walk you through some examples, just to further your understanding of the difference between the linux distro and the linux kernel

---

### Post by WernerLioen on 2008-03-03
Yes, there is...

[http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

Thanks...

---

### Post by WernerLioen on 2008-03-04
I'm sorry about my mistake, talking about an Ubuntu kernel and a vanilla kernel. As I understand by now all linux distributions have the same kernel. The problem with the ldd examples is that it is based on a kernel version which is older than what the Ubuntu Gutsy distribution uses.

In the meantime I have got the scull example compiling for Gutsy. It looks like some definitions in the kernel include files have been moved around.:shock:

---

### Post by rbprogrammer on 2008-03-17
sorry for a bit of a long time to reply, but i think you can use the examples in the book.  but like i said before i'm not expert. so dont quote me on this, but the version that is used in the book ( ie. 2.6 ) is not that different from the one used in gutsy.  when i executed this command, i got the following output:
```

uname -r
2.6.22-14-generic

```
so i my best guess is that the book is still up to date.  i highly doubt think there are many difference between the book and the kernel gutsy uses.  but if you do run into a problem when working on your own drivers, then you can use the book to show what example lead you to develop your code.

i would worry about it if the book was using kernel 2.4, then there would be significant changes.  but version 2.6 should be fine.

:guitar:

---

