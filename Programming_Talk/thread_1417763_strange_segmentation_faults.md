---
title: "strange segmentation faults"
date: 2010-02-27
forum: Programming Talk
---

### Post by felinethropist on 2010-02-27
Hi, 

I was trying out this code : 

#include<stdio.h>

void main()
{  char exp[] = {};
    char*ptr = exp;
    char a;
    int i=0;
    printf("enter the expression : \n");
    while((int)(a=getchar()) != 10)
    {
        *ptr = a;
         ptr++;
       
        
    }
*ptr = '\0';
ptr = exp;
putchar('\n');

    putchar('\n');
    puts(exp);
    putchar('\n');
    puts(ptr);
}

the strange thing about this is :
1. it gives a segmentation fault for an input bigger than 12 characters on my 32 bit   
    machine.
2. it does not give a segmentation fault for any input on my friend's 64 bit machine
3. it gives a an 'aborted' error for 28 chars input, and seg fault for 29 char input  on my 
    64 bit machine
4. it gives a seg fault for input bigger than 8 chars on my other friend's 64 bit machine

can someone help me understand why?

Thanks

---

### Post by dwhitney67 on 2010-02-27
This is why...
```

char exp[] = {};

```
You have not allocated any space on the stack for this array.  How do you expect to put anything into this array without corrupting memory in the process.  Jeez...  ](*,)

---

### Post by felinethropist on 2010-02-27
I am aware that I have not allocated the array size. 

But if that is the case, then why does it work for a small size input? and that too for different input sizes on different machines?

It should give an error at the beginning itself if array size is the problem.

---

### Post by lisati on 2010-02-27
> **felinethropist said:**
> I am aware that I have not allocated the array size. 

But if that is the case, then why does it work for a small size input? and that too for different input sizes on different machines?

It should give an error at the beginning itself if array size is the problem.

You could have been lucky. For the most part, C assumes that you know what you're doing, and doesn't hold your hand with run-time error checking to the same extent as some of the other languages I've used.

---

### Post by felinethropist on 2010-02-27
I don't think it is about being lucky. 

There's something that happens in stack allocation on different machines when array size is not mentioned and I am trying to find that out.

---

### Post by Simon17 on 2010-02-27
Use code tags.

The correct prototype for main is 
```
int main(void)
```

Just because the code accidentally works some of the time doesn't make it correct.

---

### Post by felinethropist on 2010-02-27
I don't think declaring main differently solves the segmentation fault problem though. 
But thanks for pointing that out.

---

### Post by MadCow108 on 2010-02-27
errors on stack are dependent various parameters like compiler implementation, compiler flags, machine architecture, calling conventions, used C library, the operating system, stack alignment and probably loads more.
What happens with when you mess up the stack is not standardized in any way.

So there is no definite answer.
We can just say your code is most likely faulty and definitely non-portable (assuming your error was intentional to produce a certain effect)

---

### Post by felinethropist on 2010-02-27
Even I thought so but was looking for a definitive answer. 

Thanks

---

### Post by pbrane on 2010-02-27
when your code is compiled on my 64-bit machine and run in gdb, 32 bytes are allocated on the stack.
```

Dump of assembler code for function main:
0x00000000004005c4 <main+0>:	push   rbp
0x00000000004005c5 <main+1>:	mov    rbp,rsp
0x00000000004005c8 <main+4>:	sub    rsp,0x20 **<--- 32 bytes on the stack**
0x00000000004005cc <main+8>:	mov    DWORD PTR [rbp-0x14],edi
0x00000000004005cf <main+11>:	mov    QWORD PTR [rbp-0x20],rsi
0x00000000004005d3 <main+15>:	mov    QWORD PTR [rbp-0x10],rbp
0x00000000004005d7 <main+19>:	mov    DWORD PTR [rbp-0x8],0x0
.
.
.
.

```

I think you are just overwriting the stack frame. Why don't you run it in a debugger and see what you get. I can only get 7 chars, 8 gives a SIGSEGV.

---

### Post by felinethropist on 2010-02-27
I ran it in gdb and it gives this :

```

Program received signal SIGSEGV, Segmentation fault.
0x080484ec in main () at pointer.c:25
25    }
(gdb) bt
#0  0x080484ec in main () at pointer.c:25
(gdb) list
20        putchar('\n');
21        puts(exp);
22        putchar('\n');
23        puts(ptr);
24        return 0;
25    }

```
what should I make out from this?

---

### Post by MadCow108 on 2010-02-27
depends on what you want to know...
above just tells you there was an segmentation violation while executing main.

to see whats going on exactly you'll have to read about how the stack is organized on your system and how it is handled by the compiler (don't forget gcc has a stack protector on by default).

---

### Post by pbrane on 2010-02-28
in gdb type **disassemble main**. Then you can look at the instructions and see if this starts to make any sense. Do what MadCow108 says, read about how the x86 uses the stack and how gcc compilers setup the stack. What you are doing is a stack based buffer overflow. As MadCow pointed out gcc tries to protect against this type of exploit.

---

### Post by felinethropist on 2010-02-28
Thanks guys. Will read some more and post back.

---

