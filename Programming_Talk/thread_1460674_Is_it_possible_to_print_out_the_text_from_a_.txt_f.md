---
title: "Is it possible to print out the text from a .txt file in pyhton?"
date: 2010-04-23
forum: Programming Talk
---

### Post by jakeeee on 2010-04-23
For example..

print "text.txt"

Then it would print out the contents of the text file.
i know that wouldnt work, but like thats what I want it to do..
Any ideas fellow ubuntu users? :)

---

### Post by Compyx on 2010-04-23
[http://wiki.python.org/moin/BeginnersGuide]("http://wiki.python.org/moin/BeginnersGuide")

---

### Post by nvteighen on 2010-04-23
Well, it's one of the first things you usually learn in Python. Look up the 'open()' built-in function (not 'os.open()' which is something else).

---

### Post by wmcbrine on 2010-04-23
> **jakeeee said:**
> print "text.txt"print file("text.txt").read()

---

### Post by soltanis on 2010-04-23
Python list comprehensions: oh exploitable.

```

import sys

def write(x):
    sys.stdout.write(str(x) + "\n")

[write(x) for x in file("file.txt").readlines()]

```

Not actually useful though, you should really use the method mentioned above this post. Just proving that there's always another (convoluted, yet somehow more functionally satisfying) way to do it.

---

### Post by lavinog on 2010-04-23
```

print open('textfile.txt').read()

```

> 
open(...)
    open(name[, mode[, buffering]]) -> file object
    
    Open a file using the file() type, returns a file object.  This is the
    preferred way to open a file.

Not sure why it is preferred though.

---

### Post by wmcbrine on 2010-04-23
Personally I prefer to use "file" instead of "open" whenever I don't match it with an explicit "close", but that's just me.

---

### Post by jakeeee on 2010-04-24
Thanks guys(:

---

