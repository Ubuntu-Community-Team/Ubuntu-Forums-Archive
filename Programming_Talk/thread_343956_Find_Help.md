---
title: "Find Help"
date: 2007-01-22
forum: Programming Talk
---

### Post by dillzz on 2007-01-22
Perhaps someone can lead me in the right direction.  I am trying to do a filesystem global search within all txt files for a certain string(s).  I need to be able to output these found strings in this format:

string(s) was found in

FILE - LINE NUMBER(S) IN FILE

I have tried this with an advanced find statement with grep but with no success.  I have started hacking away at awk and perl but am running into difficulty as well.  Does ayone know of a better way to accomplish this?  Thanks in advance...

---

### Post by ghostdog74 on 2007-01-22
what have you written so far?

---

### Post by Mirrorball on 2007-01-22
Here is a Python script you can modify:

```

import os
for root, dirs, files in os.walk('/'):
    for file in files:
        #open file, find your string and print line number, filename

```

---

### Post by pmasiar on 2007-01-22
os.walk() is a real gem, I missed it somehow - thanks for mentioning it :-) This is exactly what I love in python: smart, powerfull functions which are simple to use.

I don't even want to think how many convoluted lines it would take in Java :evil:

---

### Post by ghostdog74 on 2007-01-23
you can use the find powertool too
something like this
```

find /dir -type f -print | xargs egrep -n "searchstring" 

```

---

### Post by dillzz on 2007-01-23
I ended up getting it working through good old shell.  Did a find through the whole system with a grep for strings >> new file.  I then just did a simple for loop with the new file as the input and found exact numbers that way.  Ugly as hell but thats what makes linux so great - there is more than one way to get stuff done.  

I will check into the python. Thanks much!

---

