---
title: "python options"
date: 2006-12-17
forum: Programming Talk
---

### Post by Ubuntuud on 2006-12-17
Hi,

I have a fairly simple question.
How do you process things like:

python sample_program.py -debug sample_file.txt

I didn't know how to call it, so I couldn't Google it up.

Thanks in advance!
pieter.

---

### Post by ghostdog74 on 2006-12-17
hi
maybe this is what you are looking for
[http://docs.python.org/lib/module-getopt.html]("http://docs.python.org/lib/module-getopt.html")

---

### Post by Wybiral on 2006-12-17
They are called command line arguments and in python it is incredibly easy...

This will print them all
```

import sys
for arg in sys.argv:
    print arg

```

To find out how many there are...

```

import sys

print len(sys.argv)

```

And to access them individually...

```

import sys

if len(sys.argv) > 1:
	print sys.argv[1]

```

Just remember that the first argument is the file name itself. So you really have len(sys.argv)-1 arguments.

---

### Post by Ubuntuud on 2006-12-17
Now that is easy... Thanks to the both of you!

---

