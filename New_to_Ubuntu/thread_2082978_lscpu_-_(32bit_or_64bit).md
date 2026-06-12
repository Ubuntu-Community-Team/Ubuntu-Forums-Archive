---
title: "lscpu - (32bit or 64bit)"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-11-11
i want to know if my cpu hardware is 32bit or 64bit...although i know i have installed 32bit Ubuntu 12.04 version on my system,,, yet i m not sure if my system/cpu is 32bit or 64bit,, as in either case, i could have installed 32bit operating sys on it...
1...when i try to check it by lscpu,, it show CPU op mode both 32bit and 64 bit as shown under...what does this mean????
2....architecture says i686,,,, what does this mean,, what are other options??what does it show/means????
someone to plz guide in detail

nasir@NASIR:~$ lscpu
Architecture:         ** i686**
CPU op-mode(s):        **32-bit, 64-bit**
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               1000.000
BogoMIPS:              3325.32
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K

---

### Post by NikTh on 2012-11-11
> **syednasirraza said:**
> i want to know if my cpu hardware is 32bit or 64bit...although i know i have installed 32bit Ubuntu 12.04 version on my system,,, yet i m not sure if my system/cpu is 32bit or 64bit,, as in either case, i could have installed 32bit operating sys on it...
1...when i try to check it by lscpu,, it show CPU op mode both 32bit and 64 bit as shown under...what does this mean????
2....architecture says i686,,,, what does this mean,, what are other options??what does it show/means????
someone to plz guide in detail

nasir@NASIR:~$ lscpu
Architecture:         ** i686**
CPU op-mode(s):        **32-bit, 64-bit**


Hi ,

The first result (Architecture) points to your current installed system. Your current installed system is Ubuntu 32bit. 

The second result (CPU op-mode) is the capabilities of your CPU. So your CPU is 64 bit capable. You can install Ubuntu 64bit without a problem. 

Another command you can use and double-check your CPU 64bit capability is this
```
grep -e flags -e lm /proc/cpuinfo
``` 
if you see lm flags exist , then is another prove that your CPU is 64bit capable. 

Also read this : [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Thanks

---

### Post by Calinou on 2012-11-11
Pretty much any CPU sold after 2004 (~ Pentium 4 era) supports 64 bit.

---

### Post by syednasirraza on 2012-11-11
> **NikTh said:**
> Hi ,

The first result (Architecture) points to your current installed system. Your current installed system is Ubuntu 32bit. 



thanks for precise reply....
when my Architecture says i686, u said it means its 32 bit...what would be here if it would be 64bit...what are other options like somewhere on net if find these words like i386, i686, x86 etc...

---

### Post by ibjsb4 on 2012-11-11
> **syednasirraza said:**
> thanks for precise reply....
when my Architecture says i686, u said it means its 32 bit...what would be here if it would be 64bit...what are other options like somewhere on net if find these words like i386, i686, x86 etc...

I find that strange, a 686 should read 32 bit only.  What kind of processor is this?

sudo lshw -class cpu

---

### Post by NikTh on 2012-11-11
> **syednasirraza said:**
> thanks for precise reply....
when my Architecture says i686, u said it means its 32 bit...what would be here if it would be 64bit...what are other options like somewhere on net if find these words like i386, i686, x86 etc...

32bit = X86 , i686 , i386 

64bit= X86_64 , amd64 , X64. 

If you had (or when you install 64bit Ubuntu) you will see 

Architecture : X86_64

@ibjsb4, the result "Architecture" from the lscpu command is not for the processor , but for the Operating System that processor running at current time. 

Architecture: i686 
and
Cpu op-mode 32bit , 64bit 

means that OP running a CPU capable for 32 & 64bit in a Operating System 32bit. (Ubuntu 32bit).

Thanks

---

### Post by syednasirraza on 2012-11-11
> **ibjsb4 said:**
> I find that strange, a 686 should read 32 bit only.  What kind of processor is this?

sudo lshw -class cpu

i guess when it says width 64bits (as highlighted here under), that means it is 64bit capable cpu 
and by the way what is cpu 1 highlighted hereunder...

nasir@NASIR:~$ sudo lshw -class cpu
  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
       capacity: 1667MHz
       width:[COLOR=Red][U][B] 64 bits
[/B][/U]***[COLOR=Black]       continued..............[/COLOR]***[/COLOR] [COLOR=Red]_** *-cpu:1**_[/COLOR]
       physical id: 1
       bus info: cpu@1
       size: 1GHz
       capacity: 1GHz
       capabilities: ht cpufreq
        ***continued ..................***

---

### Post by syednasirraza on 2012-11-11
> **nikth said:**
> 32bit = x86 , i686 , i386 
64bit= x86_64 , amd64 , x64. 
If you had (or when you install 64bit ubuntu) you will see 
architecture : X86_64


thanks alot nik.... Got my doubts clear

---

