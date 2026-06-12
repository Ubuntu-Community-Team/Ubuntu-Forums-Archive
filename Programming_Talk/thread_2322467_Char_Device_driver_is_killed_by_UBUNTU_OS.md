---
title: "Char Device driver is killed by UBUNTU OS"
date: 2016-04-28
forum: Programming Talk
---

### Post by Guy_Zur on 2016-04-28
Hello,

I am learning how to develop device drivers for ubuntu. I've followed this guide - [http://derekmolloy.ie/writing-a-linux-kernel-module-part-2-a-character-device/](http://derekmolloy.ie/writing-a-linux-kernel-module-part-2-a-character-device/)
Compile goes well and insmod succeeds as well. But when I execute it (on ubuntu only) the user application is killed by the OS while executing the write function.
uname -r: 4.4.0-21-generic

Attached strace of the test application

I am really have no idea what is wrong - since on other distributions it works fine.

```
execve("./test", ["./test"], [/* 32 vars */]) = 0
brk(NULL)                               = 0xbc2000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fdb27ee0000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=96527, ...}) = 0
mmap(NULL, 96527, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fdb27ec8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\t\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1864888, ...}) = 0
mmap(NULL, 3967488, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fdb278f4000
mprotect(0x7fdb27ab4000, 2093056, PROT_NONE) = 0
mmap(0x7fdb27cb3000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1bf000) = 0x7fdb27cb3000
mmap(0x7fdb27cb9000, 14848, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fdb27cb9000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fdb27ec7000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fdb27ec6000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fdb27ec5000
arch_prctl(ARCH_SET_FS, 0x7fdb27ec6700) = 0
mprotect(0x7fdb27cb3000, 16384, PROT_READ) = 0
mprotect(0x600000, 4096, PROT_READ)     = 0
mprotect(0x7fdb27ee2000, 4096, PROT_READ) = 0
munmap(0x7fdb27ec8000, 96527)           = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 17), ...}) = 0
brk(NULL)                               = 0xbc2000
brk(0xbe3000)                           = 0xbe3000
write(1, "Starting device test code exampl"..., 37Starting device test code example...
) = 37
open("/dev/ebbchar", O_RDWR)            = 3
write(1, "Type in a short string to send t"..., 53Type in a short string to send to the kernel module:
) = 53
fstat(0, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 17), ...}) = 0
read(0, testing
"testing\n", 1024)              = 8
write(1, "Writing message to the device [t"..., 41Writing message to the device [testing].
) = 41
write(3, "testing", 7 <unfinished ...>
+++ killed by SIGKILL +++
Killed



```

Thanks,
Guy

---

### Post by jyang772 on 2016-05-11
You should never directly dereference a pointer from user space. 
Use the function copy_from_user() in your write() function.

---

