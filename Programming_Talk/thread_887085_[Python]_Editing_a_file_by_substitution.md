---
title: "[Python] Editing a file by substitution"
date: 2008-08-11
forum: Programming Talk
---

### Post by GammaPoint on 2008-08-11
Hi, what I'd like to do is edit an input file for a calculation with Python. Let's say that I have an input file like the following

```

BLAH BLAH BLAH

Other inputs, Volume 940 m^3, maybe some more stuff

STUFF STUFF

```

So let's say I want to edit this file and change Volume from 940 to 950.

This is how I would guess I would do something like it:

```

import re
expr=r'.*Volume\s+(?P<VolValue>\d+[.]?[\d+]?)'
exprComp=re.compile(expr)
infile=open('myfile','r')
outfile=open('outfile','w')

for line in infile:
     match=exprComp.search(line)
     if match:
         newline=<HELP ME!>
         print >> outfile, newline
     else:
         print >> outfile, line
infile.close()
outfile.close()

```

So what I would like to do in the section labeled <HELP ME!> is to use something like the re.sub() function and replace the contents of the "VolValue" group with another number. However I am not sure how exactly to do this. Help please pythonistas :)

---

### Post by days_of_ruin on 2008-08-11
Does the input file have to be like that?It would be much
better if you used an xml file for data like that and used 
ElementTree module [http://www.learningpython.com/2008/05/07/elegant-xml-parsing-using-the-elementtree-module/]("http://www.learningpython.com/2008/05/07/elegant-xml-parsing-using-the-elementtree-module/").A whole lot simpler.

---

### Post by GammaPoint on 2008-08-11
> **days_of_ruin said:**
> Does the input file have to be like that?It would be much
better if you used an xml file for data like that and used 
ElementTree module [http://www.learningpython.com/2008/05/07/elegant-xml-parsing-using-the-elementtree-module/]("http://www.learningpython.com/2008/05/07/elegant-xml-parsing-using-the-elementtree-module/").A whole lot simpler.

Yeah, the input file is read by a different program that I'm not associated with. So it needs to be like that. That XML module you linked to is nice looking though- I might need that sort of thing with something I'll be doing in the next couple months.

---

### Post by days_of_ruin on 2008-08-11
Here ya go!:guitar:

```
import re
expr=r'.*Volume\s+(?P<VolValue>\d+[.]?[\d+]?)'
exprComp=re.compile(expr)
infile=open('myfile','r')
outfile=open('outfile','r+')

for line in infile:
    match=exprComp.search(line)
    if match:
        mynumber ="950"
        t = re.compile(match.group(1))

        s = t.sub(mynumber,line)
        print >> outfile, s
    else:
        print >> outfile,line
infile.close()
outfile.close()

```

---

### Post by ghostdog74 on 2008-08-12
no need re, simple string methods will do.
```

for line in open("file"): 
    n=line.strip().split()
    if "Volume" in line:
        n[n.index("Volume")+1]="950"
        print " ".join(n)
    else: 
        print line.strip()

```

---

