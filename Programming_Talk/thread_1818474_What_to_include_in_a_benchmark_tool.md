---
title: "What to include in a benchmark tool"
date: 2011-08-04
forum: Programming Talk
---

### Post by alegomaster on 2011-08-04
Hi, I plan on making a small benchmarking tool that will test the cpu, and give it a score afterward. I wonder what sort of tests I should incorporate. I plan to do jumps and numerous mathematical equations to test the cpu. Also should I use assembly to make the benchmark or is C good. I know assembly would give more control but I wonder if C could be used too.

---

### Post by Zugzwang on 2011-08-05
If you want the results of your benchmarks to be meaningful, stay away from assembler. In fact, most modern programs do not have an assembler part anymore, even for the computation-heavy stuff. As a consequence, processor makers have optimized their processors towards the code of the form "typical" for what compilers produce. 

If you now take custom assembler code, what you are actually measuring is which processor type happens to work well with the "assembler style" that you are using (e.g., how well you avoid pipeline stalls, etc.), which is nothing that tells you anything about execution speed in practice.

---

### Post by alegomaster on 2011-08-05
I want to evalute the performance of the processor such as branch prediction and the speed of execution units. Should I use C or Assembly for that. I plan not to make it a real world benchmark, just a low level one.

---

