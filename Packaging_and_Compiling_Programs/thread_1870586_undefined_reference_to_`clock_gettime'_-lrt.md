---
title: "undefined reference to `clock_gettime' -lrt"
date: 2011-10-27
forum: Packaging and Compiling Programs
---

### Post by remusmp on 2011-10-27
Hi,

I am trying to compile a simple C file (taken from maple15) with the following commands:

MAPLE=/usr/local/bin/maple15
export LD_LIBRARY_PATH=$MAPLE/bin.IBM_INTEL_LINUX

gcc simple.c -I$MAPLE/extern/include -L$MAPLE/bin.IBM_INTEL_LINUX -o simple -lmaplec -lrt

...and I get an error:
/usr/local/bin/maple15/bin.IBM_INTEL_LINUX/libmaple.so: undefined reference to `clock_gettime'
collect2: ld returned 1 exit status

Why do I get an undefined reference to clock_gettime? I do have -lrt as an option to gcc (I also tried to put -lrt before -lmaplec). I don't think the error is related to Maple commands.

I am compiling under Kubuntu 11.10, 32bits.

Regards,
Remus.

---

### Post by MadCow108 on 2011-10-27
libmaple is underlinked, meaning it is not linked against all libraries whos symbols it needs.
This makes it hard to link it with --as-needed

[http://wiki.mandriva.com/en/Underlinking](http://wiki.mandriva.com/en/Underlinking)
This is a bug you should report.

you will have to disable as-needed:
```
gcc simple.c -I$MAPLE/extern/include -L$MAPLE/bin.IBM_INTEL_LINUX -o simple -lmaplec -Wl,--no-as-needed -lrt
```

note the parameter is positional and you can turn it on and off for every library

sometimes adding a library twice also works.

---

### Post by remusmp on 2011-10-28
Thanks a lot! It works!

---

