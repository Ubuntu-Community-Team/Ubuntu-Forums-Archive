---
title: "Unicode text input in Python programming"
date: 2010-01-18
forum: Programming Talk
---

### Post by SnappyU on 2010-01-18
Hi,

I'm just starting to writing a POC (proof-of-concept) app in python to receive unicode (Chinese) text input.

I'm using Tkinter libraries.  But the default Entry widget do not seem to support unicode text input.  Searches on google return not much of a solution except for cries for help dating back to 2000!

In 2010, I really don't want to have to code a text entry class just to support unicode.  

Any ideas how I can do it in Tkinter or should I restart with another GUI library for Python, eg pyGTK, QT or something?  Or should I choose another language altogether?

The app is targeted to run on:

[LIST=1]
[*]Ubuntu & Windows XP
[*]Use either access database (mdb) or sqlite3
[*]Support Unicode (Chinese) text input
[/LIST]

---

### Post by SnappyU on 2010-01-18
ok, I just tried a sample app inn using pyGTK and it supports Chinese text input.

Anyone have any idea how I can get this to work in Tkinter without resorting to pyGTK?  I hope to keep external libraries to a minimum.

---

### Post by Can+~ on 2010-01-18
Python3 has native Unicode support for strings (and old ascii strings are renamed as bytearrays). I would assume that TK in Python3 would support unicode too.

---

### Post by Narayana on 2010-08-02
I tried adding the so called "Magic comment" at the top of the file:
# This programme uses unicode characters encoding: UTF-8

and the unicode text got displayed..(python 2.6.3.0, Ubuntu Jaunty)
My problem however is that the Telugu lanugage text input is mangled at the top.. am unable to crack the issue..any ideas?

---

### Post by SnappyU on 2010-10-28
> **Narayana said:**
> I tried adding the so called "Magic comment" at the top of the file:
# This programme uses unicode characters encoding: UTF-8

and the unicode text got displayed..(python 2.6.3.0, Ubuntu Jaunty)
My problem however is that the Telugu lanugage text input is mangled at the top.. am unable to crack the issue..any ideas?
Sorry for the belated reply.  Just enabled the thread subscription.

Did you managed to get the mangled text fixed?
What is the problem you faced?  Details?

---

### Post by worksofcraft on 2010-10-28
```

$> ./digits.py
&#38646;&#22777;&#36144;&#21441;&#32902;&#20237;&#38470;&#26578;&#25420;&#29590;
&#2406;&#2407;&#2408;&#2409;&#2410;&#2411;&#2412;&#2413;&#2414;&#2415;
&#1632;&#1633;&#1634;&#1635;&#1636;&#1637;&#1638;&#1639;&#1640;&#1641;

```

Seems to work with following:
[php]
#!/usr/bin/python
# -*- coding: utf-8 -*-

for line in ["&#38646;&#22777;&#36144;&#21441;&#32902;&#20237;&#38470;&#26578;&#25420;&#29590;", "&#2406;&#2407;&#2408;&#2409;&#2410;&#2411;&#2412;&#2413;&#2414;&#2415;", "&#1632;&#1633;&#1634;&#1635;&#1636;&#1637;&#1638;&#1639;&#1640;&#1641;"]:
    print line
[/php]

so I tried this:
[php]
#!/usr/bin/python
# -*- coding: utf-8 -*-

import fileinput
for line in fileinput.input():
    print line
[/php]

and that seems to read them ok...

```

$ echo "&#38646;&#22777;&#36144;&#21441;&#32902;&#20237;&#38470;&#26578;&#25420;&#29590;&#2406;&#2407;&#2408;&#2409;&#2410;&#2411;&#2412;&#2413;&#2414;&#2415;&#1632;&#1633;&#1634;&#1635;&#1636;&#1637;&#1638;&#1639;&#1640;&#1641;"|./digits.py
&#38646;&#22777;&#36144;&#21441;&#32902;&#20237;&#38470;&#26578;&#25420;&#29590;&#2406;&#2407;&#2408;&#2409;&#2410;&#2411;&#2412;&#2413;&#2414;&#2415;&#1632;&#1633;&#1634;&#1635;&#1636;&#1637;&#1638;&#1639;&#1640;&#1641;

```

---

### Post by SnappyU on 2010-10-28
hmmm ... so u got it to work in python?

btw, I think php is diff fr python right?

---

### Post by worksofcraft on 2010-10-28
> **SnappyU said:**
> hmmm ... so u got it to work in python?

btw, I think php is diff fr python right?

Yes, PhP is an C/C++ like interpreted language that usually runs on web servers to filter HTML files. If you do not specify encoding for PhP I think it defaults to ISO-8859-1 which AFIK only does European languages. I don't know much about PhP except that I hate it ;)

p.s. the trick in Python seems to be that second line:
# -*- coding: utf-8 -*- 

and it HAS TO BE the second line too I think or it gets ignored :Shock:

p.s. #2:
If you are after Utf-8 for PhP... this web page looks like a really practical solution: [http://webcollab.sourceforge.net/unicode.html](http://webcollab.sourceforge.net/unicode.html)

---

### Post by spam12345 on 2012-04-07
I had the same problem and found this thread by google. 

Programs with gui built with tkinter can not take unicode text input on Ubuntu (using iBus Input method). Some reported it works fine on Windows. A pretty good example is the Python IDLE itself (also built with tkinter). I can't type unicode texts (using ibus) in it.   

I wonder if you guys have found a fix or work-around?

---

