---
title: "Ubuntu 12.04 DELL Inspiron N5010 Issues"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by biswajitdey on 2012-08-22
Ubuntu 12.04 32 bit
Dell Inspiron N5010

Hello,

I am facing the following issues while using Ubuntu 12.04 :-

1) Sometimes while increasing/decreasing brightness/sound using keyboard, the system hangs and there is no way I can restart the system  unless I press the power key.

2) The system doesn't restore from sleep or for that case even after once the screen turns off , nothing works , the cursor moves but can't click on anything.

I am a big fan of Ubuntu and it used to work fine with previous versions(upto 10.04) but as now I am facing these problems, I am not too comfortable using it nowadays. Please someone can explain why this is happening and is there any way that this can be fixed.

Thanks.
Biswajit Dey.

---

### Post by eneskuray on 2012-08-22
my crazy idea is do you have same problems when using ubuntu live cd?

---

### Post by biswajitdey on 2012-08-23
Nope.

I have installed ubuntu.

---

### Post by 2F4U on 2012-08-23
Did you look into the log files? For the first issue, the main log file would be the first source, while for the second you would also look into /var/log/pm-suspend.log.
Since I don't know your hardware, I probably would be a good idea if you post details about your specs. If your graphics card is ATI or nVidia also post what graphics driver you are using.

---

### Post by biswajitdey on 2012-08-31
My hardware specs - display

id:	
display
description: 	VGA compatible controller
product: 	Core Processor Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	18
width: 	64 bits
clock: 	33MHz
capabilities: 	msi pm vga_controller bus_master cap_list rom
configuration:	
driver	=	i915
latency	=	0
resources:	
irq	:	47
memory	:	fa400000-fa7fffff
memory	:	c0000000-cfffffff
ioport	:	f080(size=8)

cpu
id:	
cpu:0
description: 	CPU
product: 	Intel(R) Core(TM) i3 CPU M 350 @ 2.27GHz
vendor: 	Intel Corp.
physical id: 	
4
bus info: 	
cpu@0
version: 	6.5.5
serial: 	0002-0655-0000-0000-0000-0000
slot: 	CPU 1
size: 	931MHz
capacity: 	2261MHz
width: 	64 bits
clock: 	533MHz
capabilities: 	x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
configuration:	
cores	=	2
enabledcores	=	1
id	=	5
threads	=	2


Am not so much pro in debugging and reading log files.
Could you plz help me out how to fix these problems.

Thanks.

---

