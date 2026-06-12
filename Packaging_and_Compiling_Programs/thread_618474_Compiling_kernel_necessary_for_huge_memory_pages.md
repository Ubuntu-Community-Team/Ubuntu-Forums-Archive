---
title: "Compiling kernel necessary for huge memory pages?"
date: 2007-11-20
forum: Packaging and Compiling Programs
---

### Post by misja on 2007-11-20
I have a (Java) application that uses a lot of memory. Now I have read that such an application can benefit from using large (huge) memory pages.
However for all I can see, my Gutsy 64 does not have huge pages support. I found the Linux documentation (vm/hugetlbpage.txt) about this and it said compiling the Linux kernel with the setting CONFIG_HUGETLB_PAGE was necessary.

I have never compiled a kernel before so I would like to skip this step if it isn't necessary. So am I right that Gutsy does not support huge (like 2MB) memory pages?

---

