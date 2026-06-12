---
title: "how to add library files to current library"
date: 2010-04-13
forum: Packaging and Compiling Programs
---

### Post by hannounest on 2010-04-13
[SIZE=4]hi
im trying to compile file that contains #include nua.h
how can i add this file to this directory home/usr/include[/SIZE]
[SIZE=3]
[SIZE=4]thanks  for help[/SIZE][/SIZE]

---

### Post by SevenMachines on 2010-04-13
rather than manually installing to /home/usr or something like that....

1. Install sofia-sip, that contains nua.h
$sudo apt-get install libsofia-sip-ua-dev

2. change header in your code from <nua.h> to
<sofia-sip/nua.h>

3. pass the sofia directory to the compiler in your build, either using your ide's preferred way or, for example, using the standard 'gcc -I/some/include/directory myfile.c', eg
$ gcc -I/usr/include/sofia-sip-1.12/ test.c

---

