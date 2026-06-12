---
title: "Use all of my RAM in Ubuntu Server"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by dolphin194 on 2012-05-08
I was wondering if I can use all 8 gigs of my RAM in my server computer. 

**Every forum post I have seen online is that this is impossible to do, and that only applied to Windows. However, people in real life have said that Linux 32-Bit is capable of using all of the RAM a computer. I have no idea who is correct.**

My computer is a Dell PowerEdge 2650 running Ubuntu Server 10.04. It has *32-Bit Processors *(as in Intel Xeon 2.8GHz). It has 8GB of RAM installed in it.

A website at [http://www.memorystock.com/memory/DellPowerEdge2650.html](http://www.memorystock.com/memory/DellPowerEdge2650.html) says this:
**You can upgrade your Dell *PowerEdge 2650* Server to up to a *maximum* of 12.0 GB**

The document at this place says:
**It provides SDRAM *memory* capabilities from 256MB up to 12GB**

This is proof that the computer is capable of using all of the RAM.

How can I use all 8GB of my RAM in this computer?

---

### Post by Cheesemill on 2012-05-08
You can use all of the memory if you have a PAE enabled kernel installed, which I believe comes as default on 10.04 server.

What is the output of:
```
uname -a
```
and
```
free -m
```

---

### Post by dolphin194 on 2012-05-08
The output of uname -a is:
```
Linux PowerEdge 2.6.32-40-generic-pae #87-Ubuntu SMP Mon Mar 5 21:44:34 UTC 2012 i686 GNU/Linux
```

The output of free -m is:
```
             total       used       free     shared    buffers     cached
Mem:          3782        239       3542          0         38        106
-/+ buffers/cache:         94       3687
Swap:         5711          0       5711
```

However, there is 8GB of RAM installed in the machine.

---

### Post by Cheesemill on 2012-05-08
OK, you have the correct kernel installed so your machine should be reporting the full amount. What is the output of:
```
cat /proc/cpuinfo
```

---

### Post by dolphin194 on 2012-05-08
The output of /proc/cpuinfo is:
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
cpu MHz        : 2790.931
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5581.86
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
cpu MHz        : 2790.931
cache size    : 512 KB
physical id    : 3
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 6
initial apicid    : 6
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5581.77
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
cpu MHz        : 2790.931
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5581.74
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
cpu MHz        : 2790.931
cache size    : 512 KB
physical id    : 3
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 7
initial apicid    : 7
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5581.84
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

```

so it does support pae

---

### Post by Cheesemill on 2012-05-08
How much memory does the BIOS report at boot?

You probably have to either change a BIOS setting or update your BIOS for it to recognise all of the RAM.

---

### Post by dolphin194 on 2012-05-08
Unfortunately I do not have physical access to the machine, only SSH and etc. right now, but I will later in the day. I will check the BIOS to see if there are any issues in there.

---

### Post by Cheesemill on 2012-05-08
I've just looked at the official Dell documentation and it gives a maximum of 6GB of RAM for the machine, the motherboard is probably only capable of recognising 1GB of memory per slot.

If you are using 4x2GB sticks then the BIOS would only recognise 4x1GB

Look at the second link on this page:
[http://support.dell.com/support/edocs/systems/pe2650/en/index.htm](http://support.dell.com/support/edocs/systems/pe2650/en/index.htm)

---

