---
title: "Best File Compression Libary"
date: 2008-04-18
forum: Programming Talk
---

### Post by JupiterV2 on 2008-04-18
After a quick couple searches through the Ubuntu forums I couldn't find an answer to the following question:

What is the best file compression library to use in C++? I know there is gzstream and boost which act as wrappers for zlib c bindings. What is the general preference? Is there a better one yet?

The task is to compress an xml or text based file which acts as a dictionary for my program.

---

### Post by mike_g on 2008-04-18
It depends on what you want. The most effective compression algos tend to take a long time to decompress.  I havent done any of this stuff with C++, but I expect anything fast and simple should do as dictionaries arent all that big. Apart from that I wouldent worry about the details too much. Maybe I'm just reckless.

---

