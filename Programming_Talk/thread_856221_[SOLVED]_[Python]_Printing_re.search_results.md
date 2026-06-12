---
title: "[SOLVED] [Python] Printing re.search results"
date: 2008-07-11
forum: Programming Talk
---

### Post by TreeFinger on 2008-07-11
How do I get re to print the string i'm searching for that matches re.search? All I can do is print the entire line right now. 

All I get is : '<_sre.SRE_Match object at 0x00A83608>'

edit.. nevermind.

[php]
if p.search(line):
		m = p.search(line)
		print m.group()
[/php]

---

### Post by maximinus_uk on 2008-07-11
One simple way is:

```
#!/usr/bin/python

import re

foo=re.search(r".+[W]","Hello, World")

print foo.string[foo.start():foo.end()]

```

---

