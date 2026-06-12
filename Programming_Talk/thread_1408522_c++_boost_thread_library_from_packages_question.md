---
title: "c++ boost thread library from packages question"
date: 2010-02-16
forum: Programming Talk
---

### Post by daweefolk on 2010-02-16
I installed the boost thread library from the package manager and I'm wondering if I'd use the same code to include it in my c++ program as the examples i found:
```
#include <boost/thread.hpp>
```

---

### Post by dwhitney67 on 2010-02-16
EDIT:  You are correct  (Bad info.... The correct include path is <boost/thread/thread.hpp>.)

You will also need to link with libboost_thread-mt.so.
```

g++ your_app.cpp -lboost_thread-mt

```

---

