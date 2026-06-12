---
title: "Inline asm -&gt; MS to GNU ?"
date: 2011-01-28
forum: Programming Talk
---

### Post by WitchCraft on 2011-01-28
Do we have a resident inline-assembler Guru here ?

I need the below functions changed (to GNU inline assembly), so they compile with g++ (MinGW)


Context is this one:
[http://stackoverflow.com/questions/4823649/is-my-stdcall-wrapper-for-usercall-function-correct](http://stackoverflow.com/questions/4823649/is-my-stdcall-wrapper-for-usercall-function-correct)

Note:
```

int __stdcall func_hook_payload(int callnum, int* args);

```


The 3 functions I need changed:
```

__declspec(naked) void func_hook()
{
    __asm
    {
        push [esp + 4]          //int* - pArgs
        push ebx                //int - nArgs
        call func_hook_payload  //imo, you can even just jump to this, the stack should clean itsself up correctly
        retn
    }
}

```



```

__declspec(naked) void func_hook()
{
    __asm
    {
        lea eax,[esp + 4]       //int* - &nArg[0]: here we abuse the way the windows stack grows, creating a stack based buffer 
        push eax                //int* - pArgs
        push ebx                //int - nArgs
        call func_hook_payload
        retn
    }
}

```


```

void __declspec(naked) __stdcall CallTheOldVMFunc(int nArgs, int* pArgs)
{
    __asm
    {
        push ebx                //save ebx, its not a scratch register
        mov ebx,[esp + 8]       //set the number of args
        push [esp + 12]         //push the arg ptr
        call TheOldVMFunc
        pop ebx                 //restore ebx
        retn 8                  //ret and cleanup
    }
}

```

---

### Post by WitchCraft on 2011-01-29
bump.

---

### Post by worksofcraft on 2011-01-29
> **WitchCraft said:**
> bump.

AFIK the register usage and also call stack frames and all that is completely different between gcc and msvc. You might find something of interest about [inline assembler]("http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html") here but TBH I think you may be flogging a dead horse :shock:

---

### Post by SevenMachines on 2011-01-29
You could give intel2gas a try instead of going through all the intel->at&t standard changes by hand.
```
 $ intel2gas -c -I -o <output.c> <input.c>
```    -c        understand C style comments
    -I        convert inline assembler (intel to at&t only)

I've had reasonable joy using it in the past although its been a while

[EDIT] Sorry, i thought you were talking about a straight intel->gas syntax change, which this isnt :)

---

### Post by WitchCraft on 2011-01-30
> **SevenMachines said:**
> You could give intel2gas a try instead of going through all the intel->at&t standard changes by hand.
```
 $ intel2gas -c -I -o <output.c> <input.c>
```    -c        understand C style comments
    -I        convert inline assembler (intel to at&t only)

I've had reasonable joy using it in the past although its been a while

[EDIT] Sorry, i thought you were talking about a straight intel->gas syntax change, which this isnt :)


Nice find, but the result is not very convincing:
```


int __stdcall func_hook_payload(int callnum, int* args);


__declspec(naked) void func_hook()
{
      __asm__ (
MISMATCH: "        push [esp + 4]          "
        "pushl %ebx                  \n\t" //int - nArgs
        "call func_hook_payload      \n\t" //imo, you can even just jump to this, the stack should clean itsself up correctly
MISMATCH: "        retn"

       : // FIXASM: output regs/vars go here, e.g.:  "=m" (memory_var)

       : // FIXASM: input regs, e.g.:  "c" (count), "S" (src), "D" (dest)

       : // FIXASM: clobber list, e.g.:  "%eax", "%ecx", "cc"
    );
}


__declspec(naked) void func_hook()
{
      __asm__ (
        "leal 4(%esp),%eax           \n\t" //int* - &nArg[0]: here we abuse the way the windows stack grows, creating a stack based buffer 
        "pushl %eax                  \n\t" //int* - pArgs
        "pushl %ebx                  \n\t" //int - nArgs
        "call func_hook_payload      \n\t"
MISMATCH: "        retn"

       : // FIXASM: output regs/vars go here, e.g.:  "=m" (memory_var)

       : // FIXASM: input regs, e.g.:  "c" (count), "S" (src), "D" (dest)

       : // FIXASM: clobber list, e.g.:  "%eax", "%ecx", "cc"
    );
}


void __declspec(naked) __stdcall CallTheOldVMFunc(int nArgs, int* pArgs)
{
      __asm__ (
        "pushl %ebx                  \n\t" //save ebx, its not a scratch register
        "movl 8(%esp),%ebx           \n\t" //set the number of args
MISMATCH: "        push [esp + 12]         "
        "call TheOldVMFunc           \n\t"
        "popl %ebx                   \n\t" //restore ebx
MISMATCH: "        retn 8                  "

       : // FIXASM: output regs/vars go here, e.g.:  "=m" (memory_var)

       : // FIXASM: input regs, e.g.:  "c" (count), "S" (src), "D" (dest)

       : // FIXASM: clobber list, e.g.:  "%eax", "%ecx", "cc"
    );
}




```

