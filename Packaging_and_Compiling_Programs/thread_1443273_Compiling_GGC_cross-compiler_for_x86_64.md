---
title: "Compiling GGC cross-compiler for x86_64"
date: 2010-03-30
forum: Packaging and Compiling Programs
---

### Post by quanganht on 2010-03-30
I'm compiling clean x86_64-elf target cross-compiler suite on my x86 Ubuntu. I compiled binutils without any problems, but when I move on with GCC, it produces error:
```
checking for suffix of object files... configure: error: in `/home/quanganht/build-gcc/x86_64-elf/libgcc':
configure: error: cannot compute suffix of object files: cannot compile

```

Help please!
PS: tar version: binutils 2.20, gcc 4.4.3

---

### Post by SevenMachines on 2010-03-31
you'd probably need to attach more output (for me at least :) ) to know what the problem is. I'd guess that perhaps your gcc cross compile isnt finding your  compiled binutils, are you sure the paths are set right or its installed to the location the gcc compile expects it?

In case you've missed them though, i'd add that gcc-multilib in the repository will cross compile for 64 bit fine, and there are a fair amount of 64 bit libraries already available in the repository ( search for '64' in synaptic and you'll see quite a range, usually somethiing like lib64something or libsomethingelse-amd64). Unless you especially need to do it manually for some reason its certainly the easiest way

---

