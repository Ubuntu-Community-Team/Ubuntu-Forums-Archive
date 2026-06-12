---
title: "new to assembly difficult first assigment"
date: 2010-02-27
forum: Programming Talk
---

### Post by Tpolich on 2010-02-27
I have just started working with assembly and this is the first assignment. As you can see I am having some issues with it, any help would be really nice. I don't need answer just a some pointers and maybe a hint or two in the right direction.


```
(gdb) disass main
Dump of assembler code for function main:
0x080483c7 <main+0>:    lea    0x4(%esp),%ecx
0x080483cb <main+4>:    and    $0xfffffff0,%esp
0x080483ce <main+7>:    pushl  -0x4(%ecx)
0x080483d1 <main+10>:   push   %ebp
0x080483d2 <main+11>:   mov    %esp,%ebp
0x080483d4 <main+13>:   push   %ecx
0x080483d5 <main+14>:   sub    $0x18,%esp
0x080483d8 <main+17>:   movl   $0x5,-0xc(%ebp)
0x080483df <main+24>:   movl   $0xa,0x4(%esp)
0x080483e7 <main+32>:   mov    -0xc(%ebp),%eax
0x080483ea <main+35>:   mov    %eax,(%esp)
0x080483ed <main+38>:   call   0x8048394 <foo>
0x080483f2 <main+43>:   mov    %eax,-0x8(%ebp)
0x080483f5 <main+46>:   mov    $0x0,%eax
0x080483fa <main+51>:   add    $0x18,%esp
0x080483fd <main+54>:   pop    %ecx
0x080483fe <main+55>:   pop    %ebp
0x080483ff <main+56>:   lea    -0x4(%ecx),%esp
0x08048402 <main+59>:   ret
End of assembler dump.
(gdb) disass foo
Dump of assembler code for function foo:
0x08048394 <foo+0>:     push   %ebp
0x08048395 <foo+1>:     mov    %esp,%ebp
0x08048397 <foo+3>:     sub    $0x10,%esp
0x0804839a <foo+6>:     movl   $0x0,-0x4(%ebp)
0x080483a1 <foo+13>:    jmp    0x80483bc <foo+40>
0x080483a3 <foo+15>:    mov    0xc(%ebp),%eax
0x080483a6 <foo+18>:    add    %eax,0x8(%ebp)
0x080483a9 <foo+21>:    mov    -0x4(%ebp),%edx
0x080483ac <foo+24>:    add    $0x1,%edx
0x080483af <foo+27>:    mov    0xc(%ebp),%eax
0x080483b2 <foo+30>:    imul   %edx,%eax
0x080483b5 <foo+33>:    mov    %eax,0xc(%ebp)
0x080483b8 <foo+36>:    addl   $0x1,-0x4(%ebp)
0x080483bc <foo+40>:    cmpl   $0x3,-0x4(%ebp)
0x080483c0 <foo+44>:    jle    0x80483a3 <foo+15>
0x080483c2 <foo+46>:    mov    0x8(%ebp),%eax
0x080483c5 <foo+49>:    leave
0x080483c6 <foo+50>:    ret
End of assembler dump.
(gdb)
```

The questions I need to answer.

```
 Please answer the following questions:

   1. (10 Points) How many local variables does main() have?
      Where are they on the stack? (give an offset from ebp)

   2. (20 Points) How many parameters does main() pass to foo()?
      What are these values?

   3. (10 Points) Within foo() where (as an offset from ebp) are the parameters?

   4. (10 Points) How many local variables does foo() have?
      Where are they on the stack? (give an offset from ebp)

   5. (20 Points) Inside of foo() what are the values that both its parameters and local variables take on?

   6. (10 Points) What value does foo() return to main()?

   7. (20 Points) In C the code for main() looks something like:

      int main ()
      {
        /* Code to initializing local vars and call foo() */
        return(0);
      }

      Please get the assembly-language of main by saying:

      (gdb) disass main

         1. Which line(s) correspond to setting up for main?
         2. Which line(s) correspond to initializing local vars and call foo()?
         3. Which line(s) correspond to return(0);?
         4. Which line(s) correspond to cleaning up after main? 

```

What I have so far

```
1.

There are two local variables.
One with an offset from %ebp of -0xc or 3 down
Two with an offset from %ebp of -0x14 or 5 down

2.

main() passes one parameter to foo() that has a value of 5

3.

The single parameter has an offset of two down from %ebp

4.

There is one local variables

One with an offset from ebp of -0x4 of 1 down

5.


6.


7.

A. 10,11,13
B. 17,24
C. 56,59
D. 54,55
```

Thank you for any help in advance.

---

### Post by Lux Perpetua on 2010-02-27
It might help to "decompile" the assembly by hand to C code. In other words, name the local variables, replace the assembly instructions with C statements, replace the jumps with gotos, etc. Then (optionally) take a higher-level view of the control flow and rewrite it using loops and if-else as necessary. 

That's all I'm going to say for now. You didn't ask a specific question, so it's impossible for me to know what in particular is giving you trouble.

---

### Post by gnometorule on 2010-03-01
As lux said, I'd always try to parse back the underlying C program. I've recently only toyed with MIPS assembly, but from a quick look and what I remember, I believe this is (or is close to) the underlying program:

int main()
{   
    static int a =5;
    int b = 10;

    return foo(a);
}

int foo(int a)
{
   int i = 0;
   while (i <= 3)
        a += a*(++i);
   return a;
}

This should allow you to answer the questions; however, do cross check, in particular x86 conventions for arg-handoff as I didn't dig into those areas of the core dump (and don't really remember the conventions).

---------

How do you post this in the neat code window instead?

---

### Post by Majorix on 2010-03-01
You can't ask for help with your homework/assignment here. I am pretty sure it is stated somewhere in the rules.

---

### Post by LKjell on 2010-03-01
> **Majorix said:**
> You can't ask for help with your homework/assignment here. I am pretty sure it is stated somewhere in the rules.

The reason is plagiarism and the user that ask do not learn anything. However you might ask other question related to the task like how do I calculate the offset of the stack etc... It might sound stupid but you do learn something.

---

### Post by Majorix on 2010-03-02
> **LKjell said:**
> The reason is plagiarism and the user that ask do not learn anything. However you might ask other question related to the task like how do I calculate the offset of the stack etc... It might sound stupid but you do learn something.
 
I don't get what you say :p

---

