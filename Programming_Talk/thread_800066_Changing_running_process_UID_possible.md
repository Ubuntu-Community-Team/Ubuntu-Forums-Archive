---
title: "Changing running process UID: possible?"
date: 2008-05-19
forum: Programming Talk
---

### Post by ivze on 2008-05-19
I (and not only I) wonder, if it is possible to change UID of a running process, given root password. If this is found, that will be great for scripting. 
Thanks!

---

### Post by Tuna-Fish on 2008-05-19
Technically, yes. Practically, no. The process id is used to sort the kernel data structures, and determines where data of the process is placed. You could write a kernel module that creates a new process, copies to it all the data of the running process, and then removes the running one, but it would be hard, and it would break if the kernel changes.

The question that this brings up is why? I cannot imagine how being able to change a process number would make scripting easier. This leads me to believe that you are doing something wrong. Tell us what it is you are trying to do, and perhaps we can help with that.

---

### Post by ivze on 2008-05-19
UID="user identificator", or am i wrong? =)
Anyhow, i feel that the situation with uid will be the same to that of pid - no ways of implementing this, without kernel hacking. Am i right?

---

### Post by Thirtysixway on 2008-05-19
System > Administration > Users and Groups

You can add/edit users and their ID numbers

---

### Post by ivze on 2008-05-19
> **Thirtysixway said:**
> System > Administration > Users and Groups

You can add/edit users and their ID numbers
Thanks, I know. The task is different, however. =)

---

### Post by Tuna-Fish on 2008-05-19
> **ivze said:**
> UID="user identificator", or am i wrong? =)
Anyhow, i feel that the situation with uid will be the same to that of pid - no ways of implementing this, without kernel hacking. Am i right?

uh, yes. I completely misread that.

You cannot change the real uid either, but you can change the effective uid, by running code in the process. If you are a good enough hacker, you can write the code needed, assemble it, and somehow inject it into the process. (Perhaps into the open() library call, or malloc() ) Still hard, but easier than kernel hacking.

OFC, if you can change the sourcecode of the process, this turns into a trivial task.

---

