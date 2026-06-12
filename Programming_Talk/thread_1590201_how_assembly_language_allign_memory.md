---
title: "how assembly language allign memory?"
date: 2010-10-07
forum: Programming Talk
---

### Post by piyush.neo on 2010-10-07
I came across this snippet on wiki to align memory. I am not able to figure out how its working. I know basic assembly language....
```
#if defined(__GNUC__)
# if defined(__i386__)
    /* Enable Alignment Checking on x86 */
    __asm__("pushf\norl $0x40000,(%esp)\npopf");
# elif defined(__x86_64__) 
     /* Enable Alignment Checking on x86_64 */
    __asm__("pushf\norl $0x40000,(%rsp)\npopf");
# endif
#endif


```

---

