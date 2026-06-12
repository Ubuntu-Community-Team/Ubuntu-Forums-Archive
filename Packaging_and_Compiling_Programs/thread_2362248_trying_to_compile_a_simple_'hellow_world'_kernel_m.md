---
title: "trying to compile a simple 'hellow world' kernel module in ubuntu"
date: 2017-05-25
forum: Packaging and Compiling Programs
---

### Post by sblu23 on 2017-05-25
folks,

trying to compile the attached 'hello world' module (helloWorldK.c), with the attached makefile, and the following invocation:

```
sudo make -C '/home/owais/Kernel/linux-joule-4.4.0/' M='pwd' modules
```

getting the following error message:

```
make: Entering directory '/home/owais/Kernel/linux-joule-4.4.0'


  WARNING: Symbol version dump ./Module.symvers
           is missing; modules will have no dependencies and modversions.


scripts/Makefile.build:44: pwd/Makefile: No such file or directory
make[1]: *** No rule to make target 'pwd/Makefile'.  Stop.
Makefile:1420: recipe for target '_module_pwd' failed
make: *** [_module_pwd] Error 2
make: Leaving directory '/home/owais/Kernel/linux-joule-4.4.0'
```

---

### Post by dinesh2909eee on 2017-08-07
Hi,

The command 'pwd' is not executing... so Makefile is not detected. try giving relative path to the Makefile source directory.

"make -C /usr/src/linux-x.x.x/ M=~/home/<kernel_driver_source_folder_path>/ modules"

---

