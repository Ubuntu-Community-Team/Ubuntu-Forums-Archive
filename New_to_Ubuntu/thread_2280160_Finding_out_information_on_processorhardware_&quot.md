---
title: "Finding out information on processor/hardware &quot;Linux_foo&quot;"
date: 2015-05-28
forum: New to Ubuntu
---

### Post by wizrddreams on 2015-05-28
Hi. I am trying to find out a particular line of information about my processor. I need this information to install the ATLAS library. 
The processor ID (if I am even calling it by the correct name) will look something like this : 
Linux_C2D64SSE3

As far as I know this a label for the type of processor i.e. Pentium III. 

I'm just not sure how to find this information. 

Any suggestions? 
Thanks!

---

### Post by v3.xx on 2015-05-28
I think what you meant is 'C2D 64 SSE3'

Maybe this will help
```
cat /proc/cpuinfo
```

---

### Post by wizrddreams on 2015-05-28
Where in that output can I find that spec? 
Are they 3 different categories?

---

### Post by mörgæs on 2015-05-28
Better to post the output in CODE tags than letting us guess how it looks.

Still, if I have to guess then C2D could be Core 2 Duo. It's 64 bit and supports SSE3.

---

### Post by slickymaster on 2015-05-28
> **mörgæs said:**
> Better to post the output in CODE tags than letting us guess how it looks.

Still, if I have to guess then C2D could be Core 2 Duo. It's 64 bit and supports SSE3.
+1

---

### Post by wizrddreams on 2015-05-28
Here is the output:
```


cat /proc/cpuinfo

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.71
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.71
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.71
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5387.71
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

I see now that under a huge list of things there is "sse2". As well as several other similar things.

I was hoping there was a command that would output for my system exactly the "Linux_foo" spec.

Anymore advice?

---

### Post by v3.xx on 2015-05-28
Features:    

SSE / Streaming SIMD Extensions
SSE2 / Streaming SIMD Extensions 2
SSE3 / Streaming SIMD Extensions 3
SSSE3 / Supplemental Streaming SIMD Extensions 3
SSE4 / SSE4.1 + SSE4.2 / Streaming SIMD Extensions 4

[http://www.cpu-world.com/CPUs/Core_i7/Intel-Core%20i7%20Mobile%20I7-2620M%20FF8062700838809.html](http://www.cpu-world.com/CPUs/Core_i7/Intel-Core%20i7%20Mobile%20I7-2620M%20FF8062700838809.html)

Thats my findings and looks like cpuinfo agrees.

---

### Post by mörgæs on 2015-05-29
It's a very strong processor, better than the Core 2 Duo I talked about. 

What exactly do you need in relation to ATLAS?

---

### Post by wizrddreams on 2015-05-29
The following is an example of a typical install for ATLA's.
I am following out a textbook for this. 
The following assumes that you have downloaded and packed out the source code into a directory ATLAS. 
```

cd ATLAS
**hardware=Linux_PIIISSE1**
make
make install arch=$hardware

#make optimized LAPACK libraries:
cd lib/$hardware
mkdir tmp; cd tmp
ar x ../liblapack.a
cp ../../../../LAPACK/lapack.a ../liblapack.a
ar r ../liblapack.a *.o
cd ..; rm -rf tmp

```
As far as I know this should perform the installation. However I don't know what the *hardware variable* (bold text) needs to be for my system. That is what I am trying to find out. Thanks for all the help thus far!

---

### Post by v3.xx on 2015-05-29
That reference looks to date back to the 90s.  Like this one.

[http://math-atlas.sourceforge.net/atlas_install/node30.html](http://math-atlas.sourceforge.net/atlas_install/node30.html)

I can't help you with this.  Good luck

---

### Post by Yellow Pasque on 2015-05-31
Have you tried just using the defaults? ATLAS seems to autodetect the information, so I wouldn't worry about it. My CPU is a 2.8GHz Phenom II and has SSE3. This is what configure gave me:
```
./xconfig -d s /home/user/source/ATLAS/build/../ -d b /home/user/source/ATLAS/build 

OS configured as Linux (1)

Assembly configured as GAS_x8664 (2)

Vector ISA Extension configured as  SSE3 (6,960)

Architecture configured as  AMD64K10h (35)

Clock rate configured as 2800Mhz
```

The only thing I had to do was turn off CPU throttling while building (I run Debian, so the command I used was 'sudo cpufreq-set -g performance' ). That may not even me necessary if you manually specify the CPU speed.

---

### Post by Yellow Pasque on 2015-06-02
BTW, the answer to your question (using ATLAS 3.10.2 and assuming you're trying to build a 64-bit binary) is 'Corei264AVX' since your CPU supports AVX. I think the names they choose are a bit inconsistent/confusing, which is why I still recommend just letting the configure program autodetect your CPU attributes.
Note: You can see a full list of CPU options under /ATLAS/CONFIG/ARCHS

---

### Post by wizrddreams on 2015-06-03
[QUOTE=Temujin]
Have you tried just using the defaults? ATLAS seems to autodetect the  information, so I wouldn't worry about it. My CPU is a 2.8GHz Phenom II  and has SSE3. This is what configure gave me:
[/QUOTE]

I have not tried the defaults. I was unsure of how to set turn off the CPU throttling. I believe that this link provides the answer for how to do that( on Ubuntu 14.04 Trusty):

[http://jahanzebnotes.blogspot.com/2013/02/turn-off-cpu-throttling-ubuntu.html](http://jahanzebnotes.blogspot.com/2013/02/turn-off-cpu-throttling-ubuntu.html)

[QUOTE=Temujin]
```

./xconfig -d s /home/user/source/ATLAS/build/../ -d b /home/user/source/ATLAS/build   
OS configured as Linux (1)  
Assembly configured as GAS_x8664 (2)  
Vector ISA Extension configured as  SSE3 (6,960)  
Architecture configured as  AMD64K10h (35)  
Clock rate configured as 2800Mhz

```
[/QUOTE]

I just want to clarify that I understand correctly. 
s and b specify source and build directories?

As an a extra question, do you know of a quick test for cpu throttling? I want to check it is indeed off now. 

Thanks for all the help thus far!

---

### Post by Yellow Pasque on 2015-06-03
> s and b specify source and build directories?
The configure program runs xconfig and sets those automatically. All I did was download Atlas and use the commands below:

```

tar -xjf atlas3.10.2.tar.bz2
cd ATLAS
mkdir build
cd build
sudo cpufreq-set -g performance
../configure
```

> As an a extra question, do you know of a quick test for cpu throttling? I want to check it is indeed off now. 
I always just look at cpufreq-info
```
cpufreq-info
```

---

