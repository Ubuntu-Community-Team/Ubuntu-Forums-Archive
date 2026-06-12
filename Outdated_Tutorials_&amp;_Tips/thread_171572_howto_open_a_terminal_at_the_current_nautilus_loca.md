---
title: "howto open a terminal at the current nautilus location"
date: 2006-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Melciah on 2006-05-06
This is a mind numbingly simple script to open a terminal at the current nautilus location. It's helped me a bit, so I thought I would share it.

```

cd .gnome2/nautilus-scripts/
touch cd-terminal.sh
chmod 755 cd-terminal.sh
gedit cd-terminal.sh

```

add this to the file:

```

#!/bin/bash
gnome-terminal --working-directory=%f

```

Save and exit.

This script will now appear when you right-click, under scripts. I hope this is useful for you.

---

### Post by manicka on 2006-05-06
You can also achieve this by installing nautilus-open-terminal

```
sudo apt-get install nautilus-open-terminal
```

---

### Post by Melciah on 2006-05-08
thanks for the heads up. both methods achive the same thing, but I must admit, the nautilus-open-terminal package is much prettier.

---

