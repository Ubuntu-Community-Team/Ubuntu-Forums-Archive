---
title: "Embedded programming newbie problem.."
date: 2014-08-03
forum: Programming Talk
---

### Post by Blackbug on 2014-08-03
Hello,

I am new to embedded programming and trying to run the following code, however, it crashes with core dump.
I am trying to assign memory to a specific address 0x400380 and, while I try to modify one of the bitfields, it results in a core dump.
However, when I don't specify any address everything works perfectly.

```
typedef union siu_pcr_u 
{
    volatile unsigned short REG;
    struct 
    {
        volatile unsigned short :3;
        volatile unsigned short PA:3;
        volatile unsigned short OBE:1;
        volatile unsigned short IBE:1;
        volatile unsigned short DSC:2;
        volatile unsigned short ODE:1;
        volatile unsigned short HYS:1;
        volatile unsigned short SRC:2;
        volatile unsigned short WPE:1;
        volatile unsigned short WPS:1;
    } FIELDS;
} SIU_PCR;


int main()
{
    volatile SIU_PCR *siu_pcr_ptr;
    siu_pcr_ptr = (SIU_PCR*)(0X400380); // Assigned to a specific address
    
    for(int i=122; i<130; i++)
    {
        siu_pcr_ptr[i].FIELDS.PA = 0;  // Crashes here
    }
       return 0;
}

```

The gdb gives following info:

```
Program terminated with signal SIGSEGV, Segmentation fault.
#0  0x00000000004006f8 in main () at ex04.cpp:211
211            siu_pcr_ptr[i].FIELDS.PA = 0; 
(gdb) p siu_pcr_ptr[i]
$1 = {REG = 0, FIELDS = {PA = 0, OBE = 0, IBE = 0, DSC = 0, ODE = 0, HYS = 0, SRC = 0, WPE = 0, WPS = 0}}
(gdb) p siu_pcr_ptr
$2 = (volatile SIU_PCR *) 0x400380
(gdb) 

```
Can anyone point out whats wrong here?

Thanks.

---

### Post by xb12x2 on 2014-08-03
I assume you're trying to run this code on a modern, x86-based (or x64-based) O.S. such as Linux or Windows or iOS etc. If so, what you're seeing is the O.S. purposely preventing your code from having direct access to any hardware you happen to want access to. It's called ***Protected Mode***. It prevents your user-level code from conflicting with other parts of the running system and potentially causing system-wide problems which could bring down (crash) the entire machine. 

If you need to access a particular address you need to get permission from the O.S. to do so before you try to access it. This usually requires writing a device-driver of some sort (kernel-level code).

If you're testing hardware, one approach is to not use a protected-mode O.S to run your code: replace the O.S. with something that lets you have unrestrained access to all the hardware directly from your application, i.e. DOS (DOS-32), or a custom boot-loader, etc.

---

### Post by Blackbug on 2014-08-04
Thanks for answering. What you explained make sense.
However, I wonder how people then model or do virtual prototyping of the different components on linux using systemC etc.
There should be a definite pattern or way to write the register with the bitfields ( for modelling their different pins ).

---

