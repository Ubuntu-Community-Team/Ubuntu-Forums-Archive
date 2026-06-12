---
title: "How efficient is this (Python Program)"
date: 2007-04-20
forum: Programming Talk
---

### Post by chakkaradeep on 2007-04-20
Hi All,

I want to convert an XML file (file size not > 300 kb) to text file where all the data are readable.

The python code is below,

```

import sys
from xml.dom import minidom, Node

def showNode(node):
    if node.nodeType == Node.ELEMENT_NODE:
        print 'Element name: %s' % node.nodeName
        for (name, value) in node.attributes.items():
            print 'Attr Name: %s  Value: %s' % (name, value)  

def main():
    doc = minidom.parse('device-data.xml')
    node = doc.documentElement
    #showNode(node)
    for child in node.childNodes:
        for children in child.childNodes:
                if children.nodeType == Node.ELEMENT_NODE:
                        print
                        print "Device ID : " + children.attributes.get('id').value
                for siblings in children.childNodes:
                        showNode(siblings)

if __name__ == '__main__':
    main()

```

The input file is the system hardware data xml which can be generated as, from your terminal,

```

hwdb-xml -d > device-data.xml

```

Many tell XML Programming is quite tricky :) . So just wanted to know how far the code is efficient. My aim is to create text files from the XML file.

Thanks.

---

### Post by Mirrorball on 2007-04-20
XML files are text files already. ;) And you could use recursion to print the tree.
```

def showNode(node):
    if node.nodeType == Node.ELEMENT_NODE:
        # print node
    for child in node.childNodes:
        showNode(child)

```

---

