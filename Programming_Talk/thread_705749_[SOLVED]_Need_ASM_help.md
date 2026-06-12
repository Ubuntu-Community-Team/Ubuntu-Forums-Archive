---
title: "[SOLVED] Need ASM help"
date: 2008-02-23
forum: Programming Talk
---

### Post by WitchCraft on 2008-02-23
Hi!

I need a little help with asm code for my C++ program.
The problem is I need to lookup an OP-code from a gdb disassembly.

I need an operation that translates to a JMP rel32, or better direct a JMP rel32 in inline assembly, so that I can lookup the "JMP rel32" OP-Code value in GNU debugger (if it's translated to another platform).

Here  a little description:
OP-Code;	Mnemonic;	Description 
EB cb;	JMP rel8;	Jump short, relative, displacement relative to next instruction 
E9 cw;	JMP rel16;	Jump near, relative, displacement relative to next instruction 
E9 cd;	JMP rel32;	Jump near, relative, displacement relative to next instruction

I tried 
```

void function1()
{	
}


int main()
{
label1:
	int a = 5;
	int b=5 ;
	goto label1;
	function1();
	return EXIT_SUCCESS ;
}

```

but the OP-Code for goto was 0xEB and the OP Code for function1() was 0xE8.
But I need 0xE9...

I think it should be a jump to another function from inside a function...
But with C, i can only either call a function (call: 0xE8 ), and what i would need is a goto, but that doesn't work because I can't place a label inside another function (scope resolution)...

---

### Post by aks44 on 2008-02-23
> **WitchCraft said:**
> the OP-Code for goto was 0xEB and the OP Code for function1() was 0xE8.

Calling function1() actually issues a CALL, not a JMP. No wonder it uses the CALL (0xE8) op-code then.

As to why the goto uses the rel8 (0xEB) version of JMP instead of rel32 (0xE9) is simply because the displacement fits into the range -128/+127 and that GCC uses the most efficient op-code.


> **WitchCraft said:**
> But I need 0xE9...
Why? If you really want to code that close to the metal, use plain ASM not C... even that way there is no guarantee that you'll be able to get the assembler output a rel32 op-code unless you specifically craft your instructions by hand (DB 0xE9, ...).


EDIT: BTW double-posting is not a good idea, you should have edited your other post but nevermind now. -_-

---

### Post by luisito on 2008-02-23
I'm curious. Why would you need an operation that translates as JMP rel32????

---

### Post by WitchCraft on 2008-02-23
To copy the content of one function on the stack to another location, and place a jump to there in the original function...

---

### Post by Wybiral on 2008-02-23
If you already know the byte-values for the machine code, why not just JIT compile it (as in manually manipulate the machine code as an array)?

Or better yet, tell us why you need this :)

---

### Post by LaRoza on 2008-02-23
> **aks44 said:**
> 
EDIT: BTW double-posting is not a good idea, you should have edited your other post but nevermind now. -_-

That thread was removed. (Sort of, anyway.)

---

### Post by WitchCraft on 2008-02-23
> **aks44 said:**
> Calling function1() actually issues a CALL, not a JMP. No wonder it uses the CALL (0xE8) op-code then.

I already got that point when i read the disassembly.

> **aks44 said:**
> 
As to why the goto uses the rel8 (0xEB) version of JMP instead of rel32 (0xE9) is simply because the displacement fits into the range -128/+127 and that GCC uses the most efficient op-code.


Aaaaaaaaaargh...

> **aks44 said:**
> 
Why? 

That's becausse you jump inside a process's possible memory (0-4GB) if you relocate functions.
Now to write a generic code, you need the maximum size of a process addressable by the jump, or you will get situations, in which the code doesn't work.
and 2^32 = 4 GB... --> REL32

---

### Post by WitchCraft on 2008-02-23
> **LaRoza said:**
> That thread was removed. (Sort of, anyway.)

Thanks! (the double post was an accident (browser crash) )  ;-)

---

### Post by Fbot1 on 2008-02-23
... is it really just this?
```
void function1()
{	
}
```

---

### Post by aks44 on 2008-02-23
From the top of my head, you should be able to do something along the lines of:

```
int function1()
{
  printf("In function1\n");
  return 1;
}

int function2()
{
  printf("In function2\n");
  __asm
  {
    db 0xe9                             ; op-code for JMP rel32
    dd function1 - displacement_origin  ; displacement
  displacement_origin:
  };
  // will never be executed
  return 2;
}

int main()
{
  printf("Result is: %d\n", function2());
  return 0;
}
```

