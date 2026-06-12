---
title: "Python file reading"
date: 2007-08-18
forum: Programming Talk
---

### Post by Nekiruhs on 2007-08-18
Can anyone help me with this script? I'm trying to open a glade file (main.glade) in the same folder as my script, read the lines into a list, then iterate through them, printing the a segment of a line that matches the pattern ```
<widget class="(\w*)" id="(?P<widg>[a-zA-Z_]\w*)">
```
I want to return the group widg. I have tested this script on sample strings and it works, so I have a feeling that my way of accessing the file is wrong.

Heres the script:
```
#!/usr/bin/env python

import re
import gtk
import gtk.glade
import os

def extract_all():
    xml = open('main.glade').readlines()
    for line in xml:
        widget = re.match('''<widget class="(\w*)" id="(?P<widg>[a-zA-Z_]\w*)">''', line)
        if  widget:
            print widget.group('widg')
extract_all()
```

The XML file is attached (open it with a text editor)

---

### Post by scooper on 2007-08-19
It seems you're not accounting for whitespace at the start of the line.  Insert "\s*" at the beginning of the expression and it will give results.
```
#!/usr/bin/env python

import re
import gtk
import gtk.glade
import os

def extract_all():
    xml = open('main.glade').readlines()
    for line in xml:
        widget = re.match(''**'[COLOR="DarkRed"]\s*[/COLOR]**<widget class="(\w*)" id="(?P<widg>[a-zA-Z_]\w*)">''', line)
        if  widget:
            print widget.group('widg')
extract_all()
```

---

### Post by bashologist on 2007-08-19
Maybe use read() then I think there's a method named find_all() which will put all matches into a list or something. 

Can you have a question mark right after the opening parenthesis like that?
 ```
id="[COLOR="Red"](?[/COLOR]P<wi

```
That might cause problems at least in Perl I think.

---

### Post by Quikee on 2007-08-19
Is there a reason that you don't use elementtree? Because I can go to the main.glade and change:
```
<widget class="GtkVBox" id="vbox1">
```
to:
```
<widget 
       class="GtkVBox" 
       id="vbox1">
```

which is still perfectly valid XML and glade file but regex will not match any more. 

Try something like this with elementtree:
```

#!/usr/bin/env python

from elementtree import ElementTree

if __name__ == "__main__":	
	tree = ElementTree.parse("main.glade")
	root = tree.getroot()
	iter = root.getiterator("widget")
	for i in iter:
		print i.attrib

```

---

### Post by Nekiruhs on 2007-08-19
> **bashologist said:**
> Maybe use read() then I think there's a method named find_all() which will put all matches into a list or something. 

Can you have a question mark right after the opening parenthesis like that?
 ```
id="[COLOR="Red"](?[/COLOR]P<wi

```
That might cause problems at least in Perl I think.
Yeah, its for Named Capturing Groups, its a Python thing.

---

### Post by Nekiruhs on 2007-08-19
> **scooper said:**
> It seems you're not accounting for whitespace at the start of the line.  Insert "\s*" at the beginning of the expression and it will give results.
```
#!/usr/bin/env python

import re
import gtk
import gtk.glade
import os

def extract_all():
    xml = open('main.glade').readlines()
    for line in xml:
        widget = re.match(''**'[COLOR="DarkRed"]\s*[/COLOR]**<widget class="(\w*)" id="(?P<widg>[a-zA-Z_]\w*)">''', line)
        if  widget:
            print widget.group('widg')
extract_all()
```
Genius! Thank you, it works now! That would have never occurred to me.

---

### Post by pmasiar on 2007-08-19
parsing XML by manual regexes is sucker's game - use ElementTree, standard in py2.5

---

