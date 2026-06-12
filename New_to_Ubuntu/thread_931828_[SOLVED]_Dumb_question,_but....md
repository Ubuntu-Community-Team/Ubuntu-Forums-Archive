---
title: "[SOLVED] Dumb question, but..."
date: 2008-09-27
forum: New to Ubuntu
---

### Post by finalrequiem on 2008-09-27
How do I find out whether my notebook is 32bit or 64?

---

### Post by oldsoundguy on 2008-09-27
plug the processor make and model into google.

to get that
(Linux)  in terminal: sudo lshw
(Windows) download and run Belarc Advisor

---

### Post by Sef on 2008-09-27
> plug the processor make and model into google.

to get that
(Linux)  in terminal: sudo lshwEasier still is this command:

```
cat /proc/cpuinfo
```No password needed. 

(Applications > Accessories > Terminal)

---

### Post by drs305 on 2008-09-27
System, Administration, System Monitor > System tab. If you still don't know, then google what it says.

---

### Post by finalrequiem on 2008-09-27
lshw -C cpu | grep width

gives me: width 64 bits

The "cat /proc/cpuinfo" and systems tab give me the processor brand\type but nothing else (that I can decipher, anyway).  Is what I get from the "lshw -C cpu | grep width" command correct or is it referring to something else?  I googled my cpu but couldn't find anything definitive (maybe just missed it).

---

### Post by bumanie on 2008-09-27
Post the output (cut and paste) of > cat /proc/cpuinfo as someone else will be able to decipher it for you.

---

### Post by finalrequiem on 2008-09-27
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips	: 4394.66
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips	: 4388.99
clflush size	: 64

---

### Post by bumanie on 2008-09-27
I know a bit more about amd processors, but as far as I can tell the Intel(R) Core(TM)2 Duo CPU T7500 @ 2.20GHz is a dual core 64bit intel chip

---

### Post by robalcorn on 2008-09-27
Cant remember if i installed this or default in ubuntu gnome but if you go to applications/system tools/sysinfo it shows all info regarding your pc and under cpu you might see. At least for me it shows 64bit.

---

### Post by Crash 0verride on 2008-09-27
Most Processors are Basic x32 I believe like Intel
And AMD is 64.

---

### Post by steveneddy on 2008-09-27
> **Crash 0verride said:**
> Most Processors are Basic x32 I believe like Intel
And AMD is 64.

Your processor is a 64 bit processor and you should be able to run Ubuntu 64 bit.

Many folks prefer 64 bit if the processor will support it.

If you are running 32 bit Ubuntu you will have to do a total reinstall to run 64 bit.

The Intel 64 bit processor is also referred to an amd64 as it uses the same specs.

---

### Post by finalrequiem on 2008-09-27
I have wiped everything and installed the 64 bit version.  Thanks to everyone!

---

