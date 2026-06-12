---
title: "custom filter is not working on client's system?"
date: 2012-05-28
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-05-28
Hi Experts,

I am working on to develop cups printer driver for a 24-pin DMP.
I have created a custom filter from the code of rastertoepson filter. I have done some additions in the rastertoepson code, compiled and output filter created with a different name like 'myfilter'.
Now, when i am trying to use this filter on client's machine, it is giving some error or not printing at all. 
I have googled but not found anything relevant.
Please guide me what may be the problem?
Is there any filter registration process? if yes then how to do this?

Thanks in advance.

---

### Post by pbrane on 2012-05-28
I am not that familiar with CUPS programming. Did you compile this filter on the clients machine? If not are you sure that machine has the same libraries and is the same architecture?

Have you looked at the CUPS documentation? You can find this at **[http://localhost:631](http://localhost:631)** on your or the clients machine.

Perhaps posting the error messages would help.

---

### Post by Gurmeet Singh on 2012-05-28
Thanks pbrane.

> I am not that familiar with CUPS programming. Did you compile this  filter on the clients machine? If not are you sure that machine has the  same libraries and is the same architecture?Machine has same architecture that is 32 bit. kernel version on both side is 2.x.x -x but not exactly same.
cups version is 1.4.2 on client side and 1.5.0 on my side but i have compiled 1.4.2 source file of rastertoepson filter.

> Have you looked at the CUPS documentation? You can find this at **[http://localhost:631]("http://localhost:631/")** on your or the clients machine.

Perhaps posting the error messages would help.     error received is "scheduler could not execute the filter". snapshot for the same has been attached.

Thanks in advance.

---

