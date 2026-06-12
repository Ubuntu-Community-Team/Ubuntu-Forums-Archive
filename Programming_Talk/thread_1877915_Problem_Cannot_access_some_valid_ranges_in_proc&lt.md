---
title: "Problem: Cannot access some valid ranges in /proc/&lt;pid&gt;/mem"
date: 2011-11-08
forum: Programming Talk
---

### Post by voidlogic on 2011-11-08
Hey Everyone,

I am having a problem accessing /proc/<pid>/mem ranges after mprotect has made them readable.

[LIST=1]
[*]Process A ptrace ATTACHs to process B
[*]Process A cannot access of a given range in process Bs /proc/<pid>/mem due to the associated mapping (as visible in /proc/<pid>/maps) being non-readable
[*]Process A requests process B use mprotect to mark given mapping as readable (mprotect returns success)
[*]Process A now should be able to read the range (as visible in /proc/<pid>/mem) but can only read part of the range...
[/LIST]

Example:

```
Mapping Before Request (Step 3):
7f63671af000-7f63673ae000 ---p 0000c000 08:01 269062     /lib/x86_64-linux-gnu/libnss_files-2.13.so
Mapping After Request (Step 3):
7f63671af000-7f63673ae000 r--p 0000c000 08:01 269062     /lib/x86_64-linux-gnu/libnss_files-2.13.so
```

Problem: std::ifstream can read a first part of the range from /proc/<pid>/mem, but cannot read the remaining range data. (By cannot read I mean !fin.good and errno = 5)

```
Mapping Range:             7f63671af000-7f63673ae000 (2044 Kbytes)
Successfully Read Range:   7f63671af000-7f63671affff (4095 bytes, ~one page)
Unsuccessfully Read Range: 7f63671b0000-7f63673ae000 (2040 Kbytes)
```

I do not believe the error is related to procfs because if rather than reading /proc/<pid>/mem, I attempt to access the data word by word using PTRACE_PEEKTEXT, the result is still failure on the same boundaries.

I have also tried calling mprotect again on just the trouble region with no change.

Any ideas or hints on what I might be doing wrong would be great! Or- is it a possibly a bug? Let me know if there is any further information I can provide.

---

### Post by voidlogic on 2011-11-13
Bump? :confused:

---

