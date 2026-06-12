---
title: "Some basic help with ptrace"
date: 2008-10-23
forum: Programming Talk
---

### Post by nigelenki on 2008-10-23
I'm thinking of toying with ptrace() and I'm wondering about its limitations.  I specifically want to ptrace() literally anything and have my process pick up all syscalls and soft interrupts.  I think a userspace jail implementation is a good start.  It will only attach to processes it created via exec().

Some basic questions:

[list]
[*]Can I pick up interrupts?
[*]Can I catch fork() and implement my own version?
[*]How do I trace a program that's executing multiple threads?
[/list]

What I'm considering, for fun, is writing a microkernel that uses Linux as its ABI interface and driver core.  The overall structure will be as follows (stripped down):

[list]
[*]Core 'kernel' is the core program
[*]File I/O 'service' handles open(), write(), read(), close(), etc
[*]Socket I/O 'service' handles socket calls
[*]File system 'driver' is called by File I/O service, and simply uses Linux's file system structure and some controls (i.e. jail the programs in a directory)
[/list]

This is structured as an OS but it'll basically aim to behave as a jail.  I'll have it read a configuration file that details 'devices' for disks, and intercept i.e. 'mount /dev/hda2 /home' as "redirect writes to path /home into path /home/joe/jail/1/home" and other such magic.  I'll also have it manage the process list (as it will be the direct parent of all processes), mapping real PIDs to virtual.

It will be written as a microkernel with a small library for message passing.  In implementation, it'll link as a monolithic program.

Interesting directions I could go would include backing the File I/O service with an actual file system driver, i.e. writing to a disk image in a file.

At this point I'm only brainstorming.  It's mostly academic.

---

