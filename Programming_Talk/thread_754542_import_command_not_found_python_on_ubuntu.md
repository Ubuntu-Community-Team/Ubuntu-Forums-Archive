---
title: "import: command not found: python on ubuntu?"
date: 2008-04-13
forum: Programming Talk
---

### Post by psychoman.exe on 2008-04-13
I recieved a python script that runs perfectly on windows, but when I try running it in terminal I get several of these:

import: command not found

now, as far as I know, import is a basic command in any version of python.
Do I need to get another library, or (as strange as it sounds) are some commands just different in ubuntu?

---

### Post by Wybiral on 2008-04-13
Can you show us the code that's doing this? "import" is built into the language, it's a keyword.

---

### Post by LaRoza on 2008-04-13
You most likely are missing the shebang line.

Windows uses file extensions to determine the file type (and everything else...), Linux is a bit more smart about it.

This should be the first line:
```

#!/usr/bin/python

```

---

### Post by psychoman.exe on 2008-04-13
```

import sys

import socket

import string

import random
```

those are the first four lines of code

this is what terminal tells me:

```

/home/steven/Desktop/Scrambles.py: line 1: import: command not found
/home/steven/Desktop/Scrambles.py: line 2: import: command not found
/home/steven/Desktop/Scrambles.py: line 3: import: command not found
/home/steven/Desktop/Scrambles.py: line 4: import: command not found
```

---

### Post by LaRoza on 2008-04-13
> **psychoman.exe said:**
> [CODE]
those are the first four lines of code

this is what terminal tells me:


Do what I said above.

---

### Post by Wybiral on 2008-04-13
LaRoza is right, it looks like you're trying to execute it using "./program.py" which won't work without the shebang. You could, however, use "python program.py" to execute it without a shebang.

---

### Post by psychoman.exe on 2008-04-13
ah, thanks Larosa, it works perfectly now

---

### Post by LaRoza on 2008-04-13
> **psychoman.exe said:**
> ah, thanks Larosa, it works perfectly now

Of course it does. It worked perfectly before as well, just not the way you expected ;)

That line will be ignored in Windows, so it is safe that way.

---

