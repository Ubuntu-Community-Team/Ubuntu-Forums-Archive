---
title: "Linux Kernel License Question: Do we need to also open InitRamFS image"
date: 2019-03-11
forum: Programming Talk
---

### Post by Robin_Hsu on 2019-03-11
Since InitRamFS is compiled with the Linux kernel, the question is:
    
  Can we keep InitRamFS close-sourced? or even close-binary? 

We know if we modify the kernel, we need to open the source.
Our InitRamFS contains sole non-modified open-source binaries, plus our own proprietary software binaries.
Is it OK to make it close-source, or even close-binary (encrypted kernel + InitRamFS, so virtually the binary is closed)?

---

### Post by TheFu on 2019-03-11
Speak with a lawyer to get legal advice, especially in a business.  Find one familiar with the GPLv2.  That's the license that matters for the kernel. Nobody here is qualified to provide any advice for the specific situation based on 5 sentences.  Further, each jurisdiction can have slightly different interpretations of any license.

Talk to a lawyer who you are paying.  The payment part is very important too.

---

