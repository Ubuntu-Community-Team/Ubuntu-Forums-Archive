---
title: "Beginner to python"
date: 2010-08-18
forum: Programming Talk
---

### Post by CaptainMark on 2010-08-18
Thanks to the advice of the guys on this here forum I've been teaching myself python recently as my first programming language. I was wondering 
1. when I make my own programs to make them executable in a terminal I add the line ```
#!/usr/bin/python3
```at the start of my code, if I give this code to a friend who also runs ubuntu will the bin files still be in the same place presuming they have python3
2. how would this change if I was to give the code to someone with a windows pc, again presuming they've installed python3

---

### Post by surfer on 2010-08-18
the linux-independent form of the first line would be:
```

#!/usr/bin/env python3

```
that should find python3. but if you run it on ubuntu machines only, there is no problem (if python3 is installed).

windows will not know what to do with this first line (this is just a message for the shell). but as the line is commented anyway, the code should run.

---

### Post by GenBattle on 2010-08-18
As surfer said, it should work on Ubuntu if they've installed python3 from the repositories. In windows it will ignore this line and use the default application for opening .py files. If you only have Python3 installed, then windows will use python3 to execute/edit the script.

---

### Post by CaptainMark on 2010-08-18
thanks good to know

---

### Post by juancarlospaco on 2010-08-18
I make it cross-compatible to Python 2/3, just like:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# This is Python 2 / 3 Compatibility
try:
    import Tkinter as tk  # Python2
except ImportError:
    import tkinter as tk  # Python3
```

*and so on...*
My code works with python 2 and 3 :)

---

### Post by worksofcraft on 2010-08-18
> **juancarlospaco said:**
> I make it cross-compatible to Python 2/3, just like:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# This is Python 2 / 3 Compatibility
try:
    import Tkinter as tk  # Python2
except ImportError:
    import tkinter as tk  # Python3
```

*and so on...*
My code works with python 2 and 3 :)

That's very thorough, but isn't it going to be making your scripts an awful lot harder to read and maintain in the long run`.... and a twice as much work to test and debug?

---

### Post by juancarlospaco on 2010-08-18
> **worksofcraft said:**
> That's very thorough, but isn't it going to be making your scripts an awful lot harder to read and maintain in the long run`.... and a twice as much work to test and debug?

No, 
Meerkat+1 will ship Python 3 only as i read on the roadmapz :)
*and 2to3 ftw*

---

### Post by Bachstelze on 2010-08-18
> **worksofcraft said:**
> That's very thorough, but isn't it going to be making your scripts an awful lot harder to read and maintain in the long run`.... and a twice as much work to test and debug?

That's just 4 lines of code instead of one, not exactly "an awful lot". :p

---

### Post by worksofcraft on 2010-08-18
> **Bachstelze said:**
> That's just 4 lines of code instead of one, not exactly "an awful lot". :p

I thought it was only one *example* and has to be repeated for countless similar discrepancies peppered throughout your script. Forgive my lack of Python knowledge, but are you saying those 4 lines are all you need for full compatiblity with both Python 2 and 3?

---

### Post by Bachstelze on 2010-08-18
> **worksofcraft said:**
> I thought it was only one *example* and has to be repeated for countless similar discrepancies peppered throughout your script. Forgive my lack of Python knowledge, but are you saying those 4 lines are all you need for full compatiblity with both Python 2 and 3?

Most discrepancies between Python 2 and 3 don't need that much boilerplate code.  For example, this

```
print 'foo'
```

will work only in Python 2, while this

```
print('foo')
```

will work in both Python 2 and 3.

---

### Post by worksofcraft on 2010-08-18
> **Bachstelze said:**
> Most discrepancies between Python 2 and 3 don't need that much boilerplate code.  For example, this

```
print 'foo'
```

will work only in Python 2, while this

```
print('foo')
```

will work in both Python 2 and 3.

z0mg I've just been using Python 2 style everywhere... so now I have to go edit all my scripts to put brackets in... What a pain! Is there an easy way to make my old scripts require Python 2 until I get round to un-deprecating them all?

---

### Post by Bachstelze on 2010-08-18
I wouldn't worry about that too much.  99% of the time, if you put [font=monospace]/us/bin/env python[/font] on your shebang line, you will get Python 2.  If someone has [font=monospace]python[/font] pointing to Python 3 on his system, he'll know about it, and will know enough to act accordingly.

---

### Post by juancarlospaco on 2010-08-19
No, transition is automatic, see 2to3 :)

---

### Post by Bachstelze on 2010-08-19
> **juancarlospaco said:**
> No, transition is automatic, see 2to3 :)

2to3 will make your code compatible with Python 3 only, not with both.

---

