---
title: "kernel message unreadable with printk()"
date: 2007-12-12
forum: Programming Talk
---

### Post by RaistlinU on 2007-12-12
I defined the state() function as below: 
#define state(format, arg...) \
{ \
printk(KERN_ERR "SCI: " format "\n" , ## arg); \
}

Running on this newly compiled kernel ( with a few files I added in), in most functions it works well, I can see the kernel message correctly. However, in one function, it returns unreadable message, as below:

> Dec 13 11:11:02 raistlin710 kernel: nrs]    _0ic9>reI.0111dtaS22oi _58[i p  7<_rssC6( iii] lrrao9>cs_ 8<,_S92lg3 _0ic7>reI...............)dtaS9nni _1 tt ps53  rcI.0iiee 2rhhdi9[eaa_ 8<,__2lgsss] uciiiic5>reeeI.)dtii 2oi  _3 tr  snl93srrrrrrrrrrrrrrsI...)dtaS22oi _7[[i ps23 sC67 i] l di3[ea:3
Dec 13 11:11:02 raistlin710 kernel: 
Dec 13 11:11:02 raistlin710 last message repeated 48 times
Dec 13 11:11:02 raistlin710 kernel: ssssssssssssssssssssssssssssssssssss

Any idea about this error? Thank you.

---

