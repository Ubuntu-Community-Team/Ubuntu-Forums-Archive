---
title: "Need some scripting help"
date: 2009-02-05
forum: Programming Talk
---

### Post by Vadi on 2009-02-05
Hi,

Can anyone help me write a script that removes duplicate files from a .pot file?

For example, I need to turn

> msgid "text to be translated"
msgstr ""

msgid "unique text"
msgstr ""

msgid "text to be translated"
msgstr ""

msgid "text to be translated"
msgstr ""

Into

> msgid "text to be translated"
msgstr ""

msgid "unique text"
msgstr ""

I'm just not quite sure how to go about making a such script :\

(or, on the other hand, can anyone share the secret to translate-fying a Qt app into the standard GNU GetText?)

---

### Post by unutbu on 2009-02-05
Perhaps this would work:
Call this rm_dup.py:
[PHP]#!/usr/bin/env python
import sys
fh=open(sys.argv[1],'r')
keys={}
previous=[]
result=[]
for line in fh:
    line=line.strip()
    if line=='':
        key=tuple(previous)
        if not key in keys:
            result.append('\n'.join(previous))
            keys[key]=True
        previous=[]
    else:
        previous.append(line)

print '\n\n'.join(result)
[/PHP]
Make it executable, and run it like this:
```

rm_dup.py file.pot
```

---

### Post by kapok on 2009-02-05
can you code?

you could make a program that sets each first instance of a name or whatever you are trying to get rid of duplicates of to a member of an array of strings. than print that array to a new file and delete the old one.

---

### Post by ghostdog74 on 2009-02-07
here's a one liner for you.
```

# awk 'BEGIN{RS="\n\n"}{_[$0]++}END{for (i in _) print i}' file
msgid "text to be translated"
msgstr ""
msgid "unique text"
msgstr ""


```

---

### Post by Vadi on 2009-02-07
Thanks a bunch!

---

