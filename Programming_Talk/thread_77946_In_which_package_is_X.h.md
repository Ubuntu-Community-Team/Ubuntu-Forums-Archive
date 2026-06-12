---
title: "In which package is X.h"
date: 2005-10-17
forum: Programming Talk
---

### Post by alxle on 2005-10-17
Hi friends,

please can anyone tell me in which package is the file X.h?
I want to compile xvnkb and it hangs while seaching for this file in /usr/X11R6/include/X11/X.h

Thanks for your help!
Alex

---

### Post by lithorus on 2005-10-17
x11proto-core-dev
```
apt-get install apt-file
apt-file update
apt-file search X.h
```

---

### Post by alxle on 2005-10-18
Thanks for the hint.
Everything i did as described, but apt say ths x11proto-code-dev is installed.
But I can not find X.h?

Maybe reinstall? But how?

---

### Post by worldgnat on 2005-12-18
Go into System->Administration->Synaptic Package Manager and click Search. Then type in x11proto-core-dev. It'll probably take a while, but once it loads, click on the box next to x11proto-core-dev and click "Mark for Reinstallation". This thread really helped me install e17.

Thanks,
-Peter

---

