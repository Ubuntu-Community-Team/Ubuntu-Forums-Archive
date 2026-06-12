---
title: "share memory problem"
date: 2006-02-10
forum: Programming Talk
---

### Post by reza-ts on 2006-02-10
Hi all,

When we build a big share memory with 'shmget' and 'shmat' functions, we have no problem in RedHat linux. 
In Fedora 4 linux we get "Segmentation Fault" error with the same program. we must set 
"ulimit -s unlimited" in every terminal console that we open. 
Can anyone help me how can correct this problem permanently in fedora linux?


Thank you in-advance.

---

