---
title: "How to find the active TCP and PIDs corresponding to them in Linux programming?"
date: 2010-10-19
forum: Programming Talk
---

### Post by tetelee on 2010-10-19
Hi all,

I am programming on Linux middleware so I need to get a list of all active TCP connections. Is there any API to get such information? I know I can find the connections in /proc/net/tcp, but how to find the PIDs corresponding to the connections? Apparently ps or netstat command is not an option since it is a middleware. Any help will be appreciated!

Cheers
Tete

---

### Post by johnl on 2010-10-19
```

$ sudo lsof -i tcp:22

```

Will work, but I suspect you can't use lsof.  So you need to do what it's doing :).   I took a look at the strace of the above and it looks like it combines the information in /proc/net you are talking about with any socket file descriptors it finds in each /proc/<proc-id>/fd/<fd-num>

---

### Post by tetelee on 2010-10-19
> **johnl said:**
> ```

$ sudo lsof -i tcp:22

```

Will work, but I suspect you can't use lsof.  So you need to do what it's doing :).   I took a look at the strace of the above and it looks like it combines the information in /proc/net you are talking about with any socket file descriptors it finds in each /proc/<proc-id>/fd/<fd-num>

Did you say any socket file descriptor in each /proc/<proc-id>/fd/<fd-num>? Will it be a huge search workload? I noticed that netstat with -p option will print the PID/Program name. But when I was checking the source code but I couldn't figure out how it does it (I am new to programming so hard for me to understand it). Thanks for your help!

---

