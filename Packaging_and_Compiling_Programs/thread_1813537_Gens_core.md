---
title: "Gens_core"
date: 2011-07-27
forum: Packaging and Compiling Programs
---

### Post by chips24 on 2011-07-27
I am trying to compile GENS from source.
how do i correct this error message?


mkdir -p gens_core/gfx gens_core/io gens_core/mem gens_core/misc gens_core/sound gens_core/cpu/sh2 gens_core/vdp gens_core/cpu/z80 ;
nasm -O1 -D __GCC2 -f elf -I./gens_core/ -I./gens_core/io/ -I./gens_core/misc/ -I./gens_core/vdp/ -I./gens_core/sound/ -I./gens_core/gfx/ -I./gens_core/cpu/sh2/ -I./gens_core/cpu/z80/ -I./gens_core/mem/ gens_core/gfx/blit.asm -o gens_core/gfx/blit.o
/bin/bash: nasm: command not found
make[3]: *** [gens_core/gfx/blit.o] Error 127
make[3]: Leaving directory `/home/caleb/Desktop/gens-2.15.5/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/caleb/Desktop/gens-2.15.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/caleb/Desktop/gens-2.15.5'
make: *** [all] Error 2

---

### Post by fdrake on 2011-07-28
```
/bin/bash: nasm: command not found
```

nasm     - General-purpose x86 assembler

try to install it:
```
sudo apt-get install nasm
```

---

### Post by chips24 on 2011-07-28
thanks

---

