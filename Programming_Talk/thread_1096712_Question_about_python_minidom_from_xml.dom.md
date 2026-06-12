---
title: "Question about python minidom from xml.dom"
date: 2009-03-15
forum: Programming Talk
---

### Post by smetj on 2009-03-15
Hi all,

I am wondering why the following returns empty results:
print commandlet.firstChild.toxml()
print commandlet.childNodes[0].toxml() #this is the same as firstChild
print commandlet.childNodes[2].toxml()

It must be something I overlook, ... but I can't put my finger on it.
Thanks for having a look on it, 

Here's the complete picture:

>>> from xml.dom import minidom
>>> xmldoc = minidom.parse('/tmp/test.xml') 
>>> print xmldoc.firstChild.toxml()
<commandlet>
    <properties>
        <version>0.1 Beta</version>
        <name>test</name>
        <description>just a test</description>
        <author>somebody</author>
        <platform>linux2</platform>
        <exitcode>0</exitcode>
        <errors/>
        <totaltime>3.19</totaltime>
    </properties>
    <grid>
        <row number="2">
            <column number="8" value="100"/>
        </row>
        <row number="3">
            <column number="8" value="97.8"/>
        </row>
        <row number="4">
            <column number="8" value="97.7"/>
        </row>
        <row number="5">
            <column number="8" value="97.6"/>
        </row>
    </grid>
</commandlet>


>>> commandlet=xmldoc.firstChild
>>> print commandlet.firstChild.toxml()

   
>>> print commandlet.childNodes[0].toxml()

   
>>> print commandlet.childNodes[1].toxml()
<properties>
        <version>0.1 Beta</version>
        <name>test</name>
        <description>just a test</description>
        <author>somebody</author>
        <platform>linux2</platform>
        <exitcode>0</exitcode>
        <errors/>
        <totaltime>3.19</totaltime>
    </properties>
>>> print commandlet.childNodes[2].toxml()

   
>>> print commandlet.childNodes[3].toxml()
<grid>
        <row number="2">
            <column number="8" value="100"/>
        </row>
        <row number="3">
            <column number="8" value="97.8"/>
        </row>
        <row number="4">
            <column number="8" value="97.7"/>
        </row>
        <row number="5">
            <column number="8" value="97.6"/>
        </row>
    </grid>
>>>

---

### Post by WW on 2009-03-15
The newlines in your XML document become Text nodes in your DOM object:
```

In [28]: commandlet.firstChild
Out[28]: 
<DOM Text node "
">

In [29]: commandlet.firstChild.toxml()
Out[29]: u'\n'

In [30]: print commandlet.firstChild.toxml()



In [31]: commandlet.childNodes[0]
Out[31]: 
<DOM Text node "
">

In [32]: commandlet.childNodes[1]
Out[32]: <DOM Element: properties at 0x1524468>

In [33]: commandlet.childNodes[2]
Out[33]: 
<DOM Text node "
">

In [34]: commandlet.childNodes[3]
Out[34]: <DOM Element: grid at 0x1524a08>

In [35]: 


```
See how the first and third children of commandlet are Text nodes? In sample statements that you used, the functions are not returning empty results.  The print statements are simply printing the single newline character in the Text nodes.

---

### Post by smetj on 2009-03-29
Excellent! It's so obvious :)
Thanks!

---

