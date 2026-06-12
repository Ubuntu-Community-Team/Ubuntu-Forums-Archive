---
title: "Kernel build name"
date: 2019-01-11
forum: Packaging and Compiling Programs
---

### Post by sylvain30 on 2019-01-11
Dear all,

Previoulsy I used the ```
make-kpkg 
``` to package kernel newly built. On the command line I can add the option ```
--apped-to-version=xxxxxx 
```in order to modify (specialize) the name of the package and of the Kernel.
But now I follow another tutorial to build the kernel and on the command line I can't set something to differentiate the outputs. The new command line is 
```
fakeroot debian/rules binary
```

Could you help me to find the simplest and most efficient way to produce a kernel (and package) with a dedicated suffix ?

I've looked for "make-kpkg" in scripts in my build folder without success. So this command is not used now. 

Thank a lot.

---

