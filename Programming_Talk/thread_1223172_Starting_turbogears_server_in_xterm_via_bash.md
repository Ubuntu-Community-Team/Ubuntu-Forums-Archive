---
title: "Starting turbogears server in xterm via bash"
date: 2009-07-25
forum: Programming Talk
---

### Post by Bios Element on 2009-07-25
So I've been hacking away and this is the best I've came up with so far. Granted it doesn't work. I'm hoping someone who knows shell a tad better then me can help out. I just need it to stay open while the server runs.

```
#!/bin/sh

cd /home/william/Workspace
source tg2env/bin/activate
cd BiosRPG
paster serve development.ini
```

---

