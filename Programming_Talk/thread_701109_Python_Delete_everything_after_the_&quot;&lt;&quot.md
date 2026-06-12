---
title: "Python: Delete everything after the &quot;&lt;&quot;(Advanced string formatting)"
date: 2008-02-19
forum: Programming Talk
---

### Post by xelapond on 2008-02-19
I am writing a really simple applet to be able to take any part of a web page and parse it into plain text that a human can rad, and deliver it to there desktop.  This is more of a learning experience, because I am kind of new to python, I did follow the entire tutorial though.  This one piece has me stumped though.

How would I convert a string like

Hello World<Goodbye World

and make python delete the "<" and everything after it?

Thanks, 

Alex

---

### Post by LaRoza on 2008-02-19
[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

You will find several methods there that you can use.

Depending on what you want, you can split the string into several using whatever character you wish as the delimiter (returns a tuple) with split().

```

>>> str = "Hello world<Goodbye World"
>>> print str.split("<")
['Hello world', 'Goodbye World']

```

---

### Post by ghostdog74 on 2008-02-19
> **xelapond said:**
> , I did follow the entire tutorial though.

looks like not enough. You should also read the library docs.

> 
  This one piece has me stumped though.

How would I convert a string like

Hello World<Goodbye World

and make python delete the "<" and everything after it?

Thanks, 

Alex

```

>>> s="Hello World<Goodbye World"
>>> print s.split("<")[0]
Hello World
>>> s[:s.index("<")]
'Hello World'

```

---

### Post by Erdaron on 2008-02-19
A brute force and unrefined way:

[PHP]blah = 'hello world<goodbye world'
blah = blah[0:blah.index('<')][/PHP]

---

### Post by xelapond on 2008-02-19
Thanks everyone, I got it working.

Im reading the library doc now, hopefully I can figure these out on my own in the future.

---

### Post by pmasiar on 2008-02-19
Parsing HTML/XML by hand is sucker's game - too many exceptions. 

Instead, use HTML/XML parser. ElementTree is good for well-formed HTML, I am told that BeautifulSoup can handle also malformed (as in random webpage) HTML. All these parses have function to get the text, excluding tags.

---

### Post by slavik on 2008-02-19
if you want to delete stuff starting at some character, I would advise against using split ... the Perl hacker in me says to use substitution: s/<.*// :) or you can do the array slice that someone suggested to only keep the part you want :)

---

