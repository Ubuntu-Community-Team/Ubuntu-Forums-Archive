---
title: "Running 64-bit tools in Ubuntu 32-bit"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by Remcotjuuh on 2012-10-14
[FONT="Verdana"]Hey!

First of all: yes, I have searched forums, but I couldn't find a useable answer.

I'm a total Ubuntu noob, so this question may be stupid or already answered somewhere else.

Is it possible to execute a 64-bit tool on my 32-bit machine? I'm playing around with Ubuntu to modify a LiveSuite flashable Android image for my tablet. I'm using [this]("https://www.miniand.com/wiki/Allwinner/Unpacking+and+building+LiveSuit+images") website as my guide. Everything works as planned, expect when I want to extract system.fex. When I type the command it says: "cannot execute binairy file". This is probably because the tool used for it is intended for 64-bit machines.

Does anyone know how to still extract the file/execute the command? I think I can't install Ubuntu 64-bit on my computer with this processor: Intel® Pentium(R) Dual CPU E2220 @ 2.40GHz × 2 . 

Many thanks in advance! [/FONT]

---

### Post by Cheesemill on 2012-10-14
It's not possible to run 64-bit software on a 32-bit OS.

---

### Post by mips on 2012-10-14
No.

---

### Post by Remcotjuuh on 2012-10-14
Ah, well, that's a shame. Does someone know how to extract the system.fex file then?

---

### Post by wojox on 2012-10-14
> **Remcotjuuh said:**
> [FONT="Verdana"]I think I can't install Ubuntu 64-bit on my computer with this processor: Intel® Pentium(R) Dual CPU E2220 @ 2.40GHz × 2 . [/FONT]

```
grep -q "^flags.*\blm\b" /proc/cpuinfo && echo "Yes you have a 64 bit cpu" || echo "No 64 bit for you"
```

---

### Post by Remcotjuuh on 2012-10-14
> **wojox said:**
> ```
grep -q "^flags.*\blm\b" /proc/cpuinfo && echo "Yes you have a 64 bit cpu" || echo "No 64 bit for you"
```

Well THAT surprises me. It says I DO have a 64-bit cpu. I think that I will install Ubuntu 64-bit soon then \\:D/

---

### Post by Cheesemill on 2012-10-14
> **Remcotjuuh said:**
> [FONT=Verdana]I think I can't install Ubuntu 64-bit on my computer with this processor: Intel® Pentium(R) Dual CPU E2220 @ 2.40GHz × 2 .[/FONT]
Your CPU is 64-bit:
[http://ark.intel.com/products/32430/Intel-Pentium-Processor-E2220-1M-Cache-2_40-GHz-800-MHz-FSB](http://ark.intel.com/products/32430/Intel-Pentium-Processor-E2220-1M-Cache-2_40-GHz-800-MHz-FSB)

---

### Post by Remcotjuuh on 2012-10-14
Thanks for the quick and awesome support everyone!

---

