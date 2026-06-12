---
title: "[SOLVED] what is the &amp;quot;core-flag&amp;quot;"
date: 2008-03-30
forum: Programming Talk
---

### Post by DJTurboToJo on 2008-03-30
Hey Community,

when a process terminates it normally gives a termination status.
The status is a two byte integer. If the process was terminated by a signal the first byte is 0x00 and the second one is the signal number + (mostly the high-end bit) the core-flag.

What is this core-flag indicating? Has this something to do with writing a core file?

Thanks in advance
TurboToJo

---

### Post by PaulFr on 2008-04-01
**[http://www.gnu.org/software/libc/manual/html_node/Process-Completion-Status.html](http://www.gnu.org/software/libc/manual/html_node/Process-Completion-Status.html)** indicates the valid macros you can use for the termination status return by the waitXXX calls. See **WCOREDUMP** - if the process termination was accompanied by the writing of a core file, this will be true.

---

