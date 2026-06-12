---
title: "Set cpu frequency"
date: 2016-10-14
forum: New to Ubuntu
---

### Post by lschw on 2016-10-14
Hello all, I'm new at this forum and I have a question about the cpu frequency setting:

I downloaded cpufrequtils and with the command cpufreq-info I found out that the frequency is hold between 3.30 GHz and 3.30 GHz which is quite energy consuming as you might guess... So I tried to set a governor to "powersave" which cpufreq-info also detects. But still the frequency is hold on 3.30 GHz. 
I then looked at /sys/devices/system/cpu/cpu*/cpufreq/scaling_min_freq
There I saw  3.30 GHz again and I changed it to the value from /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_min_freq
But still cpufreq-info shows 3.30 GHz...
I also observed that after a reboot all the file get reset to the energy consuming setting.

My machine runs a Intel Core i7 processor with 4 cores.

What have I overlooked to get a less energy consuming setting?

---

### Post by colmax on 2016-10-14
Hi lschw
Wonder if your motherboard supports overclocking / adjustment of the i7 chip
Bios may also be in performance mode
i'm pretty new to this stuff as well so maybe post your machines specs so more knowledgeable people may have some ideas
Cheers

---

### Post by lschw on 2016-10-16
Thanks for your answer. 
So here some information about my machine:
```
Handle 0x0000, DMI type 0, 24 bytesBIOS Information
    Vendor: American Megatrends Inc.
    Version: K55VM.211
    Release Date: 09/11/2012
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 6144 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Product Name: K55VM
    Version: 1.0       
    Serial Number: C5N0AS038687186     
    UUID: 8351BB00-9605-81E1-2262-10BF4815CBDB
    Wake-up Type: Power Switch
    SKU Number: ASUS-NotebookSKU
    Family: K



```

```
processor    : 0vendor_id    : GenuineIntel
cpu family    : 6
model        : 58
model name    : Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
stepping    : 9
microcode    : 0x12
cpu MHz        : 1754.199
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 4589.66
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:



```

---

### Post by mcduck on 2016-10-16
looking at the last output, when you ran that, the CPU was scaled down to 1.8GHz. So I'd assume you are just getting false number from cpufreq-info and the scaling is actually working just fine.

That would definitely not be uncommon situation with a modern CPU that has some control over the frequency on it's own instead of relying on the OS to do everything.

---

### Post by lschw on 2016-10-17
Hmm that might be true but actually it is around 3.3 GHz most of the time. After a reboot all the [COLOR=#000000]scaling_min_freq - files are set to 3.3 GHz and the processors look very busy again. Can I change the standard behavior after boot somewhere?[/COLOR]

---

### Post by mcduck on 2016-10-17
if the processor is actually busy, then you'd definitely *want* it to run at full speed. With the modern CPU's, it's less energy consuming to do whatever task the CPU has at fastest possible speed so you can drop to low-speed idle as soon as possible. So if there's any work to do you'd actually use more energy by forcing the CPU to lower frequency, since it would take much longer to complete the task.

Then only exception would be "uncompletable" tasks, like playing a game, which would last as long as you keep the game running and therefore the CPU can't complete it any quicker and get back to idle.

Anyway, If the CPU is busy after boot, give it a bit of time, and if it doens't drop to idle then you might want to chekc what's keeping it busy and solve that instead.

---

### Post by QIII on 2016-10-17
Have you used top or htop to determine what is consuming your CPU resources when utilization is so high?

CPU throttling is pretty much handled at hardware level any more and frequency scaling by the OS is generally not necessary.  If the CPU is running that hard, something is running and causing it.

---

### Post by lschw on 2016-10-19
Thanks for the answers.

Well, according to htop the utilization of the different cores is less then 10 % each. But cpu-frequency still seems to be around 3 GHz. I don't know if the cpus spin around or something like that?

---

### Post by QIII on 2016-10-19
Hello again!

Just to reiterate:  your CPU is designed with a max frequency of 2.3GHz.  At the time you gave us the results of your commands in the terminal, it was running at roughly 1.8GHz.

Where are you seeing 3.0GHz?

---

### Post by mcduck on 2016-10-19
Well, the max turbo boost frequency for i7-3610QM *is* 3.3GHz. But that's controlled by the CPU itself, not the OS, so changing the governors on Ubuntu side would not have any effect on that,the governors would only get to the highest base frequency (2.3GHz) . If you see the CPU running at that speed it's because it has itself decided that whatever it is doing at the moment would benefit from the boost. (which would mean there must be something actually using at least one core heavily)

If you aren't seeing that kind of load, and cpufreq-info reports that speed while other tools don't, I'd assume cpufreq-info's reading as false.

---

### Post by colmax on 2016-10-19
If battery power is the issue i'd suggest dimming your display cos the screen uses most power by far
If your chip is running overclocked that tends to be bios & os control
Agree with QIII with chip speed
Cheers

---

### Post by lschw on 2016-10-21
Hi all

After all your answers and advice I think the 3 GHz cpufreq shows are simply wrong. The informations from htop seem to be more accurate and also the battery time is not too bad for a quite old laptop with a big screen. 

So thank you all :D

---

