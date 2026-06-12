---
title: "Ubuntu script help."
date: 2008-09-04
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-09-04
I need a script that will use "metacity --replace" if compiz is running or "compiz --replace" if metacity is running.

If someone would be that kind to post one.

---

### Post by hyper_ch on 2008-09-04
how about:

```

#!/bin/bash

DEFERRED=metacity

if [ -n `ps -e | grep $DEFERRED ]; then
    compiz --replace
else
    metacity --replace
fi

```

---

