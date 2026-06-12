---
title: "Trying to understand i686 architecture"
date: 2010-02-24
forum: Programming Talk
---

### Post by jacksmash on 2010-02-24
Hi,

I'm hoping someone can help me with this.

The command `uname -r` gives the following output on my machine:

```
Linux ***-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```

(Note: I am running Ubuntu 9.04 on VirtualBox)

Here is some code that I am trying to run:

```

#include <stdio.h>

void function(int a, int b, int c) {
  char buffer1[5];
  char buffer2[10];
  int *ret;

  ret = (int *)buffer1 + 16;
  (*ret) += 7; // have checked to make sure we need 7 bytes to skip x=1;
}

void main() {
  int x;

  x = 0;
  function(1,2,3);
  x = 1;
  printf("%d\n",x);
}


```

The goal of the above code is to skip the instruction `x = 1;`, and so the output of the printf statement should be "0".

However, in order to do that I need to know precisely how much to increment the return pointer in "function". This is where I'm a bit stuck.

I have been reading an article that has been somewhat helpful:

[http://www.ethicalhacker.net/content/view/122/2/]("http://www.ethicalhacker.net/content/view/122/2/")

It has helped me to understand that the `(*ret) += 7;` statement is likely correct.

Here is an assembly dump of the main function:

```

(gdb) disassemble main
Dump of assembler code for function main:
0x08048404 <main+0>:	push   %ebp
0x08048405 <main+1>:	mov    %esp,%ebp
0x08048407 <main+3>:	sub    $0x10,%esp
0x0804840a <main+6>:	movl   $0x0,-0x4(%ebp)
0x08048411 <main+13>:	movl   $0x3,0x8(%esp)
0x08048419 <main+21>:	movl   $0x2,0x4(%esp)
0x08048421 <main+29>:	movl   $0x1,(%esp)
0x08048428 <main+36>:	call   0x80483e4 <function>
**0x0804842d <main+41>:	movl   $0x1,-0x4(%ebp)** <-- *the instruction to skip*
0x08048434 <main+48>:	mov    $0x8048510,%eax
0x08048439 <main+53>:	mov    -0x4(%ebp),%edx
0x0804843c <main+56>:	mov    %edx,0x4(%esp)
0x08048440 <main+60>:	mov    %eax,(%esp)
0x08048443 <main+63>:	call   0x804831c <printf@plt>
0x08048448 <main+68>:	leave  
0x08048449 <main+69>:	ret    
End of assembler dump.

```

Since we want to skip the statement at 0x0804842d and get to 0x08048434, we can calculate the difference to by 7 bytes easily enough. Hence, that's why I know it's correct to increment the ret pointer by 7.

What I can't figure out for the life of me is how many bytes have been allocated on the stack.

The memory layout should be like this:

```

bottom of                                                                                    top of
memory                                                                                       memory
                              buffer2     buffer1     sfp     ret 
<------                    [            ][           ][     ][     ]

top of                                                                                        bottom of
stack                                                                                         stack

```

My best guess is from this line:

```
0x08048407 <main+3>:	sub    $0x10,%esp
```

... which suggests 16 bytes have been allocated, hence: `ret = (int *)buffer1 + 16;`

But, compiling and executing the program does not result in skipping the x=1 command.

So, I'm not asking anyone to tell me what the answer is (believe it or not). in terms of what the right number is. Rather, I'm hoping that someone can point me in the right direction so I can understand the stack layout on the machine.

Hope this makes sense. Thanks for any advice!!

---

### Post by uljanow on 2010-02-24
Just fill the instruction in the binary with NOPs.

---

### Post by Bill Zimmerly on 2010-02-24
Here's my hint:

(gdb) disass function <Enter>

And keep in mind that THAT is where the code is running. ;)

---

### Post by jacksmash on 2010-02-25
Thanks, guys. Yes, I realize that the code is running in 'function'.

Output:

```

(gdb) disass function
Dump of assembler code for function function:
0x080483e4 <function+0>:	push   %ebp
0x080483e5 <function+1>:	mov    %esp,%ebp
0x080483e7 <function+3>:	sub    $0x14,%esp
0x080483ea <function+6>:	lea    -0x9(%ebp),%eax
0x080483ed <function+9>:	add    $0x10,%eax
0x080483f0 <function+12>:	mov    %eax,-0x4(%ebp)
0x080483f3 <function+15>:	mov    -0x4(%ebp),%eax
0x080483f6 <function+18>:	mov    (%eax),%eax
0x080483f8 <function+20>:	lea    0xa(%eax),%edx
0x080483fb <function+23>:	mov    -0x4(%ebp),%eax
0x080483fe <function+26>:	mov    %edx,(%eax)
0x08048400 <function+28>:	leave  
0x08048401 <function+29>:	ret    
End of assembler dump.

```

From this it seems that 20 bytes are allocated on the stack. So maybe I need to be adding 20 instead of 16. I'm not really sure.

---

