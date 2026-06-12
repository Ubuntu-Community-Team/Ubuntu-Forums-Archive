---
title: "ElementTree and Python"
date: 2009-05-06
forum: Programming Talk
---

### Post by MaxVK on 2009-05-06
Hi, I have an XML file (snippet below), and I am using ElementTree to parse it and load it into a wxTreeCtrl. I am able to add items to the tree and save these changes back to the XML file, however, I have come unstuck when it comes to removing items from the tree. See below:

SNIPPET OF XML FILE
```
<tree>
    <category title="Item 1">item 1 text
        <subitem title="subitem1">subitem1 text</fileitem>
        <subitem title="subitem2">subitem2 text</fileitem>
    </category>
   
    <category title="Item 2">item 2 text
        <subitem title="subitem21">subitem21 text</fileitem>
        <subitem title="subitem22">subitem22 text</fileitem>
    </category>
</tree>
``` 

PYTHON CODE
```
import xml.etree.cElementTree as ET
    ...
    ...
    ...
    self.xml = ET.parse(self.fpath)
    ...
    ...
    ...
    titem = "subitem21"
    xml = self.xml.getroot()
    iterator = xml.getiterator("subitem")
    for item in iterator:
        text = item.attrib["title"]
        if text == titem:
            xml.remove(item)
```

By rights I should be able to remove the element 'item' in this code, but no matter which way I play with this, the best I get is the following error:
"ValueError: list.remove(x): x not in list" 

I have hunted for an answer to this for hours now and I have had no luck at all. There are lots of ways to iterate through the ElementTree structure, but in every single case, once I reach the correct item (Or any item for that matter) and try to remove() it, I get the same error.

Anyone got any ideas please - I'm stumped and going in circles at the moment.

Cheers

Max

BTW: Just in case it matters - I am currently on 7.10 using Python 2.8.9.2

---

### Post by dandaman0061 on 2009-05-06
Well first of all, it looks like you posted an error in your code (probably from your copying/translating to here)
The 'subitem' lines are closed with </fileitem>, so those need to be changed to </subitem>

Secondly, I haven't worked with the XML module at all, but playing with your code a bit, I'm pretty sure the problem is that you are trying to remove an element that is actually a level deeper than what you are trying to do.

```

>>> xm = ET.parse('tmp.xml')
>>> xm_root = xm.getroot()
>>> for x in xm_root:
...     print x
...
<Element 'category' at 0xb7e9f998>
<Element 'category' at 0xb7e9fa10>
>>> for x in xm_root:
...     for y in x:
...             print y
...
<Element 'subitem' at 0xb7e9f9e0>
<Element 'subitem' at 0xb7e9f9c8>
<Element 'subitem' at 0xb7e9fa28>
<Element 'subitem' at 0xb7e9fa40>

```

hopefully that makes sense.  you are trying to remove a 'subitem' from root, but root only contains 'category' objects.  Like I said, I haven't used or looked at the XML module past this, so your 'remove' call may be valid or there may be another function that does what you want (deleting item from root).

P.S.  I'm pretty sure that is an invalid version of Python that you stated.  2.6/3.0 is the last stable, and 2.7 is under development.

---

### Post by MaxVK on 2009-05-06
Errors! Yeah I'm typing loads of them today - The example was typed out so thats why I got things wrong.

Your code: Excellent! That did the trick with much less code! Thank you very much indeed!

best regards

Max

As an aside, how are you finding Jaunty? I have the disk (came today) and I'm planning on installing in the next few days.

---

