---
title: "Testing new system call -- syscall doesn't work from userspace"
date: 2012-02-11
forum: Programming Talk
---

### Post by Kdar on 2012-02-11
I was trying to add new system call to Linux Kernel: mynewcall (just to learn how to do it).
I followed this tutorial:
[http://tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/](http://tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/)

After I added new system call and compiled new kernel, I wrote basic test program to call that new system call:
```
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#define __NR_mynewcall 272

long mynewcall(int i){
        return syscall(__NR_mynewcall, i);
}

int main(void)
{
   printf("%d\n", mynewcall(15));
   return 0;
}
```
Then I reboot, boot into new kernel and try to execute my test program, however it doesn't seem to do anything at all.

Do I declare system call in a wrong way there?

---

### Post by nebukadnezzar on 2012-02-11
Are we supposed to guess the rest? ;)

Unfortunately it's close to impossible to help without any code...

---

### Post by Kdar on 2012-02-11
Ah right, sorry, here is my system call.

```
#include <linux/kernel.h>
#include <linux/linkage.h>
#include <linux/sched.h>

asmlinkage long sys_mynewcall(int i)
{
printk(KERN_DEBUG "Hello World! The number was %d \n", current->pid);
return i+10;
}
```

I added ```
.long sys_mynewcall /*349*/
``` to linux-3.2.5/arch/x86/kernel/syscall_table_32.S

I added ```
asmlinkage long sys_mynewcall(int i);
``` to  linux-3.2.5/include/linux/syscalls.h

I added 
```
#define __NR_mynewcall 349
__SYSCALL(__NR_mynewcall, sys_mynewcall)
```
to linux-3.2.5/include/asm-generic/unistd.h

---

### Post by Bachstelze on 2012-02-11
> **Kdar said:**
> 
I added 
```
#define __NR_mynewcall 349
__SYSCALL(__NR_mynewcall, sys_mynewcall)
```
to linux-3.2.5/include/asm-generic/unistd.h

Should be in arch/x86/include/asm/unistd_32.h.

*EDIT:* Also, you don't need te second line, and don't forget to increment NR_syscalls.

---

