---
title: "Help with Asm in C code (GCC)"
date: 2014-02-15
forum: Programming Talk
---

### Post by dan60 on 2014-02-15
Hello guys,
Im trying to understand the how to code asm inside a C code. So, i want to use the "cpuid" assembly instruction, but im doing something wrong on the code:

```

#include <stdio.h>


int main()
{
   unsigned int maxBasicCPUID;
   char vendorString[13];
   char *vendorStringPtr=(char *)vendorStringPtr;


        __asm__("movl %a,%%edi\n\t"
                "movl $0,%eax\n\t"
                "cpuid\n\t"
                "movl %%eax,%0\n\t"
                "movl %ebx,(%edi)\n\t"
                "movl %edx,4(%edi)\n\t"
                "movl %ecx,8(%edi)\n\t"
                :"=g" (maxBasicCPUID)
                :"m" (vendorStringPtr)
                :"memory"
                );


        vendorString[12]=9;
        printf("maxBasicCPUID=%x, vendorString=%s\n", maxBasicCPUID,vendorString);


return 0;          
}

```

When i try to compile, i got the following error:

# gcc -o cpuid cpuid.c 
cpuid.c: In function ‘main’:
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter
cpuid.c:9: error: invalid 'asm': operand number missing after %-letter

Can anyone help me with that!?
Tks guys!

---

### Post by Bachstelze on 2014-02-15
What is %a supposed to represent?

---

### Post by xb12x2 on 2014-02-15
I'm going to suggest something that might get me lambasted by the purists here.

The AT&T syntax that you're trying to use has always been confusing. And it's never been popular, especially in the x86 world. And it's obsolete now that gcc supports the Intel syntax for inline assembly.

My reasons for using Intel syntax is that it's much easier to learn. Most of the assembly code in the world is written with it so you'll find many, many more examples of it. And I suspect that given the same level of expertise with both syntaxes you'll always code much quicker using the Intel syntax.

And don't think that you are forced to use the AT&T syntax becaue a C file you're modifying already has inline assembly with that syntax. You can add Intel style inline assembly without having to rewrite the existing inline assembly.

I really do believe that it could actually be quicker for you to start over with Intel syntax than trying to debug what you have.

Let me apologize for not making an effort to debug your code. I've forgotten whatever little I knew about the AT&T syntax as I purposley haven't used it for years.