Just adjust the ASM part to use AT&T syntax rather than Intel... ;)

---

### Post by WitchCraft on 2008-02-23
> **aks44 said:**
> 
  __asm
  {
    db 0xe9                             ; op-code for JMP rel32
    dd function1 - displacement_origin  ; displacement
  displacement_origin:
  }


You got exactly the point of what I want to do. 
Well, actually I'm doing it with
#define DATATYPE_ADDRESS unsigned long

DATATYPE_ADDRESS address ;
address = (DATATYPE_ADDRESS*) malloc( 1 + sizeof (DATATYPE_ADDRESS)  );
memcpy(address, 0xE9,1) and then 
memset(address+1, lngRel32, sizeof (DATATYPE_ADDRESS))


But the problem is, if not x86, the OP-Code won't be 0xE9, that's why I want to read it out with gdb.

But my problem is that I need a instruction that equals to 0xE9 in C, so that I can get the disassembly.

---

### Post by WitchCraft on 2008-02-23
OK, so question for a workaround:

would if be possible to use call instead, and just pop once afterwards, to emulate a JMP Rel32? Or wouldn't that work?

---

### Post by aks44 on 2008-02-23
> **WitchCraft said:**
> would if be possible to use call instead, and just pop once afterwards, to emulate a JMP Rel32? Or wouldn't that work?

On x86 and most other platforms, that would work if the jumped-to function doesn't take arguments. It *may* differ on some platforms though.


Anyway, as soon as you start using assembly, it is impossible to avoid platform-dependency. So IMHO you may as well go with the kind of solution I gave, and have specific code for each architecture.

> But the problem is, if not x86, the OP-Code won't be 0xE9, that's why I want to read it out with gdb.
You got your info about JMP from the x86 reference manual, right? Other CPUs have one, too... ;)

---

### Post by WitchCraft on 2008-02-23
> **aks44 said:**
> 
Anyway, as soon as you start using assembly, it is impossible to avoid platform-dependency. 

True, but what I plan to do is to use GCC inline assembly, write a minimal application that contains CALL to a function, and place an inline asm pop somewhere.

Then I use GDB to get the OP-code for CALL and POP, and the I use these op-codes to patch functions at runtime.

Then I will write a define, so that you can set the jump rel32 opcode manually if automatic retrieving via GDB didn't work out for the respective platform.


> **aks44 said:**
> 
You got your info about JMP from the x86 reference manual, right? Other CPUs have one, too... ;)

Well, no, actually from a website that summarizes the important points of the reference manual in short ;-)))


> **aks44 said:**
> 
On x86 and most other platforms, that would work if the jumped-to function doesn't take arguments. It *may* differ on some platforms though.


Anyway, as soon as you start using assembly, it is impossible to avoid platform-dependency. So IMHO you may as well go with the kind of solution I gave, and have specific code for each architecture.


You got your info about JMP from the x86 reference manual, right? Other CPUs have one, too... ;)


As long as x86 and ppc works, maybe even sparc, that is good enough for me. ;-) 
The rest will have to do hands-on work themselves ;-)

---

### Post by WitchCraft on 2008-02-24
> **aks44 said:**
> 
Just adjust the ASM part to use AT&T syntax rather than Intel... ;)


Nah, that's not even necessary, you only need to quote it. Watch closely:

```

#include <iostream>

void myfunction()
{}

int main() 
{
  __asm (
    ".intel_syntax noprefix\n"
    "jmp farlabel\n"
     "mov  EAX,EAX\n"
     "farlabel:\n"
     "mov  EAX,EAX\n"
     ".att_syntax \n"
  );
  return 0;
}

```

---

### Post by supirman on 2008-02-24
You can just look up the instruction set for the different architectures.

On PPC, there are no jumps or calls, everything is a done with branch/branch and link instructions.  To call a function, you'd typically use 'bl', to branch and put the effective address of the next instruction in the link register.  Then to return from the called routine, you would 'bclr  20,0', which would unconditionally branch to the address contained in the link register.

---

### Post by WitchCraft on 2008-02-24
> **supirman said:**
> You can just look up the instruction set for the different architectures.

On PPC, there are no jumps or calls, everything is a done with branch/branch and link instructions.  To call a function, you'd typically use 'bl', to branch and put the effective address of the next instruction in the link register.  Then to return from the called routine, you would 'bclr  20,0', which would unconditionally branch to the address contained in the link register.

Oh, ok. Than there is anyway no more value in this little project (that is more complicated than I thought it would be). Thanks for this info!

---

