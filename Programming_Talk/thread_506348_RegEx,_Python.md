---
title: "RegEx, Python"
date: 2007-07-21
forum: Programming Talk
---

### Post by skeeterbug on 2007-07-21
Hello,
I have a regex that I am using to match a piece of HTML from a fairly large document (the HTMLParser class was giving me malformed exceptions, I guess it is common in that library). The reason I don't really need a HTML/XML Parser to do this, is that I have only one thing I need to find. I was doing my regex in Expresso, and it found the html block I wanted, when I go to use it in Python, I get nothing.

Here is the regex:
```

reg = re.compile(r'<span\sid="replaceFaction">(?P<faction>\w+)', re.MULTILINE | re.DOTALL)
```

reg.match(htmlstring) returns Nothing. The html string I am searching for looks like this:
```
<span id="replaceFaction">Alliance
```
or
```
<span id="replaceFaction">Horde
```

Any obvious errors I am making? I am a bit new to Python, so I don't know of the <> or " characters are throwing this off. Thanks in advance for any help.

---

### Post by bbzbryce on 2007-07-21
This works perfect for me:
```
import re
reg = re.compile(r'<span\sid="replaceFaction">(?P<faction>\w+)', re.MULTILINE | re.DOTALL)
html = '<span id="replaceFaction">Alliance'
match = reg.match(html)
print match.group(1)
```

---

### Post by skeeterbug on 2007-07-21
Yeah that works for me too, try this:

```

import re
import urllib

url = 'http://armory.worldofwarcraft.com/guild-info.xml?r=Eredar&n=Corruption&p=1'
opener = urllib.FancyURLopener({})
f = opener.open(url)
content = f.read()
reg = re.compile(r'<span\sid="replaceFaction">(?P<faction>\w+)', re.MULTILINE | re.DOTALL)
match = reg.match(content)
print match.group(1)

```

---

### Post by bbzbryce on 2007-07-21
I see now. Your problem is with the javascript in the page. The html by itself doesn't have anything in between the span tags:

```
<span id="replaceFaction"></span>
```

You'll have to process the javascript somehow to get the information you need.

---

### Post by bbzbryce on 2007-07-21
I did a little research for you, this is the javascript that gets the faction:

```
var theRace = 8;

                if (theRace == 1 || theRace == 3 || theRace == 4 || theRace == 7 || theRace == 11) {
                        document.getElementById('replaceFaction').innerHTML = "Alliance";
                } else {
                        document.getElementById('replaceFaction').innerHTML = "Horde";
                }
```


So I'd recommend regexing for the value of theRace as above and then applying the same if else statement.

---

### Post by skeeterbug on 2007-07-21
> **bbzbryce said:**
> I see now. Your problem is with the javascript in the page. The html by itself doesn't have anything in between the span tags:

```
<span id="replaceFaction"></span>
```

You'll have to process the javascript somehow to get the information you need.
 
Ahh thanks for the help, I can't believe I didn't see that. I copied the page source from an already rendered page in FF.

---

### Post by pmasiar on 2007-07-21
Using regex to match HTML is sucker's game (I know I do it too :-) ). For solid solution, use ElementTree instead, all corner cases solved for you.

---

### Post by skeeterbug on 2007-07-21
> **pmasiar said:**
> Using regex to match HTML is sucker's game (I know I do it too :-) ). For solid solution, use ElementTree instead, all corner cases solved for you.

Is there an easy way to get it installed on a shared host? I only need to grab one thing out of this html document, the app's main ability is not to pull or build html docs.



I came up with ```
reg = re.compile(r'var\stheRace\s=\s(?P<race>\w+)', re.MULTILINE | re.DOTALL)
```

Works on a test string, but not the content yet again. Argh.

---

### Post by skeeterbug on 2007-07-21
Just changed the front to .*, as I don't care what the first part is, just the number. Works now :)

---

### Post by pmasiar on 2007-07-21
Famous dot-star sometimes pronounced death-star: read [Death to Dot Star!](http://www.perlmonks.org/?node_id=24640)

---

### Post by skeeterbug on 2007-07-23
> **pmasiar said:**
> Famous dot-star sometimes pronounced death-star: read [Death to Dot Star!](http://www.perlmonks.org/?node_id=24640)

Not a bad read. For some reason it wasn't matching without it. I tried everything, newline, etc. Not sure what it's problem was, the Espresso IDE I was using matched it OK without the dot star.

---

