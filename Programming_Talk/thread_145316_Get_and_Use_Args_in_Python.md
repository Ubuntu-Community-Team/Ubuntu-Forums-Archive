---
title: "Get and Use Args in Python"
date: 2006-03-16
forum: Programming Talk
---

### Post by noob_Lance on 2006-03-16
Hey, Im writing a python script and i need it so the user can specify a file, the destination [optiona] and the option [optional, ntr 1 for this. default 0]

anyone please help me with this.. thank you very much

~Lance

---

### Post by jpkotta on 2006-03-16
I'd recommend reading the Python Tutorial, section "2.1.1 Argument Passing".

```

#!/usr/bin/python

import sys

for arg in sys.argv:
    print arg


```

---

### Post by ow50 on 2006-03-16
Option parser module
[http://docs.python.org/lib/module-optparse.html](http://docs.python.org/lib/module-optparse.html)

---

### Post by noob_Lance on 2006-03-16
tried both and neiter were useful... :( anyone else??

---

### Post by thumper on 2006-03-16
What?  What do you mean not useful?

The option parser module is excellent.

How about you tell us what you need, and someone (maybe me) will show you how to use the option parser?

For what you mentioned above, something like this would suffice:

```
from optparse import OptionParser

if __name__ == '__main__':
   parser = OptionParser
   parser.set_defaults(ntr=0)
   parser.add_option("-n", "--ntr", action="store", type=int, help="no idea what this is for")
   (options, args) = parser.parse_args()

   if len(args) < 1: print "missing file"
   filename = args[0]
   dest = ''
   if len(args) > 1: dest = args[1]

   print options.ntr, filename, dest

```

---

### Post by noob_Lance on 2006-03-16
well i tried them last night at 3 am and got nowhere... not that its morning and ive had time to rest lol ive gottin way past this stage and am now nearing completion of my program. :)

---

