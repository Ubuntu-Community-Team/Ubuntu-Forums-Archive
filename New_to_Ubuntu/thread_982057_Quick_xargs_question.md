---
title: "Quick xargs question"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by pzs on 2008-11-14
I've been meaning to learn how to use xargs for ages. Anyway.

I have a Python script I wrote that takes one filename as an argument. Can I use xargs to run the script on a list of files in turn? I've tried things like:

```

ls *.html | xargs ~/bin/myscript.py

```

and 

```

find . -name *.html | xargs ~/bin/myscript.py

```

but both pass in the file lists all at once. I know I could alter my Python or write a shell loop for this, but a nice one liner would be preferable. Any ideas?

---

### Post by aeiah on 2008-11-14
i think however you do it, you'll still be passing all arguments to your python script at once, and not iterate over each item in the list. you'll need to either create a for loop in bash or in the python script its self. why are you reluctant to do this? if its simply because you dont know how then i could point you in the right direction.

---

### Post by aeiah on 2008-11-14
[PHP]
#/usr/bin/python

import os, sys

#take the argument supplied
thepath = sys.args[1]
cmd = os.popen("ls "+thepath+"*.html", "r")
thelist = cmd.read()

#split the ls output into a python list
thelist = thelist.splitlines()

#iterate over each file in the list called 'thelist'
for file in thelist:
     #do whatever you have in your script

[/PHP]

then just in a terminal
```

~/bin/myscript.py /path/to/directory/

```

---

### Post by geirha on 2008-11-14
Try:
```

for file in *.html; do
  ~/bin/myscript.py "$file"
done

```
and
```
find . -name "*.html" -exec ~/bin/myscript.py {} \;
```

---

### Post by pzs on 2008-11-17
```
find . -name "*.html" -exec ~/bin/myscript.py {} \;
```

Of course. Thanks.

---

