---
title: "How to determine PENTIUM 4 , 64 bit capability"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Jonas thomas on 2008-07-24
I'm currently running the 32 bit version of 8.04 
My understanding is that some P4's can run 64 bit OS.
[http://ubuntuforums.org/showthread.php?t=716840]("http://ubuntuforums.org/showthread.php?t=716840")

The link above points to this intel chart:  [http://www.intel.com/products/proces...t/pentium4.htm]("http://www.intel.com/products/proces...t/pentium4.htm")

Questions: 
1)Short of tearing my computer apart to see what's on printed on the processor, is there a easy Ubuntu utility that will tell me the detailed information I need?

2) Aside from the processor,memory, are there any other land mines I need to watch out for? I suppose the next logical step would be to  get a 64 bit live CD to try it. If anyone has some other pre-test suggestions, I appreciate hearing them.
Btw I found this link interesting:
[http://ubuntuforums.org/showthread.php?t=836350]("http://ubuntuforums.org/showthread.php?t=836350")

3) Assuming my box is capable of running this in theory, will I regret doing this in the long run? Is anyone out there actually running 64-bit on a Pentium 4? (My main interested is to get OpenCascade running and most of the Debian work on this has been focused on the 64 bit enviroment?  (I experienced a lot of pain getting the 32 bit version working)

---

### Post by YaroMan86 on 2008-07-24
**Applications -> System Tools -> Device Manager** will tell you the details about your processor... or should.

64-bit Ubuntu doesn't really run any differently than 32-bit. The only real problem you'll have is getting Java to work. But if you're like me, you hate Java and won't care.

I'm running 64-bit Hardy on an Athlon 64. It runs fine.

There are three big benefits to x86_64, though.

1. It is slightly faster.

2. You can access a lot more memory than 32-bit, which is fast approaching its 4 GiB ceiling. That was one of the biggest reasons why the x86-type market went 64-bit.

3. You future-proof your machine. By the end of this decade, I imagine there's going to be primarily 64-bit operating systems. Just like when we jumped from 16-bit to 32-bit.

---

### Post by a0u on 2008-07-24
> **YaroMan86 said:**
> **Applications -> System Tools -> Device Manager** will tell you the details about your processor... or should.

 
The "device manager" of previous Ubuntu versions (hal-device-manager) has been replaced by gnome-device-manager, but I don't believe this is installed in Hardy by default.
```
sudo apt-get install gnome-device-manager
```
 
There's a slight mistake in the application's desktop configuration file that prevents it from automatically appearing in the GNOME menu. Go to [http://ubuntuforums.org/showthread.php?t=861473](http://ubuntuforums.org/showthread.php?t=861473) and look at post #7 for a solution.
 
Alternatively, you can simply open the device manager through the terminal:
```
gnome-device-manager
```

---

### Post by LowSky on 2008-07-24
when you boot up the computer just enter the BIOS menu it should display what model P4 chip you have, write it down and google it for specs..

---

### Post by Jonas thomas on 2008-07-25
I checked the BIOS as well the gnome-device-manager.  Both say Pentium 4 253 Ghz.   My mother board is a ASUS P4V8X-MX.
For some reason I'm having trouble getting the specs on that one from Intel.
I guess I should try ASUS tech support.

---

### Post by cariboo on 2008-07-25
THe easiest way to find your cpu's capabilities is open up a terminal and type:

```
cat /proc/cpuinfo
```

This will tell you as much as you need to know.

Jim

---

### Post by Thelasko on 2008-07-25
The best way to find out about 64 bit is the 64 bit community.  Many of the most common questions are answered on [this page.]("http://ubuntuforums.org/showthread.php?t=765428")

If you've tried everything and still can't figure out if your processor is supported, burn a 64-bit live disk and try it.  If your processor isn't 64-bit it will give you an error message telling you, quite specifically, that your processor isn't 64-bit.

---

### Post by Jonas thomas on 2008-07-26
I tried this is terminal  ```
cat /proc/cpuinfo
```
This definately spits out the most information about the processor so far suggested. What most of it means I haven't got a clue..  I'm going to need to do some more research on this..
results are below:

```
jonas@Ubuntu4:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.53GHz
stepping	: 7
cpu MHz		: 2533.422
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts sync_rdtsc cid xtpr
bogomips	: 5074.36
clflush size	: 64
```

---

### Post by ET! on 2008-07-26
just type

grep flags /proc/cpuinfo

in terminal

lm means Long mode - 64 bit CPU

this is what i got

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **_lm _**constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

there is lm..mening i have a 64 bit processor

---

### Post by Jonas thomas on 2008-07-26
I'm feeling fair confident that I don't have a 64-bit Pentium-4
I just tried the grep thing....
```
jonas@Ubuntu4:~$ grep flags /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts sync_rdtsc cid xtpr
```

No lm... things are looking not too good.

In addition, I just burned a Live CD of the 64-bit version 8.04.01 and thought I'd give a try:
I got the message (had to retype)
THIS KERNEL REQUIRES AN X86-64CPU BUT ONLY DETECTED A i1586 CPU. UNABLE TO BOOT - PLEASE USE A KERNEL APPROPRIATE TO YOUR CPU.
I guess I'm out of luck here.... :(

---

