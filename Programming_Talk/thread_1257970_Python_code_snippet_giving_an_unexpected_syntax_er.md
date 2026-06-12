---
title: "Python code snippet giving an unexpected syntax error: but I can't find the problem!"
date: 2009-09-04
forum: Programming Talk
---

### Post by AFarris01 on 2009-09-04
Hey all! I've been experimenting with using Python and XML together in a program I'm writing, but I decided that I wanted to be able to use my XML document as a regular python object. So, before I got started writing my own wrapper, I googled to see if someone had already done the same thing, and indeed they had: [http://code.activestate.com/recipes/534109/](http://code.activestate.com/recipes/534109/)

My problem is that the code does not appear to work. I just copied it verbatim from the website above, pasted it into a test python file with an attribution comment, then tried to run it to make sure it would work. here's the issue I get:

```

./test.py: line 48: syntax error near unexpected token `('
./test.py: line 48: `def xml2obj(src):'

```

I don't know what's causing this error. I even added another function above it to see if it was actually a problem with the code i downloaded... I added the following function:

```

def isafunction(self,args):
    pass

```
and when I run with that I get same error:
```

./test.py: line 48: syntax error near unexpected token `('
./test.py: line 48: `def isafunction(self,args):'

```
Can anybody explain this? :confused:
Thanks!

---

### Post by unutbu on 2009-09-04
The error is not on the lines you posted, but (probably) on the lines immediately before it. If the little bugger defies recognition, please post lines 1--48.

---

### Post by AFarris01 on 2009-09-04
lines 1-48 are just the 2 imports and a huge comment block... here it is though: 

```


import re
import xml.sax.handler

# This code is taken from: http://code.activestate.com/recipes/534109/
# Origional Code Author: Wai Yip Tung
#
# --------------- EXAMPLES FROM THE ABOVE PAGE -----------------------
#
#Discussion
#
#XML is a popular mean to encode data to share between systems. Despite its ubiquity, there is no straight forward way to translate XML to Python data structure. Traditional API like DOM and SAX often require undue amount of work to access the simplest piece of data.
#
#This method convert XML data into a natural Pythonic data structure. For example:
#
#>>> SAMPLE_XML = """<?xml version="1.0" encoding="UTF-8"?>
#... <address_book>
#...   <person gender='m'>
#...     <name>fred</name>
#...     <phone type='home'>54321</phone>
#...     <phone type='cell'>12345</phone>
#...     <note>&quot;A<!-- comment --><![CDATA[ <note>]]>&quot;</note>
#...   </person>
#... </address_book>
#... """
#>>> address_book = xml2obj(SAMPLE_XML)
#>>> person = address_book.person
#
#To access its data, you can do the following:
#
#person.gender        -> 'm'     # an attribute
#person['gender']     -> 'm'     # alternative dictionary syntax
#person.name          -> 'fred'  # shortcut to a text node
#person.phone[0].type -> 'home'  # multiple elements becomes an list
#person.phone[0].data -> '54321' # use .data to get the text value
#str(person.phone[0]) -> '54321' # alternative syntax for the text value
#person[0]            -> person  # if there are only one <person>, it can still
#                                # be used as if it is a list of 1 element.
#'address' in person  -> False   # test for existence of an attr or child
#person.address       -> None    # non-exist element returns None
#bool(person.address) -> False   # has any 'address' data (attr, child or text)
#person.note          -> '"A <note>"'
#
#This function is inspired by David Mertz' Gnosis objectify utilities. The motivation of writing this recipe is for simplicity. With just 100 lines of code packaged into a single function, it can easily be embedded with other code for ease of distribution.

#def isafunction(self,args):
#    pass

def xml2obj( self,src ):


```

the "import ro" is line 1, and the 'def' is line 48...  Would the comment make any difference?

---

### Post by The Cog on 2009-09-04
I pasted you snippet into a python prompt (with an added pass for the function body) and got no error. Odd.

You should be able to delete the comment lines - try it just in case. If it's still bad, maybe you can make a really short file containing just the few bad lines and post the file.

---

### Post by Can+~ on 2009-09-04
```
./test.py: line 48: syntax error near unexpected token `('
./test.py: line 48: `def xml2obj(src):'
```

Well, you're executing it directly and not defining a shebang?

```
**#!/usr/bin/env python**

import re
import xml.sax.handler

# This code is taken from: http://code.activestate.com/recipes/534109/
# Origional Code Author: Wai Yip Tung
#
# --------------- EXAMPLES FROM THE ABOVE PAGE -----------------------
#
# ... more stuff here ...

```

Or run it with [FONT="Courier New"]python test.py[/FONT].

---

### Post by AFarris01 on 2009-09-04
> **Can+~ said:**
> 

Well, you're executing it directly and not defining a shebang?

```
**#!/usr/bin/env python**

import re
import xml.sax.handler

# This code is taken from: http://code.activestate.com/recipes/534109/
# Origional Code Author: Wai Yip Tung
#
# --------------- EXAMPLES FROM THE ABOVE PAGE -----------------------
#
# ... more stuff here ...

```


OMG i Feel like an idiot. Thanks Can+~! That was what I was missing.:KS

---

### Post by The Cog on 2009-09-05
Doh!

---

### Post by nvteighen on 2009-09-05
Now I see why I thought that error message was weird... I was reading this thread and gazed upon this absolutely astonished... Python always raises an exception, but bash not :p

---

