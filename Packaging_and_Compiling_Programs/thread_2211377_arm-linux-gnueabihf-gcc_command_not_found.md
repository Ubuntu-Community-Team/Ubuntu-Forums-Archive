---
title: "arm-linux-gnueabihf-gcc: command not found"
date: 2014-03-15
forum: Packaging and Compiling Programs
---

### Post by kelamahim on 2014-03-15
Hi!

I was following the instructions at [http://linux-sunxi.org/U-Boot#Compilation](http://linux-sunxi.org/U-Boot#Compilation) and when I hit 


$ make CROSS_COMPILE=arm-linux-gnueabihf- a20-olinuxino_micro 
 
I get this error:

/bin/bash: line 2: arm-linux-gcc: command not found

I installed gcc-4.7-arm-linux-gnueabihf and that gives me arm-linux-gnueabihf-gcc**-4.7** in /usr/bin/

How should I fix that?

Thanks!

Miha

---

### Post by kelamahim on 2014-03-15
I fixed that renaming the file/command...

---

