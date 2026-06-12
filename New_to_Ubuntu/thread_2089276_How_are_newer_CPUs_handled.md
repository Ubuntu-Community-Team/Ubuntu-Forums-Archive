---
title: "How are newer CPUs handled?"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by newb85 on 2012-11-28
It's come to my attention that I very much lack understanding of how Ubuntu/Linux handles newer CPUs with multiple cores, multi-threading, and "turbo speeds".

Case in point, my laptop is currently running an Intel i5-2410M.  The vendor lists it as having 2 cores, 4 threads, a clock speed of 2.3GHz, and a turbo speed of 2.9 GHz.

When I open System Monitor, it shows percent usages for 4 CPUs.  Is that because of 4 threads??

Also, lshw returns this:
```
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
       serial: To Be Filled By O.E.M.
       slot: CPU 1
       size: 800MHz
       **capacity: 3800MHz**
       width: 64 bits
       **clock: 400MHz**
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
       configuration: cores=2 **enabledcores=1 threads=2**

```

(I bolded the parts that don't make sense.)

Also, lscpu gives this:

```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
[b]CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1[/b]
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 42
Stepping:              7
**CPU MHz:               800.000**
BogoMIPS:              4589.55
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
NUMA node0 CPU(s):     0-3

```

---

### Post by audiomick on 2012-11-28
I have no idea, but a search on DuckDuckGo for "Multi-Core Linux" found this

[http://www.informationweek.com/whitepaper/Enterprise_Software/wp902463?articleID=902463]("http://www.informationweek.com/whitepaper/Enterprise_Software/wp902463?articleID=902463")

It looks like that might be relevant to your question.

---

### Post by drmrgd on 2012-11-28
I don't know about the speed question.  But, the system does show each thread as a "core" of sorts.  My system has a 6-core i7 processor, which show in htop and other utilities as having 12 cores since it's hyperthreaded.

---

### Post by haqking on 2012-11-28
preferably with care and an electrostatic wristband ;-)

---

### Post by audiomick on 2012-11-28
> **haqking said:**
> preferably with care and an electrostatic wristband ;-)

#-o

---

### Post by benbrockn on 2012-11-28
This part seems right:

> configuration: cores=2 **enabledcores=1 threads=2**

For whatever reason it's reading your dual-core processor, but only enabled 1 of those cores.

Also this is correct:

> [B]CPU(s):                4 
On-line CPU(s) list:   0-3 
Thread(s) per core:    2 
Core(s) per socket:    2 
Socket(s):             1[/B]

The first core is usually core 0, so 0-3 would mean you have 4 cores.

You have 1 socket (1 CPU in 1 CPU socket), there are 2 cores on that 1 socket, and each core has 2 threads (4 threads total).

As for how to configure Ubuntu to optimize the 2.3-2.9GHz, I have no clue... sorry.

---

### Post by newb85 on 2012-11-28
> **benbrockn said:**
> For whatever reason it's reading your dual-core processor, but only enabled 1 of those cores.
...
The first core is usually core 0, so 0-3 would mean you have 4 cores.
You have 1 socket (1 CPU in 1 CPU socket), there are 2 cores on that 1 socket, and each core has 2 threads (4 threads total).

This is part of what's confusing me.  I know I have one processor, two cores, and four threads.  And I'm being told (by various commands) I have one CPU, two CPUs, and four CPUs.

---

### Post by Bashing-om on 2012-11-28
newb85; 
I run 
```
dmidecode
``` and all my cores are shown (enabled).

---

### Post by newb85 on 2012-11-28
> **Bashing-om said:**
> newb85; 
I run 
```
dmidecode
``` and all my cores are shown (enabled).

Thanks for the tip.  Once I filtered the results with "-t processor" option,

```
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0004, DMI type 4, 42 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Core 2 Duo
	Manufacturer: Intel            
	ID: A7 06 02 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 42, Stepping 7
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz       
	Voltage: 0.0 V
	External Clock: 400 MHz
	Max Speed: 3800 MHz
	Current Speed: 2300 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 2
	[b]Core Enabled: 1
	Thread Count: 2[/b]
	Characteristics:
		64-bit capable

```

Still looks like only one core (with two threads) is enabled.  Meanwhile, System Monitor is still showing four different CPU levels.

---

### Post by Bashing-om on 2012-11-28
I do not know what I can say ?? I would have expected the installer to pick up on both processors and enable them...hummmm
here is mine:
```

         HTT (Multi-threading)
        Version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
        Voltage: 1.3 V
        External Clock: 200 MHz
        Max Speed: 3000 MHz
        Current Speed: 2600 MHz
        Status: Populated, Enabled
        Upgrade: Socket 940
        L1 Cache Handle: 0x000A
        L2 Cache Handle: 0x000B
        L3 Cache Handle: Not Provided
        Serial Number:  
        Asset Tag:  
        Part Number:  
        Core Count: 2
        Core Enabled: 2
        Thread Count: 2
        Characteristics:
                64-bit capable

```I presently have 4 ubuntu installs on this system, all installs through GParted, the last 2 simple installs with the installer on liveCD. All of them see both processors.

I wish I had further to add, but nada...
[INDENT][INDENT]best regards < == BDQ

[/INDENT][/INDENT]

---

### Post by Bashing-om on 2012-11-28
I just noticed on your out put ....voltage: 0.0 where as mine shows voltage: 1.3 volts. That, I should think, warrants some investigation, prior to tearing the box down and reseating the processors.
[INDENT]help'n ?? <== BDQ

[/INDENT]

---

