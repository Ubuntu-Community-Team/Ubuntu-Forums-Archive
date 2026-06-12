---
title: "swap?"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Yezinki on 2012-11-01
Hi,

Despite ample physical memory free, 7.6 MiB of 4 GiB of swap is being used, no big deal but a hypothetical question........any ideas?

Thanks.

---

### Post by HiImTye on 2012-11-01
occasionally I'll use some miniscule amount of swap as well, even when my physical memory is nowhere near full. it's likely a combination of how *vm.swappiness* works and disk caching. there's no reason to be alarmed by it

---

### Post by Yezinki on 2012-11-01
Thanks HiImTye for your expert opinion.

Previously swap was never used on my machine, do you feel that i should increase it by 1 GiB?

This 7.6 MiB is being used when 700 MiB of physical memory is being used.

Thanks anyways.

---

### Post by HiImTye on 2012-11-01
everyones' swap needs are  different. the rule of thumb is that you want it to be more than your  physical memory, in case you have a crash, so that you can write-out  without running into 'out of memory' errors, or for hibernation. if you  never go anywhere near your physical memory limit, that is obviously not  necessary. swap is used as a buffer to protect from crashes due to  memory limits, as well as a place to store data for hibernation, etc. it  all depends on your usage. I typically never touch my swap, save for a  few MiB here and there for whatever reason, but I make sure that it is  there just in case I run into that time that I need it. some people like  setting *vm.swappiness=0*. it all depends on how comfortable you feel with whatever amount of swap you have.

---

### Post by Yezinki on 2012-11-01
Thanks HiImTye for the in depth reply!

---

