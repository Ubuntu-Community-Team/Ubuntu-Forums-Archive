---
title: "find command"
date: 2006-07-19
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2006-07-19
Can I avoid the cannot open and cannot search lines from the output of the find command?  I just want to print the line if the find the file is present else nothing.

**vijay@server: find / -name "tnsnames.ora" -type f -print**
find: cannot search /etc/ftpd
find: cannot open /etc/sam/custom
find: cannot open /etc/opt/resmon/persistence
find: cannot open /etc/opt/resmon/pipe
find: cannot open /stand/dlkm.vmunix.prev
find: cannot open /tmp/.AgentSockets
find: cannot open /tmp/install.dir.11040
find: cannot open /home/thoran
find: cannot open /home/oratst1
find: cannot open /home/arbort/.dt/Desktop
find: cannot open /home/emcftp
find: cannot open /home/oraprd1
find: cannot open /home/poconnel
find: cannot open /home/srussell
find: cannot open /home/arbslice/.dt/Desktop
find: cannot open /home/csgfxbcv/.dt/Desktop
find: cannot open /home/gbyrne/.dt/Desktop

---

### Post by jordilin on 2006-07-19
type the same command with sudo:
```
vijay@server: sudo find / -name "tnsnames.ora" -type f -print
```

---

### Post by x64Jimbo on 2006-07-19
Why not use Locate? I find it quite powerful and suited to all tasks that I have pitted it against.

---

### Post by cwaldbieser on 2006-07-19
> **vijayanand_sodadasi said:**
> Can I avoid the cannot open and cannot search lines from the output of the find command?  I just want to print the line if the find the file is present else nothing.

**vijay@server: find / -name "tnsnames.ora" -type f -print**
find: cannot search /etc/ftpd
find: cannot open /etc/sam/custom
find: cannot open /etc/opt/resmon/persistence
find: cannot open /etc/opt/resmon/pipe
find: cannot open /stand/dlkm.vmunix.prev
find: cannot open /tmp/.AgentSockets
find: cannot open /tmp/install.dir.11040
find: cannot open /home/thoran
find: cannot open /home/oratst1
find: cannot open /home/arbort/.dt/Desktop
find: cannot open /home/emcftp
find: cannot open /home/oraprd1
find: cannot open /home/poconnel
find: cannot open /home/srussell
find: cannot open /home/arbslice/.dt/Desktop
find: cannot open /home/csgfxbcv/.dt/Desktop
find: cannot open /home/gbyrne/.dt/Desktop

I think the errors are printed to stderr, so you should be able to redirect them:
```

$ find / -name "tnsnames.ora" -type f -print 2> /dev/null

```

---

