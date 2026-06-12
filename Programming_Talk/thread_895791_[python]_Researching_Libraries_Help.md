---
title: "[python] Researching Libraries Help"
date: 2008-08-20
forum: Programming Talk
---

### Post by Titan8990 on 2008-08-20
What is the best way of determining what libraries are needed to import of a command? For example: [http://docs.python.org/lib/module-htmllib.html](http://docs.python.org/lib/module-htmllib.html)

That page from the reference manual describes the parser in the htmllib library. So I started with "import htmllib" thinking that would include the commands shown as examples for the htmllib library on the reference page. I was wrong.

I fooled with it for about 15min trying to get it to work. Kept getting "NameError: name 'parser' is not defined" error. This usually happened to me when I had not imported the correct library so I gave this a shot:

```
import parser
```

And I am a step further: "AttributeError: 'module' object has no attribute 'feed'"

So now I think I have got it down how it works so I try:

```
import feed
```

and I hit a brick wall with: "ImportError: No module named feed"


Any library researching tips for a newb?

---

### Post by days_of_ruin on 2008-08-20
Check for any files in the directory you working in to make sure
there is not any files named parser.

---

### Post by pmasiar on 2008-08-20
parser and feed live in sgmllib.

formatter is independent (fron htmllib) module

try one of:
[php]
from htmllib import HTMLParser
#or 
import formatter
[/php]

---

### Post by Titan8990 on 2008-08-20
Thanks for the try guys but still no luck:

```
>>> from htmllib import HTMLParser
>>> import urllib2
>>> xhtml_file = open("index.xhtml", "w")
>>> web = urllib2.urlopen('http://google.com')
>>> xhtml_file.write(web.read())
>>> xhtml_file.close()
>>> xhtml_file = open("index.xhtml", "r")
>>> parser.feed(open('index.xhtml').read())
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'parser' is not defined
>>> import formatter
>>> parser.feed(open('index.xhtml').read())
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'parser' is not defined
```

---

### Post by WW on 2008-08-20
feed() is a method of the HTMLParser object.  So, in that code snippet in the docs, it appears that **parser** must have already been created as an instance of an HTMLParser, e.g.
```

    parser = htmllib.HTMLParser(formatter)

```
That's as far as I got with the docs; I don't know anything about the "formatter" argument of the HTMLParser initialization method.

EDIT: [This discussion](http://cis.poly.edu/cs912/parsing.txt) looks useful.

---

### Post by pmasiar on 2008-08-20
As I said, parser and feed live in sgmllib, and you did not imported it.

What exactly you want to accomplish? What is your goal?

IMHO you may want to focus on learning basics little better before trying hard task like reliable parsing of random HTML/XML.

---

### Post by WW on 2008-08-20
> **pmasiar said:**
> As I said, parser and feed live in sgmllib, and you did not imported it.

HTMLParser *inherits* feed() from SGMLParser; SGMLParser is the base class of HTMLParser.  It should not be necessary to import sgmllib.

---

### Post by Titan8990 on 2008-08-21
I was going to use it for extra credit part 2 of programming challenge #4. I was going to use regular expression at first since I at least had a small amount of experience with that. The challenge was to pull the text betweeen <title></title> and use it as the name of a text file.


Why is some of the python documentation so poor? I understand that the reference manual is not meant to be a tutorial but I would think that the reference page would at least tell you what libraries you will need to import to match their example.


That documentation does look a bit better WW. When I'm fully woke up (had my coffee) I will look that over.

---

