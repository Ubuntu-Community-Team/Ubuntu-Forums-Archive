---
title: "Ubuntu 14.04-CPU Core Detection &amp; Touch-Pad"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by alfaceor on 2014-06-06
Hi everyone i just installed ubuntu 14.04 in mi notebook and i have a lot of problems
1. Just detect 1 processor of an core i5 (windows detect the 4)
2. The touchpad and the function key doesn't work either.

```

$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping    : 2
microcode    : 0xc
cpu MHz        : 2266.701
cache size    : 3072 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4533.40
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by sudodus on 2014-06-06
I think the core issue is very different from the other two issues.

If we can solve one of the issues quickly, we can change the title to cover the remaining problem(s)

I think you are better off getting help for the different issues in different threads (with good titles, that attract those who know about it and can help).

Anyway, I suggest that you do a few things to make it easier for us to help

1. Install and run htop

```
sudo apt-get install htop
```

```
htop
```

htop should show 4 lines at the top (one for each core)
```
  1  [||                        2.6%]     Tasks: 125, 248 thr, 61 kthr; 1 runnin
  2  [|                         0.7%]     Load average: 0.13 0.09 0.06 
  3  [|                         2.6%]     Uptime: 04:31:41
  4  [|                         0.7%]
  Mem[||||||||||||        613/4030MB]
  Swp[                      0/8199MB]

  PID USER      PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 5926 olle       20   0  780M  142M 42944 S  0.0  3.5  0:16.23 /usr/lib/thunderb
 6238 olle       20   0  6672  1840  1332 R  1.0  0.0  0:00.34 htop
 2791 root       20   0 69700 50376 14252 S  1.0  1.2  3:05.15 /usr/bin/X :0 -au
    1 root       20   0  3768  2168  1352 S  0.0  0.1  0:00.83 /sbin/init
    2 root       20   0     0     0     0 S  0.0  0.0  0:00.00 kthreadd
    3 root       20   0     0     0     0 S  0.0  0.0  0:00.05 ksoftirqd/0
    6 root       RT   0     0     0     0 S  0.0  0.0  0:00.00 migration/0
    7 root       RT   0     0     0     0 S  0.0  0.0  0:00.02 watchdog/0
    8 root       RT   0     0     0     0 S  0.0  0.0  0:00.05 migration/1
   10 root       20   0     0     0     0 S  0.0  0.0  0:00.05 ksoftirqd/1
   12 root       RT   0     0     0     0 S  0.0  0.0  0:00.02 watchdog/1
   13 root       RT   0     0     0     0 S  0.0  0.0  0:00.00 migration/2
F1Help  F2Setup F3SearchF4FilterF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit
```

```
  1  [||                        2.6%]
  2  [|                         0.7%]
  3  [|                         2.6%]
  4  [|                         0.7%]
```

How many such lines are there (1 or 4)?

---

### Post by sandyd on 2014-06-06
Are you using nolapic?
Whats the output of
```

/proc/cmdline
```

---

### Post by alfaceor on 2014-06-06
My outputs are

alfaceor@rolandito:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=9f7542a5-7d1c-4986-9470-677df22ce97d ro acpi=off quiet splash vt.handoff=7

I can't copy and paste this is the output of [htop]("http://s15.postimg.org/73oqvt63v/Screenshot_from_2014_06_07_00_25_22.png")
Windows detect the 4 cores and the touchpad i use ubuntu before (8.04) and have no problems.
By the way i install ubuntu 14.04 with the apic=off option because the normal installation doesn't work, and in the installation process the touchpad doesn't work either.

I try to work with ubuntu but maybe i must return to windows, please some help will be appreciated.

---

### Post by sudodus on 2014-06-07
htop also detects only one core.

Please describe your computer. It makes it easier for us to help.

- Brand name and model of the computer and/or the motherboard
- CPU: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz (you told us already)
- RAM: size
- graphics chip/card
- wifi chip/card

-o-

- Try extensively different [boot options]("https://help.ubuntu.com/community/BootOptions"), not only one each time but also combinations. You can try live (without installing) until you find a good combination.

- It might be easier to succeed with the previous long time support version, Ubuntu 12.04 LTS.

- Did you try the 32-bit or 64-bit version of 14.04 LTS? It might work better with the other one.

---

### Post by alfaceor on 2014-06-07
Ok my computer is a Republic of gamers, asus g60jx [here]("http://support.asus.com/download.aspx?SLanguage=en&p=3&s=195&m=G60JX&os=30&hashedid=wNlU5jNxXL3CrjRU"). The bios is updated to version 208.

CPU: core i5
Graphic card: Geforce GTS 360M 1GB
RAM: 4GB
i don't know about mi wifi card, how can i get that information?

I try different boot options combinations, but that acpi=off load the live cd. I will try again just to be sure.

---

### Post by Frogs Hair on 2014-06-07
The following will display the wifi card .```
 lspci 