---

### Post by SevenMachines on 2011-01-30
I didnt realise intel2gas was so old, worth a stab though.

gcc can actually use inlined intel assembly, my knowledge of it is very basic though. If its any help an extremely basic example follows.
[B]
* [/B]_**Hello AT&T**_
    
    The really very simplest hello world example in at&t style

hello-att.c:
```
#include <stdio.h>
#include <string.h>

char message[] = "Hello at&t!\n";
int len;

void hello(){
    __asm__ __volatile__  (
        "movl    $len,%edx        \n\t"
        "movl    $message,%ecx    \n\t"
        "movl    $1,%ebx            \n\t"
        "movl    $4,%eax            \n\t"
        "int    $0x80            \n\t"
    );
}

int main (int args, char * argv[]){
        len = strlen(message);
        hello();
        return 0;
}

``````
$ gcc -o hello-att hello-att.c 
$ ./hello-att 
Hello at&t!
```*** _Hello Intel_**

    The same thing in inlined intel

hello-intel.c
```
#include <stdio.h>
#include <string.h>

char message[] = "Hello intel!\n";
int len;

void hello(){
    __asm__ __volatile__(
        ".intel_syntax noprefix    \n\t"
        "mov edx,len    \n\t"
        "mov ecx,offset message    \n\t"
        "mov ebx,1    \n\t"
        "mov eax,4    \n\t"
        "int 0x80    \n\t"
    );
}

int main (int args, char * argv[]){
    len = strlen(message);
    hello();
    return 0;
}
```The intel changes are the addition of ".intel_syntax noprefix" as the first instruction to switch to intel style and...
```
$ gcc -o hello-intel hello-intel.c -masm=intel
$ ./hello-intel 
Hello intel!
```...the addition of -masm=intel to let gcc know we want intel and not at&t

I'm afraid thats about as advanced as i get :)

---

### Post by SevenMachines on 2011-01-31
Just as an example, though not necessarily how it *should* be done, i would probably do something like...
```

// For non win32 compilers, define away these calling conventions
// gcc will know whats best :)
#ifndef _WIN32
    #define __declspec(naked) 
    #define __stdcall
#endif

__declspec(naked) void func_hook()
{
     __asm__ __volatile__  (
        ".intel_syntax noprefix    \n\t"          // Tell gcc that we're intel, not at&t
        "push [esp + 4]         \n\t"
        "push ebx               \n\t"
        "call func_hook_payload \n\t"
        "ret                    \n\t"                               // use ret not retn and let compiler decide whats near or far
    );
}

// .....etc for other functions

```This would compile under gcc and mingw32 as a 'direct' translation, but i couldn't say whether it would need more indirect translation, a lot of my knowledge may be poor but i especially know literally nothing about windows these days.

---

### Post by WitchCraft on 2011-02-01
> **SevenMachines said:**
> Just as an example, though not necessarily how it *should* be done, i would probably do something like...
```

// For non win32 compilers, define away these calling conventions
// gcc will know whats best :)
#ifndef _WIN32
    #define __declspec(naked) 
    #define __stdcall
#endif

__declspec(naked) void func_hook()
{
     __asm__ __volatile__  (
        ".intel_syntax noprefix    \n\t"          // Tell gcc that we're intel, not at&t
        "push [esp + 4]         \n\t"
        "push ebx               \n\t"
        "call func_hook_payload \n\t"
        "ret                    \n\t"                               // use ret not retn and let compiler decide whats near or far
    );
}

// .....etc for other functions

```This would compile under gcc and mingw32 as a 'direct' translation, but i couldn't say whether it would need more indirect translation, a lot of my knowledge may be poor but i especially know literally nothing about windows these days.

Yep, that looks much better.
Funny, I knew about this once, but I seem to have forgotten it.
Thank you so much.

---

