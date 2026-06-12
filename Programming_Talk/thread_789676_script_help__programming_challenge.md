---
title: "script help / programming challenge"
date: 2008-05-10
forum: Programming Talk
---

### Post by tattrat on 2008-05-10
I have manged to add a script to me right click menu for "open as root"
but now I want to add a script which will take the select file(s) and/or folder(s) and will wrap them in a new folder.

Any help would be appreciated; always ending up with a scruffy desktop, such an option would be a boon.

Cheers,

Brendan

Thanks will go to the most elegant solution!

---

### Post by yaaarrrgg on 2008-05-10
Would this work?

```

#!/bin/sh
mv $@ new_folder

```

---

### Post by Wybiral on 2008-05-11
Typical response to people asking for free work:

1. Learn a language.
2. Use it.

---

### Post by LaRoza on 2008-05-11
Got fired by Microsoft, reopened.

---

