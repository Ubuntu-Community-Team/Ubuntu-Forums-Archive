---
title: "problem generating core files"
date: 2006-09-22
forum: Programming Talk
---

### Post by sunadrad on 2006-09-22
I need to do some corefile debugging, and I can't seem to change the corefile size with ulimit:

```

$ ulimit -c unlimited
bash: ulimit: core file size: cannot modify limit: Operation not permitted
$ ulimit -c 1000
bash: ulimit: core file size: cannot modify limit: Operation not permitted
```

And this is despite the fact that I've edited /etc/security/limits.conf to add the lines:

```

*               soft    core            0
*               hard    core            100000
```

I did reboot after making this change.  I am still wondering about permissions on this file, as pointed out by an old post on ubuntuforums, but right now, it's:

```

$ ls -l /etc/security/limits.conf
-rw-r--r-- 1 root root 1664 2006-09-22 10:43 /etc/security/limits.conf
```

Where are default limits are set if not in /etc/security/limits.conf (which was entirely commented lines before my change above)?

thanks,

wes


Some other possibly relevant things:
```

$ cat /proc/sys/kernel/core_uses_pid
0
$ cat /proc/sys/kernel/core_pattern
core
$ sudo -i
Password:
# ulimit -c unlimited
# ulimit -c
unlimited
```

I'm running kernel 2.6.15-26-686

---

