---
title: "Repeative Mouse clicks."
date: 2008-10-11
forum: New to Ubuntu
---

### Post by RedNikon on 2008-10-11
Any program or script out there that can make my mouse click in one location every five minutes or so? Or perhaps you could teach me how to do something like this. Thanks in advance.

---

### Post by jamesrl on 2008-10-11
First install xautomation
```
sudo apt-get install xautomation
```
then look up "man xte"
and have commands in a script like 
```

xte 'mousemove 500 400'
xte 'mouseclick 1'

```
in whatever kinda script you prefer.
E.g., within bash
```

#!/bin/bash

while true; do
xte 'mousemove 500 400'
xte 'mouseclick 1'
sleep 300  ## pause for 300s=5 min
done

```

---

