---
title: "filp_open(exe) inside module"
date: 2009-05-01
forum: Programming Talk
---

### Post by karthikbalaji on 2009-05-01
Hi All,

I am trying to implement a capability model in linux. For this, first I add set of capabilities in the security namespace of any executable.

So when an executable executes ,it invokes system call (my own) to read its own security namespace to know its capability.

But inside the system call implementation I am unable to filp_open the executable to read its security namespace. I tried to filp_open(/proc/self/exe). It returns error 26 (file busy).

I also tried to use get_mm_exe_file() implemented in linux kernel like,
get_mm_exe_file(current->mm) which supposedly returns mm->exe_file. But the system simply crashes on encountering this call. 

Is there anyway to solve this issue ? Please ask me if any more clarifications are needed.

To simply put, executable -> invokes sys call -> sys call should read executables security namespace in extended attribute. But I am not even able to open the system call inside the syscall.

Thank you,
Karthik

---

### Post by karthikbalaji on 2009-05-01
Am I not clear ? Can someone suggest me the appropriate forum to ask this question ?

Thank you all,
Karthik.

---

