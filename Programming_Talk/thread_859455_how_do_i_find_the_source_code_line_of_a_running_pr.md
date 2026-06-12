---
title: "how do i find the source code line of a running program compiled with gcc -O5?"
date: 2008-07-14
forum: Programming Talk
---

### Post by glok_twen on 2008-07-14
hi. i have a job that's been running in prod on an ubnutu box for a while. it's written in c++, compiled with gcc -O5.

then it froze up. so i attached gdb and did a bt. can i use any of these hex numbers to cross reference back to my source code in some way? even if i need to re-compile it with a different paramter that ties either the assembly or the address space to source code? way back in the day on a now extinct platform we could compile code with the assembly and line offsets, then use the hex address of a running program to determine in exactly which source line a process was executing at that momement. can i do such a thing with my linux gcc app?

```
#0  0xb7f6a410 in __kernel_vsyscall ()
#1  0xb7d992f3 in write () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d375a4 in _IO_file_write () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7d37255 in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0xb7d3754f in _IO_do_write () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7d37d36 in _IO_file_sync () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7d2c860 in fflush () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7ed8a10 in ?? () from /usr/lib/libstdc++.so.6
#8  0xb7eda1d2 in std::ostream::flush () from /usr/lib/libstdc++.so.6
#9  0xb7edc0a9 in std::endl<char, std::char_traits<char> > () from /usr/lib/libstdc++.so.6
#10 0x0806a289 in Ctest01::Cgonow ()
```

---

### Post by CptPicard on 2008-07-14
You need to compile with the debugging symbols in the binary, see the -g flag.

---

### Post by glok_twen on 2008-07-14
cptP, ok got that part, but it will need to run another huge number of hours. i could do that of course and will as a last resort, just wanted to see if there is a way to get to the source code just by looking at the hex addresses and mapping them back to some other output of the compiler. otherwise ok i will re-run.

---

### Post by LaRoza on 2008-07-14
> **glok_twen said:**
> just wanted to see if there is a way to get to the source code just by looking at the hex addresses and mapping them back to some other output of the compiler.

You could disassemble it, but even if you knew assembly to the fullest, you'd likely get very little use out of it.

---

### Post by hod139 on 2008-07-14
Also, that level of optimization is going to make it really difficult to hunt down the source line.  If the optimization level was -O0, then I think maybe you could do it, but gcc is going to be doing all sorts of crazy things to your code (unrolling, inlining, etc) that will make it almost impossible.

---

### Post by slavik on 2008-07-15
umm, highest optimisation is O3 ... there is nothing higher :)

---

