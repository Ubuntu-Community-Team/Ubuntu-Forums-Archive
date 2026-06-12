---
title: "writing in Farsi or Arabic in IDE Python"
date: 2010-12-20
forum: Programming Talk
---

### Post by shafagh on 2010-12-20
Hi;
I'm using ubuntu 10.04 and want Python to print something in Farsi or Arabic for me like this:

print(u"&#1587;&#1604;&#1575;&#1605;".encode('utf8'))

but it didn't work properly-just give something tangled.

I'd installed every necessary pack for language support, and tried sort of things like changing unicode. But nothing happen. 

When I run the program with utf-8 I get this:

"SyntaxError: Non-ASCII character '\xd8' in file /home/shafagh/Desktop/2.py on line 3, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details" 

I checked the page but nothing was new.

In other programs I don't have any problem with Farsi or Arabic language.

Does anybody know what should I do?

Thanks in advance.
shafagh

---

### Post by StephenF on 2010-12-20
Make the first two lines in your source file like this (obtained from that link):
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

```
You will then be able to enter utf-8 characters directly into the source code provided your text editor is also in utf-8 mode.

Ideally you would just do this in one language file if your program has more than one file.

---

