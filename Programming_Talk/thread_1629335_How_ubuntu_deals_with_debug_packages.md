---
title: "How ubuntu deals with debug packages"
date: 2010-11-23
forum: Programming Talk
---

### Post by sroberts82 on 2010-11-23
Hi,
I have a few questions about how ubuntu handles debug packages. This may not all be specific to ubuntu but I suspect some of it might.

So, I have my C hello world and I want to debug libc. I install the libc6-dbg and it puts some files into /usr/lib/debug/lib. So I fire up gdb on my hello world, try and step into printf, and it mathces the symbol but not the source. So I do info source, and it tells me it should be in /build/buildd/somewhere.... So I get the source from aptitude and put it there and then I am debugging libc. Great. It all works, but I would like to understand how.

1. How does gdb know to use the libc from the debug dir. ldd gives me:
```
$ ldd a.out 
        linux-gate.so.1 =>  (0x0069b000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00360000)
        /lib/ld-linux.so.2 (0x00dcc000)
```
(where it gets lib tls from is also something of a mystery)
Is gdb, or ubuntus flavour of gdb, look in /usr/lib/debug first by default? When it's loading the symbols, does it scan the debug dir for those 3 libraries above, in this case just finding libc? What is the convention for this?

2. The source path. Is there a better way to do it than creating a /build/buildd/... folder? Can I get it to look somewhere in my home dir? I may not always be admin. 

Thanks in advance,
Stephen

---

