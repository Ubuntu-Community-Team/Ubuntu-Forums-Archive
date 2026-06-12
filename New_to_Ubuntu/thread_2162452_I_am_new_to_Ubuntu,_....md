---
title: "I am new to Ubuntu, ..."
date: 2013-07-14
forum: New to Ubuntu
---

### Post by CrimsonDragon on 2013-07-14
Hello All,
 I am new to ubuntu and now am loading 12.04 for the secondtime ... I am having issues with
low-graphics mode ... I searched the forum but most of what it has to say is shall we say a little
above my skill set as of yet. I need to take baby steps...

---

### Post by Bashing-om on 2013-07-14
CrimsonDragon; Hi ! Welcome to the forum .

Small steps and a little at the time:
From your install desktop . key combo ctl+alt+t yields a terminal:
To see your graphics card and info:
Post back - between code tags (#) the output of:

```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
And we will want your CPU info to insure it is capable of running high end graphics:
```
cat /proc/cpuinfo
```

[INDENT][INDENT]once we know we can advise further.[/INDENT][/INDENT]

---

### Post by CrimsonDragon on 2013-07-14
```

PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: RS880M [Mobility Radeon HD 4200 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:e0000000-efffffff ioport:3000(size=256) memory:f0300000-f030ffff memory:f0200000-f02fffff

```

```

01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Kernel driver in use: radeon
    Kernel modules: radeon

```

```

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) II P340 Dual-Core Processor
stepping    : 3
microcode    : 0x10000c8
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
bogomips    : 4389.33
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) II P340 Dual-Core Processor
stepping    : 3
microcode    : 0x10000c8
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
bogomips    : 4389.33
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```
Hopefully I did that correctly ...

---

### Post by Bashing-om on 2013-07-14
CrimsonDragon; 
Doable ,, but please use the code tag available at the top of the post to insure your output is readable.

To situation at hand...You are in the same boat as:
[http://ubuntuforums.org/showthread.php?t=2162391&p=12731014#post12731014](http://ubuntuforums.org/showthread.php?t=2162391&p=12731014#post12731014)
And the same advise applies.
If you desire a stable system using proprietary drivers ... the best thing at this time is to install the 12.04.1 version.

[INDENT][INDENT]not even a perfect world, but[/INDENT][/INDENT]

---

### Post by CrimsonDragon on 2013-07-14
Bashing-om -- I am not certain I understand what you mean by 'use the code tag available at the top of the post', did I mention newby?
and your assitance is most appreciated ...

---

### Post by CrimsonDragon on 2013-07-14
I would also like to know if that means I need to down grade my version of Ubuntu?

---

### Post by Bashing-om on 2013-07-14
CrimsonDragon; Hey ..

Not a problem, we were all new at one time...
Code tag: when you respond on the forum, at the top of that post are a number of "tools", second row, 3rd from end is "#" (code tag). Click on that and will place the tag into you post, selecting "paste" from right click after "copy" action will place the contents between the code tags.

Downgrading... Yeah it is in one sense... you are then using the 3.2 series kernel.. that still has full support until 2017.
That will entail (re-)installing with version 12.04.1 (currently 12.04.2 has been introduced with the 3.5 series kernel - no support from AMD for their proprietary drivers, nor anything above for your graphics card).

Now if you want to stay stable cutting edge, then the only recourse you have presently to maintain that stable/updatable system is to use the open source driver.

[INDENT][INDENT]comprende ??[/INDENT][/INDENT]

---

### Post by CrimsonDragon on 2013-07-14
```
 ok but I am not certain what that does or why?
```

---

### Post by CrimsonDragon on 2013-07-14
Ok now I get it, it goes around the code that I pasted so you know where it starts and ends ... lol ...

---

### Post by lamlom on 2013-07-14
Hello All,
I'm new on this site, and I want to discuss some topics,
But it is difficult to achieve that.
I hope from the site to make this easy to access.

---

### Post by CrimsonDragon on 2013-07-14
Hello lamlom ... welcome
would you like to open a new topic / thread ?

---

### Post by Bashing-om on 2013-07-14
@ CrimsonDragon -- Hey ..
Ya got the code thing down ! ( ya can also do it from terminal, next lesson ).

Ya got an idea of what you want to do in respect to your graphics ? Hint: if it ain't broke, do not fix it !

---------------------------
@ lamlom; Hi, Welcome to the forum.

This forum is easy to navigate. See a subforum in the area of your interest, click on it and read away. Got something pertinent to the thread to add... you now know how. "new Thread" at the top of the post, starts your own personal dialog. Start that new thread within the subforum pertaining to your question.
Be advised, this is an open forum... there is no such thing as a "dumb" question. Only dumb thing is if you do not ask.

2nd lesson: fonts ! Bold font is considered shouting. There is no need to shout in order to be "heard" . Your last font is offensive to the eyes.
Attend well to the "do's and dont's", follow the guidelines and you will be up-to-speed in no time.

[INDENT][INDENT]hey yall, just try'n to help
[/INDENT][/INDENT]

[INDENT][INDENT]choose an area and ask away[/INDENT][/INDENT]

---

### Post by CrimsonDragon on 2013-07-14
@Bahing-om,
 Well it all depends on the def of broken, I need the graphics functions for work and games ... So that
being said I loaded 12.04.01 ... now I have to do all of the configuring to get things to play nice ...
Thanks for the assist, will more than likely post as things go wrong ... lol

---

### Post by Bashing-om on 2013-07-14
CrimsonDragon;
Ok ! ... 
Give the open source drivers a fair shake before think'n that a proprietary driver will fix ya right up ... may not even be as good as the ubuntu developed driver.
Try the easy way first from 12.04.1 install; system setting -> Additional Drivers; let the wizard choose and install the proprietary driver.
In the event that is still not satisfactory - yuk - there are other options that one may consider.
a) Bleeding edge drivers from ubuntu supported PPA (Personal Package Archive)
b) ATI support site, download and install the driver manually.

One other word of advise, when you go to messing about with drivers, clean up behind yourself ! Only install different drivers after you have completely removed the prior driver. It can get real messy if one does not know what they are doing and paying attention to the details.

Staying with ubuntu's package manager ( Additional drivers is a part of it ) the package manager will take care of all details. Step out from under ubuntu's umbrella of protection, well then you are expected to know how to handle it !

By all means we are here and can offer all kinds of guidance, and point ya at the docs ya need to to read and heed - there are plenty of how-to's. When all is  said and done, installing  graphics drivers ain't no step for a stepper.

[INDENT][INDENT]one thing then another[/INDENT][/INDENT]

---

### Post by CrimsonDragon on 2013-07-14
Bashing-om --- well here is the list of tests and trials ...

-- tried the generic ubuntu driver but would not run the graphics ...
-- manually loaded the ati catylist drivers but it kept saying there were load failures ...
-- So Loaded 12.04.1 .. lo and behold the driver appeared in the system settings .. aditional drivers ...
-- Loaded software updates first ... then rebooted ... 
-- Activated the driver in the aditional drivers window and rebooted when it was complete ... 
-- System now show this driver in use and will have load and test the games/software to see if it works ...

thanks bashing you have been a huge help ... :)

---

