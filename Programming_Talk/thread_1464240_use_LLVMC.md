---
title: "use LLVMC?"
date: 2010-04-28
forum: Programming Talk
---

### Post by Jpenguin on 2010-04-28
So I ave GCC and it works fine, but I decided to try LLVM.  So, I installed via synaptic & am trying to compile UltimateStunts with it--

```
jpenguin@ubuntu:~/Downloads/ultimatestunts-srcdata-0751$ ./configure CC="llvmc" CXX="llvmc"
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... llvmc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
jpenguin@ubuntu:~/Downloads/ultimatestunts-srcdata-0751$ 

```

---

### Post by MadCow108 on 2010-04-28
is llvm-gcc installed? (the default used by llvmc)
whats in the config.log?
can you create executables by yourself?

you could also try using clang, a new C frontend for llvm not based on gcc
it works without problems on my projects and is also packaged in lucid (not karmic)
but its C++ support is unfinished

llvmc -clang
or directly
clang

it also has a quite nice static analyzer :)

---

### Post by Jpenguin on 2010-04-28
thx, I'll try compileing Hello-Word later when I'm at my Ubuntu box; I'll make sure "llvm-gcc" is installed.

It won't be to long for lucid (I'm still on Karmic, lucid's still in my VM)

---

### Post by Jpenguin on 2010-04-28
thx, I'll try compileing Hello-Word later when I'm at my Ubuntu box; I'll make sure "llvm-gcc" is installed.

It won't be to long for lucid (I'm still on Karmic, lucid's still in my VM)

---

### Post by Jpenguin on 2010-05-02
I've updated to lucid and installed cland; I tried that, but it failed in the 'make' stage.

clang seems to be more like boreland than gcc in array handling.  

> cfile.cpp:111:14: error: variable length arrays are not permitted in C++
        Uint8 buffer[maxlen];
                    ^
cfile.cpp:127:14: error: variable length arrays are not permitted in C++
        Uint8 buffer[b.size()];
                    ^

---

### Post by MadCow108 on 2010-05-02
variable length arrays are not c++ standard
gcc offers that as an extension, clang does seemingly not (yet)

anyway using clang for c++ is not really recommended. clangs c++ support is not yet finished.
here is its status:
[http://clang.llvm.org/cxx_status.html](http://clang.llvm.org/cxx_status.html)

use the gcc frontend llvmc (uses llvm-g+) instead, it may be more mature

---

### Post by Jpenguin on 2010-05-02
> **MadCow108 said:**
> variable length arrays are not c++ standard
gcc offers that as an extension, clang does seemingly not (yet)

anyway using clang for c++ is not really recommended. clangs c++ support is not yet finished.
here is its status:
[http://clang.llvm.org/cxx_status.html](http://clang.llvm.org/cxx_status.html)

use the gcc frontend llvmc (uses llvm-g+) instead, it may be more mature
Yep, it was just something to try.  llvmc couldn't compile ustunts either, but llvmmc could compile "Hello World", while clang coldn't

---

