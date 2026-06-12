---
title: "Python: Read/Write memory of another process"
date: 2009-08-05
forum: Programming Talk
---

### Post by tom66 on 2009-08-05
I need an easy way to read and write the memory of another process, from Python. Does anyone know if this is possible and how it could be done?

Btw, I've tried python-ptrace, but ReadBytes throws exceptions.

---

### Post by CptPicard on 2009-08-05
[http://en.wikipedia.org/wiki/Memory_protection](http://en.wikipedia.org/wiki/Memory_protection)  ;)

---

### Post by CatsRninja on 2009-08-05
I had the same doubt, but it was with C.
if you alter the kernel and disable the memory protection, you can write to any place.

Edit:

i think you can read write, if you make that process run in a controled envyroment, like a debugger that permits itself to write on its own memory.Dunno.

---

### Post by stroyan on 2009-08-05
Have a look at the python-ptrace package.
See [http://freshmeat.net/projects/python-ptrace/](http://freshmeat.net/projects/python-ptrace/) for more about it.
It provides peak and poke operations to access the memory of a process that is attached to using the ptrace system calls.

---

### Post by tom66 on 2009-08-05
I know about memory protection. Which doesn't make it easy to access another processes' memory. However, it can be done: For example, Windows supports ReadProcessMemory and WriteProcessMemory if you are the Admin on the machine. ptrace is the equiv. on Linux, if you have root permissions, but I don't know how to get it working with Python (using python-ptrace). It just throws exceptions:

```

(--) Importing ptrace...
(--) Importing psyco...
(--) Creating process debugger...
(--) Creating process tracer...
(--) Attempting to get PID...
(--) Got PID: 18652
(--) OK, now going to look at registers...
(--) Common registers for PID 18652:
(--)    EIP = 0xB8099430
(--)    ESP = 0xBFF928F4
(--)    EAX = 0xFFFFFE00
(--)    EDX = 0x00000001
(--)    EBX = 0x0000000B
(--)    ESI = 0x00000001
(--)    ECX = 0xBFF9295B
(--) Examining data...
Traceback (most recent call last):
  File "readproc.py", line 70, in <module>
    print_debug(tracer.readBytes(4, 4))
  File "/var/lib/python-support/python2.5/ptrace/debugger/process.py", line 562, in readBytes
    formatAddress(address), size, err))
ptrace.debugger.process_error.ProcessError: readBytes(0x00000004, 4) error: [Errno 5] Input/output error

```

I am running this script as sudo.

I can access the process - If I change EAX, EIP or ESP I can crash or freeze the application. Which could be good or bad, but at least I can influence it.

Some processes support /proc/PID/mem (where PID is a process ID number) which allows access to the memory. But not all applications do, in particular, Java, which I'm trying to modify on the fly...

---

### Post by tom66 on 2009-08-06
Just checking if anyone has a solution... Thanks

---

