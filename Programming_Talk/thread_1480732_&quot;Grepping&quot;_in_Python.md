---
title: "&quot;Grepping&quot; in Python"
date: 2010-05-11
forum: Programming Talk
---

### Post by stryker213 on 2010-05-11
Hello All, I currently have the following python code:
```

#usr/bin/python
import os

variable=raw_input('Search for this string: ')
os.system("grep $variable sample.txt")

```

Basically what I want to do is to grep a string found in the text file "sample.txt" When I run the code, it just hangs. How can I make it so that grep accepts the variable?

---

### Post by trent.josephsen on 2010-05-11
How about

```
#!/usr/bin/python

variable = raw_input("Search for string: ")

lines = [line for line in open('sample.txt') if variable in line]
```

You should usually try to avoid using system() when you can, especially for things like grep which are pretty easy to do portably in Python.

Oops, forgot to address the issue.  You can't interpolate variables in Python with $ like you can in Perl or bash.  You have to use the str.format method or string concatenation with the + operator:
```
cmdLine = 'grep ' + variable + ' ' + filename
cmdLine = 'grep %s %s' % (variable, filename)
```

Better is to use the subprocess module to spawn processes with greater control over arguments; you can find documentation for that elsewhere.

---

