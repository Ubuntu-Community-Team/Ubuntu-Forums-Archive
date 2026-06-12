---
title: "python: splliting a file using a word"
date: 2008-04-15
forum: Programming Talk
---

### Post by bala_biophy on 2008-04-15
Dear Friends,

I have attached below the sample of a file im processing,

 step =     1000   tps =    3746  tk =   301  ps =   248
 E1   =    -86920  E2   =     18487  E3      =   -105407
                                                                                                                                                             
------------------------------------------------------------------------------
                                                                                                                                                             
 step =     2000   tps =    3748  tk =   300  ps =  -150
 E1   =    -87032  E2   =     18386  E3      =   -105419
                                                                                                                                                             
------------------------------------------------------------------------------
                                                                                                                                                             
 step =     3000   tps =    3750.000  tk =   302  ps =    50
 E1   =    -87089  E2   =     18502  E3      =   -105591
                                                                                                                                                             
------------------------------------------------------------------------------

My objective is to extract the values of the  variable (tps,tk etc)  for each step value and arrange them in columns. I would like to know how i can split the file contents by the word "step".   I would also appreciate any better way to do the same.

Thanks,
Bala

---

### Post by themusicwave on 2008-04-15
All the string methods you need are here: [http://docs.python.org/lib/string-methods.html]("http://docs.python.org/lib/string-methods.html")

Basically it will look something liek this

[PHP]

text = open(path_to_file).read()
text = text.split("step")

[/PHP]

You could also split it at spaces or tabs.  If the data file is something you are producing I would recommend using commas to delimit the data.

---

### Post by ghostdog74 on 2008-04-15
how would you want your final output to look like?

---

### Post by meastp on 2008-04-15
check [http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

suggestion:

```
thefile2 = thefile.replace( ' = ', '=')
thelist = thefile2.split()

#thelist = [ 'step', 1000,  'tps', 3746, 'tk', 301 etc. ]

thedictionary = dict([(x,x+1) for x in thelist])

#thedictionary = { 'step':1000, 'tps':3746 etc..
```

---

### Post by Martin Witte on 2008-04-15
I would go for  [regular expressions]("http://docs.python.org/lib/module-re.html"), for a start you can parse the first type of lines as
[PHP]#!/usr/bin/env python
import re
line = 'step = 1000 tps = 3746 tk = 301 ps = 248'
m = re.match(r"step\s=\s(?P<step>\d+)\stps\s=\s(?P<tps>\d+)\stk\s=\s(?P<tk>\d+)\sps\s=\s(?P<ps>\d+)", line)
if m:
    print m.groupdict()[/PHP]

the result of this snippet will be; {'ps': '248', 'step': '1000', 'tps': '3746', 'tk': '301'}

---

