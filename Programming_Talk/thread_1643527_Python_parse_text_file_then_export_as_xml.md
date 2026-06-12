---
title: "Python: parse text file then export as xml?"
date: 2010-12-12
forum: Programming Talk
---

### Post by _joachim_ on 2010-12-12
Hey there, I' have a text file along this kind of formatting:

abc : def
ghi : jkl
mno : pqr
stu : vwx

and so on,

What I would like to accomplish is to parse the colon and store the 'abc' as say <item1> and the 'def' as <item2> in a xml file, I'm quite new to programming and not sure if this is more than I can bite off.  If anyone knows of any tutorials that could walk me through this particular problem that would be great as my google-foo has failed me.  

For the moment the only thing I've come up with is:

```

f = open('tmp', 'r')
lines = f.readlines()
for line in lines:
    items = line.replace(':', ' ', 1)
    f.seek(0)
    f.truncate()
    f.write(items.join('\n'))
f.close()


```


Excuse the indenting, having issues with it.  Any advice/tips much appreciated

---

### Post by MadCow108 on 2010-12-12
there are a bunch of xml handliny libraries for python:
[http://wiki.python.org/moin/PythonXml](http://wiki.python.org/moin/PythonXml)

Example with lxml and ElementTree (you need to install python-lxml first):
```

import lxml.etree as ET

f = open("test.txt")
lines = f.readlines()
root = ET.Element("root")
for l in lines:
  elems = l.split(":")
  if len(elems) == 2:
    elems = map(lambda x: x.strip(), elems)
    line = ET.SubElement(root, "line")
    item1 = ET.SubElement(line, "item1")
    item2 = ET.SubElement(line, "item2")
    item1.text = elems[0]
    item2.text = elems[1]

tree = ET.ElementTree(root)
tree.write("test.xml", pretty_print=True)

```

---

