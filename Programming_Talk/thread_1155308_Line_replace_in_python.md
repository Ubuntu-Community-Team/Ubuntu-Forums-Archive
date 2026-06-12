---
title: "Line replace in python"
date: 2009-05-10
forum: Programming Talk
---

### Post by gazmac on 2009-05-10
Hi,

I would like to search a .txt file using python for a certain pattern at the start of a line and then replace that whole line with some new text. I can search and replace, but it doesn't replace the full line. Here's an example...

The .txt looks like this:

Country=variable1
City=variable2
Street=variable3

I know everything before the "=" but have no idea what the variables are.

How could I search for "Country" and replace the whole line so that the file would read:

Country=variable999
City=variable2
Street=variable3


Thanks in advance! :)

---

### Post by Bodsda on 2009-05-10
Hi, in future please use code tags around your code to make it more readable [ code][/code ]

As for your question, I would be inclined to read the lines into a list then do something like 

```
if 'Country' in list[0]:
    list[0] = "Country=%s" % newVar
```

Hope this helps,

Bodsda

---

### Post by ghostdog74 on 2009-05-10
if you are only searching for "Country", no need to spend time reading everything into a list. Just search for it line by line
```

import fileinput
for line in fileinput.FileInput(open("file"),inplace=1):
  line=line.strip()
  if line.startswith("Country"):
     print "Country=%s" % newvar
  else:
     print line

```

---

### Post by gazmac on 2009-05-11
That's great, thanks guys. To get it working I used ghostdog74's code, but changed the first line to...

```
for line in fileinput.FileInput("file",inplace=1):
```

as it was having problems with the 'open'

Thanks again.

---

