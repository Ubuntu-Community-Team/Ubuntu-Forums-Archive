---
title: "latest mono debugger"
date: 2006-01-07
forum: Programming Talk
---

### Post by dave84 on 2006-01-07
i tried to compile the latest mono-debugger (svn-checkout), but it throwing the following message:
```
wrapper.o: In function `debugger_run_finally':
/home/david/debugger/wrapper/wrapper.c:177: undefined reference to `mono_debugge r_run_finally'
wrapper.o:(.data+0x18): undefined reference to `mono_trampoline_code'
collect2: ld returned 1 exit status

```

i did some research, but i found no solution.
has s.b an idea?

ps: this debugger should work with x-develop for debugging mono-code the graphical way. wouldn't that be great?

---

