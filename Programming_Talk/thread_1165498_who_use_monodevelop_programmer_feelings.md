---
title: "who use monodevelop: programmer feelings"
date: 2009-05-20
forum: Programming Talk
---

### Post by fr4nko on 2009-05-20
Hi all,

I was wondering if anyone is really using monodevelop and, more generally mono tools, on linux.

I particular I was wondering about the actual performance of the framework: is it memory demanding and bloated like Java ? Is there any real added values in using the mono tools ?

From my point of view I'm more oriented toward Python and OCaml for high level programming and to C for low level / highly optimized code so I tend to avoid tools like Mono but I would like to have some feeling from other linux programmers.

Francesco

---

### Post by directhex on 2009-05-20
Mono is *MUCH* more RAM-efficient than Java, for various reasons - RAM consumption compared to a C app is measured in percentage points, not orders of magnitude. The GC is worse though, so apps which do a LOT of object destruction are likely to be slower than Java equivalents.

Both Java and Mono are, however, orders of magnitude faster than Python at raw performance - for what it matters to you.

---

