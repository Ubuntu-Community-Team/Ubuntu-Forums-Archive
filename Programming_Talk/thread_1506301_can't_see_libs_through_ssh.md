---
title: "can't see libs through ssh"
date: 2010-06-10
forum: Programming Talk
---

### Post by eotakos on 2010-06-10
Hello,

I'm trying to execute a cpp program over ssh, on a pc that compiled that same program (through ssh), and I get a segmentation error. Using strace, I found that the program can't see the lib files.
```
execve("./a.out", ["./a.out"], [/* 21 vars */]) = 0
brk(0)                                  = 0x19d7000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041dea2000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041dea0000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/usr/local/lib/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/tls", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/local/lib64/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/tls", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64/tls", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240h\5\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1023448, ...}) = 0
mmap(NULL, 3195704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d977000
mprotect(0x7f041da68000, 2097152, PROT_NONE) = 0
mmap(0x7f041dc68000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf1000) = 0x7f041dc68000
mmap(0x7f041dc71000, 74552, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f041dc71000
close(3)                                = 0
open("/usr/local/lib/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/x86_64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib64/tls/x86_64", 0x7fff1954b880) = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib64/tls", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib64/x86_64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib64/x86_64", 0x7fff1954b880) = -1 ENOENT (No such file or directory)
open("/usr/lib64/libm.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
stat("/usr/lib64", {st_mode=S_IFDIR|0755, st_size=65536, ...}) = 0
open("tls/x86_64/libm.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/libm.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("x86_64/libm.so.6", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("libm.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=91618, ...}) = 0
mmap(NULL, 91618, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f041de89000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P>\0\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=542928, ...}) = 0
mmap(NULL, 2638040, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d6f2000
mprotect(0x7f041d776000, 2093056, PROT_NONE) = 0
mmap(0x7f041d975000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x83000) = 0x7f041d975000
close(3)                                = 0
open("/usr/local/lib/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/x86_64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/libgcc_s.so.1", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("x86_64/libgcc_s.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("libgcc_s.so.1", O_RDONLY)         = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`,\0\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=96560, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041de88000
mmap(NULL, 2192376, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d4da000
mprotect(0x7f041d4f0000, 2097152, PROT_NONE) = 0
mmap(0x7f041d6f0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f041d6f0000
close(3)                                = 0
open("/usr/local/lib/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib64/libc.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/x86_64/libc.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/libc.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("x86_64/libc.so.6", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("libc.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\346\1\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1502512, ...}) = 0
mmap(NULL, 3609240, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d168000
mprotect(0x7f041d2d0000, 2097152, PROT_NONE) = 0
mmap(0x7f041d4d0000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x168000) = 0x7f041d4d0000
mmap(0x7f041d4d5000, 17048, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f041d4d5000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041de87000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041de86000
arch_prctl(ARCH_SET_FS, 0x7f041de86700) = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "\325_\351\367\364\250\334"..., 7) = 7
close(3)                                = 0
mprotect(0x7f041d4d0000, 16384, PROT_READ) = 0
mprotect(0x7f041d6f0000, 4096, PROT_READ) = 0
mprotect(0x7f041d975000, 4096, PROT_READ) = 0
mprotect(0x7f041dc68000, 28672, PROT_READ) = 0
mprotect(0x608000, 4096, PROT_READ)     = 0
mprotect(0x7f041dea3000, 4096, PROT_READ) = 0
munmap(0x7f041de89000, 91618)           = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
```

The odd about this is that cuda c programs that I execute through ssh on that same device work just fine!


any suggestions?  - thanks in advance

---