``` I'm currently using  similar hardware on an HP Elite Book W/ 14.04.

---

### Post by sudodus on 2014-06-07
I think Ubuntu has problems talking to the computer at a rather basic level. Sometimes it helps to update the BIOS/UEFI system. You can check if there is a new version for your computer.

---

### Post by squakie on 2014-06-07
> **Frogs Hair said:**
> The following will display the wifi card .```
 lspci 
``` I'm currently using  similar hardware on an HP Elite Book W/ 14.04.

For a shorter list:

lspci | grep Network

---

### Post by squakie on 2014-06-08
EDIT:  removed the text here, as my following post explains what to try.

---

### Post by squakie on 2014-06-09
Okay - the microcode is available right in ubuntu:

sudo apt-get install intel-microcode

It will install another package that is some type of manager for switching between firmware releases, but for now I would just install it and then reboot.

See if your CPU information has changed.

If it does, we can move on to the touchpad thing.


Also:  for AMD users there is also an amd-firmware package you can install.

These firmware packages are for corrections/additions to the firmware built in to the processor.  I personally never knew these existed before.  Might not be a bad idea to install the correct one for your processor brand and maybe it will be caught in the updates after that also if it changes in the future for more additions/changes.

---

### Post by squakie on 2014-06-11
Did this help your situation?

---

### Post by alfaceor on 2014-06-13
> **sudodus said:**
> I think Ubuntu has problems talking to the computer at a rather basic level. Sometimes it helps to update the BIOS/UEFI system. You can check if there is a new version for your computer.

Hi sudodus i update the bios the last version is the 208 as in my initial post. I still can't find any solution? Some people tell to change to linux mint or debian. But maybe i have the same issues there too. There is another option, because i installed ubuntu 14.04 in my desktop computer at office and works fine.

The output of the lspci is 

```

alfaceor@rolandito:~/Projects/ceor-phd/GasHeatBath$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT215M [GeForce GTS 360M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
06:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] (rev 01)
06:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
07:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)


```

---

### Post by alfaceor on 2014-06-13
> **squakie said:**
> Did this help your situation?
Hi squakie thanks for you reply but i install the intel-microcode and just 1 processor was detected after the reboot.

---

### Post by squakie on 2014-06-13
Sorry that didn' t help - that was about the only left from the things I found, and I honestly thought it would help.  Oh well.   This is beyond my skill leves at this poin so I'm bowing out.  Sory, and best of luck!

---

### Post by sudodus on 2014-06-14
> **alfaceor said:**
> Hi sudodus i update the bios the last version is the 208 as in my initial post. I still can't find any solution? Some people tell to change to linux mint or debian. But maybe i have the same issues there too. There is another option, because i installed ubuntu 14.04 in my desktop computer at office and works fine.

The output of the lspci is 

```

alfaceor@rolandito:~/Projects/ceor-phd/GasHeatBath$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT215M [GeForce GTS 360M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
06:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] (rev 01)
06:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
07:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)


```

> **squakie said:**
> Sorry that didn' t help - that was about the only left from the things I found, and I honestly thought it would help.  Oh well.   This is beyond my skill leves at this poin so I'm bowing out.  Sory, and best of luck!

I have no more ideas to get 14.04 LTS recognize all cores ... but I can suggest

1. to follow what you thought of already, to try other linux distributions. And in this case, I suggest that you try distros that are not closely related to Ubuntu, but more distant relatives. I think Linux Mint might have very similar kernels. Debian is more different, Fedora and OpenSuse are even  more distant (to mention a few of them).

2. to give up the newest version (14.04 LTS) and try with the two year old version Ubuntu 12.04 LTS which has long time support until April 2017. It is well debugged and polished, and it might work better with your hardware.

---

### Post by squakie on 2014-06-14
I do suspect it's firmware related  - the processor is recognized but the actual number of cores isn't.  A lot of times that has been problems with either the processor not identifying itself correctly, the motherboard BIOS not recognizing it correcly, the firmware in the OS, or something in a kernel module that isn't picking these up.  I would do as sudodus says:

- try an older supported version with an older kernel

- try a non-debian based distro.  Indeed Mint is actually based on ubuntu, so i would stay away from it also.

---

### Post by alfaceor on 2014-07-11
I was using debian 6 before and have no problems.

---

