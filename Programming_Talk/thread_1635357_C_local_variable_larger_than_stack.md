---
title: "C local variable larger than stack"
date: 2010-12-01
forum: Programming Talk
---

### Post by 65 mustang on 2010-12-01
If you run
```
ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```
to get the size of your stack.

Then make a C program with local variables larger than that size what happens?
```
int main()
{
  double test[100000000][10000000000];  //Large variable

  //do something

  return(0);
}
```

I have a program like this and it seems to run fine but valgrind detects stack switching?

I know the answer is to put it on the heap but i want to know what linux/gcc does to allow the program to run so i can better understand linux/C/gcc.

Thanks,

---

### Post by Npl on 2010-12-01
your big constants will get truncated to 32 or 64 bit (size_t). use constants you know that dont overflow.
the definition alone does nothing, well atleast not accessing stack.

so you should use something like
char test[ 1 * (1 << 30)] = {0}; // allocate 1GB and initialize everything to 0, increase if nothing evil happens.

An whats gonna happen, Linux will reserve a given amount of addresspace for the stack to grow. This is different to allocating physical memory as its only making sure nothing else gets placed in the reserved space, physical memory is later allocated for the addresses as needed (if you access those addresses)
So stacksize is limited by reserved addresspace for the stack, and available memory to fill it. On 64 bit systems probably only the later should be a limitation

---

### Post by Arndt on 2010-12-02
> **65 mustang said:**
> 


Then make a C program with local variables larger than that size what happens?
```
int main()
{
  double test[100000000][10000000000];  //Large variable

  //do something

  return(0);
}
```

I have a program like this and it seems to run fine but valgrind detects stack switching?



I tried the following program, which tries to actually use the stack after the big array has been allocated on it, and it crashes:

```
#include <stdio.h>
#include <stdlib.h>

int f2()
{
  int a;
  printf("f2 %p\n", &a);
}

int f1()
{
  double test[100000000][10000000000];  //Large variable

  f2();
}

int f0()
{
  int a;
  printf("f0 %p\n", &a);
  f1();
}

int main()
{
  f0();

  return 0;
}

```


```
$ ./stk 
f0 0x7fff41b6793c
Bus error
$
```

As for what really happens, you can use the 'disass' command in gdb:

```
(gdb) disass f0
Dump of assembler code for function f0:
   0x0000000000400564 <+0>:	push   %rbp
   0x0000000000400565 <+1>:	mov    %rsp,%rbp
   0x0000000000400568 <+4>:	sub    $0x10,%rsp
   0x000000000040056c <+8>:	mov    $0x4006a3,%eax
   0x0000000000400571 <+13>:	lea    -0x4(%rbp),%rdx
   0x0000000000400575 <+17>:	mov    %rdx,%rsi
   0x0000000000400578 <+20>:	mov    %rax,%rdi
   0x000000000040057b <+23>:	mov    $0x0,%eax
   0x0000000000400580 <+28>:	callq  0x400418 <printf@plt>
   0x0000000000400585 <+33>:	mov    $0x0,%eax
   0x000000000040058a <+38>:	callq  0x400547 <f1>
   0x000000000040058f <+43>:	leaveq 
   0x0000000000400590 <+44>:	retq   

```

---

