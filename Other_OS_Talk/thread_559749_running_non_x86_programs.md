---
title: "running non x86 programs"
date: 2007-09-25
forum: Other OS Talk
---

### Post by sdd231163 on 2007-09-25
Hi, I'm trying to write a new programming language which would run efficiently on lots of processors (not just the stock x86). Naturally this means I must learn the assembly languages of these other architectures, however I cannot go and buy new hardware. What is the best emulation solution for running programs for IA-64, MIPS, SPARC and other processors on my amd64?

---

### Post by LaRoza on 2007-09-25
Do you have the knowledge to do this?

If it is an exercise, I would start by doing it for one processor OR making an interpreted language in C, so the interpreter can be compiled on different platforms.

---

### Post by init1 on 2007-09-25
> **sdd231163 said:**
> Hi, I'm trying to write a new programming language which would run efficiently on lots of processors (not just the stock x86). Naturally this means I must learn the assembly languages of these other architectures, however I cannot go and buy new hardware. What is the best emulation solution for running programs for IA-64, MIPS, SPARC and other processors on my amd64?
Probably Qemu. It can emulate all of the processors you mentioned. 
```

sudo apt-get install qemu
qemu-sparc
qemu-mips
qemu-etc 

```

---

### Post by sdd231163 on 2007-09-26
> **LaRoza said:**
> Do you have the knowledge to do this?

If it is an exercise, I would start by doing it for one processor OR making an interpreted language in C, so the interpreter can be compiled on different platforms.

It's a hobby so it probably won't come to much but this is the sort of programming I am interested in. Progress will probably be slow but I can get most of the information I need from the internet. I already know x86 assembly but I want to write the language so that It is designed with running on different processors. That means learning other assemblies.

> Probably Qemu. It can emulate all of the processors you mentioned.
```

sudo apt-get install qemu
qemu-sparc
qemu-mips
qemu-etc

```


admittedly I haven't tried qemu-sparc yet but qemu-mips is missing a bios, as is qemu-ppc on ubuntu. The only working ppc solution so far has been qemu-ppc on fedora7 as host using debian 3.1 as the guest (debian etch doesn't run) but this just crawls (It would probably take days to get right through the text based installer. Finally qemu-IA64 just does not exist.

---

### Post by sdd231163 on 2007-09-26
qemu-sparc works fine for a while and then crashes during debian installation, failing to dereference a null pointer

---

### Post by mips on 2007-09-26
[http://www.linux-mips.org/wiki/Emulators](http://www.linux-mips.org/wiki/Emulators)

---

### Post by sdd231163 on 2007-09-27
> **mips said:**
> [http://www.linux-mips.org/wiki/Emulators](http://www.linux-mips.org/wiki/Emulators)
Thanks I'm now using SPIM for the MIPS

---

### Post by mips on 2007-09-27
For SPARC you could also look at [tkisem]("http://www.cs.unm.edu/~maccabe/OLD/tkisem/begin.html")

For IA-64 you could look at,
[IATO]("http://www.irisa.fr/caps/projects/ArchiCompil/iato/")
[NUE & SKI]("http://www.hpl.hp.com/research/linux/ski/nue-info.php")
Simics
[IA-64 Emulator]("http://www.diotima.cz/ia64emu/")

For ARM,
[http://embedded.hk/modules/mylinks/viewcat.php?op=&cid=17&PHPSESSID=b7f04638c420d015ef994ec4aa686e2d](http://embedded.hk/modules/mylinks/viewcat.php?op=&cid=17&PHPSESSID=b7f04638c420d015ef994ec4aa686e2d)
[http://www.cs.umu.se/~ens03mbs/index.html](http://www.cs.umu.se/~ens03mbs/index.html)
[http://www.penguin-soft.com/penguin/man/1/jimulator.html](http://www.penguin-soft.com/penguin/man/1/jimulator.html)
[http://sourceforge.net/projects/armphetamine/](http://sourceforge.net/projects/armphetamine/)
[http://arcem.sourceforge.net/](http://arcem.sourceforge.net/)

For PowerPC,
[http://pearpc.sourceforge.net/](http://pearpc.sourceforge.net/)
[http://sources.redhat.com/psim/](http://sources.redhat.com/psim/)


Various,
[http://gavare.se/gxemul/](http://gavare.se/gxemul/)
[http://simh.trailing-edge.com/](http://simh.trailing-edge.com/)
[http://www.hercules-390.org/](http://www.hercules-390.org/)
[http://en.wikipedia.org/wiki/List_of_computer_system_emulators](http://en.wikipedia.org/wiki/List_of_computer_system_emulators)
[http://en.wikipedia.org/wiki/List_of_emulators](http://en.wikipedia.org/wiki/List_of_emulators)

---

### Post by sdd231163 on 2007-09-28
thanks that's a lot of emulators to check out.
p.s. Pear pc doesnt work with debianppc (I'd already tried that)

---

