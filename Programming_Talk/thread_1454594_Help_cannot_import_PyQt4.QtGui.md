---
title: "Help cannot import PyQt4.QtGui"
date: 2010-04-14
forum: Programming Talk
---

### Post by xaegis on 2010-04-14
I'm using python 3.1 and whenever I try to run this code
```

import sys
import time
from PyQt4.QtCore import *
from PyQt4.QtGui import *

```

If I run it in IDLE it works fine but when executed from within my IDE (Geany 0.18 ) or from the terminal it says that:
```
ImportError: No module named PyQT4.QtCore
```
Does anyone have any idea how I can fix this problem?
Is it something in my environment variables?
Thanks,
:)

---

### Post by xaegis on 2010-04-15
So apparently everything works fine if i use python 2.6 (from idle or the Terminal) but python 3 refuses to handle calls to Wx, or Qt.

Is there any way to allow the Script Geany uses to access the modules or Python3?
Suggestions would be helpful.

Thanks

So I realized as I was typing that, that I changed the execute argument to read "python3 "%f" " so I altered that and geany works wonderfully even if my shebang is : "#!/usr/bin/env python3"

So Basically I'd like to thank "ME" for all my help on this issue!!!!

Can anyone confirm that this is a bug in python3.1?

Aaaanndddd... If anyone could explain why it works this way they could get extra cool points!!!

8)

---

