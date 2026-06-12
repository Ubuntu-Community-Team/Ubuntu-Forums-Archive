---
title: "Issue when I run a thread creation program"
date: 2012-09-18
forum: Programming Talk
---

### Post by rajendrapmn on 2012-09-18
Hi,
 When I try to execute a thread creation program I am getting the following error.
 allocate_stack: Assertion `size != 0' failed
 I am working on Ubuntu 12.04LTS and I am using glibc version 2.15.
 Please let me know if I have to install any additional packages to resolve this.
 
Thanks,
Rajendra

---

### Post by dwhitney67 on 2012-09-18
> **rajendrapmn said:**
> Hi,
 When I try to execute a thread creation program I am getting the following error.
 allocate_stack: Assertion `size != 0' failed
 I am working on Ubuntu 12.04LTS and I am using glibc version 2.15.
 Please let me know if I have to install any additional packages to resolve this.
 
Thanks,
Rajendra
Unless Google has something on the error you posted, it means nothing to regular people.  Why not post your code?... you will get much better help.  Or just look in your code (in allocate_stack) where you might be calling assert() or calling some other function that is.

---

### Post by rajendrapmn on 2012-09-19
dwhitney67,
 I had googled it and few people had faced this issue earlier.
 Anyway, thanks for your inputs. Figured out that I was not initializing the stacksize attribute correctly for the thread. Now it is working fine.
 
-Rajendra

---

