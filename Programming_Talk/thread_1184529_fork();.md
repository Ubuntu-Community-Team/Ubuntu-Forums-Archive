---
title: "fork();"
date: 2009-06-11
forum: Programming Talk
---

### Post by duleep on 2009-06-11
what is relay need for fork() system call in Linux kernel :(

---

### Post by PmDematagoda on 2009-06-11
> **duleep said:**
> what is relay need for fork() system call in Linux kernel :(

I've used fork() a few times myself, so why shouldn't it be there?

---

### Post by randallecook on 2009-06-11
This might be obvious, but running 'man fork' might also help.

---

### Post by NielsBhor on 2009-06-11
You need to have the [SIZE=4][B]unistd.h [SIZE=3]file included in your header..[/SIZE]
[/B][/SIZE]

---

### Post by valex on 2009-06-18
machan It's using in socket programming in networking. you can create a child process to communicate datas between two sockets.

---

### Post by monkeyking on 2009-06-18
It's not only with sockets its usefull.

If you don't need interprocess communication,
you can use fork as a low fi threading solution.

---

