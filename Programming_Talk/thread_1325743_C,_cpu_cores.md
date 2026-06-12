---
title: "C, cpu cores"
date: 2009-11-13
forum: Programming Talk
---

### Post by 65daysofstatic on 2009-11-13
hi, 
I need some help getting the number of cores of the processor, 
I know that  /proc/cpuinfo shows the cpu cores, but what happens when the processor has HT but it is not multicore? and what about the processor being HT and multicore?

for example on windows - if the processor is HT not being multicore - it shows 2 cores with the logical processor information.
And when the processor is dual core and is HT it can show up 4 cores.

thanks,
65dos

---

### Post by slavik on 2009-11-14
HT is not really a separate core and I believe that Linux doesn't support HT, although I may be wrong.

---

### Post by wmcbrine on 2009-11-14
My netbook's Atom CPU is hyperthreaded, and cat /proc/cpuinfo shows it as two processors.

---

### Post by slavik on 2009-11-14
I was wrong :(

---

