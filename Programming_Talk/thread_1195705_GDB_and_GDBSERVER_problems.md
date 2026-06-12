---
title: "GDB and GDBSERVER problems"
date: 2009-06-24
forum: Programming Talk
---

### Post by Hachaso on 2009-06-24
Hi!

I'm trying to debug a shared lib (.so file) on Android.
The shared lib holds the JNI code. So in other words, a Java function calls my function implemented in my shared lib.

I have managed to attach the gdbserver to the process loading my shared lib. Also connecting the gdb to the gdbserver with, "target remote localhost:1234". I'm running the application on the Android emulator.
I even manage to load the symbol file for the lib. The problem starts when I try to set a breakpoint and type "continue" on the gdb terminal.
I get this error message.

Error accessing memory address 0x5d3: Input/output error

Seems like the breakpoint is set at the address 0x5d3.
Looking at the start and end address in memory where the library is loaded I can verify that the breakpoint is not set between those addresses. I guess that this is why I get this error.
I looked up the address space using "cat /proc/<PID of Process>/maps"

If this is the case, how can I make sure that the breakpoint is set inside the address space of the loaded library??
Maybe with some offset? But how ?

Thanks!

---

