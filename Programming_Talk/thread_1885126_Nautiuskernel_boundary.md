---
title: "Nautius/kernel boundary?"
date: 2011-11-22
forum: Programming Talk
---

### Post by thenilly on 2011-11-22
Hi,

I have a Nautilus/linux question.

Where is the boundary between the user-level and kernel-level code in the Nautilus source code? For example, when I double-click a text file, there is inevitably a call to sys_execve with '/usr/bin/gedit' as an argument. What if I wanted to dump a message in /var/log/syslog every time I double-clicked to execute an app? I know I can modify the kernel so that the execve system call does a 'printk', but what if I wanted to do it at the user-level?

Any pointers to relevant code/readme's will be greately appreciated!

---

### Post by crdlb on 2011-11-22
Nautilus probably does something like: ```

app = g_file_query_default_handler(file)
g_app_info_launch(app, file, ctx)
```

In the end, it runs g_spawn_async (or a related function), which eventually calls fork and execv(e). Those last functions are wrappers in the C library (ie glibc) that make the syscalls.

---

### Post by ehmicky on 2011-11-22
Hi,

I might be wrong but I don't think there's any boundary, cause Nautilus don't use "kernel-mode code" : it uses Glibc, which itself calls Linux syscalls, which triggers kernel code.

---

### Post by thenilly on 2011-12-02
Thanks. This definitely points me in the right direction.

---

