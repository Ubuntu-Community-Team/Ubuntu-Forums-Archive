---
title: "Static library with -lm dumps core on run time"
date: 2015-03-31
forum: Programming Talk
---

### Post by uws on 2015-03-31
Ubuntu 64bit on an AMD C50 dual core

The c program was initially compiled using dynamic linking and tested fine.

I statically linked it with 
gcc a.c b.c -o myprogramEXE -static -lm and also by putting the full path.

I also tested with ldd.

When executing it dumps core on the same input conditions as with dynamic linking and on the same environ!

Why - what is the fix?

When tried with the trace command: 

execve("./mypro", ["./mypro"], [/* 61 vars */]) = 0 
uname({sys="Linux", node="Acer", ...})  = 0 
brk(0)                                  = 0x2668000 
brk(0x26691c0)                          = 0x26691c0 
arch_prctl(ARCH_SET_FS, 0x2668880)      = 0 
readlink("/proc/self/exe", "/home/owner/wfiles/mypro", 4096) = 23 
brk(0x268a1c0)                          = 0x268a1c0 
brk(0x268b000)                          = 0x268b000 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
write(2, "Expecting two argume"..., 35Expecting two argument 
) = 35 
exit_group(1)                           = ? 
+++ exited with 1 +++

---

