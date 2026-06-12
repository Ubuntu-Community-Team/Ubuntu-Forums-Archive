---
title: "Kernel Compile troubles after making changes"
date: 2012-05-29
forum: Packaging and Compiling Programs
---

### Post by Doug S on 2012-05-29
Only for a test, and only for a test computer, I am trying to backport a kernel.org proposed change to a previous kernel version. I can not get it to compile.
 
Compiling an unaltered kernel works fine, as does compiling several other test versions, but with only simple changes within the existing structure. The difference between this version and the others is the deletion and replacement of one procedure.
 
The error:```
  CC [M]  fs/xfs/xfs_sysctl.o
  CC [M]  fs/xfs/xfs_ioctl32.o
  LD [M]  fs/xfs/xfs.o
  LD      fs/built-in.o
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/doug/temp-kernel/linux-3.2.0'
make: *** [/home/doug/temp-kernel/linux-3.2.0/debian/stamps/stamp-build-generic] Error 2
```
 
The kernel I am working with: 3.2.0-24-generic #37, which is structured quite differently than the most recent kernel.org kernels. In the file /kernel/sched.c the function update_cpu_load is deleted and a new function update_idle_cpu_load is added. There is also a call change in sched_fair.c. I have searched the entire file structure and can not find where kernel 3.2.0.24 has the equivalent of this part of the kernel.org changes:```
diff --git a/kernel/sched/sched.h b/kernel/sched/sched.h
index 7282e7b..ba9dccf 100644
--- a/kernel/sched/sched.h
+++ b/kernel/sched/sched.h
@@ -876,7 +876,7 @@ extern void resched_cpu(int cpu);
extern struct rt_bandwidth def_rt_bandwidth;
extern void init_rt_bandwidth(struct rt_bandwidth *rt_b, u64 period, u64 runtime);
 
-extern void update_cpu_load(struct rq *this_rq);
+extern void update_idle_cpu_load(struct rq *this_rq);

```i.e. I didn't expect my compile to work just yet, but I at least hoped to get a more insightful error message.
 
Any suggestions as to how I can get further with this? Or just how to increase verbose information?
 
Reference:
[http://www.serverphorums.com/read.php?12,495685,495685](http://www.serverphorums.com/read.php?12,495685,495685)
 
My compile kernel script (since I can never remember the commands):```
doug@s15:~/temp-kernel/linux-3.2.0$ cat compile_kernel
#! /bin/bash
time fakeroot debian/rules clean
AUTOBUILD=1 NOEXTRAS=1
time fakeroot debian/rules binary-generic
```
Edit: I tried just leaving the name "update_cpu_load" for what should be "update_idle_cpu_load", so kernel/sched_fair.c becomes unchanged and there are only changes in kernel/sched.c. However, the compile error is the same. So I have some issue in my backport edit.

---

### Post by Bachstelze on 2012-05-29
Normally, you use the V or W environment variables to enable verbose output with all the compiler messages. Since you are compiling your kernel The Debian Way&#8482;, I'm not sure if you can use that, but either way, you can just omit the Debian crud while testing.

---

### Post by Doug S on 2012-05-30
Thanks for the reply. I figured out how to compile not "the debian way" and with V=2 was able to see what I had done wrong via the increased verbose messages.
 
However, I wanted to go back to "the debian way", but found it was now broken and no longer worked. I ended up having to re-create the build environment from scratch and copy over my modified files.
 
Commands used, for my own future reference:```
make clean
make oldconfig
make V=2 bzImage
```

---

### Post by Doug S on 2012-06-18
What I am wondering now is if there is a way I can go back and forth between "the debian way" and the not "the debian way". i.e. how to I restore the ability to use "the debian way"?
Note: this is not very important, because now I just copy everything to another directory so that I don't ruin "the debian way".

---

### Post by Bachstelze on 2012-06-19
What exactly goes wrong now when you try to run the debian commands?

---

### Post by Doug S on 2012-06-19
If I try to go back to "the debian way" I get:```
[... deleted some stuff ...]
scripts/kconfig/conf --silentoldconfig Kconfig
.config:5454:warning: override: TREE_RCU changes choice state
#
# configuration written to .config
#
  Using /home/doug/zzzz/linux-3.2.0 as source for kernel
  /home/doug/zzzz/linux-3.2.0 is not clean, please run 'make mrproper'
  in the '/home/doug/zzzz/linux-3.2.0' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/doug/zzzz/linux-3.2.0'
make: *** [/home/doug/zzzz/linux-3.2.0/debian/stamps/stamp-prepare-tree-generic] Error 2
```If I then run 'make mrproper', things get worse (scripts disappear and such), so I don't anymore.

---

### Post by Bachstelze on 2012-06-19
I'm not really familiar with the Debian process so I'm afraid I can't help further. Perhaps try asking in the ubuntu-kernel mailing lists or IRC channel [https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam)

---

### Post by Doug S on 2012-06-19
Bachstelze: Anyway, thanks very much for your thoughts and help with this.

---

