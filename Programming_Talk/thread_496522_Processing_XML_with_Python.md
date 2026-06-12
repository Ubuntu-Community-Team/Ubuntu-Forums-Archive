---
title: "Processing XML with Python?"
date: 2007-07-09
forum: Programming Talk
---

### Post by flummoxed on 2007-07-09
I'm trying to figure out which library to use to process XML with python. PyXML keeps seem to be getting recommended on sites I've found on google, but it hasn't been updated since 2004. That doesn't seem like a very good idea. I used xmllib in a test app, and python said "xmllib you should use xml.sax"! Now, what exactly IS sax? I went to the website, but I didn't really understand what it was talking about. In the FAQ, I looked for a helpful "What is SAX?" question, but alas, there was no such question to be found.

---

### Post by cwaldbieser on 2007-07-09
> **flummoxed said:**
> I'm trying to figure out which library to use to process XML with python. PyXML keeps seem to be getting recommended on sites I've found on google, but it hasn't been updated since 2004. That doesn't seem like a very good idea. I used xmllib in a test app, and python said "xmllib you should use xml.sax"! Now, what exactly IS sax? I went to the website, but I didn't really understand what it was talking about. In the FAQ, I looked for a helpful "What is SAX?" question, but alas, there was no such question to be found.

There are 2 main programming to parse XML irrespective of programming language-- DOM and SAX.  With DOM, the whole XML document is slurped into an object model representation, and you can access parts of it in whatever order you want.  With SAX, the tags are read in order, and events are fired that your program can respond to (similar to most GUI programming).

DOM tends to be a little more intuitive, but it requires parsing the whole document at once, which can be problematic for large documents.


Python also offers some other options, such as representing the document as native Python objects.

If you explained a little bit about what kind of XML documents you want to process, it would be easier to steer you in the right direction.

---

### Post by pmasiar on 2007-07-09
DOM and SAX are from java world. Because Python is *much* more flexible than Java, you don't have to go through same contortions to get XML. Use excellent and very pythonic ElementTree module. It builds dict of dicts, really easy to use.

ET is standard module in 2.5, for 2.4 you need to download it.

