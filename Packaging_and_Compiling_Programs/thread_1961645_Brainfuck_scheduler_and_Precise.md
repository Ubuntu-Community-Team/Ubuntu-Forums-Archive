---
title: "Brainfuck scheduler and Precise"
date: 2012-04-19
forum: Packaging and Compiling Programs
---

### Post by the-oggy on 2012-04-19
Hi,

I've compiled custom kernel for precise with Brainfuck scheduler patch because default CFQ was rendering system totally unresponsive when copying or moving large amount of data. Now, in menuconfig there is enabled option BFS scheduler but when I install compiled kernel i still reports cfq as enabled scheduler without mentioning BFS even as an option. Why is this the case? However, I did notice that the system is noticeably snappier with custom kernel under the same load as previous kernel.

Thanks

---

### Post by oldos2er on 2012-04-19
Moved to Packaging and Compiling Programs.

---

