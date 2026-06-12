---
title: "3d software dosen't work"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by 900donuts on 2008-07-23
i've asked for help twice 

simply put my computer won't start any apps that need hardware acceleration

i have geforce 6200 graphics card and i enabled the driver in the restricted driver manager i've reinstalled 3 times trying to fix this the latest attempt was today (the envy driver doesn't work either)

if this is fixable it can't be the drivers

any way i need help!

P.S. i am at the verge of mental breakdown when it comes to fixing this thing and I'm prepared to agresivily BUMP this thread if I'm ignored.

---

### Post by Xerp on 2008-07-23
Don't have a breakdown :)

Can you post the output from ```
glxinfo
```

Just the first 30 lines will be enough :)

---

### Post by 900donuts on 2008-07-23
I followed your instructions and this is what I got
```

commander@droid1138-desktop:~$ glxinfo
name of display: :0.0
Illegal instruction
commander@droid1138-desktop:~$ 

```

Also i just remembered in my efforts to fix this i have also tried using a different card (a nvidia 5200fx) i didn't work either. Anything I've tried to run has gotten this illegal instruction error if it needs the 3d hardware.

---

### Post by Xerp on 2008-07-23
Which version of Ubuntu are you running? Gutsy? And which processor do you have exactly? ("cat /proc/cpuinfo")

---

### Post by 900donuts on 2008-07-23
I'm running hardy (8.04.1) and i didn't have these problems before hardy (though there was unexplained crashes and freezes i experience and ignored)

heres the contents of my cpu info file
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 4
model name	: AMD Athlon(tm) Processor
stepping	: 2
cpu MHz		: 1007.324
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips	: 2016.45
clflush size	: 32

```

---

### Post by Xerp on 2008-07-23
Hm. The NVIDIA OpenGL Driver requires CPUs with SSE. Yours just has mmx :( You'll need a driver that was released before they took out support for CPUs without SSE... sometime around 2006?

---

### Post by 900donuts on 2008-07-23
can do i have a Geforce 4400ti siting around (i take in a lot of discarded junk)

i do have a 2.8Ghz celeron processor will the problem go away if i use that instead(the only thing thats has stopped me from dumping my athlon in favor of the celeron is that i have no mother board with an AGP slot that fits it)

P.S. for the sake of my curiosity what is sse?

---

### Post by freak42 on 2008-07-23
> **900donuts said:**
> 
P.S. for the sake of my curiosity what is sse?

SSE stands for Streaming SIMD (Single Instruction, Multiple Data) Extension.
It is a special (Intel) CPU instruction set meaning that with special instructions and special types of numbers the processor can calculate on four numbers instead on only one at a time, resulting in a speedup. Although developed by Intel, AMD also started to support it.

---

### Post by Xerp on 2008-07-23
Yes, the Celeron will work just fine :)

---

