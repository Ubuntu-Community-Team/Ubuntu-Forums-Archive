---
title: "Help me in understanding this macro"
date: 2009-06-26
forum: Programming Talk
---

### Post by Rij on 2009-06-26
```

#define MY_DEBUG(format, args...) syslog (LOG_INFO, format, ##args)

```

This is my understanding:
MY_DEBUG is a macro that accepts a format string and variable number of arguments. It prints "##args" according to format in syslog. 

What is ##args? Is it number of arguments?

---

### Post by Zugzwang on 2009-06-26
See: [http://en.lmgtfy.com/?q=c+macro+variable+arguments](http://en.lmgtfy.com/?q=c+macro+variable+arguments)

---

