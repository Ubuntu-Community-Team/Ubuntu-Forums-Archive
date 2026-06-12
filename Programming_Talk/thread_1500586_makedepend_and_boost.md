---
title: "makedepend and boost"
date: 2010-06-03
forum: Programming Talk
---

### Post by sharpdust on 2010-06-03
I am trying to include boost in my project.

```
#include <boost/xpressive/xpressive.hpp>
```

However when running makedepend over my project, it looks at that line and then starts looking in the xpressive.hpp file to build dependencies there.
This takes way too long to do. Is there a way to prevent makedepend from doing this?

---