[http://effbot.org/zone/element-index.htm](http://effbot.org/zone/element-index.htm)

---

### Post by flummoxed on 2007-07-09
This is what I'm looking to do. I'm creating a tutorial creator/viewer that will hopefully make tutorials easy to be read in a step-by-step fashion. The XML for a tutorial would look something like this.

```
<Tutorial>
	<general>
		<author>MaxMight</author>
  		<homepage>http://flummoxed.conforums.com</homepage>
  		<title>Test Tutorial</title>
  		<version>0.1</version>
	</general>
 
 	<content pages="10">
		<page id="1">
			<text xpos="center" ypos="top"> Welcome to the tutorial creator</text>
			<image xpos="center" ypos="center">image.png</image>
			<code xpos="center" ypos="bottom" lang="python">snippet1.py</code>
   		</page>
  	<page id="2">
			<text xpos="center" ypos="center">This page has only text</text>
	</page>
 	</content>
</Tutorial>  
```

I'm just working on the viewer right now, and I need to be able to display it  like this.

[IMG]http://img170.imageshack.us/img170/4711/text2190ke5.png[/IMG]

So basically I want my tutorial viewer to read the XML, glean the important information from it and put it all together into a finished tutorial.

---

### Post by cwaldbieser on 2007-07-10
It looks like your documents are not particularly large, so an in-memory representation like DOM or ElementTree (as pmasiar suggested) would be appropriate.  If you need compatibility, with older versions of python, and you don't want to download extra modules, the xml.dom.minidom standard module should be sufficient for your needs (though possibly a bit more cumbersome to work with).

---

### Post by cwaldbieser on 2007-07-10
> **pmasiar said:**
> DOM and SAX are from java world. Because Python is *much* more flexible than Java, you don't have to go through same contortions to get XML. Use excellent and very pythonic ElementTree module. It builds dict of dicts, really easy to use.

ET is standard module in 2.5, for 2.4 you need to download it.

[http://effbot.org/zone/element-index.htm](http://effbot.org/zone/element-index.htm)

From section 13.6 of the Python Standard library:
> 
The Document Object Model, or ``DOM,'' is a cross-language API from the World Wide Web Consortium (W3C) for accessing and modifying XML documents. A DOM implementation presents an XML document as a tree structure, or allows client code to build such a structure from scratch. It then gives access to the structure through a set of objects which provided well-known interfaces. 
 The DOM is extremely useful for random-access applications. SAX only allows you a view of one bit of the document at a time. If you are looking at one SAX element, you have no access to another. If you are looking at a text node, you have no access to a containing element. When you write a SAX application, you need to keep track of your program's position in the document somewhere in your own code. SAX does not do it for you. Also, if you need to look ahead in the XML document, you are just out of luck.
[...]
The specification provided by the W3C defines the DOM API for Java, ECMAScript, and OMG IDL. The Python mapping defined here is based in large part on the IDL version of the specification, but strict compliance is not required (though implementations are free to support the strict mapping from IDL). See section 13.6.3, ``Conformance,'' for a detailed discussion of mapping requirements.

DOM and SAX are used in Java programming, but they are by no means limited to it, nor did they originate with that language.  

SAX would still be a good option in python if you are simply scanning for the presence of certain tags in very large documents.

You are correct, though, that for some applications, ElementTree would likely be a more appropriate choice because it is easier to work with.

---

### Post by anthro398 on 2007-07-10
I really like 4suite, but their website has been down for awhile.  Great for doing xquery stuff.

---

### Post by flummoxed on 2007-07-19
Ok, I'm struggling to understand this ElementTree module. Here is what I want to do for simple code to get started:

[LIST]
[*]import the ElementTree module
[*]read the XML file and parse it
[*]get all the subelements of the "general" element, and then display their data
[/LIST]

I've managed to do the first two steps, but the third is eluding me. The only thing I seem to be able to do with this parsed XML file is see that the root is "Tutorial". I've been looking in the elementtree documentation for methods to do what I want to do, but I don't think I understand what I'm doing entirely. Parsing the file only seems to give me the root element, and nothing more. Like, after trying to manipulate the element "general" to no avail, I ran the method "iselement" on it to check whether or not it actually is being recognized as an element. The answer was false. 

Here is the code I have so far. Where do I go next?

```

# Initialize
import xml.etree.ElementTree as ET

# Read the XML file, then get the root element
tree = ET.ElementTree(file="tut1.xml")
elem = tree.getroot()

# This does not work. If I understand correctly, the list command should list all the subelements of general, but since general isn't being recognized as an element, it is not doing so
general = Element("general")
titleInfo = list(general)

```

---

### Post by pmasiar on 2007-07-19
Looks like you don't have element (tag) "general". What your XML is? Not all, just little relevant snippet. And read docs:

[http://effbot.org/zone/element-index.htm](http://effbot.org/zone/element-index.htm)
[http://effbot.org/zone/element.htm](http://effbot.org/zone/element.htm)

---

### Post by flummoxed on 2007-07-20
I posted the XML earlier in this thread. The element "general" is there. Here's the XML again.

```

<Tutorial>
	<general>
		<author>MaxMight</author>
  		<homepage>http://flummoxed.conforums.com</homepage>
  		<title>Test Tutorial</title>
  		<version>0.1</version>
	</general>
 
 	<content pages="10">
		<page id="1">
			<text xpos="center" ypos="top"> Welcome to the tutorial creator</text>
			<image xpos="center" ypos="center">image.png</image>
			<code xpos="center" ypos="bottom" lang="python">snippet1.py</code>
   		</page>
  	<page id="2">
			<text xpos="center" ypos="center">This page has only text</text>
	</page>
 	</content>
</Tutorial>

```

---

### Post by cwaldbieser on 2007-07-21
> **flummoxed said:**
> Ok, I'm struggling to understand this ElementTree module. Here is what I want to do for simple code to get started:

[LIST]
[*]import the ElementTree module
[*]read the XML file and parse it
[*]get all the subelements of the "general" element, and then display their data
[/LIST]

I've managed to do the first two steps, but the third is eluding me. The only thing I seem to be able to do with this parsed XML file is see that the root is "Tutorial". I've been looking in the elementtree documentation for methods to do what I want to do, but I don't think I understand what I'm doing entirely. Parsing the file only seems to give me the root element, and nothing more. Like, after trying to manipulate the element "general" to no avail, I ran the method "iselement" on it to check whether or not it actually is being recognized as an element. The answer was false. 

Here is the code I have so far. Where do I go next?

```

# Initialize
import xml.etree.ElementTree as ET

# Read the XML file, then get the root element
tree = ET.ElementTree(file="tut1.xml")
elem = tree.getroot()

# This does not work. If I understand correctly, the list command should list all the subelements of general, but since general isn't being recognized as an element, it is not doing so
general = Element("general")
titleInfo = list(general)

```


I have python 2.4, so I had to install an older version to try this out.  I also found the standard library docs to be somewhat sparse.  I actually guessed at attributes like "text" and "tag", which I couldn't find references to in the docs.
```

# Initialize
import sys
sys.path.append("/home/carl/lib/python/elementtree/")
import ElementTree
ET=ElementTree
# Read the XML file, then get the root element
tree = ET.ElementTree(file="test.xml")
elem = tree.getroot()

general_list = elem.findall("general")
for general in general_list:
    for elm in general:
        print "<%s> == '%s'" % (elm.tag, elm.text)

```
I hope this helps.

---

### Post by flummoxed on 2007-07-22
Wow, that worked. Thanks. I might need more help later on. :P

---

