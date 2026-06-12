---
title: "Strange files"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by thgthg on 2008-10-12
Hi all,

can anyone help me with with some info about the files under folder "/proc".
Why is it updating and creating new files all the time??

---

### Post by aeiah on 2008-10-12
the short answer is that /proc is actually a pseudo filesystem. it houses temporary files which describe ongoing processes that the kernel is dealing with.

the long answer is here:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/ch-proc.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/ch-proc.html)

---

### Post by forger on 2008-10-12
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/proc.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/proc.html)
> /proc is very special in that it is also a virtual filesystem. It's sometimes referred to as a process information pseudo-file system. It doesn't contain 'real' files but runtime system information (e.g. system memory, devices mounted, hardware configuration, etc). 

In simple english, it contains information about your processor, mounted devices, hardware, currently running processes (the numbers are process ID numbers, or PID in short)

---

### Post by thgthg on 2008-10-12
Ok, tnx for info!

---

