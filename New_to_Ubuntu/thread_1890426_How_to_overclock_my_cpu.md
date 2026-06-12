---
title: "How to overclock my cpu?"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by James.A.Parnell on 2011-12-03
Since the new ubuntu decides it wants to continually use the fan at full rpm, i may aswell overclock the cpu.. The Cpu runs between 55-57degrees all the time, and i want to beef it up some more..mainly just because i can. Turns out though, i cant without asking how. Does anyone have any tips on how to do such a thing.

**Edit:** It can't be done via BIOS, i've already checked

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping	: 9
cpu MHz		: 3058.854
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips	: 6117.70
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by Frogs Hair on 2011-12-03
I don't know of any over clocking software for Linux . If the bios is not an option there is not much you can do except continue to look for Linux OC software .

---

### Post by 2F4U on 2011-12-03
If you don't know how to overclock, you should probably not do it. Chances are that you ruin your hardware.

---

### Post by James.A.Parnell on 2011-12-03
> **2F4U said:**
> If you don't know how to overclock, you should probably not do it. Chances are that you ruin your hardware.

I know how to do it, just not on 11.10 & without a bios option xD

---

### Post by Lisiano on 2011-12-03
AFAIK, and I hope I'm wrong. There is no Linux software to OC a CPU. You can OC your GPU though. I'd take this thread to the [Overclock forums]("http://www.overclock.net/"). They can probably help you more.

---

### Post by Basher101 on 2011-12-03
you can ONLY overclock your Processor from the BIOS. It is controlled by your Motherboard and if you do not have the option by default, it is not capable of overclocking the CPU. End of story.


regards

---

### Post by Lisiano on 2011-12-03
@Bansher101 Some BIOSes allow directly modifying the clock settings  but some only allow to edit those settings in software, even OEM motherboards, I can easily OC my CPU from 2.7Ghz to 3.0Ghz during runtime, BUT only if I'm in Windows (I can't OC higher since the CPU itself is locked). But that is not the point, point is, you can OC in software even if your motherboard doesn't allow to OC using the BIOS. The OP wanted to know if there is a way to do a software OC in Linux just like you can do a software OC in Windows.

---

### Post by grahammechanical on 2011-12-03
A quick internet search shows that this question has been asked before over the last few years and the answer is still the same. 

I have found this dated last year.

[http://www.phoronix.com/scan.php?page=news_item&px=ODY2MA]("http://www.phoronix.com/scan.php?page=news_item&px=ODY2MA")

The manufacturers are best placed for creating utilities for manipulating their hardware but as usual they provide Windows utilities with the motherboard but not Linux ones. This is the state for my motherboard maker Asus. I have a motherboard that can be over-clocked both in BIOS and software. Everything is there to make it easy but the utilities are for Windows. And I do not use Windows.

Regards

---

### Post by Basher101 on 2011-12-03
overclocking by such a minor amount, i would not really call that actual overclocking but rather the "turbo boost" that most CPUs do (going up by 300 MHz). Everything around 600 MHz and up is what would actually push performance considerably, and in my opinion considered an actual overclock..

but thats just me..

---

### Post by Lisiano on 2011-12-03
For me it's still OC since I am going above the manufacturers settings which I consider OC. Regardless, the point that it's possible to OC in software still stands and as grahammechanical noted, most manufacturers only release tools to OC in Windows.

---

### Post by Basher101 on 2011-12-03
> **Lisiano said:**
> For me it's still OC since I am going above the manufacturers settings which I consider OC. Regardless, the point that it's possible to OC in software still stands and as grahammechanical noted, most manufacturers only release tools to OC in Windows.

MSI Afterburner being a good example, for overclocking and overvolting video cards...but yeah when you go by theory, even 1 MHz more would be an overclock..

---

### Post by SpawnHappyJake on 2012-03-31
[duplicate post minimized]

---

### Post by SpawnHappyJake on 2012-03-31
I know this thread is a little old, but it's one of the first that come up when one Googles "overclock cpu Linux".

So I feel a little obligated to debunk some very common myths, at least if they show up as the first search result.

Overclocking of modern CPUs is done by writing to a certain spot in the MSR (model/machine specific register).

It is my current understanding that the CPU sends whatever is at that spot in the MSR to a PLL chip. Using a crystal and other PLL systems, the PLL chip that the CPU sent the code to creates the requested frequency. The CPU is connected to this and goes that frequency.

If the BIOS is setting the CPU clock speed, it is writing to the MSR.

If software running under your operating system is setting the CPU clock speed, it is writing to the MSR.

Either way, you're overclocking via writing to the MSR. The two techniques (if you can even call them two _different_ techniques; more like one technique) do the same thing, and thus one's not better than the other, contrary to common belief (myth).


Another fallacy, though usually very subtly implied, is that the BIOS isn't software. The BIOS (or any firmware for that matter) is just as much 1s and 0s scurrying across your processor as FireFox is. There's not even a gray area. It can't be "partially software". It's either hardware or software.


There is an MSR kernel module for Linux that allows you to overclock the CPU from within Linux. And c2ctl and k10ctl use the MSR kernel module for you in your overclocking endeavors (both are Linux-native programs, of course).

See this thread:*[http://www.overclock.net/t/1205257/overclock-cpu-in-linux-necessary-program-names-given]("http://www.overclock.net/t/1205257/overclock-cpu-in-linux-necessary-program-names-given")

---

