---
title: "[SOLVED] System Monitor"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Tom Atkins on 2008-09-09
All,

The system monitor shows 2 CPUs on my system. I only have one. It is not a big deal for me but I wonder if it is a known problem.

TIA

Tom Atkins

---

### Post by Thingymebob on 2008-09-09
Is your one CPU a dual core?

---

### Post by skymera on 2008-09-09
What is your CPU?

```
 cat /proc/cpuinfo 
```

---

### Post by Tom Atkins on 2008-09-09
No it is just a 4 year old pentium.

Tom

---

### Post by skymera on 2008-09-09
Is it a Pentium 4 HT or HTT? (Should say on Intel sticker)

If so that's why 2 CPU's are showing.

---

### Post by Tom Atkins on 2008-09-09
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping	: 9
cpu MHz		: 3066.297
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips	: 6137.94
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping	: 9
cpu MHz		: 3066.297
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips	: 6132.71
clflush size	: 64

```

---

### Post by skymera on 2008-09-09
I believe that CPU is hyper threaded which explains why 2 CPU's show up.

But it's still a single core.

---

