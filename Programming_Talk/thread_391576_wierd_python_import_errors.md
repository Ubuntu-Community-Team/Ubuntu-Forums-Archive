---
title: "wierd python import errors"
date: 2007-03-23
forum: Programming Talk
---

### Post by Choad on 2007-03-23
i first found this when i was trying to do some xml stuff in python, but got bored and couldnt be bothered to figure out why it was happening, but now im trying to follow the first pyGame tutorial im getting the same wierd error.

```
#/usr/bin/env python
import os, sys
import pygame
from pygame.locals import *

if not pygame.font: print "no fonts"
if not pygame.mixer: print "no sounds"

```

all this does is change the cursor to a cross hair... then it waits for me to click on something, and then it says  can't read /var/mail/pygame.locals and quits. i just copied the full source and tried again, and it does roughly the same thing but then goes on to complain about unexpected symbols.

any clues? wtf is the crosshair about?

---

### Post by invalid on 2007-03-23
I can't say why it is doing this, but I can say what it is doing.
```
import <filename>
```is a utility to grab a screenshot and save it to filename. It presents a cross hair for you to select what a screenshot will be taken of.

For some reason, it is not recognizing that you are trying to use python to parse the script.

---

### Post by invalid on 2007-03-23
Looking at it again, try replacing the first line with```
#!/usr/bin/env python
```

(notice the !)

---

### Post by Choad on 2007-03-23
how strange. python test.py worked fine

this is a little annoying. all my other projects, including ones that import gtk etc. all work fine just typing ./whatever.py

---

### Post by Choad on 2007-03-23
> **invalid said:**
> Looking at it again, try replacing the first line with```
#!/usr/bin/env python
```

(notice the !)
ahaaa!

wonder why there is a typo in the tutorial.. seems a bit lame :p

---

### Post by invalid on 2007-03-23
> **Choad said:**
> how strange. python test.py worked fine

this is a little annoying. all my other projects, including ones that import gtk etc. all work fine just typing ./whatever.py

Using ```
python <filename>
``` forces it to run through the python interperter. Using it as a shell script, the shell needs to know how to interpert it. The character # is just used as a comment, and ignored unless followed by a !.

Glad it worked out !

---

### Post by pmasiar on 2007-03-23
```
#/usr/bin/env python
from pygame.locals import *

```

1) it there really is an error in tutorial (and not your typo), you may want to be a good citizen and report the error to the author - so next guy has smoother sailing.

2) import * is IMHO not very good way to do it: it might populate your namespace with names which might clash with yours. Better way is to always import explicit name. Like "from pygame.locals import font, mixer". It helps also  in debugging: you can search and see where the name came from. With * you cannot.

---

