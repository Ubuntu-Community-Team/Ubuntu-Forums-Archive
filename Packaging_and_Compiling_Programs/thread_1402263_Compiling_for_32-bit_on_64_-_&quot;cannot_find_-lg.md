---
title: "Compiling for 32-bit on 64 - &quot;cannot find -lgcc&quot;"
date: 2010-02-08
forum: Packaging and Compiling Programs
---

### Post by l0xin on 2010-02-08
I've got the gcc-multilib and lib32gcc1 packages which supposedly provide 32-bit support, but my compilation fails with :

> /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc

I do have this file though : /usr/lib/gcc/x86_64-linux-gnu/4.4/32/libgcc.a which I assume is the 32-bit version. So why doesn't ld find it?

Adding -L/usr/lib/gcc/x86_64-linux-gnu/4.4/32/ as a linker flag, or creating a symbolic link in /usr/lib32 pointing to the above file results in errors about architecture incompatibility :

> /usr/bin/ld: i386:x86-64 architecture of input file `/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o' is incompatible with i386 output

Any ideas?

---

### Post by Bachstelze on 2010-02-09
Sure you installed the right version of gcc-multilib? You need [font=monospace]gcc-4.4-multilib[/font].

---

### Post by l0xin on 2010-02-09
Yep...

The following packages are installed :

gcc
gcc-4.4
gcc-4.4-base
gcc-multilb
gcc-4.4-multilib
lib32gcc1
lib32gomp1
libgcc1
libgomp1

---

### Post by Bachstelze on 2010-02-09
You also need [font=monospace]libc6-dev-i386[/font]. I missed that earlier. ^^;

---

### Post by l0xin on 2010-02-09
Yeah, I've got that one too. As well as : ia32-libs

---

### Post by Bachstelze on 2010-02-09
Then the problem is most likely on your side. Can we see your code and combilation command?

---

### Post by l0xin on 2010-02-09
I'm trying to compile the [C++ Sockets Library]("http://www.alhem.net/Sockets/"). Doing 'make' on the unmodified source - it compiles, no problem (but as 64-bit).

So I added to the Makefile :

```

CFLAGS += -m32

```Which builds 32-bit objects, but the linker complained about :

> 
g++  -o Sockets-config Sockets-config.o
/usr/bin/ld: i386 architecture of input file `Sockets-config.o' is incompatible with i386:x86-64 output
/usr/bin/ld: final link failed: Invalid operation
collect2: ld returned 1 exit status
make: *** [Sockets-config] Error 1
So I added :

```

LDFLAGS += -m elf_i386

```and got :

> 
g++ -m elf_i386 -o Sockets-config Sockets-config.o
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libm.so when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libm.so when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../libm.so when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status
make: *** [Sockets-config] Error 1
Finally, adding :

```

LDFLAGS += -L/usr/lib32
 
```Supresses the above warnings, leaving the -lgcc error :

> 
g++ -m elf_i386 -L/usr/lib32 -o Sockets-config Sockets-config.o
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status
make: *** [Sockets-config] Error 1


---

### Post by l0xin on 2010-02-09
Ahhhhhhh. I've got it... The LD flag for 32-bit isn't :

```
LDFLAGS += -m elf_i386
```It's :

```
LDFLAGS += -m32
```Going over it again just caused me to notice. So simple!

---

