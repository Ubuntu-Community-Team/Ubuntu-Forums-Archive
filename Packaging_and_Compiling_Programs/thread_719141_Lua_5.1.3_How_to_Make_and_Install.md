---
title: "Lua 5.1.3: How to Make and Install?"
date: 2008-03-08
forum: Packaging and Compiling Programs
---

### Post by sgiandubh on 2008-03-08
I installed Lua 5.1.2 using the Synaptic Package Manager, but I'd like to update to Lua 5.1.3. I downloaded the 5.1.3 tarball from the Lua website, extracted to a makeshift directory, and tried to follow the INSTALL instructions. I'm new to building applications in *nix, so I'm not sure how I'm supposed to proceed. Here's what I tried:

```

cd /sgiandubh/lua-5.1.3/
make linux install
make generic install

cd /sgiandubh/lua-5.1.3/src/
make linux install
make generic install
```

The errors I encountered are no such file errors for assert.h, math.h, and string.h. I understand these are dependencies. How do I resolve this problem? Thank you.

---

### Post by geraldm on 2008-03-09
If you do not have the compilers installed
```

sudo apt-get install build-essential

```

I think that should install the headers needed.  The headers are in the glibc package, the dev headers are in the package for libc6-dev ; you need the version that is compatible with your glibc package. 

Most packages in linux use three commands (to precheck requirements)
./configure
make
make install
The instructions are usually contained in the package, INSTALL or README.

Gerald

---

### Post by sgiandubh on 2008-03-09
Excellent. That worked like a charm. Thanks a lot!

---

