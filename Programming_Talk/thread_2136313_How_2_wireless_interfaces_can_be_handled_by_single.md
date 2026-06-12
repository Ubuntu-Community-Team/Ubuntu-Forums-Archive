---
title: "How 2 wireless interfaces can be handled by single device driver module"
date: 2013-04-17
forum: Programming Talk
---

### Post by ymsaputra on 2013-04-17
Dear All,

I want to understand the performance of one device driver module in  linux kernel. In this case I use carl9170 device driver in linux.

1. If I use two physical interfaces, how can the single module carl9170 handle 2 different physical interfaces? 

    Because so far, I have known that these 2 physical interfaces will  make 2 instances and use different packet buffers for each but just  using single carl9170 module. So it's confusing me.

2. And which file in linux kernel source code can I find about this handling method?


Thank you very much for your help

---