Here is a link if you're interested the Intel syntax:
[http://www.rohitab.com/discuss/topic/28661-inline-assembly-on-gcc-using-intel-syntax/](http://www.rohitab.com/discuss/topic/28661-inline-assembly-on-gcc-using-intel-syntax/)

---

### Post by Bachstelze on 2014-02-15
> **xb12x2 said:**
> I'm going to suggest something that might get me lambasted by the purists here.

Yes, but not for the reason you are probbly thinking of: it's just completely irrelevant to the problem here.

---

### Post by xb12x2 on 2014-02-15
> **Bachstelze said:**
> Yes, but not for the reason you are probbly thinking of: it's just completely irrelevant to the problem here.

Totally uncalled for, Bachstelze, since it's not completely true. 

It's true I didn't debug his code, but how did your question "What is %a supposed to represent?" help him? If you know what the bug is why didn't you just tell him? Now that would have been relevant.

---

### Post by dan60 on 2014-02-15
> **xb12x2 said:**
> I'm going to suggest something that might get me lambasted by the purists here.

The AT&T syntax that you're trying to use has always been confusing. And it's never been popular, especially in the x86 world. And it's obsolete now that gcc supports the Intel syntax for inline assembly.

My reasons for using Intel syntax is that it's much easier to learn. Most of the assembly code in the world is written with it so you'll find many, many more examples of it. And I suspect that given the same level of expertise with both syntaxes you'll always code much quicker using the Intel syntax.

And don't think that you are forced to use the AT&T syntax becaue a C file you're modifying already has inline assembly with that syntax. You can add Intel style inline assembly without having to rewrite the existing inline assembly.

I really do believe that it could actually be quicker for you to start over with Intel syntax than trying to debug what you have.

Let me apologize for not making an effort to debug your code. I've forgotten whatever little I knew about the AT&T syntax as I purposley haven't used it for years.

Here is a link if you're interested the Intel syntax:
[http://www.rohitab.com/discuss/topic/28661-inline-assembly-on-gcc-using-intel-syntax/](http://www.rohitab.com/discuss/topic/28661-inline-assembly-on-gcc-using-intel-syntax/)

I actually dont mind using the Intel syntax, but can you help me with the code for intel ( and how to compile it)!?

---

### Post by xb12x2 on 2014-02-15
> **dan60 said:**
> I actually dont mind using the Intel syntax, but can you help me with the code for intel ( and how to compile it)!?  Since I made a suggestion it's only fair that I try to help with it.  But first let me give you a bit of code, AT&T syntax, that does the cpuid instruction, and some C code that calls it. Just to try to help you get quickly beyond the bug.  I know it worked at the time, but it's been several years since I wrote it.   If you're still interested in an Intel syntax version let me know and I'll try to help with it.  ```
 /******************************************************************************  ** GetCpuID        Executes a CPUID instruction  *  *  parameters:    The CPUID function to execute  *  *  returns:           results in eax, ebx, ecx, edx returned via pointer  *  */ volatile DWORD _eax, _ebx, _ecx, _edx; void GetCpuID(DWORD func) {     asm      (            "cpuid"         : "=a" (_eax),           "=b" (_ebx),           "=c" (_ecx),           "=d" (_edx)         : "a"  (func)     ); }     
```  The following code was written for unique, one-off hardware:  [CODE]  /******************************************************************************  ** ClearEccAbove4MB    Clears memory above 4MB in the first four dimms.   *                            The last two dimms are battery backed.  *  *  parameters:    none  *  *  returns:        none  *  *  This routine clears memory that is NOT battery-backed.  *  */  extern volatile DWORD _eax, _ebx, _ecx, _edx;  void ClearEccAbove4MB( void )[CODE] {     //     // Just for fun check for PSE-36 feature bit: EDX[17] for CPUID 1     //     GetCpuID( 1 );      // If PSE-36 not supported then return (this should never happen on Slammer).     if( !(_edx & (1

---

### Post by xb12x2 on 2014-02-15
> **dan60 said:**
> I actually dont mind using the Intel syntax, but can you help me with the code for intel ( and how to compile it)!?

I screwed-up my previous attemtp to post some code. Let me try again:

This is AT&T syntax that does cpuid, and following it is some code that calls it. 
This code worked at the time I wrote it several years ago, and was written for unique one-off hardware.


If you still want to write it in Intel syntax I be glad to try and help.



```
/******************************************************************************
 ** GetCpuID        Executes a CPUID instruction
 *
 *  parameters:    The CPUID function to execute
 *
 *  returns:        results in eax, ebx, ecx, edx returned via pointer
 *
 */
volatile DWORD _eax, _ebx, _ecx, _edx;
void GetCpuID(DWORD func)
{
    asm 
    (    
       "cpuid"
        : "=a" (_eax),
          "=b" (_ebx),
          "=c" (_ecx),
          "=d" (_edx)
        : "a"  (func)
    );
}    
```



```
/******************************************************************************
 ** ClearEccAbove4MB    Clears memory above 4MB in the first four dimms. 
 *                            The last two dimms are battery backed.
 *
 *  parameters:    none
 *
 *  returns:        none
 *
 *  This routine clears memory that is NOT battery-backed.
 *
 */
extern volatile DWORD _eax, _ebx, _ecx, _edx;

void ClearEccAbove4MB( void )
{
    //
    // Just for fun check for PSE-36 feature bit: EDX[17] for CPUID 1
    //
    GetCpuID( 1 );

    // If PSE-36 not supported then return (this should never happen on Slammer).
    if( !(_edx & (1 << 17)) )
    {
        return;
    }

    // Clear 4MB to 2GB.
    ClearMemory( (_int64)0x400000, (_int64)0x80000000 );

    // If there is only 3GB total ram then return.
    if( CONFIG_512MB == ReadExCMOS( CMOS2_MEM_CONFIG ) )
    {
        return;
    }


    //
    // Must be either 6GB or 12GB at this point.
    //


    // Clear 2GB to (4GB - 64MB).
    ClearMemory( (_int64)0x80000000LL, (_int64)(0x100000000LL - 0x4000000LL) );


    // If there is 6GB total ram then clear the 64MB
    // in the first 4 dimms that is remapped above 6GB.
    if( CONFIG_1GB == ReadExCMOS( CMOS2_MEM_CONFIG ) )
    {
        // Clear 6GB to (6GB + 64MB).
        ClearMemory( (_int64)0x180000000LL, (_int64)(0x180000000LL + 0x4000000LL) );
        return;
    }


    //
    // 12GB Memory Configuration
    //

    // Clear 4GB to 6GB.
    ClearMemory( (_int64)0x100000000LL, (_int64)0x180000000LL );

    // Clear 6GB to 8GB
    ClearMemory( (_int64)0x180000000LL, (_int64)0x200000000LL );

    // Clear the 64MB in the first 4 dimms that is remapped above 12GB.
    ClearMemory( (_int64)0x300000000LL, (_int64)(0x300000000LL + 0x4000000LL) );

    // Clear the ERS register
    WritePciWord( 0, 0, 0, 0x4C, 0x3FFF );

    return;
}


```

---

### Post by dan60 on 2014-02-15
> [COLOR=#000000]If you're still interested in an Intel syntax version let me know and I'll try to help with it.[/COLOR]
[COLOR=#000000]If you could, i'll appreciate your help :)

Regading the:
[/COLOR]```
 asm 
    (    
       "cpuid"
        : "=a" (_eax),
          "=b" (_ebx),
          "=c" (_ecx),
          "=d" (_edx)
        : "a"  (func)
    );
```[COLOR=#000000]

I didnt understand how exactly you passed the C variables into the asm code, what does "a" "b" "c" and "d" means!?

Oh...how do i compile it (using the intel syntax) !?

Thank you so much for the help![/COLOR]

---

### Post by xb12x2 on 2014-02-15
> **dan60 said:**
> [COLOR=#000000]If you could, i'll appreciate your help :)

Regading the:
[/COLOR]```
 asm 
    (    
       "cpuid"
        : "=a" (_eax),
          "=b" (_ebx),
          "=c" (_ecx),
          "=d" (_edx)
        : "a"  (func)
    );
```[COLOR=#000000]

I didnt understand how exactly you passed the C variables into the asm code, what does "a" "b" "c" and "d" means!?

Oh...how do i compile it (using the intel syntax) !?

Thank you so much for the help![/COLOR]

This is what I was afraid of. This is AT&T syntax. The GNU Assembler, known as gas or as, has built-in higher-level pseudo ops, or macros, so to speak. And this just adds to the overall dificulties and confusion when using AT&T syntax. And inline assembly adds it's own little bit of complexity.

Again, I know this isn't what you want to do at this particular time, and I apologize for that, but I'll suggest it anyway:

I found that my quickest way to code (and debug) things like this was to write all my assembly routines inside a stand-alone assembly file (a  *.asm file) using an assembler like nasm (open source, based on Microsoft's masm assemblers) And then link it to my gcc C files.

The reason nasm was created is because not only is most of the assemly code in the world in Intel syntax, it's also mostly in the masm style.

I'm obvously trying to avoid not only AT&T syntax, but the Gas assembler as well. I found that having a stand-alone nasm file always worked out better, no matter the circumstances.

I will try to provide an example of what I just suggested in my next post.

---

### Post by dan60 on 2014-02-15
Ok,
Thank you. I'll look forward to read it!
I'll embrace your suggestion and create a nasm.

Thank you again!

---

### Post by xb12x2 on 2014-02-16
Sorry I took so long to get back here. My family went out for a few hours.

This bulds and runs on my Linux x86_64 box. If you need a 32 bit version let me know.


This simple example shows:
 how to execute the cpuid instruction 
 how to call a an assembly file function from a C file 

This builds and runs on a x86_64 Linux.
Minor changes are needed for a 32bit x86 Linux.

To install the nasm assembler on Ubuntu 
 $ sudo apt-get install nasm

utils.asm 
 contains the function GetCpuID() 
 $ nasm -Wall -f elf64 -o utils.o utils.asm

cpuid.c 
 Calls the GetCpuID function  
 prints the results.
 $ gcc -Wall -c -o cpuid.o cpuid.c

Link:
 $ gcc -Wall -g -o cpuid cpuid.o utils.o

run:
 $./cpuid

```
;+---------------------------------------------------------------------------
; utils.asm 
;
; GetCpuID() executes the cpuid instruction. 
; Called from main.c

; Built using the nasm assembler for x86_64 Linux.
; Minor changes are needed for a 32bit x86 Linux.
; 
; nasm -Wall -f elf64 -o utils.o utils.asm
; gcc  -Wall -c -o main.o main.c
; gcc  -Wall -o cpuid main.o utils.o
;+---------------------------------------------------------------------------
 
global vendor_id, version, features, input, GetCpuID

section .bss 

vendor_id       resd    12      ;reserve 12 bytes of memory
version         resd    4
features        resd    4

section .text

GetCpuID:
                push    rax
                push    rbx
                push    rcx
                push    rdx
                
                ; get vendor id 
                mov     eax,0
                cpuid
                mov     [vendor_id],ebx
                mov     [vendor_id+4],edx
                mov     [vendor_id+8],ecx

                ; get version and features
                mov     eax,1
                cpuid
                mov     [version],eax
                mov     [features],edx
                
                pop     rax
                pop     rcx
                pop     rbx
                pop     rax
                
                ret


```

```
/*
 * main.c
 * 
 * This simple example shows:
 *  How to execute the cpuid instruction. 
 *  How to call a function in an assembled file, utils.asm. 
 * 
 * This builds and runs on a x86_64 Linux.
 * Minor changes are needed for a 32bit x86 Linux.
 *
 * gcc  -Wall -g -c -o main.o main.c
 * nasm -Wall -g -f elf64 -o utils.o utils.asm
 * gcc  -Wall -g -o cpuid main.o utils.o
 * 
 */

#include <stdio.h>

/* Defined in utils.asm */
extern void GetCpuID(void);
extern char vendor_id[12];
extern unsigned version;
extern unsigned features;

int main(void) 
{
  GetCpuID();
  printf("\nvendor_id is %s", vendor_id);
  printf("\nversion is 0x%04X", version);
  printf("\nfeatures are 0x%04X\n\n", features);
  return 0;
} 
```

---

### Post by dan60 on 2014-02-20
Thank you!!! I manage to code the CPUID using only asm code, your suggestion and GAS syntax!
Again, thank you!!!

---

