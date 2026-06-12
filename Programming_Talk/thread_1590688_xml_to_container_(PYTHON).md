---
title: "xml to container (PYTHON)"
date: 2010-10-08
forum: Programming Talk
---

### Post by Blackbug on 2010-10-08
i am reading an xml file and need to store the contents (elements) of that to a container.
 
mapping = {}
titleTuple =[]
i=0
for node in doc.getElementsByTagName("book"):
    isbn = node.getAttribute("isbn")
    L = node.getElementsByTagName("title")
    for node2 in L:
     title = ""
     print title
     for node3 in node2.childNodes:
      if node3.nodeType == Node.TEXT_NODE:
       title += node3.data
       print "title %s,node3.data %s"%(title,node3.data)
      titleTuple.append[node3.data]
      mapping[isbn] = title

I am confused which container to be used and how.
I tried set "titleTuple.append[node3.data]" but it gives an error 
'builtin_function_or_method' object is unsubscriptable
 
i am new to python so kindly help me on this.

---

### Post by surfer on 2010-10-08
```
titleTuple.append(node3.data)
```

round brackets for functions.

---

