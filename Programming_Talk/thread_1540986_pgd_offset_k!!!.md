---
title: "pgd_offset_k!!!"
date: 2010-07-28
forum: Programming Talk
---

### Post by interval1066 on 2010-07-28
Wrote a simple kernel driver a few years ago for 2.6.1xxx whatever. Or its might have been 2.6.2something. Well, here we are at 2.6.32 w/lucid so I decided to compile this one driver to see if it needed a refresh. Why yes, it does. It seems that the api "pgd_offset_k" which we used to use for access to kernel mapped memory is deprecated. Ok, no problem; except I can't figure out what the new way of doing things is! The def of this function is here, as far as I can see:

[http://lxr.free-electrons.com/source/arch/x86/include/asm/pgtable.h?v=2.6.32](http://lxr.free-electrons.com/source/arch/x86/include/asm/pgtable.h?v=2.6.32)

Yet there's no note regarding the func's deprecation or replacement or anything! This is really frustrating. Can anyone shed some light on what I'm supposed to use in its place?

---

