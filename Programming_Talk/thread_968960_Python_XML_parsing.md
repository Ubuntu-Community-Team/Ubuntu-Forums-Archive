---
title: "Python XML parsing"
date: 2008-11-03
forum: Programming Talk
---

### Post by PryGuy on 2008-11-03
Good day! I'm writing a simple python program that parses my XML file. What I want to do is to put tags called 'Name' into array. I do it with 'for' condition. The problem is noone knows how many 'Name' tags XML file will have, so i have to count from 0 to the last 'Name' tag. How do I get the total quantity of these tags?

Here's a sample code:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

from xml.dom import minidom
xmldoc = minidom.parse('myfile.xml')
title = []
for i in [COLOR="Red"]?[/COLOR]:
	title.append (xmldoc.getElementsByTagName('Name')[i].firstChild.data)
print title
```
Thank you!

---

### Post by pmasiar on 2008-11-03
arrays == lists in Python are flex-arrays - they will expand as needed,
len(title) gives you number of items in array

---

### Post by moephan on 2008-11-04
I'm not 100% certain what you are trying to do. However, it appears to me that you want to pull out all the "name" nodes, iterate through them, and append the value of each node to a list.

So the approach that I would take is to:
1. Use the getElementsByTagName method to create a list of Dom Elements
2. Iterate through that list and pull the values of each child node of the dom element.

So maybe it would look more like this:

```

from xml.dom import minidom
xmldoc = minidom.parse('myfile.xml')
nameEls = xmldoc.getElementsByTagName('Name')
title = []
for el in nameEls:
	title.append (el.childNodes[0].nodeValue)
print title

```

I hope I understood your problem and that helps a little.

Cheers, rick

---

### Post by Portmanteaufu on 2008-11-06
When I started doing XML parsing in Python, I found it was immensely more intuitive to use the ElementTree module. It lets you iterate through subnodes of a node, uses a single function to return all nodes of a given type as a list, etc. It's included in a standard install of Python, too.

[ElementTree Tutorial]("http://www.learningpython.com/2008/05/07/elegant-xml-parsing-using-the-elementtree-module/")
[ElementTree API]("http://effbot.org/zone/pythondoc-elementtree-ElementTree.htm")

---

### Post by PryGuy on 2008-11-06
Okay, here's what I finally got:```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

def getdata():
	#importing a nice library
	import libxml2
	# declaring global arrays
	global names
	names = []
	global paths
	paths = []
	global active
	active = []
	# reading XML file
	doc = libxml2.parseFile('file.xml')
	# getting names
	getnames = doc.xpathEval('//name')
	for node in getnames:
		names.append (node.content)
	# getting paths
	getpaths = doc.xpathEval('//path')
	for node in getpaths:
		paths.append (node.content)
	# getting active states
	getactive = doc.xpathEval('//active')
	for node in getactive:
		active.append (node.content)
	# closing the XML file
	doc.freeDoc()

getdata()
print names
print len (names)


```'name', 'path' and 'active' are tags in my XML file. Everything is very simple!

---

