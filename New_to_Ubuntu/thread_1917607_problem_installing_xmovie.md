---
title: "problem installing xmovie"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by riehen on 2012-01-30
Hi everyone
Im a newbi. Im trying to install xmovie as part of installing the LAMMPS software (which has worked out). I am getting the following error message: 

```
@ubuntu:~/LAMMPS/tools/xmovie$ make
gcc -c -O2 -finline-functions -g -DMISSINGDEFS -D_POSIX_SOURCE -DUSEPRIVATE -DINCL_FLOAT -Wimplicit -Wunused -Wmissing-prototypes  version.c
gcc -o xmovie -O2 -finline-functions -g  version.o xmovie.o control.o scene.o read.o hpsort.o -L/usr/X11R6/lib -lX11 -lXaw -lm
/usr/bin/ld: scene.o: undefined reference to symbol 'XpmWriteFileFromPixmap'
/usr/bin/ld: note: 'XpmWriteFileFromPixmap' is defined in DSO /usr/lib/libXpm.so.4 so try adding it to the linker command line
/usr/lib/libXpm.so.4: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make: *** [xmovie] Error 1
```Can anyone help me out in trying to apply the note suggested above? How can I add [COLOR=Red]XpmWriteFileFromPixmap [COLOR=Black]to add to the linker command line? 

thx in advance.
riehen
[/COLOR][/COLOR]

---

