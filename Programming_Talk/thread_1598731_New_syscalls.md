---
title: "New syscalls"
date: 2010-10-16
forum: Programming Talk
---

### Post by laryf on 2010-10-16
Hi
i'm trying to create a new syscall for a project in college
i'm suppose to create the syscall msg_recv and msg_send
witch already exists in the kernel code

anyway.. i create both and compile the kernel
but i'm having a little trouble
when i compile the kernel i receiving the follow errors:
multiple definition of `l'
or
undefined reference to `l'

---

### Post by Some Penguin on 2010-10-16
Don't declare variables in header files.

Exception:  'extern' variables, which declare existence of but do not define them.

---

### Post by laryf on 2010-10-17
> **Some Penguin said:**
> Don't declare variables in header files.

Exception:  'extern' variables, which declare existence of but do not define them.

but i need a global variable
cause i'm using in both syscalls

---

### Post by dwhitney67 on 2010-10-17
> **laryf said:**
> but i need a global variable

Rarely should one ever use the word "need" in such a context.

You chose to separate your receive and send functions into separate modules, and thus you forced yourself into a position where now you must use a global variable.  But there are alternatives....

1.  Implemented both receive and send functions in one module;

2.  Keep both receive and send function in separate modules, but have one of the modules provide an accessor function where the "l" object can be obtained.  For instance, in msg_recv.c:
```

...

static Lista l;

Lista getLista()
{
   return l;
}

```

3.  Implement a third module, say called decl.c, and from within it define a macro that instructs your common header file to declare the Lista; if the macro is not defined, then you extern the variable as Some Penguin indicated.  For example:
decl.c:
```

#define MODULE_DECL

#include "struct.h"

```
struct.h:
```

...

#ifdef MODULE_DECL
   LISTA l;
#else
   extern LISTA l;
#endif

...

```

P.S.  Some criticisms of your code:

1.  Avoid the use all uppercase letters for a name that identifies a structure; use uppercase letters only when defining a macro.  For example
```

typedef struct msg* Lista;    /* don't use LISTA */

```

2.  Don't typedef a pointer to a structure.  It would be better to do:
```

typedef struct msg Lista;

#ifdef MODULE_DECL
   Lista* l;         /* note how the pointer is specified here */
#else
   extern Lista* l;
#endif

```

3.  Your sys_msg_send's last parameter, buf, should be declared const.

4.  And for heaven's sake, use the space-bar when writing code.
```

struct msg* prox;   /* this is easier to read */

/* versus */

struct msg*prox;

```

---

### Post by laryf on 2010-10-17
msg_recv/msg_recv.c:12: error: conflicting types for &#8216;l&#8217;
include/linux/struct.h:24: note: previous declaration of &#8216;l&#8217; was here
msg_recv/msg_recv.c:15: warning: function declaration isn&#8217;t a prototype
msg_recv/msg_recv.c: In function &#8216;sys_msg_recv&#8217;:
msg_recv/msg_recv.c:30: error: invalid operands to binary == (have &#8216;Lista&#8217; and &#8216;void *&#8217;)
msg_recv/msg_recv.c:37: error: incompatible types when assigning to type &#8216;struct msg *&#8217; from type &#8216;Lista&#8217;
msg_recv/msg_recv.c:48: error: incompatible types when assigning to type &#8216;Lista&#8217; from type &#8216;struct msg *&#8217;

the problem is that i have a process in user level that send a message witch is storage in a list in kernel level
and another process in user level should get this message in the list

---

### Post by dwhitney67 on 2010-10-17
If I understand correctly, you are attempting to develop a Linux kernel module, but you have never, ever, developed a multi-module C program before.  Is this assessment correct?

I provided you with 3 options, and it appears that you decided to formulate a 4th using pieces of the first 3.  :confused:

Why are you including a .c file within your other .c files?

Why are you re-declaring the Lista object within msg_recv.c?

**Take a look at the attached tar-ball which employs option 3; this seems to be a close approximation with which you were trying to build.**

Btw, the <linux/struct.h> file does not exist on my system.  I'm using Ubuntu 10.04, with kernel revision 2.6.32-25-generic.  Where are you getting this file from?

---

### Post by laryf on 2010-10-17
struct.h is mine... and i put it on /linux/include/linux/ =P
but already remove it

now i'm getting this error:
arch/x86/built-in.o: In function `sys_call_table':
(.rodata+0x554): undefined reference to `sys_msg_recv'
arch/x86/built-in.o: In function `sys_call_table':
(.rodata+0x558): undefined reference to `sys_msg_send'

i create the syscall following the steps:

in /.../linux/arch/x86/kernel/syscall_table32.S
i add .long sys_msg_send and .long sys_msg_recv

in /.../linux/include/asm_generic/unistd.h
i add #define __NR_msg_recv 1079 and  #define __NR_msg_send 1080
and increase NR_system calls

in /.../linux/include/linux/syscalls.h
i add asmlinkage long sys_msg_recv(int pid_remet, int pid_dest, int msgsz, int __user *buf)
and asmlinkage long sys_msg_send(int pid_remet, int pid_dest, int msgsz, const int __user *buf)

in /.../linux/Makefile i add msg/ in core-y

and in /.../linux/ i create the folder 'msg' which contains the files: decl.c, header.h, Makefile, msg_recv.c and msg_send.c

the file header.h has 5 includes: 
#include <linux/module.h>
#include <linux/linkage.h>
#include <linux/slab.h>
#include <linux/kernel.h>
#include <asm/uaccess.h>

am i missing something?

---

