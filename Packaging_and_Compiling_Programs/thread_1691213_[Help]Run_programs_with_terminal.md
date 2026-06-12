---
title: "[Help]Run programs with terminal"
date: 2011-02-19
forum: Packaging and Compiling Programs
---

### Post by 4ndr3w88 on 2011-02-19
Hi guys,
After build two programs in C with the terminal (client.c and server.c), i try to execute them(./server and ./client 127.0.0.1) but it show me that i haven't authorized, Why?With others terminals, for example at the university, they run. But on my notebook, even if in the account settings i've set administrator grant, they don't run.

---

### Post by SevenMachines on 2011-02-19
Do your program files have the executable flag set? For example,
```
$ ./hello
bash: ./hello: Permission denied
$ chmod +x hello
$ ./hello 
hello!

```

---

