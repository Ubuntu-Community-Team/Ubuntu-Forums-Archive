---
title: "Restoring old version of libc? RPC does not run properly"
date: 2008-11-24
forum: Programming Talk
---

### Post by gogetadbl on 2008-11-24
I recently clicked on the upgrade manager and upgraded all my libraries...but I do not remember which ones they all were.  Well, doing this upgrade wouldn't let me run any of the new RPC stuff I'm doing.  I'm not 100% sure its the upgrade though, but none of my old code works if I recompile.

I'm getting errors like this on the server side:
*** glibc detected *** ./server: munmap_chunk(): invalid pointer: 0x0804d848 ***

======= Backtrace: =========

/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7e8b92b]

And on the client side 
Error is localhost: RPC: Unable to receive; errno = Connection reset by peer


When I remove libc6-dev, then it gets rid of gcc and build essential and I can't get them back

---

