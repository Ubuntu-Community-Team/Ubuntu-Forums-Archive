---
title: "Trouble installing python-pygame"
date: 2008-10-26
forum: Programming Talk
---

### Post by ReyJavikVI on 2008-10-26
When I run sudo apt-get install python-pygame, it says it's already installed. But when I start the python interpreter and try to import the module, it says it's not there. I also can't find the pygame files anywhere. Thanks in advance for any help.

---

### Post by jimi_hendrix on 2008-10-26
try sudo apt-get remove python-pygame first

---

### Post by ReyJavikVI on 2008-10-26
Still not working.:(

---

### Post by jimi_hendrix on 2008-10-26
reinstall python?

---

### Post by moephan on 2008-10-26
FWIW - the import should just look like:

[code]
import pygame
[/game]

The module is not named exactly the same as package. Importing "python-pygame" won't work.

HTH

Cheers, Rick

---

### Post by fiddler616 on 2008-10-26
If the above don't work, try checking your PYTHONPATH.

---

### Post by sheto on 2008-10-27
An alternate way is ```
from pygame import *
``` It's the same as ```
import pygame
```

---

