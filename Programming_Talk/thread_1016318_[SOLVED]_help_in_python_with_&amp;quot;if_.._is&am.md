---
title: "[SOLVED] help in python with &amp;quot;if .. is&amp;quot; and &amp;quot;if .. in&amp;quot;"
date: 2008-12-19
forum: Programming Talk
---

### Post by giuspen on 2008-12-19
if I write the following code:

[PHP]for dirpath, dirnames, filenames in os.walk(self.pyextensions_dir):
			for filename in filenames:
				print os.path.splitext(filename)[1]
				if os.path.splitext(filename)[1] is '.py':
					print filename[/PHP]

it doesn't works, otherwise if I write like this it works:
(just changed "if .. is" with "if .. in")

[PHP]for dirpath, dirnames, filenames in os.walk(self.pyextensions_dir):
			for filename in filenames:
				print os.path.splitext(filename)[1]
				if os.path.splitext(filename)[1] in ['.py']:
					print filename[/PHP]
anybody can help me?
I would like to use "is" or "==" but doesn't works and I really don't understand why.

---

### Post by mssever on 2008-12-19
> **giuspen said:**
> if I write the following code:

[php]for dirpath, dirnames, filenames in os.walk(self.pyextensions_dir):
            for filename in filenames:
                print os.path.splitext(filename)[1]
                if os.path.splitext(filename)[1] is '.py':
                    print filename[/php]it doesn't works, otherwise if I write like this it works:
(just changed "if .. is" with "if .. in")

[php]for dirpath, dirnames, filenames in os.walk(self.pyextensions_dir):
            for filename in filenames:
                print os.path.splitext(filename)[1]
                if os.path.splitext(filename)[1] in ['.py']:
                    print filename[/php]anybody can help me?
I would like to use "is" or "==" but doesn't works and I really don't understand why.
```
if os.path.splitext(filename)[1] == '.py':
```works for me. Unless you provide the error, and/or describe exactly what happens, it's hard to know what's wrong.

EDIT: Here are some tests to prove my point: ```
>>> import os
>>> filename = '/sffd/fds.py'
>>> os.path.splitext(filename)[1]
'.py'
>>> '.py' == os.path.splitext(filename)[1]
True
>>> '.py' is os.path.splitext(filename)[1]
False
>>> 
```

---

### Post by giuspen on 2008-12-19
yes now I tried with '==' and it works, I thought that it was absolutely the same as 'is' but I was wrong, because 'is' doesn't work.
thanks, regards.

---

### Post by ghostdog74 on 2008-12-19
the "is" operator checks whether objects are the same, not just equal. "in" and "is" are different.

---

### Post by nvteighen on 2008-12-20
**is** checks if two object's **id()** are the same.

---

