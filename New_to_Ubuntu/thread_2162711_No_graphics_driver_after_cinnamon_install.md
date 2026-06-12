---
title: "No graphics driver after cinnamon install"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by Meanmachine187 on 2013-07-15
Hi all,

I'm quiet new in using Ubuntu and have only a little experiences in using Debians Shell.

I installed the current Ubuntu version on my IntelliBook. Because I liked the default theme not that much, I installed CINNAMON. Everything worked fine so far, until I logged in. On the desktop, a message box appeared that told me, that CINNAMON is running hardware rendered only, because no driver for my graphical device could be found.

I thought, the theme is only a gui thing that uses the same drivers just as the already installed theme.

May anyone tell me what to do to install the drivers? I already tried to search under hardware -> drivers that no device was found.

Is there a default way to go if a driver was not found?

If you need more information I can post them in here.

Thanks and best regards,

Dirk

---

### Post by CinTUX on 2013-07-15
Could you try out the command **jockey-text**?
This will search for available drivers and apply them.

---

### Post by Meanmachine187 on 2013-07-16
Thanks, I entered jockey-text --list in terminal and got the message "kmod: cedarview_gfx - Cedar Trail drm driver in DKMS format. (Proprietary, disalbed, Not in use)". When I enter jockey-text, the first time nothing happens at all, the second time, "Additional Drivers Searching for available drivers..." is output. But nothing else.

I googled a little bit and read, that there is a need to install three additional drivers, but not which drivers, etc.? Does anyone have a newbie friendly explanation what I have to do?

Thanks and best wishes,

Dirk

---

### Post by Bashing-om on 2013-07-16
Meanmachine187; Hi !

Back to basics; let's see what hardware and drivers you have:
Post back the outputs of terminal codes:
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
and a look at the hardware to see if it supports higher ended graphics:
```

cat /proc/cpuinfo

```

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by Meanmachine187 on 2013-07-17
Hi Bashing-om,

thanks for your response. As you can see, I ran your commands on the terminal. This is the information I got:
[B]
sudo lshw -C display[/B]
```
 *-display               
       description: VGA compatible controller
       product: Atom Processor D2xxx/N2xxx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:44 memory:80200000-802fffff ioport:40d0(size=8)

```

**lspci -nnk | grep -iA3 vga**
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device [1558:2100]
    Kernel driver in use: gma500
    Kernel modules: gma500_gfx

```

**cat /proc/cpuinfo**
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 54
model name    : Intel(R) Atom(TM) CPU N2600   @ 1.60GHz
stepping    : 1
microcode    : 0x10d
cpu MHz        : 600.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm arat dtherm
bogomips    : 3192.01
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 54
model name    : Intel(R) Atom(TM) CPU N2600   @ 1.60GHz
stepping    : 1
microcode    : 0x10d
cpu MHz        : 600.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm arat dtherm
bogomips    : 3192.01
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 54
model name    : Intel(R) Atom(TM) CPU N2600   @ 1.60GHz
stepping    : 1
microcode    : 0x10d
cpu MHz        : 600.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm arat dtherm
bogomips    : 3192.01
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 54
model name    : Intel(R) Atom(TM) CPU N2600   @ 1.60GHz
stepping    : 1
microcode    : 0x10d
cpu MHz        : 600.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm arat dtherm
bogomips    : 3192.01
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

The thing is, the graphics device seems to be recognized properly and be used instead of hardware rendering.

Hope, this information helps you to help me. ;)

Thanks and best wishes,

Dirk

---

### Post by Bashing-om on 2013-07-17
Meanmachine187; Morning .

Looks good,  Great processor - driver is loaded;
Let me do a bit of looking about... To be Honest, best I recall performance with the gma500 driver is not the best in the world...
I could be mistaken ... will do my homework and get back at ya.

[INDENT][INDENT]later later
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-17
Meanmachine187; -later to present.

Yeah .. looking about ... the performance with gma500 is poor, due to lack of support. see:
[https://wiki.archlinux.org/index.php/Poulsbo](https://wiki.archlinux.org/index.php/Poulsbo)
There is a little bit of help that might apply from Arch for ubuntu...more info here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
Advisement is that ubuntu version 12.04.1 (note this version has the 3.2 kernel series and Xserver is more compatible with your graphics card) will perform better.
To check the driver performance: Terminal code:
```
lsmod | grep gma
```
The output of  should look like this:
> 
gma500_gfx            131893  2 
i2c_algo_bit            4615  1 gma500_gfx
drm_kms_helper         29203  1 gma500_gfx
drm                   170883  2 drm_kms_helper,gma500_gfx
i2c_core               16653  5 drm,drm_kms_helper,i2c_algo_bit,gma500_gfx,videodev


Hey not much help, sorry... see what you can do and advise us, as additional guidance is needed. AND let me know how thing go, please.
We are here to help.

[INDENT][INDENT]step'n out, but not as tall[/INDENT][/INDENT]

---

### Post by Meanmachine187 on 2013-07-19
Hi,

thanks a lot for your answer(s). Because I'm quite new and I don't have the experiences, I tried another theme (it seems as only the cinnamon theme does not recognize my graphical device), the MacBuntu theme which I like from the lookalike and it works with my graphics device ;)

I already have a question to this theme (in another topic).

Thanks once again for the great help here! If I would have more experience I think I would be motivated to solve the graphics problem, but because I'm new I just want to use Ubuntu and try it out.

Thanks and best wishes,

Dirk

---

### Post by Bashing-om on 2013-07-19
Meanmachine187; Hey ,

You are quite welcome. Time will garner the experience !
Ubuntu desktop edition is "one size fits all" and when the fit is not right, gotta roll ones sleeves up and go to work ! Then it does take some know how and that, my friend, is where we can come in.
This is open source -> no secrets ! On this forum the policy is there are no dumb questions, the only dumb thing is a question not asked.

[INDENT][INDENT]it is all a learning experience[/INDENT][/INDENT]

---

