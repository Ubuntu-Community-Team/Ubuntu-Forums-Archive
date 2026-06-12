---
title: "[B]Compiling dr'ex source code...!?!?!?[/B]"
date: 2008-11-05
forum: Packaging and Compiling Programs
---

### Post by louvros10 on 2008-11-05
Hi everyone!
I sure that there are a lot of people that can help me compile the dr'ex source code. Dr'ex is an exokernel: [HTML]http://sourceforge.net/projects/drex/[/HTML]
My problem is that when I type make on the containing folder of drex-murgiahack-0.0.6, I get the following:
```
make -C boot ../boot.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/boot'
ld -r boot.o video.o core.o gdt.o ppages.o core_mmu.o interrupt.o criticalexceptions.o tss.o memcpy.o   -o ../boot.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/boot'
make -C kern ../kern.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/kern'
ld -r kern.o kstack.o stack.o udata.o kdata.o uthread.o exceptions.o hash.o aspace.o _exit.o useg.o uthep.o scheduler.o   -o ../kern.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/kern'
make -C cons ../cons.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/cons'
ld -r printk.o   -o ../cons.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/cons'
make -C mm ../mm.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/mm'
ld -r mm.o getfreepage.o ppage.o metaslab.o slabcache.o   -o ../mm.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/mm'
make -C timing ../timing.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/timing'
ld -r events.o timer.o timing.o   -o ../timing.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/timing'
make -C elf ../elf.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/elf'
ld -r elf.o   -o ../elf.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/elf'
make -C api ../api.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/api'
ld -r api.o syscall.o sys_aspace.o sys_uthread.o temp.o   -o ../api.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/api'
make -C capsys ../capsys.o
make[1]: Entering directory `/home/andreas/drex--murgiahack/capsys'
ld -r cap.o capsys.o capset.o   -o ../capsys.o
make[1]: Leaving directory `/home/andreas/drex--murgiahack/capsys'
ld -T =utils/ldscript boot.o kern.o cons.o mm.o timing.o elf.o api.o capsys.o -o drex 
boot.o: In function `printf':
(.text+0x5d6): undefined reference to `__stack_chk_fail'
boot.o: In function `ce_3':
(.text+0x1798): undefined reference to `__stack_chk_fail'
boot.o: In function `ce_11':
(.text+0x187e): undefined reference to `__stack_chk_fail'
boot.o: In function `ce_10':
(.text+0x1960): undefined reference to `__stack_chk_fail'
boot.o: In function `ce_17':
(.text+0x1a54): undefined reference to `__stack_chk_fail'
boot.o:(.text+0x1b33): more undefined references to `__stack_chk_fail' follow
make: *** [drex] Error 1

```

Please someone help...
Thanks in advance!!!

---

