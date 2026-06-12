---
title: "Some inital questions after successful 15 10 installation"
date: 2016-03-04
forum: New to Ubuntu
---

### Post by William_Fuller on 2016-03-04
Hi !

I’m new to linux, having dabbled with a couple of distribs over the years but never able to leave my XP SP3 which has served me faithfully for over 10 years, until now (more and more unsupported). I’m still using the following config which I built myself in 2005 and upgraded with more powerful graphics cards, changed hard drives etc. It’s really solid and stable and I don’t want to invest in new hardware (complete change) if I can avoid it.

&#65279;
Processor
AMD Athlon(tm) XP 3200+
&#65279;
BIOS
Date
11/12/2004
Vendor
Phoenix Technologies, LTD ([www.phoenix.com]("http://www.phoenix.com"))
Version
ASUS A7N8X-E Deluxe ACPI BIOS Rev 1013
Board
Name
A7N8X-E
Vendor
ASUSTeK Computer INC. (SEAGATE, [www.seagate.com]("http://www.seagate.com"))

&#65279;
Multimedia
Audio Adapter
NFORCE - NVidia nForce2
Audio Adapter
MPU-401 UART - MPU-401 UART
&#65279;
VGA compatible controller
NVIDIA Corporation G71 [GeForce 7800 GS] (rev a2) (prog-if 00 [VGA controller])

I had a look around the myriad of Linux OS and plumped for Lubuntu 15.10 which seems to fit my bill best. May I ask a few newbie questions to all you experts out there ?

My install from usb went perfectly. After a couple of days the only problem I have been having is intermittent crashes of firefox. I transferred my passwords and bookmarks from my previous OS but I don’t think the crashes are due to this.

I also tried to install skype (ubuntu 10.04 32 bit ). The installation went fine but I couldn’t use the app. Is this because my processor doesn’t support SSE2 ( ubuntu info &#65279;"Certaines configurations anciennes équipées de processeurs tels que des Athlon n'intégrant pas le SSE2 ne peuvent actuellement plus faire tourner la version 4.3«) or because I need &#65279;PulseAudio, or both ?

Quite honestly I can survive without Skype if I have to. My real questions are:
With my config, what critical limitations and problems may I encounter ? 
Would it be better to install Lubuntu 14 04 lte now or wait and update to the lte 16 04 in April ?

I hope maybe somebody else has followed the same path as myself and can help me to shorten my learning curve! 

Thanks, Bill

---

### Post by mastablasta on 2016-03-04
> **William_Fuller said:**
> 
&#65279;
Processor
AMD Athlon(tm) XP 3200+
I also tried to install skype (ubuntu 10.04 32 bit ). The installation went fine but I couldn&#8217;t use the app. Is this because my processor doesn&#8217;t support SSE2 ( ubuntu info &#65279;"Certaines configurations anciennes équipées de processeurs tels que des Athlon n'intégrant pas le SSE2 ne peuvent actuellement plus faire tourner la version 4.3«) or because I need &#65279;PulseAudio, or both ?

if this is Athlon 64 XP 3200+ then it has SSE2 as well as SSE3.

install Skype from software center. enable partner repositories and install Skype. what exactly does not work? you may need to use the ld preload trick to get it to load. LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so Skype

is this a 64 bit OS you installed? if so you will need to install i386 architecture files first before installing Skype.

in any case run it form terminal you should get errors there you can use to troubleshoot, if it doesn't launch.

&#65279;
> 
My install from usb went perfectly. After a couple of days the only problem I have been having is intermittent crashes of firefox. I transferred my passwords and bookmarks from my previous OS but I don&#8217;t think the crashes are due to this.

I've been noticing sporadic crashes of firefox on Kubuntu as well. Not sure where the issue is exactly. could be the old flash plugin. you can use chromium or chrome. though Chrome and it's pepperfelsh plugin will loose 32bit OS support soon.


> 
With my config, what critical limitations and problems may I encounter ? 


How much RAM do you have? if you can pump it up as much as you can but at the same time don't invest too much in it. motherboard can go out any time now...

GPU is still supported by NVidia. probably for a couple more years. then oyu can decide what to do.

> 
Would it be better to install Lubuntu 14 04 lte now or wait and update to the lte 16 04 in April ?

I think you are good. you can upgrade to 16.04 form 15.10 for a bit longer support period.


by the way I have a very similar setup. only with AMD GPU. I haven't moved to Linux yet as I still play games on XP. but yes, more and more stuff is no longer supported. only I am really short on money so I do what I can with my old PC's. I will change it when it's bricked. until then if it works, why change?!

---

### Post by William_Fuller on 2016-03-04
Hi Mastablasta !

If I remember right my Barton was the best 32bit at that time as I couldn&#8217;t afford the then new 64bit processor- so apparently just SSE .  I&#8217;ve got a spare MB, processor and  2GB of ram which is the max supported so I think I will crash before my hardware does ! . I&#8217;ve uninstalled skype but when I&#8217;ve got a moment I&#8217;ll have another try...just in case

Processor
Name
AMD Athlon(tm) XP 3200+
Family, model, stepping
6, 10, 0 (AMD Athlon XP/MP (Barton))
Vendor
AuthenticAMD
Configuration
Cache Size
512kb
Frequency
2200,00MHz
BogoMIPS
4426,00
Byte Order
Little Endian
Features
FDIV Bug
no
HLT Bug
no
F00F Bug
no
Coma Bug
no
Has FPU
yes
Cache
Level 1 (Data)
2-way set-associative, 512 sets, 64KB size
Level 1 (Instruction)
2-way set-associative, 512 sets, 64KB size
Level 2 (Unified)
16-way set-associative, 512 sets, 512KB size
Capabilities
fpu
Floating Point Unit
vme
Virtual 86 Mode Extension
de
Debug Extensions - I/O breakpoints
pse
Page Size Extensions (4MB pages)
tsc
Time Stamp Counter and RDTSC instruction
msr
Model Specific Registers
pae
Physical Address Extensions
mce
Machine Check Architeture
cx8
CMPXCHG8 instruction
apic
Advanced Programmable Interrupt Controller
sep
Fast System Call (SYSENTER/SYSEXIT)
mtrr
Memory Type Range Registers
pge
Page Global Enable
mca
Machine Check Architecture
cmov
Conditional Move instruction
pat
Page Attribute Table
pse36
36bit Page Size Extensions
mmx
MMX technology
fxsr
FXSAVE and FXRSTOR instructions
sse
SSE instructions
syscall
SYSCALL and SYSEXIT instructions
mmxext
Extended MMX Technology
3dnowext
Extended 3DNow! Technology
3dnow
3DNow! Technology
3dnowprefetch

vmmcall

Memory
Memory
Total Memory
2062868 kB
Free Memory
517528 kB

Thanks for the upgrade advice. I&#8217;ll just hang on till 16.04 comes out. Must say the Ubuntu community is vast and pretty technical: it&#8217;s going to be some time before I can contribute something.

Thanks again. I feel much less uncertain about the change and I&#8217;m looking forward to discovering more about this new environment.

---

### Post by ajgreeny on 2016-03-04
Just for your info, you can see more detail of the cpu's  abilities and what it supports by using command ```
cat /proc/cpuinfo
``` and looking for the **flags** line

---

