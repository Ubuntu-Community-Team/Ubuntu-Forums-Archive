---
title: "64 bit windows debuggers running under WINE"
date: 2017-09-18
forum: Programming Talk
---

### Post by mark allyn on 2017-09-18
Hello,

I posted something quite similar to this on the WINE ubuntu sub-forum and got exactly 0 replies.  So, here I am ...

I am using 64 bit Wine under ubuntu 16.04.  It works fine.  I happen to be writing assembly language programs, but this is a more general question applicable to any language running win pe's.  Namely, is there a 64-bit debugger that would handle win-64 executables.  Ollydbg came to mind, but there is no release version as far as I can tell.  Anything else?

Thanks,
Mark Allyn

---

### Post by mihaitodor on 2017-11-23
Hi Mark,

Please have a look at this thread for advice on how to use the Wine debugger (winedbg) for x64 apps: [https://bugs.winehq.org/show_bug.cgi?id=44018](https://bugs.winehq.org/show_bug.cgi?id=44018) Basically, running `wine64 winedbg myapp.exe` should let you do some rudimentary debugging (no symbol support for x64 apps yet).

Hope this helps.

Regards,
Mihai

---

