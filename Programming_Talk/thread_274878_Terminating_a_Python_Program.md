---
title: "Terminating a Python Program"
date: 2006-10-10
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-10
Hi,

What command do you use in python to terminate a program?

i.e. the equivalent of "end" in basic, or "quit" in BASH.

I see that "break" takes you out of a loop, and "quit" is all tied up with "class" stuff that I do not comprehend yet.

I'm looking for something that will just end the program carte blanche.

Thanks,
Tom

---

### Post by Tomosaur on 2006-10-10
import sys
sys.exit()

I think. Maybe sys.quit(), mind's gone blank :P.

---

### Post by thomasaaron on 2006-10-10
I tried it both ways, and it is not working.

I also tried 

import os
os.system("quit")

and 

import os
os.system("exit")

Neither of them worked.

I can use "break" to bring me out of the loop, but it's won't end the program.

---

### Post by xtacocorex on 2006-10-10
It should be:
import sys
sys.exit(0) or sys.exit(1)

---

### Post by po0f on 2006-10-10
You shouldn't need an integer to sys.exit() from a Python script.  Something like the following would work just as well:
```
import sys
(snip...)
if not sys.argv[1:3]:
    sys.exit("Program requires 3 arguments.")
(snip...)
```

Or, you could:
```
raise SystemExit
```

---

### Post by thomasaaron on 2006-10-10
OK, below is the script.
The sys.exit(0) is not working.
Why won't it end the program when option "4" is selected?


Actually, this did not show the indentations...
I'll try to figure it out...

---

