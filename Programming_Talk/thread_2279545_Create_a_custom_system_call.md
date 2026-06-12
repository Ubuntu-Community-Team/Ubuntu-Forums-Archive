---
title: "Create a custom system call"
date: 2015-05-24
forum: Programming Talk
---

### Post by shark3 on 2015-05-24
Hi everybody, I'm trying to practice the linux kernel and I want to create a custom system call.
I was trying to follow this guide [1] but I noticed that something has changed because there isn't the syscall_table_32.S file anymore.
I discovered that the previous file was substituted by the most recent syscall_32.tbl file but they are very different.
So the question is: can someone suggest me a reference to read in order to add custom system calls to ubuntu with kernel version >= 3.16?
Thank you!



[1]: [https://arvindsraj.wordpress.com/2012/10/05/adding-hello-world-system-call-to-linux/](https://arvindsraj.wordpress.com/2012/10/05/adding-hello-world-system-call-to-linux/)

---

