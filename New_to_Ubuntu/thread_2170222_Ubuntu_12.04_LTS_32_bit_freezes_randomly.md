---
title: "Ubuntu 12.04 LTS 32 bit freezes randomly"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by kinshuk2 on 2013-08-25
Hi All,


 I am new to Linux world so pardon my ignorance and lack of understanding on linux.
 I have installed Ubuntu 12.04 LTS 32-bit on my Compaq Presario SG3630IL Desktop PC recently and loving it.
Recently, I am seeing an issue where the desktop Freezes completely. Its  completely random. not related to a particlar application or a sequence  of steps
 - Mouse or keyborad inputs does not work (checked with num lock key)
-tried entering virtual consoles and it did not work either
- waited for over 15 minutes to see if the device recovers on its own but it did not :(
Had to finally reset the computer through its power button.
 System basic detail:
RAM 1024 DDR2
HDD 250GB
Intel GMA 3100 Graphics
 ----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 15
  model name	: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
  stepping	: 13
  microcode	: 0xa3
  cpu MHz		: 1200.000
  cache size	: 1024 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 2
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov  pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm  constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl  est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
  bogomips	: 4389.71
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
   processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 15
  model name	: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
  stepping	: 13
  microcode	: 0xa3
  cpu MHz		: 2200.000
  cache size	: 1024 KB
  physical id	: 0
  siblings	: 2
  core id		: 1
  cpu cores	: 2
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov  pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm  constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl  est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
  bogomips	: 4389.71
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
 ----- /proc/cpuinfo end -----
 I have taken dmesg, hwinfo txt for information but not sure how to attach them yet.
There are too many posts with similar problem description, but i was not  sure whether to try them out without understanding what those commands  do!
 Hoping some one can help me to understand if this is a hardware issue or software ?
the PC came with windows loaded and decided to move away from it :)
 Thanks,
Kinshuk

---

### Post by Bucky Ball on 2013-08-25
Not sure why you're using 32bit. It this not an origianl Intel dual-core processor? 64bit? Correct me if I'm wrong.

```
Intel(R) Pentium(R) Dual CPU E2200 @ 2.20GHz
```

PS: Please use [code] tags around code for clarity. ;)

---

### Post by ibjsb4 on 2013-08-25
It could be compiz settings, could be a driver issue.  Try another desktop to see if it still happens.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install gnome-session-fallback
```

You can choose this desktop at boot (in the login window) by clicking on the icon.  Choose 'gnome-classic no effects'.  This will get you off the compiz window manager.

And I thibnk Bucky Ball was trying to show you:

```
System basic detail:
RAM 1024 DDR2
HDD 250GB
Intel GMA 3100 Graphics
 ----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 15
  model name	: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
  stepping	: 13
  microcode	: 0xa3
  cpu MHz		: 1200.000
  cache size	: 1024 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 2
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov   pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm   constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl   est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
  bogomips	: 4389.71
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
   processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 15
  model name	: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
  stepping	: 13
  microcode	: 0xa3
  cpu MHz		: 2200.000
  cache size	: 1024 KB
  physical id	: 0
  siblings	: 2
  core id		: 1
  cpu cores	: 2
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov   pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm   constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl   est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
  bogomips	: 4389.71
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
 ----- /proc/cpuinfo end -----
```

[ATTACH=CONFIG]245697[/ATTACH]

And welcome to the forums :)

---

### Post by Bucky Ball on 2013-08-25
Oh, yes, and welcome. ;)

---

