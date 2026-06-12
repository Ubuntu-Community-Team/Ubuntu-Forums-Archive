---
title: "Geany: Python script as a custom command"
date: 2012-12-09
forum: Programming Talk
---

### Post by jw37 on 2012-12-09
Hi all!

How to set a custom command in Geany when the custom command is actually a python script that i have created? The python script handles the first system argument and prints the result to std output.

I have set the custom command but i can't find out how to set the text argument. The script runs without passing the selected text. Or more precisely, the python script never gets the selected text. Can anyone see how to fix this?

So the reference for this Geany property is found here: [http://www.geany.org/manual/current/#sending-text-through-custom-commands](http://www.geany.org/manual/current/#sending-text-through-custom-commands)


Edit: I forgot to reduce the problem. Here's a very simple sample script.

The custom command i set: "python /home/<username>/Python/parens.py"

File parens.py:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sys

args = sys.argv[1:]

if args:
    print "(" + args[0] + ")"
```

---

### Post by jw37 on 2012-12-10
Is it possible to use python script to this purpose?


The real issue is to format python docstring paragraphs so that when you insert or remove text you can easily get nice layout. I'd prefer to do it in python but if that's impossible then something else is needed.

---

### Post by jw37 on 2012-12-10
Hey, i found the solution! It's like this:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sys

txt = sys.stdin.read()
sys.stdout.write("(" + txt + ")")
```

Now the selected text is read by the python script :)  and the stdout.write() doesn't even add extra new line as print does.

---

