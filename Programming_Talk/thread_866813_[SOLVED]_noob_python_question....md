---
title: "[SOLVED] noob python question..."
date: 2008-07-22
forum: Programming Talk
---

### Post by rlameiro on 2008-07-22
Hi everyone, I think that it is a noob question, but how can I know who is the user that runs the script? the idea is to save a file to the /home/user folder. 

thanks

---

### Post by unutbu on 2008-07-22
```
#!/usr/bin/env python

import os
print os.environ['USER']
print os.environ['HOME']
```

---

### Post by rlameiro on 2008-07-22
Thanks unutbu :) I told it was a noob question....

---

