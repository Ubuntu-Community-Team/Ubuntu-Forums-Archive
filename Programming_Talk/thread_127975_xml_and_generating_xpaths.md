---
title: "xml and generating xpaths"
date: 2006-02-10
forum: Programming Talk
---

### Post by rich on 2006-02-10
I'm wondering if anyone has any advice on processing xml docs (pref. in python).

I'd like to turn a xml doc into a list of xpaths relating to each bit of data. Something like

<apple>
 <size>4</size>
 <colour>blue</colour>
</apple>
<plum>
 <size>2</size>
 <colour>pink</colour>
</plum>

would be turned into
/apple/size
/apple/colour
/plum/size
/plum/colour

It sounds like a perfectly reasonable thing to do, but I cannot find a function that I can recycle. 


Anyone ?

cheers,
Rich

---

### Post by cwaldbieser on 2006-02-10
[QUOTE=rich]I'm wondering if anyone has any advice on processing xml docs (pref. in python).

I'd like to turn a xml doc into a list of xpaths relating to each bit of data. Something like

<apple>
 <size>4</size>
 <colour>blue</colour>
</apple>
<plum>
 <size>2</size>
 <colour>pink</colour>
</plum>

would be turned into
/apple/size
/apple/colour
/plum/size
/plum/colour

It sounds like a perfectly reasonable thing to do, but I cannot find a function that I can recycle. 


Anyone ?

cheers,
Rich[/QUOTE]

There are different ways you could do it, but I would think using one of the SAX APIs to blitz through the document would work.  You would basically create a stack of tag names, and when you reached a text node, you could contstruct the path from the current stack.

Something in xml.parsers.expat or xml.sax should do the trick, I think.

---

