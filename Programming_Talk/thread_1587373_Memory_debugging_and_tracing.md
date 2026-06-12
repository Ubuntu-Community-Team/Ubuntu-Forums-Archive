---
title: "Memory debugging and tracing"
date: 2010-10-03
forum: Programming Talk
---

### Post by erupter on 2010-10-03
My application runs in tight cycles, each time it needs to compute many vectors which are dynamically assigned since origin and destination vary.
Now this part i figured out, but i also figured out that would clog the memory if i don't release the vectors.
Since this is all done in C i'm stuck with manual allocation and deallocation.
Fine, since these vectors are connected i did a recursive function that frees all the elements contained in a vector starting from the last.
Now this works 2 times, then segmentation fault.
I tried STRACE but the output is not of help to me

```
strace ./my_simple -iter 10 -size 16 -res 0.2 -v
execve("./my_simple", ["./my_simple", "-iter", "10", "-size", "16", "-res", "0.2", "-v"], [/* 46 vars */]) = 0
brk(0)                                  = 0x25d4000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c57830000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/tls/x86_64/libplayerc.so.3.0", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/tls/x86_64", 0x7ffff30bff60) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/tls/libplayerc.so.3.0", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/tls", 0x7ffff30bff60) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/x86_64/libplayerc.so.3.0", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/x86_64", 0x7ffff30bff60) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libplayerc.so.3.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\246\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=177109, ...}) = 0
mmap(NULL, 2242784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c573ee000
mprotect(0x7f4c57411000, 2093056, PROT_NONE) = 0
mmap(0x7f4c57610000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x22000) = 0x7f4c57610000
close(3)                                = 0
open("/usr/local/lib64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=138659, ...}) = 0
mmap(NULL, 138659, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f4c5780e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360>\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=534832, ...}) = 0
mmap(NULL, 2629864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c5716b000
mprotect(0x7f4c571ed000, 2093056, PROT_NONE) = 0
mmap(0x7f4c573ec000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x81000) = 0x7f4c573ec000
close(3)                                = 0
open("/usr/local/lib64/libz.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libz.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libz.so.1", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\"\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=92752, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5780d000
mmap(NULL, 2187792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c56f54000
mprotect(0x7f4c56f6a000, 2093056, PROT_NONE) = 0
mmap(0x7f4c57169000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15000) = 0x7f4c57169000
close(3)                                = 0
open("/usr/local/lib64/libplayerinterface.so.3.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\241\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=481886, ...}) = 0
mmap(NULL, 2488936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c56cf4000
mprotect(0x7f4c56d4f000, 2093056, PROT_NONE) = 0
mmap(0x7f4c56f4e000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5a000) = 0x7f4c56f4e000
close(3)                                = 0
open("/usr/local/lib64/libplayerwkb.so.3.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\21\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=17864, ...}) = 0
mmap(NULL, 2109696, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c56af0000
mprotect(0x7f4c56af2000, 2097152, PROT_NONE) = 0
mmap(0x7f4c56cf2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f4c56cf2000
close(3)                                = 0
open("/usr/local/lib64/libgeos-3.1.0.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libgeos-3.1.0.so", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgeos-3.1.0.so", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\226\6\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1330184, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5780c000
mmap(NULL, 3426288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c567ab000
mprotect(0x7f4c568e9000, 2093056, PROT_NONE) = 0
mmap(0x7f4c56ae8000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13d000) = 0x7f4c56ae8000
close(3)                                = 0
open("/usr/local/lib64/libgeos_c.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libgeos_c.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgeos_c.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340y\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=88952, ...}) = 0
mmap(NULL, 2184080, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c56595000
mprotect(0x7f4c565a9000, 2097152, PROT_NONE) = 0
mmap(0x7f4c567a9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14000) = 0x7f4c567a9000
close(3)                                = 0
open("/usr/local/lib64/libplayercommon.so.3.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\7\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=8319, ...}) = 0
mmap(NULL, 2101336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c56393000
mprotect(0x7f4c56394000, 2093056, PROT_NONE) = 0
mmap(0x7f4c56593000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0) = 0x7f4c56593000
close(3)                                = 0
open("/usr/local/lib64/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\355\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1572232, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5780b000
mmap(NULL, 3680296, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c56010000
mprotect(0x7f4c5618a000, 2093056, PROT_NONE) = 0
mmap(0x7f4c56389000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x179000) = 0x7f4c56389000
mmap(0x7f4c5638e000, 18472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f4c5638e000
close(3)                                = 0
open("/usr/local/lib64/libplayerjpeg.so.3.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \17\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=13862, ...}) = 0
mmap(NULL, 2105576, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c55e0d000
mprotect(0x7f4c55e0f000, 2093056, PROT_NONE) = 0
mmap(0x7f4c5600e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7f4c5600e000
close(3)                                = 0
open("/usr/local/lib64/libjpeg.so.62", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libjpeg.so.62", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libjpeg.so.62", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libjpeg.so.62", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`9\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=146032, ...}) = 0
mmap(NULL, 2241144, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c55be9000
mprotect(0x7f4c55c0c000, 2093056, PROT_NONE) = 0
mmap(0x7f4c55e0b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x22000) = 0x7f4c55e0b000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5780a000
open("/usr/local/lib64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\244\5\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1044112, ...}) = 0
mmap(NULL, 3223608, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c558d5000
mprotect(0x7f4c559cb000, 2097152, PROT_NONE) = 0
mmap(0x7f4c55bcb000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf6000) = 0x7f4c55bcb000
mmap(0x7f4c55bd4000, 81976, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f4c55bd4000
close(3)                                = 0
open("/usr/local/lib64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200-\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=92552, ...}) = 0
mmap(NULL, 2188280, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4c556be000
mprotect(0x7f4c556d4000, 2093056, PROT_NONE) = 0
mmap(0x7f4c558d3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15000) = 0x7f4c558d3000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c57809000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c57807000
arch_prctl(ARCH_SET_FS, 0x7f4c57807720) = 0
mprotect(0x7f4c558d3000, 4096, PROT_READ) = 0
mprotect(0x7f4c55bcb000, 28672, PROT_READ) = 0
mprotect(0x7f4c55e0b000, 4096, PROT_READ) = 0
mprotect(0x7f4c5600e000, 4096, PROT_READ) = 0
mprotect(0x7f4c56389000, 16384, PROT_READ) = 0
mprotect(0x7f4c56593000, 4096, PROT_READ) = 0
mprotect(0x7f4c567a9000, 4096, PROT_READ) = 0
mprotect(0x7f4c56ae8000, 28672, PROT_READ) = 0
mprotect(0x7f4c56cf2000, 4096, PROT_READ) = 0
mprotect(0x7f4c56f4e000, 4096, PROT_READ) = 0
mprotect(0x7f4c57169000, 4096, PROT_READ) = 0
mprotect(0x7f4c573ec000, 4096, PROT_READ) = 0
mprotect(0x7f4c57610000, 4096, PROT_READ) = 0
mprotect(0x604000, 4096, PROT_READ)     = 0
mprotect(0x7f4c57832000, 4096, PROT_READ) = 0
munmap(0x7f4c5780e000, 138659)          = 0
brk(0)                                  = 0x25d4000
brk(0x25f5000)                          = 0x25f5000
mmap(NULL, 368640, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c577ad000
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c54ebd000
mmap(NULL, 33558528, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c52ebc000
mmap(NULL, 33558528, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c50ebb000
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 3
socket(PF_NETLINK, SOCK_RAW, 0)         = 4
bind(4, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(4, {sa_family=AF_NETLINK, pid=5498, groups=00000000}, [12]) = 0
sendto(4, "\24\0\0\0\26\0\1\3T\254\250L\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"0\0\0\0\24\0\2\0T\254\250Lz\25\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 108
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"@\0\0\0\24\0\2\0T\254\250Lz\25\0\0\n\200\200\376\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 128
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0T\254\250Lz\25\0\0\0\0\0\0\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(4)                                = 0
getpid()                                = 5498
open("/etc/resolv.conf", O_RDONLY)      = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=78, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5782f000
read(4, "# Generated by NetworkManager\nna"..., 4096) = 78
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7f4c5782f000, 4096)            = 0
uname({sys="Linux", node="FCD-Linux", ...}) = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 4
connect(4, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 4
connect(4, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5782f000
read(4, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7f4c5782f000, 4096)            = 0
open("/usr/local/lib64/libnss_files.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libnss_files.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=138659, ...}) = 0
mmap(NULL, 138659, PROT_READ, MAP_PRIVATE, 4, 0) = 0x7f4c5780e000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_files.so.2", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p!\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=51712, ...}) = 0
mmap(NULL, 2147720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f4c50cae000
mprotect(0x7f4c50cba000, 2093056, PROT_NONE) = 0
mmap(0x7f4c50eb9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xb000) = 0x7f4c50eb9000
close(4)                                = 0
mprotect(0x7f4c50eb9000, 4096, PROT_READ) = 0
munmap(0x7f4c5780e000, 138659)          = 0
open("/etc/host.conf", O_RDONLY)        = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=92, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5782f000
read(4, "# The \"order\" line is only used "..., 4096) = 92
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7f4c5782f000, 4096)            = 0
open("/etc/hosts", O_RDONLY|O_CLOEXEC)  = 4
fcntl(4, F_GETFD)                       = 0x1 (flags FD_CLOEXEC)
fstat(4, {st_mode=S_IFREG|0644, st_size=255, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5782f000
read(4, "127.0.0.1\tlocalhost\n127.0.1.1\tFC"..., 4096) = 255
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7f4c5782f000, 4096)            = 0
open("/etc/gai.conf", O_RDONLY)         = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=2987, ...}) = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=2987, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5782f000
read(4, "# Configuration for getaddrinfo("..., 4096) = 2987
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7f4c5782f000, 4096)            = 0
socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 4
connect(4, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("127.0.0.1")}, 16) = 0
getsockname(4, {sa_family=AF_INET, sin_port=htons(41173), sin_addr=inet_addr("127.0.0.1")}, [16]) = 0
close(4)                                = 0
setitimer(ITIMER_REAL, {it_interval={0, 0}, it_value={5, 0}}, NULL) = 0
rt_sigaction(SIGALRM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGALRM, {0x7f4c573f8c1c, [], SA_RESTORER, 0x7f4c56043af0}, NULL, 8) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(6665), sin_addr=inet_addr("127.0.0.1")}, 16) = 0
setitimer(ITIMER_REAL, {it_interval={0, 0}, it_value={0, 0}}, NULL) = 0
rt_sigaction(SIGALRM, {SIG_DFL, [], SA_RESTORER|SA_RESTART, 0x7f4c56043af0}, NULL, 8) = 0
fcntl(3, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(3, F_SETFL, O_RDWR)               = 0
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 2000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "Player v.3.0.2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 32, 0, NULL, NULL) = 32
sendto(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\3\0\0\0\5A\323*+\25\6\325R"..., 44, 0, NULL, 0) = 44
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\1\0\0\0\0\0\0\0\4\0\0\0\5@\2262\0\0\0\0\0"..., 40, 0, NULL, NULL) = 40
write(2, "playerc warning   : warning : [P"..., 90playerc warning   : warning : [Player v.3.0.2] connected on [localhost:6665] with sock 3

) = 90
sendto(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\3\0\0\0\3A\323*+\25\v#\34"..., 68, 0, NULL, 0) = 68
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\1\0\0\0\0\0\0\0\4\0\0\0\3@\2262fffff"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\4\0\0\0\0\0\0\0\1\0\0\0\6\0\0\0\6stag"..., 36, 0, NULL, NULL) = 36
sendto(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\3\0\0\0\3A\323*+\25\16|\252"..., 68, 0, NULL, 0) = 68
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\1\0\0\0\0\0\0\0\4\0\0\0\3@\2262fffff"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\5\0\0\0\0\0\0\0\1\0\0\0\6\0\0\0\6stag"..., 36, 0, NULL, NULL) = 36
sendto(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\3\0\0\0\4A\323*+\25\21\216?"..., 40, 0, NULL, 0) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\1\0\0\0\0\0\0\0\4\0\0\0\4@\2262\314\314\314\314\315"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, -1) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\4\0\0\0\0\0\0\0\1\0\0\0\1@\2262\314\314\314\314\315"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "@\16>i\210\27\266\361?d\253\233\304\231_\313\277\357(\337\2310d2\0\0\0\0\0\0\0\0"..., 52, 0, NULL, NULL) = 52
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\5\0\0\0\0\0\0\0\1\0\0\0\1@\2262\314\314\314\314\315"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\20\0\0\0\20@\212\"\22@}pE@\204\207\363@\223$K@\240\0\0@\240\0\0"..., 72, 0, NULL, NULL) = 72
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\5\0\0\0\1\0\0\177\377\323\31\373\200"..., 40, 0, NULL, NULL) = 40
sendto(3, "\0\0\0\0\0\0\32\t\0\0\0\5\0\0\0\0\0\0\0\3\0\0\0\1A\323*+\25\30\210\234"..., 40, 0, NULL, 0) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\5\0\0\0\0\0\0\0\4\0\0\0\1@\226333333"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\20\0\0\0\20?\263333333?\300\243\327\n=p\244\0\0\0\0\0\0\0\0"..., 776, 0, NULL, NULL) = 776
brk(0x2616000)                          = 0x2616000
fstat(1, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 2), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4c5782f000
write(1, "\n", 1
)                       = 1
write(1, "\n", 1
)                       = 1
write(1, "Map size : 16.00 meters.\n", 25Map size : 16.00 meters.
) = 25
write(1, "Resolution : 0.20 meters.\n", 26Resolution : 0.20 meters.
) = 26
write(1, "Number of cells : 81 x 95\n", 26Number of cells : 81 x 95
) = 26
write(1, "Radius : 0.115470\n", 18Radius : 0.115470
)     = 18
write(1, "Map center : ( 8.100, 8.256)\n", 29Map center : ( 8.100, 8.256)
) = 29
write(1, "\n", 1
)                       = 1
write(1, "S= 0.115470\n", 12S= 0.115470
)           = 12
write(1, "H= 0.057735\n", 12H= 0.057735
)           = 12
write(1, "R= 0.100000\n", 12R= 0.100000
)           = 12
write(1, "\n", 1
)                       = 1
write(1, "Sonar pose count : 16\n", 22Sonar pose count : 16
) = 22
sendto(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\3\0\0\0\4A\323*+\25\33T\213"..., 40, 0, NULL, 0) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\1\0\0\0\0\0\0\0\4\0\0\0\4@\226333333"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, -1) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\4\0\0\0\0\0\0\0\1\0\0\0\1@\2263\231\231\231\231\232"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "@\16>i\210\27\266\361?d\253\233\304\231_\313\277\357(\337\2310d2\0\0\0\0\0\0\0\0"..., 52, 0, NULL, NULL) = 52
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\5\0\0\0\0\0\0\0\1\0\0\0\1@\2263\231\231\231\231\232"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\20\0\0\0\20@\212\"\22@}pE@\204\207\363@\223$K@\240\0\0@\240\0\0"..., 72, 0, NULL, NULL) = 72
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\5\0\0\0\1\0\0\177\377\323\31\373\200"..., 40, 0, NULL, NULL) = 40
write(1, "\n\n", 2

)                     = 2
write(1, "\n", 1
)                       = 1
write(1, "position2d :\t   3.78    0.00   -"..., 37position2d :    3.78    0.00   -0.97
) = 37
write(1, "\n", 1
)                       = 1
write(1, "Robot actual macro cell : 59  48"..., 33Robot actual macro cell : 59  48
) = 33
write(1, "Robot map location : (59,47)\n", 29Robot map location : (59,47)
) = 29
write(1, "15 14 13 12 11 10 9 8 7 6 5 4 3 "..., 3515 14 13 12 11 10 9 8 7 6 5 4 3 2 
) = 35
sendto(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\3\0\0\0\4A\323*+\25 \342\265"..., 40, 0, NULL, 0) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\1\0\0\0\0\0\0\0\4\0\0\0\4@\2263\231\231\231\231\232"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, -1) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\4\0\0\0\0\0\0\0\1\0\0\0\1@\2264fffff"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "@\16>i\210\27\266\361?d\253\233\304\231_\313\277\357(\337\2310d2\0\0\0\0\0\0\0\0"..., 52, 0, NULL, NULL) = 52
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\5\0\0\0\0\0\0\0\1\0\0\0\1@\2264fffff"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\20\0\0\0\20@\212\"\22@}pE@\204\207\363@\223$K@\240\0\0@\240\0\0"..., 72, 0, NULL, NULL) = 72
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\5\0\0\0\1\0\0\177\377\323\31\373\200"..., 40, 0, NULL, NULL) = 40
write(1, "\n\n", 2

)                     = 2
write(1, "\n", 1
)                       = 1
write(1, "position2d :\t   3.78    0.00   -"..., 37position2d :    3.78    0.00   -0.97
) = 37
write(1, "\n", 1
)                       = 1
write(1, "Robot actual macro cell : 59  48"..., 33Robot actual macro cell : 59  48
) = 33
write(1, "Robot map location : (59,47)\n", 29Robot map location : (59,47)
) = 29
write(1, "15 14 13 12 11 10 9 8 7 6 5 4 3 "..., 3515 14 13 12 11 10 9 8 7 6 5 4 3 2 
) = 35
sendto(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\3\0\0\0\4A\323*+\25-J#"..., 40, 0, NULL, 0) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\1\0\0\0\0\0\0\0\4\0\0\0\4@\2264fffff"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, -1) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\4\0\0\0\0\0\0\0\1\0\0\0\1@\2264\314\314\314\314\315"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "@\16>i\210\27\266\361?d\253\233\304\231_\313\277\357(\337\2310d2\0\0\0\0\0\0\0\0"..., 52, 0, NULL, NULL) = 52
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\1\0\0\177\0\0\32\t\0\0\0\5\0\0\0\0\0\0\0\1\0\0\0\1@\2264\314\314\314\314\315"..., 40, 0, NULL, NULL) = 40
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\20\0\0\0\20@\212\"\22@}pE@\204\207\363@\223$K@\240\0\0@\240\0\0"..., 72, 0, NULL, NULL) = 72
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLPRI|POLLERR|POLLHUP|POLLNVAL}], 1, 5000) = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\0\0\0\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\5\0\0\0\1\0\0\177\377\323\31\373\200"..., 40, 0, NULL, NULL) = 40
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Segmentation fault

```Is there anything more useful then STRACE?
Is there any application able to show me in detail the memory usage of my application?
I don't want to be a troll, but in this case i find that a microsoft product (visual studio) is more easily fruible and more productive.
No -excessive- pun intended :P
Right now i could use an IDE able to read memory, breakpoints and the likes. Is there anything like that for linux?

---

### Post by dwhitney67 on 2010-10-03
> **erupter said:**
> 
Since this is all done in C i'm stuck with manual allocation and deallocation.


The Gods forbid me to work as a psychic on Sundays, thus I wish I could help you, but without seeing even one line of your code, it is going to be a crap-shoot of an effort to help you.

Posting your strace output is worthless for the most part; why don't you whittle your program down to something more manageable where you can practice your knowledge of how to allocate/deallocate arrays.  While you are at it, perhaps learn to use valgrind and/or gdb.

---

### Post by Zugzwang on 2010-10-03
As a start, you can try running your application using valgrind:

```

valgrind --tool=memcheck ./yourapplication <yourparameters>

```

The memcheck tool of valgrind will find many but not all typical causes of segmentation faults. You will need to install its package first. But since it is easy to use and doesn't require changes to your program, you should give it a try. Use google for finding out more about that.

---

### Post by worseisworser on 2010-10-03
> **erupter said:**
> Right now i could use an IDE able to read memory, breakpoints and the likes. Is there anything like that for linux?

Yes, there are several IDEs and/or tools for debugging C stuff.

---

### Post by unknownPoster on 2010-10-03
> **Zugzwang said:**
> As a start, you can try running your application using valgrind:

```

valgrind --tool=memcheck ./yourapplication <yourparameters>

```

The memcheck tool of valgrind will find many but not all typical causes of segmentation faults. You will need to install its package first. But since it is easy to use and doesn't require changes to your program, you should give it a try. Use google for finding out more about that.

I definitely agree. Valgrind is an excellent tool.

I'd also look into learning about gdb.

---

### Post by erupter on 2010-10-03
> **dwhitney67 said:**
> The Gods forbid me to work as a psychic on  Sundays, thus I wish I could help you, but without seeing even one line  of your code, it is going to be a crap-shoot of an effort to help you.
  
  Posting your strace output is worthless for the most part; why don't you  whittle your program down to something more manageable where you can  practice your knowledge of how to allocate/deallocate arrays.  While you  are at it, perhaps learn to use valgrind and/or gdb.
  
  Yeah i know it's useless, for me all the more because i can't read anything in it.
  But i did not want help in understanding my error, what i wanted were  means of discovering what is happening. No mind-reading stuff asked ;)
  
 
 
 > **Zugzwang said:**
> As a start, you can try running your application using valgrind:
 
 ```

 valgrind --tool=memcheck ./yourapplication <yourparameters>
 
```The memcheck tool of valgrind will find many but not all typical  causes of segmentation faults. You will need to install its package  first. But since it is easy to use and doesn't require changes to your  program, you should give it a try. Use google for finding out more about  that.
 
 Thanks, that's a nice start. I'll see what i can do.
 
 
 > **worseisworser said:**
> Yes, there are several IDEs and/or tools for debugging C stuff.

This answer is not helpful. Why answering "yes there are" without citing any one?

> **unknownPoster said:**
> I definitely agree. Valgrind is an excellent tool.

I'd also look into learning about gdb.
I'll look it up. Thanks.


Anyway it's not that i do not want to post my code, it's just that i like to figure out my errors myself unless i absolutely can't do it (that translates in: after being stuck on the same line for 2hrs+ i usually give up, counter is reset if i change the line being stuck on :p)

---

### Post by erupter on 2010-10-04
Ok i'm gonna post the code.
If you want to directly compile it, you need the playerstage suite ([http://playerstage.sourceforge.net](http://playerstage.sourceforge.net)).

Below is the actual problem.
```


void geometric_calculations (void){
    int i;
    XY_Coord *temp = malloc(sizeof(XY_Coord));
    temp->px=position2d->px;
    temp->py=position2d->py;
    
    get_discrete_coordinates(temp,robot_map_cell);
    free(temp);
    robot_macro_cell=temporary_macro_cell;
    robot_macro_cell_zone=macro_cell_zone;
    
    for (i=0;i<sonar->scan_count;i++){
      hit_coordinates_original[i]->px=position2d->px+cos(position2d->pa)*(sonar->poses[i].px+cos(sonar->poses[i].pyaw)*sonar->scan[i]-sin(sonar->poses[i].pyaw)*sonar->scan[i])-sin(position2d->pa)*(sonar->poses[i].py+sin(sonar->poses[i].pyaw)*sonar->scan[i]+cos(sonar->poses[i].pyaw)*sonar->scan[i]);
      hit_coordinates_original[i]->py=position2d->py+sin(position2d->pa)*(sonar->poses[i].px+cos(sonar->poses[i].pyaw)*sonar->scan[i]-sin(sonar->poses[i].pyaw)*sonar->scan[i])+cos(position2d->pa)*(sonar->poses[i].py+sin(sonar->poses[i].pyaw)*sonar->scan[i]+cos(sonar->poses[i].pyaw)*sonar->scan[i]);
      
      source_coordinates_original[i]->px=position2d->px+cos(position2d->pa)*sonar->poses[i].px-sin(position2d->pa)*sonar->poses[i].py;
      source_coordinates_original[i]->py=position2d->py+sin(position2d->pa)*sonar->poses[i].px+cos(position2d->pa)*sonar->poses[i].py;
      
    }
    
    for (i=0;i<sonar->scan_count;i++) {
      get_discrete_coordinates(hit_coordinates_original[i],hit_coordinates_discrete[i]);
      get_discrete_coordinates(source_coordinates_original[i],source_coordinates_discrete[i]);
      get_connecting_vector(source_coordinates_discrete[i],hit_coordinates_discrete[i],range_vectors[i]);
    }
//     get_connecting_vector(source_coordinates_discrete[1],hit_coordinates_discrete[1],range_vectors[1]);
    
}

void get_connecting_vector (map_cell_vector* discrete_origin, map_cell_vector* discrete_destination, map_cell_vector* into) {

  int first=1;
  XY_Coord *cartesian_origin=(XY_Coord *) malloc (sizeof (XY_Coord));
  XY_Coord *cartesian_destination=(XY_Coord *) malloc (sizeof (XY_Coord));
  float inc_x, inc_y, angle, distance;
  int counter1=0,counter2=0;
  map_cell_vector *actual_discrete=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  map_cell_vector *next_discrete=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  map_cell_vector *ptr1=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  map_cell_vector *ptr2;
//   map_cell_vector *ptr2=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  
  into->px=discrete_origin->px;
  into->py=discrete_origin->py;
//   into->next=ptr1;
//   ptr1=ptr2;
  get_cartesian_coordinates(discrete_origin,cartesian_origin);
  get_cartesian_coordinates(discrete_destination,cartesian_destination);  
  angle = atan2((cartesian_destination->py-cartesian_origin->py),cartesian_destination->px-cartesian_origin->px);
  inc_x=cos(angle)*radius;
  inc_y=sin(angle)*radius;
  actual_discrete->px=discrete_origin->px;
  actual_discrete->py=discrete_origin->py;
  next_discrete->px=actual_discrete->px;
  next_discrete->py=actual_discrete->py;
  
  
  distance = sqrt((cartesian_destination->px-cartesian_origin->px)*(cartesian_destination->px-cartesian_origin->px)+(cartesian_destination->py-cartesian_origin->py)*(cartesian_destination->py-cartesian_origin->py));
  while ((distance > radius) && (counter1 < 1000)) {
    if (first) {
     first=0;
     into->next=ptr1;
// printf("start\t(%d,%d) -> (%d,%d)\n",discrete_origin->px, discrete_origin->py,discrete_destination->px,discrete_destination->py);
    }
    else {
      ptr2=malloc(sizeof(map_cell_vector));
      ptr1->next=ptr2;
      ptr1=ptr2;
    }
      
    while ((actual_discrete->px == next_discrete->px) && (actual_discrete->py == next_discrete->py) && (counter2 < 5)) {
      cartesian_origin->px+=inc_x;
      cartesian_origin->py+=inc_y;
      get_discrete_coordinates(cartesian_origin,next_discrete);
      counter2++;
      
    }
    distance = sqrt((cartesian_destination->px-cartesian_origin->px)*(cartesian_destination->px-cartesian_origin->px)+(cartesian_destination->py-cartesian_origin->py)*(cartesian_destination->py-cartesian_origin->py));
    counter2=0;
    actual_discrete->px=next_discrete->px;
    actual_discrete->py=next_discrete->py;
    ptr1->px=actual_discrete->px;
    ptr1->py=actual_discrete->py;
    ptr1->distance=distance;
    ptr1->next=NULL;
//     ptr2=malloc(sizeof(map_cell_vector));
//     ptr1->next=ptr2;
//     ptr1=ptr2;
    
    
    
    counter1++;
    
    
    
    
  }
  free(cartesian_origin);
  free(cartesian_destination);
  free(actual_discrete);
  free(next_discrete);
  free(ptr2);
  
}

void free_resources (void) {
  int i=0;
  for (i=sonar->pose_count-1; i>=0; i--)  {
    free_vector(range_vectors[i]);
//     printf ("%d ",i);
  }
//   printf("\n");
  
  
}

void free_vector (map_cell_vector *ptr) {
  
  if (ptr->next != NULL)
    free_vector(ptr->next);
  free(ptr);
}

int main(int argc, const char **argv)
{
  int result=0,i;

  set_defaults();
  result=network_setup();
  
  if (result){
    printf("Network setup error\n%s",network_errors[result]);
    return -1;
  }
  
  if ((execute_command_interpreter(argc,argv)))
    return -1;
  
  init();
  
  
  // Main Cycle
  for (i = 0; i < main_cycle_iterations; i++)
  {
    playerc_client_read(client);
    
    geometric_calculations();
//     for (i=sonar->pose_count-1;i>=0;i--)
//       printf("Sonar %d, pointer %p, (%d,%d)\n",i,range_vectors[i],range_vectors[i]->px,range_vectors[i]->py);

    display_output_messages(WORKING);
    
    free_resources();

  }
  

  close_connections();

  return 0;
}
```
As you can see the flow is this:
i build a vector by dynamically allocating structures, each one pointing to the next (this happens in get_connecting_vector).
When i'm done, i call the free_resources function, which uses a recursive child function to clear all the vectors from their end.
It's this that fails giving all sorts of errors.
If no clearing is done, and the program is run in one iteration only, valgrind reports no errors nor missing pointers. Starting from two iterations obviously memory gets lost since i simply point array headers to different cells, thus leaving entire arrays to be for themselves.
I hope i made myself clear.
Following is the entire source code.

variables.h
```
char network_errors[4][80]={ "No error.\n",
              "Can't connect to the client on specified IP and Port. Check Values.\n",
              "Can't subscribe to Position2D interface, Check it is available.\n",
              "Can't subscribe to Sonar interface. Check it is avilable.\n",
              };
              
// string network_errors[3]= new string ();
// string network_errors[0] ("No error.\n");
// string network_errors[1] ("Can't connect to the client on specified IP and Port. Check Values.\n");
// string network_errors[2] ("Can't subscribe to Position2D interface, Check it is available.\n","Can't subscribe to Sonar interface. Check it is avilable.\n");






int counter;

/***********************************************************************
*                                       *
*                            Map variables                             *
*                                       *
***********************************************************************/
typedef struct fuzzy_cell {
  float universe;
  float occupied;
  float empty;
  float uncertainty;
} fuzzy_cell;

fuzzy_cell **fuzzy_map;
int **occupancy_grid;

/***********************************************************************
*                                       *
*                        Geometric variables                           *
*                                       *
***********************************************************************/
typedef struct XY_Coord {
  float px;
  float py;
} XY_Coord;

typedef struct map_cell_vector {
  int px;
  int py;
  float distance;
  struct map_cell_vector *next;
} map_cell_vector;


float cell_s_size,cell_h_size,cell_r_size=0;
float map_size;                    //meters
float map_resolution;                //meters, amplitude of cell
float radius;

XY_Coord **hit_coordinates_original, **source_coordinates_original;
XY_Coord robot_macro_cell, temporary_macro_cell ,map_center_position, map_size_real;

map_cell_vector **hit_coordinates_discrete, *robot_map_cell, **source_coordinates_discrete, **range_vectors;

int macro_cell_type;
char macro_cell_zone;
char robot_macro_cell_zone;


/***********************************************************************
*                                       *
*                        Auxiliary variables                           *
*                                       *
***********************************************************************/

long main_cycle_iterations;
int verbose=0;
int map_init=0;

playerc_client_t *client;
playerc_position2d_t *position2d;
playerc_sonar_t *sonar;








#define A_TYPE 0
#define B_TYPE 1
#define STARTUP 0
#define WORKING 1
#define MAX_STRING_SIZE 20


int network_setup(void);
void close_connections(void);

void set_defaults(void);
void init(void);
void free_resources (void);
void free_vector (map_cell_vector* ptr);

int execute_command_interpreter(int argc, const char **argv);

void geometric_calculations (void);

void display_output_messages (int type);

void get_cartesian_coordinates (map_cell_vector* origin, XY_Coord* into);
void get_discrete_coordinates (XY_Coord* original, map_cell_vector* into);

// void get_connecting_vector (XY_Coord *origin, XY_Coord *actual, XY_Coord *destination, map_cell_vector *into);
void get_connecting_vector (map_cell_vector* discrete_origin, map_cell_vector* discrete_destination, map_cell_vector* into);
// void get_next_cell (int sector, XY_Coord *origin, map_cell_vector *into);
void get_neighbours (XY_Coord *origin, map_cell_vector *into);
```source
```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <libplayerc/playerc.h>
#include "variables.h"





int main(int argc, const char **argv)
{
  int result=0,i;

  set_defaults();
  result=network_setup();
  
  if (result){
    printf("Network setup error\n%s",network_errors[result]);
    return -1;
  }
  
  if ((execute_command_interpreter(argc,argv)))
    return -1;
  
  init();
  
  
  // Main Cycle
  for (i = 0; i < main_cycle_iterations; i++)
  {
    playerc_client_read(client);
    
    geometric_calculations();
//     for (i=sonar->pose_count-1;i>=0;i--)
//       printf("Sonar %d, pointer %p, (%d,%d)\n",i,range_vectors[i],range_vectors[i]->px,range_vectors[i]->py);

    display_output_messages(WORKING);
    
//     free_resources();

  }
  

  close_connections();

  return 0;
}





void free_resources (void) {
  int i=0;
  for (i=sonar->pose_count-1; i>=0; i--)  {
    free_vector(range_vectors[i]);
//     printf ("%d ",i);
  }
//   printf("\n");
  
  
}

void free_vector (map_cell_vector *ptr) {
  
  if (ptr->next != NULL)
    free_vector(ptr->next);
  free(ptr);
}

void set_defaults(void){

  main_cycle_iterations=20;
  map_size=10;
  map_resolution=1;
  cell_s_size=map_resolution/(2*sin(M_PI/3));
  
}

void init(void){
  int i=0,j=0;  
  playerc_client_read(client);
  playerc_sonar_get_geom(sonar);
  
  robot_map_cell=malloc (sizeof(map_cell_vector));

  hit_coordinates_original = (XY_Coord**) malloc (sonar->pose_count * sizeof (XY_Coord*));
  hit_coordinates_discrete = (map_cell_vector**) malloc (sonar->pose_count * sizeof (map_cell_vector*));
  source_coordinates_original = (XY_Coord **) malloc (sonar->pose_count * sizeof (XY_Coord *));
  source_coordinates_discrete = (map_cell_vector**) malloc (sonar->pose_count * sizeof (map_cell_vector*));
  range_vectors = (map_cell_vector**) malloc (sonar->pose_count * sizeof (map_cell_vector*));
  
  
  for (i=0;i<sonar->pose_count; i++) {
    hit_coordinates_original[i]=  malloc(sizeof(XY_Coord));
    hit_coordinates_discrete[i]=  malloc(sizeof(map_cell_vector));
    source_coordinates_original[i]=  malloc(sizeof(XY_Coord));
    source_coordinates_discrete[i]=  malloc(sizeof(map_cell_vector));
    range_vectors[i]=  malloc(sizeof(map_cell_vector));

  }
  switch(map_init){
    case 2:
      cell_s_size=map_resolution/(2*sin(M_PI/3));
      break;
    case 3:
      map_resolution= (cell_s_size*2*sin(M_PI/3));
      break;
    case 4:
      cell_s_size=map_resolution/(2*sin(M_PI/3));
      break;
    case 5:
      cell_s_size=map_resolution/(2*sin(M_PI/3));
      break;
    case 6:
      cell_s_size=map_resolution/(2*sin(M_PI/3));
      break;
    case 7:
      map_resolution= (cell_s_size*2*sin(M_PI/3));
      break;
    case 9:
      cell_s_size=map_resolution/(2*sin(M_PI/3));
      break;
  }
  cell_h_size=cos(M_PI/3)*cell_s_size;
  cell_r_size=sin(M_PI/3)*cell_s_size;
  
  map_size_real.px=round (map_size/map_resolution);
  if (!((int)map_size_real.px % 2))
    map_size_real.px += 1;
  map_size_real.py=3;
  while (map_size_real.py * (cell_h_size+cell_s_size) < map_size)
    map_size_real.py+=4;

  fuzzy_map=(fuzzy_cell **) malloc (map_size_real.px * sizeof (fuzzy_cell*));
  occupancy_grid = malloc (map_size_real.px * sizeof (int *));
  for(i = 0; i < map_size_real.px; i++) {
    fuzzy_map[i]=(fuzzy_cell*) malloc (map_size_real.py * sizeof( fuzzy_cell));
    occupancy_grid[i]=malloc (map_size_real.py * sizeof (int));
  }
  for (i=0;i<map_size_real.px;i++)
    for (j=0;j<map_size_real.py;j++) {
      fuzzy_map[i][j].universe=1;
      fuzzy_map[i][j].occupied=0;
      fuzzy_map[i][j].empty=0;
      fuzzy_map[i][j].uncertainty=0;
      occupancy_grid[i][j]=0;
    }

    
  
  map_center_position.px=(map_size_real.px-1)*cell_r_size + cell_r_size;
  map_center_position.py=(map_size_real.py-1)/2*(cell_s_size+cell_h_size)+cell_s_size;
  radius = cell_s_size;
}

int network_setup (void){
    client = playerc_client_create(NULL, "localhost", 6665);
  if (0 != playerc_client_connect(client))
    return 1;

  // Create and subscribe to a position2d device.
  position2d = playerc_position2d_create(client, 0);
  if (playerc_position2d_subscribe(position2d, PLAYER_OPEN_MODE))
    return 2;
  
  sonar=playerc_sonar_create(client,0);
  if (playerc_sonar_subscribe(sonar, PLAYER_OPEN_MODE))
    return 3;
  return 0;

}

void close_connections(void){
  
  printf("\n");
  printf("Closing connections:\n");
  playerc_position2d_unsubscribe(position2d);
  playerc_position2d_destroy(position2d);
  printf("Position... ");
  playerc_sonar_unsubscribe(sonar);
  playerc_sonar_destroy(sonar);
  printf("Sonar... ");
  playerc_client_disconnect(client);
  playerc_client_destroy(client);
  printf("Client destroyed\n");
  printf("Connections closed.\n");
  
}

/**********************************************************************
*                                      *
*            Command interpreter                  *
*                                      *
**********************************************************************/
int execute_command_interpreter(int argc, const char **argv){
  int command_counter=1;
  char command_string[MAX_STRING_SIZE];
    while (command_counter<argc){
      
      strcpy(command_string,argv[command_counter]);
      
      if (!(strcmp(command_string,"-res"))|| !(strcmp(command_string,"-resolution"))){
    if (argc==command_counter+1){
      printf("Incorrect map resolution command, exiting\n");
      return -1;
    }
    else  if (!strncmp(argv[command_counter+1],"-",1)){
      printf("Incorrect map resolution command, exiting\n");
      return -1;
    }
    else{
      map_resolution=atof(argv[command_counter+1]);
      command_counter++;
      map_init+=2;
    }
      }
      
      if (!(strcmp(command_string,"-side"))){
    if (argc==command_counter+1){
      printf("Incorrect cell side command, exiting\n");
      return -1;
    }
    else  if (!strncmp(argv[command_counter+1],"-",1)){
      printf("Incorrect cell side command, exiting\n");
      return -1;
    }
    else{
      cell_s_size=atof(argv[command_counter+1]);
      command_counter++;
      map_init+=3;
    }
      }
      
      if (!(strcmp(command_string,"-s")) || !(strcmp(command_string,"-size"))){
    if (argc==command_counter+1){
      printf("Incorrect map size command, exiting\n");
      return -1;
    }
    else  if (!strncmp(argv[command_counter+1],"-",1)){
      printf("Incorrect map size command, exiting\n");
      return -1;
    }
    else{
      map_size=atof(argv[command_counter+1]);
      command_counter++;
      map_init+=4;
    }
      }
      
      if (!(strcmp(command_string,"-iter")) || !(strcmp(command_string,"-iterations"))){
    if (argc==command_counter+1){
      printf("Incorrect iterations command, exiting\n");
      return -1;
    }
    else  if (!strncmp(argv[command_counter+1],"-",1)){
      printf("Incorrect iterations command, exiting\n");
      return -1;
    }
    else{
      main_cycle_iterations=atoi(argv[command_counter+1]);
      command_counter++;
    }
      }
      
      if (!(strcmp(command_string,"-v")) || !(strcmp(command_string,"-verbose"))){
    if (argc==command_counter+1){
      verbose=1;
    }
      
    else  if (!strncmp(argv[command_counter+1],"-",1)){
      verbose =1;
    }
    else{
      verbose=atof(argv[command_counter+1]);
      command_counter++;
      
    }
      }
    
    
      command_counter++;
    }
    return 0;
}


void display_output_messages (int type){
  
  int i,j;
  
  switch (type) {
    case STARTUP:
      printf("\n\n");
      printf("Map size : %.2f meters.\n",map_size);
      printf("Resolution : %.2f meters.\n",map_resolution);
      printf("Number of cells : %d x %d\n",(int)map_size_real.px,(int)map_size_real.py);
      printf("Radius : %f\n",radius);
      printf("Map center : (%6.3f,%6.3f)\n",map_center_position.px,map_center_position.py);
      printf("\n");
      printf("S= %f\nH= %f\nR= %f\n",cell_s_size,cell_h_size,cell_r_size);
      printf("\n");
      printf("Sonar pose count : %d\n",sonar->pose_count);
      
      
      if(verbose>1){
    printf("Sonar no\tposX\tposY\tposZ\trotX\trotY\trotZ\n");
    for (j=0;j<sonar->pose_count;j++)
      printf("sonar %2d\t%-5.2f\t%-5.2f\t%-5.2f\t%-5.2f\t%-5.2f\t%-5.2f\n",j+1,sonar->poses[j].px,sonar->poses[j].py,sonar->poses[j].pz,sonar->poses[j].proll,sonar->poses[j].ppitch,sonar->poses[j].pyaw);
      }
      break;
      
    case WORKING:
      
      if (verbose){        //Verbose Level 1      
    printf("\n\n\n|---------------------- Iteration ----------------------|\n");
    printf("position2d :\t%7.2f %7.2f %7.2f\n", position2d->px, position2d->py, position2d->pa);
    printf("\n");
    printf("Robot actual macro cell : %d  %d\n",(int)robot_macro_cell.px,(int)robot_macro_cell.py);    
    printf("Robot map location : (%d,%d)\n",robot_map_cell->px,robot_map_cell->py);
      }
      
      if (verbose>1){        //Verbose Level 2
    printf("Robot actual macro cell type : ");
    switch (macro_cell_type){
      case 0:
        printf("A Type\n");
        break;
      case 1:
        printf ("B Type\n");
        break;
    }
    printf("Robot actual macro cell zone : %C\n",robot_macro_cell_zone);
    printf("Robot actual map cell : %d  %d\n",(int)robot_map_cell->px, (int)robot_map_cell->py);
      }
      
      if (verbose>2){        //Verbose Level 3
    printf("\n");
    printf("Sonar scans :\n");
    for (i=0;i<sonar->scan_count;i++) 
      printf("Sensor %2d:\t%7.2f\t%7.2f\t%7.2f\t-> (%d;%d)\n",i,hit_coordinates_original[i]->px,hit_coordinates_original[i]->py,sonar->scan[i],(int)hit_coordinates_discrete[i]->px,(int)hit_coordinates_discrete[i]->py);    
      }
      
      if (verbose>3){
    printf("\n");
//     for (i=0;i<map_size_real.px;i++) {
//       printf("%2d",map_fuzzy_values[i][0]);
//       for (j=1;j<map_size_real.py;j++) {
//         printf(", %d",map_fuzzy_values[i][j]);
//       }
//       printf("\n");
//     }
      }
      
      printf("|_______________________________________________________|\n");
//       printf("\n");
      break;
  }
}




/**********************************************************************
*                                      *
*            Geometric Calculations                  *
*                                      *
**********************************************************************/



void geometric_calculations (void){
    int i;
    XY_Coord *temp = malloc(sizeof(XY_Coord));
    temp->px=position2d->px;
    temp->py=position2d->py;
    
    get_discrete_coordinates(temp,robot_map_cell);
    free(temp);
    robot_macro_cell=temporary_macro_cell;
    robot_macro_cell_zone=macro_cell_zone;
    
    for (i=0;i<sonar->scan_count;i++){
      hit_coordinates_original[i]->px=position2d->px+cos(position2d->pa)*(sonar->poses[i].px+cos(sonar->poses[i].pyaw)*sonar->scan[i]-sin(sonar->poses[i].pyaw)*sonar->scan[i])-sin(position2d->pa)*(sonar->poses[i].py+sin(sonar->poses[i].pyaw)*sonar->scan[i]+cos(sonar->poses[i].pyaw)*sonar->scan[i]);
      hit_coordinates_original[i]->py=position2d->py+sin(position2d->pa)*(sonar->poses[i].px+cos(sonar->poses[i].pyaw)*sonar->scan[i]-sin(sonar->poses[i].pyaw)*sonar->scan[i])+cos(position2d->pa)*(sonar->poses[i].py+sin(sonar->poses[i].pyaw)*sonar->scan[i]+cos(sonar->poses[i].pyaw)*sonar->scan[i]);
      
      source_coordinates_original[i]->px=position2d->px+cos(position2d->pa)*sonar->poses[i].px-sin(position2d->pa)*sonar->poses[i].py;
      source_coordinates_original[i]->py=position2d->py+sin(position2d->pa)*sonar->poses[i].px+cos(position2d->pa)*sonar->poses[i].py;
      
    }
    
    for (i=0;i<sonar->scan_count;i++) {
      get_discrete_coordinates(hit_coordinates_original[i],hit_coordinates_discrete[i]);
      get_discrete_coordinates(source_coordinates_original[i],source_coordinates_discrete[i]);
      get_connecting_vector(source_coordinates_discrete[i],hit_coordinates_discrete[i],range_vectors[i]);
    }
//     get_connecting_vector(source_coordinates_discrete[1],hit_coordinates_discrete[1],range_vectors[1]);
    
}


void get_cartesian_coordinates (map_cell_vector *origin, XY_Coord *into) {

  into->px = origin->px*2*cell_r_size - map_center_position.px;
  into->py = -((origin->py*(cell_h_size+cell_s_size)) - map_center_position.py + cell_s_size);
  if (origin->py % 2)
    into->px += cell_r_size;

}

/**********************************************************************
*                                      *
*            Discretize Coordinates                  *
*                                      *
**********************************************************************/

void get_discrete_coordinates (XY_Coord *original, map_cell_vector * into) {

  map_cell_vector *final = malloc(sizeof(map_cell_vector));
  XY_Coord re_oriented, local;

  
  temporary_macro_cell.px = floor((original->px + map_center_position.px)/(2*cell_r_size));
  temporary_macro_cell.py = floor((-original->py + map_center_position.py)/(cell_h_size+cell_s_size));
  re_oriented.px=original->px+map_center_position.px;
  re_oriented.py=-original->py+map_center_position.py;
  local.px=re_oriented.px-(temporary_macro_cell.px*2*cell_r_size);
  local.py=re_oriented.py-(temporary_macro_cell.py*(cell_h_size+cell_s_size));
  if (((int)temporary_macro_cell.py % 2))
    local.px += cell_r_size;
/*  
  printf("\nactual coords: %5.2f\t%5.2f\n",original->px,original->py);
  printf("map center: %5.2f\t%5.2f\n",map_center_position.px,map_center_position.py);
  printf("re-oriented: %5.2f\t%5.2f\n",re_oriented.px,re_oriented.py);
  printf("local coords: %5.2f\t%5.2f\n",local.px,local.py);*/
  
  if ((int) temporary_macro_cell.py % 2){
    macro_cell_type=A_TYPE;
  }
  else{
    macro_cell_type=B_TYPE;
  }
  
  switch (macro_cell_type){
    case A_TYPE:
      
      /**********************************************************
      *                                *
      *       Part 1: inferior rectangle            *
      *                                *
      **********************************************************/
      
      if (local.py > cell_h_size) {
    final->py=(int)temporary_macro_cell.py;
    final->px=(int)temporary_macro_cell.px;
    macro_cell_zone='B';
    break;
      }
      
      /**********************************************************
      *                                *
      *       Part 2: superior rectangle            *
      *                                *
      **********************************************************/
      
      if (local.px > cell_r_size) {
    if (local.py > local.px * cell_h_size / cell_r_size - cell_h_size) {        
        final->px=(int)temporary_macro_cell.px;
        final->py=(int)temporary_macro_cell.py;
        macro_cell_zone='B';
      }
      else {        
        final->px=(int)temporary_macro_cell.px;
        final->py=(int)temporary_macro_cell.py-1;
        macro_cell_zone='C';
      }
      break;
      }

      else {
    if (local.py > -local.px*cell_h_size/cell_r_size + cell_h_size){

      final->px=(int)temporary_macro_cell.px;
      final->py=(int)temporary_macro_cell.py;
      macro_cell_zone='B';
    }
    else {
      
      final->px=(int)temporary_macro_cell.px-1;
      final->py=(int)temporary_macro_cell.py-1;
      macro_cell_zone='A';
    }
    break;
      }   

    
    case B_TYPE:

      /**********************************************************
      *                                *
      *       Part 1: inferior rectangle            *
      *                                *
      **********************************************************/

      if (local.py > cell_h_size) {
    if (local.px > cell_r_size){
      final->px=(int)temporary_macro_cell.px;
      final->py=(int)temporary_macro_cell.py;
      
      macro_cell_zone='C';
    }
    else {
      
      final->px=(int)temporary_macro_cell.px-1;
      final->py=(int)temporary_macro_cell.py;
      macro_cell_zone='A';
    }
      
    break;
      }
     
      /**********************************************************
      *                                *
      *       Part 2: superior rectangle            *
      *                                *
      **********************************************************/
      
      if (local.px > cell_r_size){
    if (local.py > -local.px*cell_h_size/cell_r_size+2*cell_h_size) {
      final->px=(int)temporary_macro_cell.px;
      final->py=(int)temporary_macro_cell.py;
      macro_cell_zone='C';
      
      
    }
    else {      
      final->px=(int)temporary_macro_cell.px;
      final->py=(int)temporary_macro_cell.py-1;
      macro_cell_zone='B';
    }
      }
      else 
    if (local.py > local.px*cell_h_size/cell_r_size) {      
      final->px=(int)temporary_macro_cell.px-1;
      final->py=(int)temporary_macro_cell.py;
      macro_cell_zone='A';
      
      
    }
    else {
      final->px=(int)temporary_macro_cell.px;
      final->py=(int)temporary_macro_cell.py-1;
      macro_cell_zone='B';
      
    }
    
    
      
      break;    
  }
  into->px=final->px;
  into->py=final->py;
  free(final);
  
}


/**********************************************************************
*                                      *
*            Build distance vectors                  *
*                                      *
**********************************************************************/

void get_connecting_vector (map_cell_vector* discrete_origin, map_cell_vector* discrete_destination, map_cell_vector* into) {

  int first=1;
  XY_Coord *cartesian_origin=(XY_Coord *) malloc (sizeof (XY_Coord));
  XY_Coord *cartesian_destination=(XY_Coord *) malloc (sizeof (XY_Coord));
  float inc_x, inc_y, angle, distance;
  int counter1=0,counter2=0;
  map_cell_vector *actual_discrete=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  map_cell_vector *next_discrete=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  map_cell_vector *ptr1=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  map_cell_vector *ptr2;
//   map_cell_vector *ptr2=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  
  into->px=discrete_origin->px;
  into->py=discrete_origin->py;
//   into->next=ptr1;
//   ptr1=ptr2;
  get_cartesian_coordinates(discrete_origin,cartesian_origin);
  get_cartesian_coordinates(discrete_destination,cartesian_destination);  
  angle = atan2((cartesian_destination->py-cartesian_origin->py),cartesian_destination->px-cartesian_origin->px);
  inc_x=cos(angle)*radius;
  inc_y=sin(angle)*radius;
  actual_discrete->px=discrete_origin->px;
  actual_discrete->py=discrete_origin->py;
  next_discrete->px=actual_discrete->px;
  next_discrete->py=actual_discrete->py;
  
  
  distance = sqrt((cartesian_destination->px-cartesian_origin->px)*(cartesian_destination->px-cartesian_origin->px)+(cartesian_destination->py-cartesian_origin->py)*(cartesian_destination->py-cartesian_origin->py));
  while ((distance > radius) && (counter1 < 1000)) {
    if (first) {
     first=0;
     into->next=ptr1;
// printf("start\t(%d,%d) -> (%d,%d)\n",discrete_origin->px, discrete_origin->py,discrete_destination->px,discrete_destination->py);
    }
    else {
      ptr2=malloc(sizeof(map_cell_vector));
      ptr1->next=ptr2;
      ptr1=ptr2;
    }
      
    while ((actual_discrete->px == next_discrete->px) && (actual_discrete->py == next_discrete->py) && (counter2 < 5)) {
      cartesian_origin->px+=inc_x;
      cartesian_origin->py+=inc_y;
      get_discrete_coordinates(cartesian_origin,next_discrete);
      counter2++;
      
    }
    distance = sqrt((cartesian_destination->px-cartesian_origin->px)*(cartesian_destination->px-cartesian_origin->px)+(cartesian_destination->py-cartesian_origin->py)*(cartesian_destination->py-cartesian_origin->py));
    counter2=0;
    actual_discrete->px=next_discrete->px;
    actual_discrete->py=next_discrete->py;
    ptr1->px=actual_discrete->px;
    ptr1->py=actual_discrete->py;
    ptr1->distance=distance;
    ptr1->next=NULL;
//     ptr2=malloc(sizeof(map_cell_vector));
//     ptr1->next=ptr2;
//     ptr1=ptr2;
    
    
    
    counter1++;
    
    
    
    
  }
  free(cartesian_origin);
  free(cartesian_destination);
  free(actual_discrete);
  free(next_discrete);
  free(ptr2);
  
}

void get_neighbours (XY_Coord* origin, map_cell_vector* into) {
  map_cell_vector *ptr=(map_cell_vector *)malloc(sizeof(map_cell_vector));
  map_cell_vector *final=ptr;
  ptr->px=origin->px;
  ptr->py=origin->py;
  
  // first step, to the right
  map_cell_vector *ptr1=(map_cell_vector *)malloc(sizeof(map_cell_vector));
  ptr->next=ptr1;
  ptr1->px=ptr->px+1;
  ptr1->py=ptr->py;
  ptr=ptr1;
  
  //second step, upper right
  ptr1=(map_cell_vector *) malloc (sizeof(map_cell_vector));
  ptr->next=ptr1;
  if ((int)origin->py % 2) {    //odd
    ptr1->px=origin->px+1;
    ptr1->py=origin->py-1;    
  }
  else {        //even
    ptr1->px=origin->px;
    ptr1->py=origin->py-1;    
  }
  ptr=ptr1;
  
  //third step, upper left
  ptr1=malloc(sizeof(map_cell_vector));
  ptr->next=ptr1;
  ptr1->px = ptr->px -1;
  ptr1->py = ptr->py;
  ptr=ptr1;
  
  //fourth step, left
  ptr1=malloc(sizeof(map_cell_vector));
  ptr->next=ptr1;
  ptr1->px = origin->px -1;
  ptr1->py = origin->py;
  ptr=ptr1;
  
  //fifth step, lower left
  ptr1=malloc(sizeof(map_cell_vector));
  ptr->next=ptr1;
  if ((int)origin->py % 2) {    //odd
    ptr1->px=ptr->px+1;
    ptr1->py=ptr->py+1;    
  }
  else {        //even
    ptr1->px=ptr->px;
    ptr1->py=ptr->py+1;    
  }
  ptr=ptr1;
  
  //sixth step, lower right
  ptr1=malloc(sizeof(map_cell_vector));
  ptr->next=ptr1;
  ptr1->px = ptr->px+1;
  ptr1->py = ptr->py;
  ptr1->next= NULL;
  
  into->px=final->px;
  into->py=final->py;
  into->next=final->next;
  free(final);
  
}
```

---

### Post by dwhitney67 on 2010-10-04
You indicated that free_resources() is causing your app some issues; yet the call to it appears commented out.

Is there any particular reason why you placed the call to free_resources(), albeit commented out, within the for-loop?  Seems to me that it should be called only once.

---

### Post by erupter on 2010-10-05
> **dwhitney67 said:**
> You indicated that free_resources() is causing your app some issues; yet the call to it appears commented out.

Is there any particular reason why you placed the call to free_resources(), albeit commented out, within the for-loop?  Seems to me that it should be called only once.

Because i copied&pasted the code when i was doing tests and had it commented out.
But it needs to stay on.
And it needs to be run in the cycle because it's not a garbage collector. Maybe i should call it some other way to make this clear.
If you notice the main cycle calls geometric_calculations() and this function calls get_connecting_vector() once for each sonar sensor.
So assuming you run m cycles, and have n sonar sensors, you end up calling get_connecting_vector() m*n times.
And since on a map you can't know in advance the number of cells between two arbitrary other cells, i can't preassign vectors' length so get_connecting_vector() has to explicitly allocate new memory in its operation.
So each cycle I need to, once work has been done with it, free the data I acquired.
I need the first pointers of the array (namely range_vectors[i]) to remain available so to assign new vectors to them, but all the memory pointed has to be freed so a new cycle can start without loosing memory.
I hope I've made it clear, if not feel free to ask.

---

### Post by erupter on 2010-10-31
I finally found the error in all my code.
There was a wrong multiplication in a malloc call, resulting in an excess allocation that was not subsequently taken care as i wasn't expecting it.
I now use Valgrind and DDD proficiently :)
Thanks

---

