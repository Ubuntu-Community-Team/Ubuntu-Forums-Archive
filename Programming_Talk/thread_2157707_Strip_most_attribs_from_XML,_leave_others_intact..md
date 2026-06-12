---
title: "Strip most attribs from XML, leave others intact."
date: 2013-06-26
forum: Programming Talk
---

### Post by Balaam's Miracle on 2013-06-26
For a translation project i need a way to strip most attributes from an XML file, and leave other attributes intact.
Basically, i could write a bash script myself without too many problems, but the thing that got me stumped is what kind of command to use to get the unneeded attributes (and its values) stripped from each tag.

To make matters worse is that the attributes often continue on a newline, AND all indentations needs to be preserved exactly as it is.

To give an example of a source XML and the intended target :

Source : 
```
<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
<floater can_close="true" can_drag_on_left="false" can_minimize="true" can_resize="true"
         height="425" min_height="200" min_width="375" name="rlvLocks" title="Active RLV Locks" width="375"
         save_rect="true" save_visibility="true" single_instance="true">
  <scroll_list bottom="-410" left="2" right="-2" draw_border="false" follows="top|left|bottom|right" height="390" multi_select="false"
               name="lock_list" draw_heading="true" draw_stripes="true" layout="topleft">
    <column label="Lock Type" name="lock_type" width="110" />
    <column label="Add / Rem" name="lock_addrem" width="65" />
    <column label="Lock Target" name="lock_target" width="150" />
    <column label="Held By" name="lock_origin" width="150" />
  </scroll_list>
</floater>

```

Target:
```

<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
<floater name="rlvLocks" title="Active RLV Locks">
  <scroll_list name="lock_list">
    <column label="Lock Type" name="lock_type" />
    <column label="Add / Rem" name="lock_addrem" />
    <column label="Lock Target" name="lock_target" />
    <column label="Held By" name="lock_origin" />
  </scroll_list>
</floater>

```

