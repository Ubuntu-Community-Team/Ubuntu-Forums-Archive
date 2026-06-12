---
title: "can't get the app running please help"
date: 2020-02-13
forum: New to Ubuntu
---

### Post by nwicked on 2020-02-13
Hi everyone! I have experienced a problem at work when I installed lubuntu I can't run RCphone app not .deb nor even .appimage version (in gethub). Would be great to hear an advise. thank you!

---

### Post by wildmanne39 on 2020-02-13
You posted this in the Resolution Centre which is for:
> This is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse. 
Moved to New to Ubuntu for support.

---

### Post by EuclideanCoffee on 2020-02-14
To run such programs, you may need some knowledge on using the terminal. Could you please provide information on how you intend to run these applications, so someone can provide further advice? Thanks!

---

### Post by nwicked on 2020-02-15
I mean I am a new user, just started up with linux, I chose lubuntu distro for it's low ram usage, bcz I run heavily loaded web tabs which require lots of ram. this is the app to receive and make calls and texts, I double click on it but nothing happens. .deb package is for amd core but I have intel, .appimage won't run for some reason

---

### Post by Holger_Gehrke on 2020-02-15
> **nwicked said:**
> [snip].deb package is for amd core but I have intel,[snap]

Packages for 64 bit PC-Systems are named amd64 because Intel had a different 64 bit architecture called Itanium which failed to get any significant market share, mainly because performance with existing 32-bit code was really bad. All PC-processors sold today use AMD's way of doing 64 bit programs no matter whether they are made by AMD or Intel. So unless you are in fact using an Itanium-based Workstation the *_amd64.deb file should run on your system.

Holger

---

### Post by mörgæs on 2020-02-15
First update your system. After this the standard way to install a .deb file is 
```
sudo dpkg -i <name-of-deb-file>
```

---

### Post by nwicked on 2020-02-15
thank you guys for being patient for noob, I will try this out and will give a feedback on the result!

---

### Post by nwicked on 2020-02-15
This is something new, thank you!

---

### Post by mörgæs on 2020-02-15
You are welcome. If it works then please mark the thread solved.

---

### Post by nwicked on 2020-02-17
Hello! So I have tried everything I could: my system is i386 so I installed amd64 arch, tried to install the app, then libappindicator1:amd64 is not installed so I installed it, didn't help, so I removed the amd64 arch and updated the system, tried to run chmod u+x .AppImage file, won't run. Please advise

---

### Post by oldrocker99 on 2020-02-17
> **Holger_Gehrke said:**
> Packages for 64 bit PC-Systems are named amd64 because Intel had a different 64 bit architecture called Itanium which failed to get any significant market share, mainly because performance with existing 32-bit code was really bad. All PC-processors sold today use AMD's way of doing 64 bit programs no matter whether they are made by AMD or Intel. So unless you are in fact using an Itanium-based Workstation the *_amd64.deb file should run on your system.

Holger
32-bit programs are named i386 in honor of the Intel i386, the first commercial 32-bit CPU.

64-bit programs are named AMD64 in honor of the AMD Athlon 64, the first commercial 64-bit CPU.

It's just nomenclature. If it's a 32-bit file, it'll work on AMD **or** Intel, and the same is true of 64-bit programs.

---

### Post by mörgæs on 2020-02-18
> **nwicked said:**
> my system is i386


I'm not sure what you mean by this. Please post the output from the commands ```
uname -a
``` and ```
lscpu
``` in CODE tags.

---

### Post by nwicked on 2020-04-23
```
Linux KJ 4.15.0-76-generic #86-Ubuntu SMP Fri Jan 17 17:25:21 UTC 2020 i686 i686 i686 GNU/Linux
kj@KJ:~$

Architecture:        i686
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  2
Core(s) per socket:  2
Socket(s):           1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               42
Model name:          Intel(R) Core(TM) i3-2365M CPU @ 1.40GHz
Stepping:            7
CPU MHz:             1023.048
CPU max MHz:         1400.0000
CPU min MHz:         800.0000
BogoMIPS:            2793.58
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            3072K
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm arat pln pts md_clear flush_l1d
kj@KJ:~$
```

The installed system is 32 bit though

---

### Post by CelticWarrior on 2020-04-23
So, you chose Lubuntu because *I run heavily loaded web tabs which require lots of ram* but then you end up installing the 32-bit version on 64-bit hardware??? BTW, 32-bit LIMITS the amount of usable RAM so there's that! Also, if you are so RAM constrained that the Desktop Environment makes a difference you definitely need more RAM, not a lighter distro. Lighter distros are ideal for very old hardware that is actually limited in the maximum amount of RAM it supports. Not really applicable to a          Intel(R) Core(TM) i3-2365M CPU @ 1.40GHz.

---

### Post by TheFu on 2020-04-23
32-bit OS cannot run programs compiled for 64-bit systems.  

You'll need to find a 32-bit version of the program
or
You'll need to install the 64-bit version of the OS
or
You'll need to give up and find some other program that has a 32-bit version which meets your requirements.

Running a 32-bit OS will be more and more difficult.

BTW, I'm in a similar boat. 
```
$ uname -m
i686

```
Due to a decision I made around 2008.  I've been planning to move to the 64-bit version, but just haven't gotten around to it.  We both have CPUs which are perfectly capable of running amd64/64-bit OSes. Your Core i3 certainly can.

If this is for work, then 18.04 should have the widest support today.  20.04 support for business programs often takes a year.

Before you ask, there is no direct upgrade patch from 32-bit to 64-bit OSes. A new install is required. There are techniques to make the migration easier, but those are usually non-trivial for people unacquainted with the Unix/Ubuntu command line.

---

