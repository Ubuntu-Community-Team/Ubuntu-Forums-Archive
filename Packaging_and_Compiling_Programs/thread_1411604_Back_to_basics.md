---
title: "Back to basics"
date: 2010-02-20
forum: Packaging and Compiling Programs
---

### Post by kernelnewbie1 on 2010-02-20
Hi, 
i downloaded linux 0.01 to experiment , and tried to compile it
no configuration option was there so, just tried to build it 
 
$make
gas -c -o boot/head.o boot/head.s
make: gas: Command not found
make: *** [boot/head.o] Error 127

// i tried 
sudo apt-get install gas
no luck :confused:

please help me , also tell me if i can be successful in having 0.01 kernel

---

### Post by SevenMachines on 2010-02-20
i take it gas is the gnu assembler. this comes with the 'binutils' package. the command is now 'as' so you might need to change references in the makefile from 'gas' to 'as' or make a symlink from 'gas' to 'as' if you like

[EDIT] I imagine the chances of either compiling it or it doing anything useful are effectively zero! maybe you can set up an ancient environment in a virtual machines i don't know but remember, its very much a museum piece :)

---

