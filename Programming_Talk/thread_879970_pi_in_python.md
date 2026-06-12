---
title: "pi in python?"
date: 2008-08-04
forum: Programming Talk
---

### Post by CloudFX on 2008-08-04
Hi all,

I'm looking for the operator to use for pi (3.1415...).  Thanks!

---

### Post by tamoneya on 2008-08-04
i believe you are looking for math.pi which is in the math module.

[http://docs.python.org/lib/module-math.html](http://docs.python.org/lib/module-math.html)

---

### Post by derjames on 2008-08-04
```

import math
math.pi

```

hope this helps

cheers

---

### Post by CloudFX on 2008-08-04
Thanks a lot for that!  I'm a beginner to python, so I'm not entirely sure on using this.  First, am I supposed to enter 'import math' in the python application?  Where do I use math.pi? Thanks!

---

### Post by tamoneya on 2008-08-04
put ```
import math
``` at the top of your script with all your other initializations.  Then whenever you want the value pi use math.pi  Here is an example:```
#calculate area of circle
import math
r = 5
area = math.pi*r*r
```

---

### Post by The Cog on 2008-08-04
Yes. import math would probably go at the top of your source file. It imports the math module, which provides a few constants and a bundle or maths functions like square root and others. You will find yourself importing several modules as you get to do bigger programs. Here are the standard modules documentation:
[http://www.python.org/doc/current/modindex.html](http://www.python.org/doc/current/modindex.html)

As for where do you use math.pi - wherever you need pi. Doing mathematical calculations perhaps.

---

### Post by xelapond on 2008-08-04
Also, if you don't want to reference it with math.pi, you can use:

[php]from math import pi[/php]Which would allow you do this this:

[php]#calculate area of circle
from math import pi
r = 5
area = pi*r*r  #<--Notice how you don't need to do math.pi, just pi[/php]Good Luck!

Alex

---

### Post by elithrar on 2008-08-04
Also, if you want to check what an imported module has available:

```

>>> import math
>>> dir(math)
['__doc__', '__file__', '__name__', 'acos', 'asin', 'atan', 'atan2', 'ceil', 
'cos', 'cosh', 'degrees', 'e', 'exp', 'fabs', 'floor', 'fmod', 'frexp', 
'hypot', 'ldexp', 'log', 'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 
'sinh', 'sqrt', 'tan', 'tanh']

```

As for where to place [FONT="Courier New"]import[/FONT] statements, have a look [here](http://www.python.org/dev/peps/pep-0008/) - they should always be at the top of a module/script.

---

### Post by xelapond on 2008-08-04
Going hand in hand with what elithrar said, if you want a brief description of an imported module:

[PHP]print <modulename>.__doc__[/PHP]

---

### Post by CloudFX on 2008-08-04
Awesome!  Thanks a lot everybody.. this is definitely enough to get going.

---

