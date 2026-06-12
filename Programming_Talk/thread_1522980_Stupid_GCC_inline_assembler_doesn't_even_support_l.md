---
title: "Stupid GCC inline assembler doesn't even support local variable"
date: 2010-07-02
forum: Programming Talk
---

### Post by xuancong on 2010-07-02
Hi,
 
It's good that GCC support inline assembly Intel syntax, but it cannot even simply address local variables/parameters properly, making itself stupid and essentially useless, look at the following example:
```

// In MSVC, this compiles successfully
int main(int argc, char *argv[])
{
        int x=1, f=2, fa=3;
        __asm{
                    int 3
                    mov eax, [x+4]
                    movss xmm1,[f+4]
                    fld [fa+4]
        }
        return 0;
}

```
 
```

// In GCC AT&T syntax, this compiles successfully
int main(int argc, char *argv[])
{
        int x=1, f=2, fa=3;
        asm("int $0x3");
        asm("mov 4%0,%%eax"::"m"(x));
        asm("movss 4%0,%%xmm1"::"m"(f));
        asm("fld 4%0"::"m"(fa));
        return 0;
}
 

```
 
```

// In GCC Intel syntax, this would fail to compile
int main(int argc, char *argv[])
{
        int x=1, f=2, fa=3;
        asm(".intel_syntax noprefix\n"
               "int 3\n"
               "mov eax, [x+4]\n"
               "movss xmm1,[f+4]\n"
               "fld [fa+4]\n"
               ".att_syntax\n");
        return 0;
}
 

```
The third piece of code would fail to compile under GCC, because although it supports intel syntax it cannot handle local variables nor function parameters. I hope future versions of GCC can support this feature better. Thanks!
 
Best regards,
Wang Xuancong

---

### Post by MadCow108 on 2010-07-03
either locate the variables with help of the stack pointer or use gcc's extended syntax:
[http://gcc.gnu.org/onlinedocs/gcc/Extended-Asm.html](http://gcc.gnu.org/onlinedocs/gcc/Extended-Asm.html)

---

### Post by xuancong on 2010-07-03
I've tried both, but how much stack is allocated for each local variable/parameter, what's their order, how many padding bytes in between, these are all compiler option dependent, will mess up unless I code my own compiler, so forget about it.
As I've already shown that the AT&T GCC extended syntax is inferior to Intel syntax, there are certain particular sequences of particular instructions which AT&T just cannot handle.

---

### Post by xb12x on 2010-07-03
Instead of writing in-line assembly, perhaps you could write your assembly in a seperate, pure assembly file which could be linked during the build.

Also, if you're not comfortable with AT&T style assembly, have a look at NASM, the Netwide Assembler.  I've used it many times. It's very good.

[http://www.nasm.us/](http://www.nasm.us/)

---

### Post by mmix on 2010-07-03
you can use intel syntax on gcc

[http://xorl.wordpress.com/2009/01/01/intel-syntax-on-gcc/](http://xorl.wordpress.com/2009/01/01/intel-syntax-on-gcc/)

---

### Post by paulsm on 2010-07-03
Hi -

> As I've already shown that the AT&T GCC extended syntax is inferior  to Intel syntax, there are certain particular sequences of particular  instructions which AT&T just cannot handle.

As far as I can tell, you have done NO such thing.

Could you please cite a specific example of something you can't do in AT&T syntax?

---

### Post by xuancong on 2010-07-04
Hey guys,
 
I don't blame things for no reason and I have already searched throughout Google and manuals and tried all possible ways but still cannot find the solution. In fact if any one of you can translate the following 3 instructions into GCC inline assembly syntax, either AT&T or Intel, the entire problem is solved:
```

// x, f and fa are either local variables or function parameters
// MSVC inline syntax --> GCC intel or AT&T inline syntax
mov eax, [x]  -->    ""::"a"(x)
mov eax, [x+4]   --> ?
movss xmm1,[f+4]   --> ?
fld dword ptr [fa+4] --> ?

```
As you can see that I've already figured out how to translate the 1st instruction exactly as it is. Take note that you are not allowed to make use of any other registers since all of them are in use; and you are not allowed to pushing any registers onto stack and use them temporarily since that will slow down speed.
 
Thanks!
XC

---

### Post by xb12x on 2010-07-05
Fist problem: 
Either make x, f, fa global varialbles or you will have to get them from the stack using the stack-pointer register ebp.   

Second problem:
_*fld*_ and _*movss*_ instructions require an unambiguous size(when using Intel syntax):  

The following is my guess at what you are trying to accomplish.

Notice the call to MyAsm(x, f, fa) where x,f,fa are left to right. They are pushed onto the stack growing DOWN. In MyAsm the x parameter is pulled using [ebp *_minus_* 4], f at [ebp-8], fa at [ebp-0xC].

This file (inline.c) builds on my Ubuntu installation. Look at the list-file (inline.lst) to see the assembly output of the C compiler. This might help you to see how the stack works during calls, so you can make changes and verify you get what you need, etc

gcc -o inline inline.c -g
objdump --source inline >inline.lst

// inline.c
int MyAsm(int x, int f, int fa)
{[INDENT]         asm(".intel_syntax noprefix\n"
[/INDENT][INDENT]                "int 3\n"
               "mov eax, [(ebp-4)+4]\n"
               "movss xmm1, dword ptr [(ebp-0x8)+4]\n"
               "fld dword ptr [(ebp-0xC)+4]\n"
               ".att_syntax\n");
        return 0;
[/INDENT]}

int main(int argc, char *argv[])
{[INDENT]     int ret;

    ret = MyAsm(1, 2, 3);  
    return 0;
[/INDENT]}

---

### Post by xuancong on 2010-07-08
I've figured out how to solve half of the problem.
```

// x, f and fa are either local variables or function parameters
// MSVC inline syntax --> GCC AT&T inline syntax
mov eax, [x]  -->    "mov $0,%%eax"::"m"(x)
mov eax, [x+4]   --> "mov 4$0,%%eax"::"m"(x)
movss xmm1,[f+4]   --> "mov 4$0,%%xmm1"::"m"(f)
fld dword ptr [fa+4] --> "mov 4$0,%%eax"::"m"(fa)

```
 
The remaining problem is that if you look at the att syntax, it's far less clear than Intel syntax. So it would be better if gcc intel syntax can support local variables.
 
Addressing frame pointer [ebp+?] directly is dangerous, what if compiler reserve more stack space for diff. levels of debugging, or byte padding, in any way you don't know exactly where your variables/parameters are on the stack.
 
XC

---

### Post by xb12x on 2010-07-08
*"So it would be better if gcc intel syntax can support local variables."*
And if a frog had wings it wouldn't bump its butt when it hopped.

*"in any way you don't know exactly where your variables/parameters are on  the stack."*
Yes you do, because: 
'C' is statically typed. You're passing three ints.
  It's your code, your makefile (your compiler options), your preprocessor directives, your #pragma directives, and your readable comments for whoever maintains it.
  
And you can always look at the list file to double check.

Other choices are:  
Make the parameters have global scope. 
Don't write inline assembly. Write it in 'C' and optimize for speed. See #pragma directives.
Modify gcc to do what you want.

---

### Post by pbrane on 2010-07-10
Probably not the best idea, but you could re-work the function as NASM code and use **intel2gas** to convert. Maybe that will help you get started on this issue.

intel2gas is in the repos. I've not used it so I don't know how well it works.

you can take a look at it here:
[http://www.niksula.hut.fi/~mtiihone/intel2gas/]("http://www.niksula.hut.fi/~mtiihone/intel2gas/")

---

