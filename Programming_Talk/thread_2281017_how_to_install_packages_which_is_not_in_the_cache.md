---
title: "how to install packages which is not in the cache"
date: 2015-06-03
forum: Programming Talk
---

### Post by wisdom2 on 2015-06-03
Hello, i install packages in my application using python apt. Some example:

```

import cache
cache = apt.Cache.cache()
pkg = cache["brukkon"]
pkg.mark_install()
cache.commit()

```

In this example, brukkon is not in the cache, hence this package cannot be downloaded. Also no available icon exists for this package.In ubuntu software center, this package is seen proprietary, and its cost is 7 dollar. However, package's information can be seen in ubuntu software center. But how? How can i access proprietary package's informations although these packages is not in  cache?

Also, some of these proprietary packages are no cost. But in order to install these packages you need to click buy button, then login with your ubuntu one account. One example package is **senetonline**. This package too is not in cache. Thus i can neither install it nor access the package's details with python apt.

With these reasons i can only use packages which exists in cache. How can i use other packages in my app?

Thanks in advance.

---

### Post by ian-weisser on 2015-06-04
> **wisdom2 said:**
> In this example, brukkon is not in the cache, hence this package cannot be downloaded. Also no available icon exists for this package.In ubuntu software center, this package is seen proprietary, and its cost is 7 dollar. However, package's information can be seen in ubuntu software center. But how?

You are right - paid software (and zero-cost paid software) is not in the apt cache.
Software Center uses more sources of information than the apt cache.


> **wisdom2 said:**
> How can i access proprietary package's informations although these packages is not in  cache?
Do not, unless you have a signed agreement with Canonical to access and use that data.
Paid software developers agreed to let Canonical distribute their software and collect the revenue for them.
Those developers did not agree to let your company do that. You don't have the right to redistribute their software.


> **wisdom2 said:**
> Also, some of these proprietary packages are no cost.
Cost is not relevant. You don't have the right to redistribute someone else's proprietary software.
That would make your company a thief, cursed by other developers and legitimate software companies.
Why would you wish to be a part of a criminal organization?

---

