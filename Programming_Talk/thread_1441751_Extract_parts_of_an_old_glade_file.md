---
title: "Extract parts of an old glade file?"
date: 2010-03-29
forum: Programming Talk
---

### Post by MacUntu on 2010-03-29
I'm trying to bring an old printer driver from 2003 to the year 2010 and currently I'm working on the GUI parts. Initially I tried to use libglade-convert but it fails and from the output I really can't tell where the problems are.

Back at that time programmers thought it's cool to have glade files with 30,000+ lines, so I definitely won't touch the whole thing and am now looking for a way to split it.

The document is of the form:

```

<?xml version="1.0"?>
<GTK-Interface>

<project>
    ...
</project>

<widget>
    ...
</widget>

...

<widget>
    ...
</widget>

</GTK-Interface>

```

How can I easily extract all those widget nodes (keeping information about their original order within the document) and save them to a file?

---

### Post by Compyx on 2010-03-29
I'd use a XML-library such as expat to extract those nodes. Most programming languages these days have XML-parsing capabilities, such as PHP, Python and Perl.

In python I'd use xml.SAX. You can set up your handlers to only process <widget> nodes and their children. The original order of the nodes in the document is kept, so just extract each node as you encounter them.

---

### Post by MacUntu on 2010-03-29
Ok, think I got something in python:

```

import xml.dom.minidom
from xml.dom.minidom import Node

doc = xml.dom.minidom.parse("file.glade")

# GTK-Interface node
root = doc.firstChild

# first node
node = root.firstChild

while True:
    # TODO save node
    node = node.nextSibling
    if not node:
        break

```

this will result in getting nodes like:

```
<DOM Element: widget at 0x8f014ac>
<DOM Text node "u'\n\n'">
<DOM Element: widget at 0x928c54c>
<DOM Text node "u'\n\n'">
<DOM Element: widget at 0x931a32c>
<DOM Text node "u'\n\n'">
<DOM Element: widget at 0x93a314c>
<DOM Text node "u'\n\n'">
<DOM Element: widget at 0x94f70ec>
```

Are those text nodes to be expected or do I need to do some pre-processing on the original glade file?

---

### Post by MacUntu on 2010-03-29
> **Compyx said:**
> In python I'd use xml.SAX. You can set up your handlers to only process <widget> nodes and their children. The original order of the nodes in the document is kept, so just extract each node as you encounter them.

Thanks, have seen your posting too late. Will now look at xml.SAX.

**Edit:**

I finally used xml.etree.ElementTree:

```
#!/usr/bin/python

from xml.etree.ElementTree import parse
from xml.etree.ElementTree import ElementTree

doc = parse('file.glade')
children = doc.getroot().getchildren()

i = 0
for node in children:
    # build a new tree ...
    newtree = ElementTree(node)
    # ... so it can be written to a file
    filename = "nodes/node_%02d.glade" % i
    newtree.write(filename)
    i += 1
```

Was a big help in finding the broken glade parts. :D

---

