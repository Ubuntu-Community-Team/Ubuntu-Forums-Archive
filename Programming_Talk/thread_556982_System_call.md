---
title: "System call"
date: 2007-09-22
forum: Programming Talk
---

### Post by DBQ on 2007-09-22
Hey guys.   I am trying to implement a system call in linux kernel.  I usually use ubutntu, but this I am doing on Fedora. I am using kernel 2.6.  Here is what I did:

1. Added a line to arch/i386/kernel/syscall_table.S: 

.long sys_foo

2. Added a line to linux/include/asm-i386/unistd.h:

#define __NR_foo               324

also incremented the call count by 1.

3. Added this code to sys.c

```

asmlinkage long sys_foo(void)
{
	printk("Hello Kernel World");
	return THREAD_SIZE;
}
[\code]

4. Wrote this user level client program to test my call:

[code]
#include <unistd.h>
#include <linux/unistd.h>


#define __NR_foo 324
__syscall0(long, foo)

int main()
{

foo();
return 0;
}


```

However, when I compile the user level program, I get the following error:

test.c:6: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;foo&#8217;
test.c: In function &#8216;__syscall0&#8217;:
test.c:9: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
test.c:6: error: parameter name omitted
test.c:13: error: expected &#8216;{&#8217; at end of input

Anybody has any idea?

---

### Post by gnusci on 2007-09-22
I really did not check very deeply your problem, but from the error output I think you are missing a "**;**", and I guess is after:

[PHP]
#include <unistd.h>
#include <linux/unistd.h>

#define __NR_foo 324
__syscall0(long, foo); <---- HERE

int main()
{

foo();
return 0;
}
[/PHP]

---

### Post by DBQ on 2007-09-22
I actually followed one of the examples.  And the examle did not have the semicolon.  Plus __syscall is a macro, and it does not require the ;. What else could it be?

---

### Post by gnusci on 2007-09-22
Ok, another possible cause of problems, here the notes:

[PHP]
#include <unistd.h> 
//#include <linux/unistd.h> // <--- the first one is enough


#define __NR_foo 324
_syscall0(long, foo) // <---- Use just one underscore

int main()
{

foo();
return 0;
}
[/PHP]

You also may need to include [COLOR="Red"]#include<linux/linkage.h>[/COLOR] into sys.c in order to use **asmlinkage**.

[PHP]
#include<linux/linkage.h>

asmlinkage long sys_foo(void)
{
printk("Hello Kernel World"); //<--- printf()
return THREAD_SIZE;
}
[/PHP]

Here a tutorial:

[http://tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/](http://tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/)

---

### Post by DBQ on 2007-09-22
Hey.  I tried your suggestions except the printf one.  Using printf is never allowed in the kernel land.  However, the error message persists.
Any other ideas?  Thanks for your support.

---

### Post by gnusci on 2007-09-23
> **DBQ said:**
> Hey.  I tried your suggestions except the printf one.  Using printf is never allowed in the kernel land.  However, the error message persists.
Any other ideas?  Thanks for your support.

Did you review all the steps in the tutorial above, specially step number **17**

**17. Testing our new system call**

---

### Post by vartak_kedar on 2007-09-29
Hi,

I was writing a system call after following the link
[http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/index.html](http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/index.html)

But then I am getting same error messages when I compile my test program to check whether my system call is working.

I have followed the steps exactly as given in the document, only instead of foo call I have used my xtime call with timespec structure.

I am getting the same error messages. It has been mentioned that the _syscall1/_syscall0 macros are defined in the unistd.h file but I dont find them there.

Help needed...

Thanks 
Kedar

---

### Post by LordShadow on 2007-10-04
Just try to compile your test program with the -D __KERNEL__ option (2 underscores before and after KERNEL). It should be something like:

gcc -D __KERNEL__ -o foo foo.c

---

### Post by regmee on 2008-08-21
(i will reply though the thread is very old)

"man _syscall"
This will tell u that after  kernel  2.6.18, the _syscall macros were removed from header files supplied to user space.  

You need to use syscall()  instead.


eg: 
```
#define __NR_sys_silly_copy 327

len_bytes_copied = syscall(__NR_sys_silly_copy, &temp, &dst, sizeof(unsigned long));

```


-regmee

---

