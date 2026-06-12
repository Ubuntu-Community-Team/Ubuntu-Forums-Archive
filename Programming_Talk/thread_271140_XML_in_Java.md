---
title: "XML in Java"
date: 2006-10-04
forum: Programming Talk
---

### Post by welshboy on 2006-10-04
Hi folks,

I'm writing a stock management system using Java and XML.  I would have used MySQL but I can't seem to get the damn thing set up properly so I've given up.

I've written the XML Schema and the XML file it self, that will contain the document, and I'm in the process of writing the administrator window that will edit the XML document.

What I want to do is, to have like a Point of Sale interface for a till.  And what I want is for a row of buttons to appear in the centre, and a table of the purchased products on the left of that.  Which will of course use the data from the XML file, which will have item description and price.

What I want to know is, should I load the XML file into another data structure such as a Vector before I begin to manipulate it?  I've never done this before, so like captain Kirk, I'm going out beyond the final frontier(for me!!)

Any help would be much obliged.

welshboy

---

### Post by Shin_Gouki2501 on 2006-10-04
its pretty easy, use XML DOM (maybe u need to use some 3rd party API just google arround)
search google for:
xml write , read dom java examples :)

wbr Shin Gouki

---

### Post by amo-ej1 on 2006-10-05
Basicly java has onboard support for two types of XML api's. The typical SAX and DOM like api's. The first one is scalable and fast and will generate events while parsing the document but you can't use it to update the xml file. The second one DOM is slower, it reads the entire file to memory and you can browse through the document that way and get the data you want. You can easily update it an write the changes back but it becomes an issue when files get extremely large. (but you shouldn't create that large xml files anyhow :p)

---

### Post by amo-ej1 on 2006-10-05
This: [http://java.sun.com/webservices/jaxp/learning/tutorial/index.html](http://java.sun.com/webservices/jaxp/learning/tutorial/index.html) will get you started ;)

---

### Post by welshboy on 2006-10-05
cool, thanks dude :)

---

