---
title: "gtkmm working with xml"
date: 2010-09-13
forum: Programming Talk
---

### Post by bstree on 2010-09-13
hi  How do I work with xml files?  thanks  Ilan

---

### Post by worksofcraft on 2010-09-13
It not is so clear what you mean.
glade produces a .glade file for gtkmm which is encoded using xml.

However you don't have to know anything about the xml to use it gtkmm loads it, parses it and instantiates your gui for you.

Perhaps you can explain better what you need to know?

---

### Post by bstree on 2010-09-14
Thanks for the reply,

I want to write a xml file that will represent my data.
I am looking for a DOM xml parser that will do the job of writing / reading the file.

Ilan

---

### Post by bstree on 2010-09-14
Hi,

I found same thread on Old Nabble forum.
I will try to use libxml++
[http://libxmlplusplus.sourceforge.net/](http://libxmlplusplus.sourceforge.net/)

Ilan

---

### Post by SledgeHammer_999 on 2010-09-14
By the way what you need is some external library that parses xml. There are quite a few open source implementations. One of them is libxml++ as you mentioned. Another one is [RapidXml](http://rapidxml.sourceforge.net/). It claims that it is the fastest xml parser that exists till now. For me, the huge advantage of this is that it is headet-based. This means that you don't an external dependency on your program. Your program at compilation time has all the code it needs and ONLY that. So no extra huge library dependency. This library is also used by Boost's [Property Tree](http://www.boost.org/doc/libs/1_44_0/doc/html/property_tree.html) which also parses XML.


EDIT: Here's a [link](http://stackoverflow.com/questions/170686/best-open-xml-parser-for-c) to an another good thread on StackOverflow.

---

