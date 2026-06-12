---
title: "64 or 32bit?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by mo.reina on 2008-06-10
i'm not sure if my laptop is 32 or 64bit.  it's an asus f8sr.  this is the output of the lshw command:

```
mo@mo-laptop:~$ sudo lshw
mo-laptop                 
    description: Notebook
    product: F8P
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: NF1S8306980004
    width: **32 bits**
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: chassis=notebook cpus=2 uuid=A72781DC-EF15-5BEE-CA80-001FC62F859D
  *-core
       description: Motherboard
       product: F8P
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 302 (02/29/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 478
          size: 1667MHz
          capacity: 1667MHz
          width: **64 bits**
          clock: 167MHz

```

in the description, the it says the width is 32bits, but in the cpu section, the width is 64bits.

---

### Post by jazzman65 on 2008-06-10
I'm no expert, but I believe Intel Core 2 Duo processors are indeed 64 bit capable.  As you see, that's what I have in my machine and it's running Hardy 64 just fine.

---

### Post by gr4nf on 2008-06-10
I would guess it's 64 bit. If it's core two duo, i dont' see how it couldn't be.

---

### Post by dudude on 2008-06-10
I just ran the same command on my 64-bit system with Ubuntu 8.04 AMD64 and it also said the width was 32 bits.

It has a Core 2 Duo processor.

---

### Post by RomeReactor on 2008-06-10
Hi. As far as I know, all core 2 duo are 64 bit capable. It seems the lshw output is incomplete; try:
```
sudo lshw -C processor
```

And look in the **capabilities** section near the end for **x86-64**, which will confirm it is 64 bit.

---

### Post by Tom Mann on 2008-06-10
Could you type this into a terminal?

uname -a

if you see i386 in the output, the 32 bit width is down to a software restriction, which you would resolve by installing 64-bit ubuntu.

Read the 32bit v 64bit articles here if the above has proven true and you want to go up to 64-bit :)

[URL="http://http://ubuntuforums.org/forumdisplay.php?f=343"]
http://ubuntuforums.org/forumdisplay.php?f=343[/URL]

---

### Post by sam_delta on 2008-06-10
yup, its 64bit, all core duo are


sam

---

### Post by sdennie on 2008-06-10
Try:

```

sudo dmidecode | grep 64-bit

```

If you see any output, the machine is 64bit capable.  Unless the BIOS doesn't support (which might be possible).

---

### Post by mo.reina on 2008-06-10
sudo dmidecode | grep 64-bit doesn't return anything.

however lshw -C processor returns 

```
  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.15.13
       serial: 0000-06FD-0000-0000-0000-0000
       slot: Socket 478
       size: 1667MHz
       capacity: 1667MHz
       width: 64 bits
       clock: 167MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
  *-cpu:1
       physical id: 1
       bus info: cpu@1
       version: 6.15.13
       serial: 0000-06FD-0000-0000-0000-0000
       size: 1667MHz
       capacity: 1667MHz
       capabilities: ht cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          capabilities: logical

```

is this a case of BIOS not supporting 64 bit architecture?  i'm currently running a 686 kernel based on uname -a:
```
mo@mo-laptop:~$ uname -a
Linux mo-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

```

---

### Post by lazyart on 2008-06-10
If you google the processor, the first link points to Intel's datasheet, and surprise, it's 64 bit.

[http://processorfinder.intel.com/details.aspx?sspec=sla4f](http://processorfinder.intel.com/details.aspx?sspec=sla4f)

---

### Post by RomeReactor on 2008-06-10
> **mo.reina said:**
> sudo dmidecode | grep 64-bit doesn't return anything.

however lshw -C processor returns 

```
  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.15.13
       serial: 0000-06FD-0000-0000-0000-0000
       slot: Socket 478
       size: 1667MHz
       capacity: 1667MHz
       width: 64 bits
       clock: 167MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce
cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse
sse2 ss ht tm pbe nx **x86-64** constant_tsc arch_perfmon pebs bts pni
monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
  *-cpu:1
       physical id: 1
       bus info: cpu@1
       version: 6.15.13
       serial: 0000-06FD-0000-0000-0000-0000
       size: 1667MHz
       capacity: 1667MHz
       capabilities: ht cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          capabilities: logical

```

is this a case of BIOS not supporting 64 bit architecture?  i'm currently
running a 686 kernel based on uname -a:
```
mo@mo-laptop:~$ uname -a
Linux mo-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

```

If you look again in the **capabilities** section of the lshw output you can see that it is 64 bit processor (**x86-64**). The 686 kernel just means you're running Ubuntu 32 bit now, instead of 64 bit.

---

### Post by The Cosmic Hobo on 2008-06-11
So what's the practical upshot of a processor being 64 bit rather than 32 bit? I gather there's a specialist kernel for 64 bit x86 processors. What are the advantages and drawbacks?

---

### Post by RomeReactor on 2008-06-11
> **The Cosmic Hobo said:**
> So what's the practical upshot of a processor being 64 bit rather than 32 bit? I gather there's a specialist kernel for 64 bit x86 processors. What are the advantages and drawbacks?

The practical benefit would be that processor-intensive tasks--such as video transcoding and code compiling--will work faster than on a 32 bit system. And as far as I recall, a 64 bit system does not have the 4 GB memory limit.

---

### Post by misfitpierce on 2008-06-11
Mine shows up as 64bit on AMD Turion 64 but yeah all core2Duo should be 64 bit as said so try out 64 bit disc should work fine.

---

### Post by hyper_ch on 2008-06-11
> **RomeReactor said:**
> And as far as I recall, a 64 bit system does not have the 4 GB memory limit.
32-bit systems with PAE can use up to 64gb ram also :)

---

