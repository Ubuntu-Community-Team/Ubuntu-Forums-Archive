---
title: "Dual Xeon Server running 8.04 CPU detection..."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by chimay on 2008-10-05
I have a Neoteris Access 5000 that I've loaded Ubuntu on. When I type in cat /proc/cpuinfo i get the following.

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 2.40GHz
stepping	: 7
cpu MHz		: 2399.844
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid
bogomips	: 4803.10
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 2.40GHz
stepping	: 7
cpu MHz		: 2399.844
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid
bogomips	: 4799.59
clflush size	: 64

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 2.40GHz
stepping	: 7
cpu MHz		: 2399.844
cache size	: 512 KB
physical id	: 3
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid
bogomips	: 4799.63
clflush size	: 64

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 2.40GHz
stepping	: 7
cpu MHz		: 2399.844
cache size	: 512 KB
physical id	: 3
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid
bogomips	: 4799.66
clflush size	: 64

That is 4 processors total, and from what I have read these should be single core Xeon processors... or did I luck out some how with dual core xeon? I didn't think they were around when this stuff came out...

Can some one help me make sense of that? 

Also conky seems to think there is only 1 processor. But I'm not 100% sure that conky would be able to tell me if there were more than 1.

---

### Post by Rocket2DMn on 2008-10-05
With conky you need to specify with cpu0, cpu1, etc.  For more detailed info about your system, can you please post the output of
```
sudo lshw
```
If you want to specifically see processor info, do
```
sudo lshw -C cpu
```
If you'd like to put all the output here, it may be cleaner to use an attachment (a text file)
```
sudo lshw > lshw.txt
```
I've never heard of Ubuntu seeing MORE processors than actually exist...

---

### Post by chimay on 2008-10-05
Thank you for the quick reply. Attached is the output. I edited out the name and a few other pieces of info.

---

### Post by Rocket2DMn on 2008-10-05
Looking at the specs page for your motherboard, it would appear that the board holds 2 xeon processors, but no mention of them being multicore.  After looking back and forth a bit, I noticed a difference between CPUs 0,1 and CPUs 2,3.  The latter don't have a slot or capacity attribute (among a few others that are missing).  I would guess that CPU2 and CPU3 are logical, in that the kernel treats them as present, but they may just show duplicate information as CPU0 and CPU1.

I'm not sure if this behavior is intentional, but you may consider filing a bug report if it bothers you.

---

### Post by cariboo on 2008-10-05
I have seen hyperthreading make it appear that the processor is a dual core. Back in the day when there was a penguin on the boot screen they used to show two penguins leading use to beleive that there were two processors when it was actually only an Intel cpu with hyperthreading.

Jim

---

### Post by chimay on 2008-10-05
> **Rocket2DMn said:**
> Looking at the specs page for your motherboard, it would appear that the board holds 2 xeon processors, but no mention of them being multicore.  After looking back and forth a bit, I noticed a difference between CPUs 0,1 and CPUs 2,3.  The latter don't have a slot or capacity attribute (among a few others that are missing).  I would guess that CPU2 and CPU3 are logical, in that the kernel treats them as present, but they may just show duplicate information as CPU0 and CPU1.

I'm not sure if this behavior is intentional, but you may consider filing a bug report if it bothers you.

Ah good catch. Perhaps 2 and 3 are showing because of hyper threading? Either way I just wanted to make some sense of it and make sure that they were being detected correctly. I moved the HD with installation over from an old p4 box I was using and was just checking to make sure all hardware was detected and working correctly when I saw this. I love that you can do that with Linux, windows, forget it. All I had to do was make the entries for the network card and reinstall xorg.

---

### Post by Rocket2DMn on 2008-10-05
Hyperthreading is as good of an explanation as I can come up with, but I don't have any boxes that can test that theory.  If you find out more, let us know.

---

