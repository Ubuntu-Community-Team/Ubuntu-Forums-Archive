---
title: "Need an XML editor"
date: 2007-09-16
forum: Programming Talk
---

### Post by Falthon on 2007-09-16
I recently started learning XML, and I'm using GEdit as my XML editor.  I like it a lot, but it lacks a few features that I need.  

Can anyone suggest an open source XML editor with a clean, simple interface that can validate a schema as well as an XML document?  Ideally I would like one that can generate an XML document from a schema and vice versa, but that's not essential.  (I would probably stick with GEdit if it had validation.)

I tried mlview, but the validator doesn't provide very helpful error messages.  (On the document I'm working on now, it just says the name of the element and "Error".)  I appreciate any suggestions you can make.

---

### Post by Mr_Smiley on 2007-09-19
Try [XML Copy Editor]("http://xml-copy-editor.sourceforge.net/").

---

### Post by Falthon on 2007-09-19
That may be what I'm looking for.  I downloaded it and I'll try it out.  Thanks.

---

### Post by Falthon on 2007-09-23
I've been using XML Copy Editor for several days, and it's almost exactly what I need.  It can't generate an XML document from a schema or a schema from a document, but the author is planning to add that feature.  Thanks for pointing me to it; it's a great program.

---

### Post by Mr_Smiley on 2007-09-24
> **Falthon said:**
> I've been using XML Copy Editor for several days, and it's almost exactly what I need.  It can't generate an XML document from a schema or a schema from a document, but the author is planning to add that feature.  Thanks for pointing me to it; it's a great program.
Not a problem, glad to be of assistance. :)

---

### Post by Arwen on 2007-09-24
[http://www.screem.org](http://www.screem.org) <--- Screem is also an XML editor but I have no idea if it has the features you need.

---

### Post by Falthon on 2007-09-24
> **Arwen said:**
> [http://www.screem.org](http://www.screem.org) <--- Screem is also an XML editor but I have no idea if it has the features you need.

I couldn't figure out how to validate a document or schema with Screem.  Its menu options seem to be more focused towards HTML.

---

### Post by David A Knight on 2007-09-30
> **Falthon said:**
> I couldn't figure out how to validate a document or schema with Screem.  Its menu options seem to be more focused towards HTML.

It is more focused towards HTML.  It doesn't understand schemas and as such requires a dtd for some features in XML.   The structure aware features such as selecting the current element, selecting the parent element etc. will still all work however.

---

### Post by Geekkit on 2007-09-30
> **Mr_Smiley said:**
> Try [XML Copy Editor]("http://xml-copy-editor.sourceforge.net/").

Thanks for this one .... I hadn't seen this one before, and I like the features it has - very useful!

:)

EDIT: Wow, and it's memory foot print is minuscule even with large XML documents!

---

### Post by RomanIvanov on 2008-12-25
Please share the way you compile xml-copy-editor. I have problem with 

```
checking wxWidgets version... ./configure: line 19847: wx-config: command not found not found configure: error: wxWidgets is required. Try --with-wx-config.
```

wxWidgets is out of Ubuntu repository :(.

---

### Post by NEET on 2009-01-05
> **RomanIvanov said:**
> Please share the way you compile xml-copy-editor. I have problem with 

```
checking wxWidgets version... ./configure: line 19847: wx-config: command not found not found configure: error: wxWidgets is required. Try --with-wx-config.
```

wxWidgets is out of Ubuntu repository :(.

Try going in through Synaptic. It won't show up as "wxWidgets" per se, though. Just pick whatever looks like it's for C++ and has dev tags on it.
Same with all the other packages listed in the INSTALL file in the folder you download. Running a fresh install of Ibex, so I don't have anything at all.

---

### Post by RomanIvanov on 2009-01-05
thanks for reminding me about this post. I succeed in building/installing XML-COPY-EDITOR.

Here are strict steps how to do it: [http://sourceforge.net/forum/forum.php?thread_id=1809338&forum_id=475215](http://sourceforge.net/forum/forum.php?thread_id=1809338&forum_id=475215)

---

### Post by kaligus on 2009-07-27
thanks all for this recommendation...

and thanks Ubuntu for keeping these forums around and friendly so I could learn about this piece of hot buttered awesome with caramel sauce and a cherry on top as easily as I did with one simple search!!

Anyone who has been using something else has been using a lesser tool in my not so humble opinion!

The promised new features would make this an almost impossible to live without editor if XML is what you need to edit.

Can I get paid for some of this excitement?? ;)

---

### Post by datakid on 2009-10-06
+1 works on Karmic on eepc1000H. Steps to install:

Grab the deb
apt-get install libxerces-c28
dpkg -i /path/to/deb

Exactly what I was looking for, thanks.

---

### Post by kaligus on 2009-10-10
Having recently been introduced to geany I can add one there as well...

---

### Post by gjoellee on 2009-10-10
I am using Gedit (with some changed preferences)

---

### Post by brucewagner on 2010-03-01
This thread is very old.  What's the latest news?
Which one is best in 2010...?

---

### Post by RomanIvanov on 2010-03-02
just for log - here is issue in launchpad
[https://bugs.launchpad.net/ubuntu/+bug/283491](https://bugs.launchpad.net/ubuntu/+bug/283491)
at the end of the comments list - link to compiled packages on Launchpad.
And it will be available in 10.04 :).

---

### Post by hanniph on 2010-03-02
How about making vim [your XML editor]("http://www.pinkjuice.com/howto/vimxml/")?

---

### Post by guikubivan on 2010-04-29
Another plus for XML Copy Editor. I just wanted something that will pretty-print an xml file(XML -> Pretty-print) and this does that and more I am sure. :popcorn:

---

### Post by paulocoghi on 2010-12-07
Don't install the version files from their official website.

Instead, install it from Ubuntu Software Center:
[http://ubuntuforums.org/showthread.php?t=1640003](http://ubuntuforums.org/showthread.php?t=1640003)


That's it!

---

### Post by ArronB on 2010-12-09
I use Liquid Technologies [XML Editor]("http://www.liquid-technologies.com/xml-studio.aspx") software, comes with all the relevant instructions

---

### Post by jti on 2010-12-20
Hello ,
[www.on-xml.com]("http://www.on-xml.com")  is a free online xml editor with syntax highligth,dtd schema validation,dtd generator, autocomplete xslt-fo transformation and other feature...and you can store your xml files on your on-xml account on server . Have a nice day! :P

---

### Post by avl555 on 2011-03-19
There's also one called 'mlview' in the repositories. It's a very simple program, but it includes an validator and an XSL transformator button.

---

