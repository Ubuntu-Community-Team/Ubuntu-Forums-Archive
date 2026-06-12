---
title: "[C] undefined symbol sleep - but I included unistd.h!"
date: 2010-03-22
forum: Programming Talk
---

### Post by linuxpenguin on 2010-03-22
Hello,
I'm doing some C code for a project.  There are two parts, a server and a client.

They're both compiling fine for me, but when I run the client, after the two exchange info I see:
```
./client: symbol lookup error: ./client: undefined symbol: sleep, version GLIBC_2.2.5
```
When I run the program in gdb there is no stack trace, and there's an exit code 0177.
If I use "catch syscall" in gdb I get this:
```
(gdb) file client
Reading symbols from /media/SPK/cs-202/Assign7/client...done.
(gdb) catch syscall
warning: Could not open "syscalls/amd64-linux.xml"
warning: Could not load the syscall XML file `syscalls/amd64-linux.xml'.
GDB will not be able to display syscall names.
Catchpoint 1 (any syscall)
(gdb) run
Starting program: /media/SPK/cs-202/Assign7/client 

Catchpoint 1 (call to syscall 12), 0x00007ffff7df4cea in ?? ()
   from /lib64/ld-linux-x86-64.so.2
(gdb) bt
#0  0x00007ffff7df4cea in ?? () from /lib64/ld-linux-x86-64.so.2
#1  0x00007ffff7df4395 in ?? () from /lib64/ld-linux-x86-64.so.2
#2  0x00007ffff7de038d in ?? () from /lib64/ld-linux-x86-64.so.2
#3  0x00007ffff7ddfaf8 in ?? () from /lib64/ld-linux-x86-64.so.2
#4  0x0000000000000001 in ?? ()
#5  0x00007fffffffe626 in ?? ()
#6  0x0000000000000000 in ?? ()
(gdb) 

```

I can't seem to figure out - what does this mean?  I did include <unistd.h> which is necessary for "sleep".

I'm on a 64-bit AMD Phenom system, with Ubuntu 9.10 - if that matters.

Any help is appreciated.  Thanks!

---

### Post by MadCow108 on 2010-03-22
are you compiling on the same machine as you are executing?
if not a version mismatch of the system libraries may be the case. ubuntu 9.10 uses glibc 2.10 and not 2.2
(or you even compile for 64 bit and run on 32 bit system or vice versa)

if impossible to fix the libraries a solution may be to statically link with libc
gcc -static file.c

---

