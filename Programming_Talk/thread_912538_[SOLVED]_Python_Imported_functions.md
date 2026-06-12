---
title: "[SOLVED] Python Imported functions"
date: 2008-09-06
forum: Programming Talk
---

### Post by kjohansen on 2008-09-06
I did:

```

import scipy.stats
a=[2,3,5,2,3,2,3]
scipy.stats.mean(a)

```

Is there a way to not have to use the full path for the mean function?

That is can I import scipy.stats and then just do:
```

mean(a)

```

---

### Post by imdano on 2008-09-06
Yep [php]from scipy.stats import mean[/php]

---

### Post by kjohansen on 2008-09-06
what if I want all the functions within the scipy.stats package to be available like that, is that possible?

---

### Post by kjohansen on 2008-09-06
nevermind.

from scipy.stats import *

---

### Post by OutOfReach on 2008-09-06
```
from MODULE_NAME import *
```

---

### Post by pmasiar on 2008-09-06
> **kjohansen said:**
> what if I want all the functions within the scipy.stats package to be available like that, is that possible?

import * is dangerous practice: you may import name clashing with your own name, and strange things might happen. Much safer to import name by name (you can list them, separated by comma), to see exactly what is coning from where. Easier to debug later, too.

---

