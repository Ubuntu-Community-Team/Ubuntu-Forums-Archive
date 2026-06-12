---
title: "Time for &gt;&gt; operator"
date: 2008-03-31
forum: Programming Talk
---

### Post by jazzgossen on 2008-03-31
Does anybody know how well bash's >> operator for appending data to the end of a file scales with large files? And is there any difference between bash, dash or other shells?

---

### Post by ghostdog74 on 2008-03-31
why don't you try it out. 
get or create a large file, use the time command to determine the time it takes to append text to it.

---

### Post by drubin on 2008-03-31
not sure but I know logging files can get huge...  and they handle pretty well up to gigs. ?

You need to append more then gigs?

---

### Post by stroyan on 2008-03-31
The strace command will show you what system calls a process makes.
It shows that bash, dash, and ksh all react to the '>>' feature with the same
method.  They open the target file with an open(2) system call with an
O_APPEND bit in the flags parameter.  I expect that all shells do the same.

The O_APPEND mechanism is simple and efficient.
It causes the kernel to make all writes happen at the end of the file.
It will scale fine with large files.

---

