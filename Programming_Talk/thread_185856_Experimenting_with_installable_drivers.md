---
title: "Experimenting with installable drivers"
date: 2006-06-01
forum: Programming Talk
---

### Post by stolu on 2006-06-01
Hi,

I am an experienced programmer but fairly new to linux. I would like to experiment with installable drivers. I installed gcc and I can compile and run a simple "hello world" app. However, when I tried compiling a hello world installable driver example, the compiler fails with errors found in <linux/module.h>. I have read that from linux-2.6.xx onwards, you have to be running the same kernel as the source headers that you include. So I firstly need to find out how to establish what version my current kernel is (installed ubuntu V 5.1), and then I need to get hold of the corresponding source files. Can someone help ?

Thanks
-stolu

---

### Post by johnc4510 on 2006-06-01
You can find out the name of your current kernel by typing in terminal:
uname -r

---

