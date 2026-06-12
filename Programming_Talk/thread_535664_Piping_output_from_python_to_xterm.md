---
title: "Piping output from python to xterm"
date: 2007-08-26
forum: Programming Talk
---

### Post by Acglaphotis on 2007-08-26
Hi

How would you pipe the output of wget from python to an xterm (or any terminal emulator)?

Thanks!

---

### Post by strider1551 on 2007-08-26
I think this will do it for you.

```

import subprocess
process = subprocess.Popen("command", shell=True, stdout=subprocess.PIPE, bufsize=0)
line = process.stdout.readline()
while line:
    print line
    line = process.stdout.readline()

```

---

### Post by Acglaphotis on 2007-08-26
Thanks!

---

