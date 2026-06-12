---
title: "how i can find out whether my cpu is 64 bits or 32 bits?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by legolas_w on 2008-10-28
Hi
Can someone please let me know how I can findout whether my CPU is 64 bits or it is 32 bits?

Thanks

---

### Post by SunnyRabbiera on 2008-10-28
Well do you know the name of your processor?

---

### Post by legolas_w on 2008-10-28
It is intel 3Ghz, when I had windows and I open the task manager it shows two diagram for CPU processing and now that I have ubunut and I open system monitor it shows two diagram for CPU history.

---

### Post by Tak11 on 2008-10-28
less /proc/cpuinfo

---

### Post by SunnyRabbiera on 2008-10-28
> **legolas_w said:**
> It is intel 3Ghz, when I had windows and I open the task manager it shows two diagram for CPU processing and now that I have ubunut and I open system monitor it shows two diagram for CPU history.

Did it have a sticker or anything?
Both Intel and AMD slap a sticker on the computer to tell you.
in the system monitor you could check the first tab as well to get the name of your processor.
We really cant tell you anything until you give us the name of what you have.

---

### Post by sudo_chop on 2008-10-28
> **legolas_w said:**
> It is intel 3Ghz, when I had windows and I open the task manager it shows two diagram for CPU processing and now that I have ubunut and I open system monitor it shows two diagram for CPU history.
 
If it is dual core (sounds like it is), then it is 64bit.
 
-sudo chop

---

### Post by legolas_w on 2008-10-28
> **Tak11 said:**
> less /proc/cpuinfo

I tried your command and it shows the following output, but nothing about the bits


```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 2992.664
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 5991.08
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 2992.664
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 5985.50
clflush size    : 64


```

---

### Post by SunnyRabbiera on 2008-10-28
Intel Pentium 4's are 32bit processors, have one myself.

---

### Post by aeiah on 2008-10-28
according to some site:
```
grep flags /proc/cpuinfo 
```
> 
lm means Long mode - 64 bit CPU 
Real mode 16 bit CPU 
Protected Mode is 32-bit CPU 


in your case, you have lm. 64 bit.

or really you could just see if this returns a result:
```

grep lm /proc/cpuinfo
```

---

### Post by SunnyRabbiera on 2008-10-28
> **aeiah said:**
> according to some site:
```
grep flags /proc/cpuinfo 
```


in your case, you have lm. 64 bit.

yeh but to be on the safe side I would go with a 32bit kernel.

---

### Post by sudo_chop on 2008-10-28
Unless you have 4GB or more of ram that needs 64bit processing to be able to access it all, then you will see no difference b/w 32 and 64 bit OS. There is not a magical performance increase unless you have a lot of memory.
 
-sudo chop

---

### Post by legolas_w on 2008-10-28
> **SunnyRabbiera said:**
> yeh but to be on the safe side I would go with a 32bit kernel.

would you please elaborate more?

Thanks

---

### Post by aeiah on 2008-10-28
suit yourself but there's really no danger any more

---

### Post by SunnyRabbiera on 2008-10-28
> **aeiah said:**
> suit yourself but there's really no danger any more

> **legolas_w said:**
> would you please elaborate more?

Thanks

Well even though I know later P4's had 64bit capacity, it was still all before Intel committed to the dual core line fully.
If the P4 can support a 64bit kernel then good, but rather if it really is a p4 with 64bit capacity is unknown.
The later P4 line I know was tricky.

---

### Post by rsambuca on 2008-10-28
> **sudo_chop said:**
> Unless you have 4GB or more of ram that needs 64bit processing to be able to access it all, then you will see no difference b/w 32 and 64 bit OS. There is not a magical performance increase unless you have a lot of memory.
 
-sudo chop

Wrong.  There are many applications where 64bit will outperform the 32bit platform, and drastically in many cases.  Multi-media, audio and video transcoding, compiling...

---

### Post by hotrod6657 on 2008-10-28
one could always just burn the 64 and 32 bit versions of the OS.  If you try installing the 64 bit version on a 32 bit CPU the installer will say you have the wrong version of the OS.  Then just install the 32 bit version and you're good.

If the 64 bit installs, or at least boots into the live CD you know you have a 64 bit capable CPU.  That's probably the easiest and most reliable way if you don't know specifically what CPU you have.

In my opinion at least,

hotrod

---

### Post by sudo_chop on 2008-10-28
> **rsambuca said:**
> Wrong. There are many applications where 64bit will outperform the 32bit platform, and drastically in many cases. Multi-media, audio and video transcoding, compiling...
 
Examples of 64bit programs outperforming the same 32bit program on the same <4GB platform please...

---

### Post by oldos2er on 2008-10-28
> **sudo_chop said:**
> Examples of 64bit programs outperforming the same 32bit program on the same <4GB platform please...

 DeVeDe.

---

### Post by rsambuca on 2008-10-28
And video transcoding from mpeg2 to mpeg4 using ffmpeg.

And as I said earlier, compiling programs is way faster.

The problem when you give blanket advice like you did, is that you assume what the OP will be doing based on your own usage.  Your assumption may not be correct, and hence your advice may be wrong for the particular user.  64 bit has its advantages.  Not every user will utilize them, but that hardly means the advantages don't exist.  I stand by my statement that your first statement is false.

---

### Post by sudo_chop on 2008-10-28
> **rsambuca said:**
> And video transcoding from mpeg2 to mpeg4 using ffmpeg.
 
And as I said earlier, compiling programs is way faster.
 
The problem when you give blanket advice like you did, is that you assume what the OP will be doing based on your own usage. Your assumption may not be correct, and hence your advice may be wrong for the particular user. 64 bit has its advantages. Not every user will utilize them, but that hardly means the advantages don't exist. I stand by my statement that your first statement is false.
 
Sorry friens! You are right, I shouldn't have said that since I dont know what OP will be using his PC for. 64bit has advantages and disadvatages, and its been argued a thousand times, no need to do it here again.
 
Use 64bit! I'm sure it will run great.
 
-sudo chop

---

