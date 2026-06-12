---
title: "why ubuntu.com recommends a 32 bit OS?"
date: 2013-01-14
forum: Recurring Discussions
---

### Post by GnuKian on 2013-01-14
1. If you go to  [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) , 32bit OS is flaged by  "recommended"? why? a 32 bit ubuntu is better than a 64 bit?
I know a 32 bit OS works on a big variety machines, but as you know, most CPUs that have been made in the last decade and earlier years, are 64 bit!

2. however, I have a 64 bit machine, which one is better for my PC? a 64 bit (recommended) or a 32bit?
more details are here:
```
$ lspci
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Radeon HD 4350]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:01.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 02)


```
grep --color=always -iw lm /proc/cpuinfo
```flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx [COLOR=Red]lm[/COLOR]  constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl  vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm tpr_shadow vnmi  flexpriority

---

### Post by snowpine on 2013-01-14
It's a bug:

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

You can download and install 64 bit with confidence, in my opinion. Take it for a test drive in Live mode (try without installing) just to be sure. :)

---

### Post by CyclicFlux on 2013-01-14
I initially was a tiny bit thrown off by that too.  However, it is just because they want to play it safe, since Ubuntu's one of the most widely used Linux variants, many people likely don't know, or aren't familiar with their architectures.  Now the role the 32-bit plays in is that its universal in compatibility, meaning 32-bit will work on either 32-bit or 64-bit systems.  Now Ubuntu.com could do what most sites do, and merely retrieve the right *.iso/*.img file for architecture can be downloaded.  But one this could be spoofed, or the user's OS-type could be different than the one that they are using to download the ubuntu system image file. So the safest bet is to go with the 32-bit recommendation for those that aren't familiar with their operating system.  

The long and the short of the differences between 64-bit and 32-bit is that data can be processed in larger chunks in 64-bit systems than in 32-bit systems.  To put it in simplistic terms, think of the architectures as a container, and a 12oz(64-bit) bottle can hold a 6oz's(32-bit) contens as well as 12oz's(this comparison of course assumes architecture-related hardware compatibilities, i.e. bus/etc...).  But in this model, looking at the capacity of a 6oz bottle, could not hold the contents of a 12oz bottle.  Easiest way of looking at it with reference to your question.

In a more technical sense,32-bit is different from a 64-bit due to the number of unique additional values a 64-bit system can hold as opposed to 32-bit.  The precise memory capability for a 64-bit system is as follows, 2^64 = 18446744073709551616, which comes out to a staggering 18 quintillion(10^18), which in byte-based memory terms, translates to roughly (2^64bytes)16 exbibytes(EiB)(2^60) of memory per register.  Whereas in 32-bit systems, there is a 4gigabyte(10^9), 2^32=4294967296 memory limit in the register/address bus for processing, the limit is much higher.  The 64-bit register is exponentially double that of the 32-bit.  So this illustrates as well that a 64-bit architecture has more than enough capacity to run a 32-bit system.  This assumes sofware/hardware compatibility are met.

A real-life illustration of the 32-bit/64-bit compatibility dates back to Microsoft before the transition from Windows XP to Vista.  During the 1990s, retailers of all sizes began to sell both 32-bit and 64-bit operating systems. As the hardware price-points for 64-bit processors, and architecture-related hardware became low enough for the masses(since the initial creation of 64-bit architecture has existed since the 1970s).  However, Windows XP was not 64-bits, although it ran on both 64-bit and 32-bit operating systems.  Interestingly enough, on 64-bit systems, the Windows Software treated them as 32-bit operating-systems. It was actually roughly 10 years, (as mentioned in link at the end of sentence) or so until Windows had an operating system which was 64-bits, and Windows installs for 64-bit systems outnumbered those of 32-bit systems[This goes over some of the architecture background]("http://www.techsupportalert.com/content/32-bit-and-64-bit-explained.htm")   Additionally, IBM was noted to use 32-bit operating systems for their Linux-based OS, and they did so all the way up until the early 2000s.  So Microsoft was not the only one[you'll find the IBM note later on in the article]("http://en.wikipedia.org/wiki/64-bit_computing").  

More information on the lag in Microsoft compatibility is mentioned here(though its not the ideal article I was looking for, the one I read was like 5 years ago), but this does mention it: [Wikipedia article examining the history of the Windows OS, and architecture]("http://en.wikipedia.org/wiki/Microsoft_Windows")

I often hear misconceptions on architecture and the like all the time.  But 32-bits being able to be ran in 64-bit environments for those that don't know their architecture type is the logical reason Ubuntu recommends the 32-bit, as a 'play it safe' method.  Furthermore, all live disks for rescue/emergency I use have a 32-bit architecture, unless I am doing  an install, which I'd definitely want to match the proper architecture to leverage the performance/processing of the system itself.

---

### Post by MadmanRB on 2013-01-14
Well there are still a great many apps/codecs/drivers and such that are made for 32bit only, and while that can be bypassed its not as easy for a newer user who may not know how to do such a thing.
Its more of a safety net, a 64bit install of Ubuntu will do no harm but expect possible incompatibilities.

---

### Post by ibjsb4 on 2013-01-14
Most 64/32 bit compatibility problems have been resolved, but if you get hit with one your sunk.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=multiarch&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=multiarch&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by oldos2er on 2013-01-14
> **CyclicFlux said:**
>   Now the role the 32-bit plays in is that its universal in compatibility, meaning 32-bit will work on either 32-bit or 64-bit systems.  

Actually I think it's been shown that UEFI systems won't boot the 32-bit version, so the above is no longer true, which makes this ongoing bug even more of an embarrassment.

Edit: The bug status shows "fix released," but the Ubuntu download page still shows 32-bit recommended.

---

### Post by rudregues on 2013-01-16
> **snowpine said:**
> It's a bug:

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

You can download and install 64 bit with confidence, in my opinion. Take it for a test drive in Live mode (try without installing) just to be sure. :)

snowpine, in the link you posted, according to user Tanya Edwards:
> 
The review of these pages will be done as part of the 13.04 release.   All your comments will be taken on board.  Hopefully you will see an  improvement to the page in 13.04 release.

(it's the last comment right now)

  [ ]'s

---

### Post by oldos2er on 2013-01-16
"Hopefully"? We had hope back in 2010, see post #19, and #30. Forgive my cynicism, but I'll believe this is fixed when I see it.

---

