---
title: "python syntax error"
date: 2009-09-01
forum: Programming Talk
---

### Post by Mad Hacker on 2009-09-01
i am trying to write a script to generate part of the backrounds.xml file, and have encountered an error that i don't understand

the error is
```

  File "wallpaper_script.py", line 4
    """<name>""", """</name>""",         \
                      ^
SyntaxError: invalid syntax

``````

from sys import argv

template = [ """<wallpaper deleted="false">,        \
               """<name>""", """</name>""",         \
               """<filename>""", """</filename>""", \
               """<options>stretched</options>""",  \
               """<shade_type>solid</shade_type>""",\
               """<pcolor>#ffffffffffff</pcolor>""",\
               """<scolor>#000000000000</scolor>""",\
               """</wallpaper>""" ]
               

prefix = ""
end = []
curlist = []

for curarg in argv:
    if curarg == argv[1]:  #curarg[1](first argument) should be the path to the files
        prefix = curarg
    curlist = template
    curlist.insert(2, prefix + curarg)  #insert curarg in the name field
    curlist.insert(5, prefix + curarg)  #insert curarg in the filename field
    end.append(curlist)

for j in end:
    for i in j:
        print i

```

---

### Post by zarthon on 2009-09-01
"""
In python are multi-line quotes
Inside multi-line quotes you don't need to reopen the quote with each line or use \ to end lines and cariage returns will be included in the string literal.

You never close the multi line quote opened on this line
template = [ """<wallpaper deleted="false">,        \

---

### Post by Mad Hacker on 2009-09-01
that did it, thanks

---