There are a few other attributes that will need to be preserved, but i think you will get the idea from my example above.
So my big question is : which command should i use? Please don't say sed or awk, because i don't understand the syntax and regex stuffs (i'm not much of a programmer, really. More of a translator).

Can you help me? I would so appreciate it!

---

### Post by ofnuts on 2013-06-26
Of course, neither sed or awk because even with only regexps it will be quite hard to  be foolproof.

Then there is this very clever solution: [http://stackoverflow.com/questions/893585/how-to-parse-xml-in-bash](http://stackoverflow.com/questions/893585/how-to-parse-xml-in-bash) (and then use sed to remove attributes)

But all in all it's really better to write your own python or perl script based on their XML parsing libraries.

---

### Post by Vaphell on 2013-06-26
i whipped up something like this
```
#!/usr/bin/env python

import sys
import xml.etree.ElementTree as ET
#doc http://docs.python.org/2/library/xml.etree.elementtree.html

def strip_attrs( e ):
  for a in e.attrib.keys():
    if a not in preserve:
      del e.attrib[a]

preserve = ( 'name', 'label', 'title' )

f = open( sys.argv[1] )
xmlheader = f.readline().strip()
tree = ET.parse( f )
xmlroot = tree.getroot()

for e in xmlroot.findall('.')+xmlroot.findall('.//*'):
  strip_attrs( e )

#tree.write( 'out.xml', xml_declaration=True ) # python 2.7+ ?
print xmlheader
print ET.tostring( xmlroot ) 
f.close()
```

```
**$ ./xml_strip_attrs.py in.xml**
<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
<floater name="rlvLocks" title="Active RLV Locks">
  <scroll_list name="lock_list">
    <column label="Lock Type" name="lock_type" />
    <column label="Add / Rem" name="lock_addrem" />
    <column label="Lock Target" name="lock_target" />
    <column label="Held By" name="lock_origin" />
  </scroll_list>
</floater>
```

probably could be made prettier with features that were added in 2.7+ but i couldn't be bothered to run vm so had to work with 2.6.5

---

### Post by Balaam's Miracle on 2013-06-26
> **Vaphell said:**
> i whipped up something like this
```
#!/usr/bin/env python

import sys
import xml.etree.ElementTree as ET
#doc http://docs.python.org/2/library/xml.etree.elementtree.html

def strip_attrs( e ):
  for a in e.attrib.keys():
    if a not in preserve:
      del e.attrib[a]

preserve = ( 'name', 'label', 'title' )

f = open( sys.argv[1] )
xmlheader = f.readline().strip()
tree = ET.parse( f )
xmlroot = tree.getroot()

for e in xmlroot.findall('.')+xmlroot.findall('.//*'):
  strip_attrs( e )

#tree.write( 'out.xml', xml_declaration=True ) # python 2.7+ ?
print xmlheader
print ET.tostring( xmlroot ) 
f.close()
```

probably could be made prettier with features that were added in 2.7+ but i couldn't be bothered to run vm so had to work with 2.6.5

This is awesome, it does exactly what i need! I also find it easy to add further attribs if/when so desired.
I do however have a few additional wishes which i failed to mention in my original post, which is my fault entirely.

Is it possible to (without too much hassle):
1 - Retain commented parts of the source XML?.
2 - Iterate over all the XML files within a directory and write the output files to a subfolder below the working dir? (eg. ./myfile.xml > ./newdir/myfile.xml).

Having said that, your code is already in a very usable state. It's just that i have 249 files to process and doing these one-by-one would be a bit of a kerfuffle ((c) Little Britain :-)).
Also, retaining comments would be great since there will be other translators after me, and they may need some hints or explanation here and there. For example, "show cookie" could refer to a cookie as served to a browser, or a cookie that you can munch on. If i could include (and keep) the comment that the cookie is the kind that you can eat, then that would help other translators a lot.

I should have mentioned these things in my original post though, i now worry that i might come off as ungrateful for the help you've already given...

---

### Post by Vaphell on 2013-06-26
2 is not a problem you can easily wrap the script call in a bit of bash

```
mkdir newdir
for f in *.xml; do ./scriptname.py "$f" > "newdir/$f"; done
```

but 1... this might stink because i suspect parsing and rebuilding from scratch might drop comments in the process. Care to give some small example of input and output accounting for these comments?
which version of python do you have?
```
python --version
```

**edit:**
```
#!/usr/bin/env python

import sys
import xml.etree.ElementTree as ET
#doc http://docs.python.org/2/library/xml.etree.elementtree.html

# preserving comments, from http://bugs.python.org/issue8277 
class CommentedTreeBuilder ( ET.XMLTreeBuilder ):
  def __init__ ( self, html = 0, target = None ):
    ET.XMLTreeBuilder.__init__( self, html, target )
    self._parser.CommentHandler = self.handle_comment
  def handle_comment ( self, data ):
    self._target.start( ET.Comment, {} )
    self._target.data( data )
    self._target.end( ET.Comment )

def strip_attrs( e ):
  for a in e.attrib.keys():
    if a not in preserve:
      del e.attrib[a]

preserve = ( 'name', 'label', 'title' )

f = open( sys.argv[1] )
xmlheader = f.readline().strip()
tree = ET.parse( f, parser=CommentedTreeBuilder() )
xmlroot = tree.getroot()

for e in xmlroot.findall('.')+xmlroot.findall('.//*'):
  strip_attrs( e )

#tree.write( 'out.xml', xml_declaration=True ) # python 2.7+
print xmlheader
print ET.tostring( xmlroot ) 
f.close()
```

after inserting some comment
```
**$ ./xml_strip_attrs.py in.xml**
<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
<floater name="rlvLocks" title="Active RLV Locks">
  [COLOR="#0000FF"]<!--  wut wut wut  -->[/COLOR]
  <scroll_list name="lock_list">
    <column label="Lock Type" name="lock_type" />
    <column label="Add / Rem" name="lock_addrem" />
    <column label="Lock Target" name="lock_target" />
    <column label="Held By" name="lock_origin" />
  </scroll_list>
</floater>

```

---

### Post by Balaam's Miracle on 2013-06-26
> **Vaphell said:**
> 2 is not a problem you can easily wrap the script call in a bit of bash

```
mkdir newdir
for f in *.xml; do ./scriptname.py "$f" > "newdir/$f"; done
```


Yes, i already had the bash wrapper (albeit not as efficient as yours), though i was kinda-sorta hoping that it could be part of the python code, since python would work on many different platforms whereas bash would not. No biggie though, because it still works. :-)

> 
which version of python do you have?


I am running Python 2.7.4, but backwards compatibility is always a good idea :-)

**edit:**
```
#!/usr/bin/env python

import sys
import xml.etree.ElementTree as ET
#doc http://docs.python.org/2/library/xml.etree.elementtree.html

# preserving comments, from http://bugs.python.org/issue8277 
class CommentedTreeBuilder ( ET.XMLTreeBuilder ):
  def __init__ ( self, html = 0, target = None ):
    ET.XMLTreeBuilder.__init__( self, html, target )
    self._parser.CommentHandler = self.handle_comment
  def handle_comment ( self, data ):
    self._target.start( ET.Comment, {} )
    self._target.data( data )
    self._target.end( ET.Comment )

def strip_attrs( e ):
  for a in e.attrib.keys():
    if a not in preserve:
      del e.attrib[a]

preserve = ( 'name', 'label', 'title' )

f = open( sys.argv[1] )
xmlheader = f.readline().strip()
tree = ET.parse( f, parser=CommentedTreeBuilder() )
xmlroot = tree.getroot()

for e in xmlroot.findall('.')+xmlroot.findall('.//*'):
  strip_attrs( e )

#tree.write( 'out.xml', xml_declaration=True ) # python 2.7+
print xmlheader
print ET.tostring( xmlroot ) 
f.close()
```

Works like an absolute charm! I love you!!! 
I am going to mark this as solved, but will keep checking back here :-)

---

### Post by Vaphell on 2013-06-26
it certainly kinda sorta could be done inside the program though the amount of boilerplate code for file management would be much much higher (juggling files is what shells do for a living and nothing can compete with them at that job) and it would be inherently less flexible. python file that does only the hard part allows you to use it with any number of files and print to screen/redirect results anywhere you want. You gain flexibility, scalability and full control.

different platforms - do you mean windows here? writing direct .bat equivalent of that shell code should be trivial with a bit of google (batch for loop, batch redirection)

---

