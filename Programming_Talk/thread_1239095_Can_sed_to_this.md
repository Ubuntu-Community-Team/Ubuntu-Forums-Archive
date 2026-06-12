---
title: "Can sed to this?"
date: 2009-08-13
forum: Programming Talk
---

### Post by PryGuy on 2009-08-13
Good day!
I have a problem here: I have a big Squid blacklist file that has lines that partly match. for instance:
> .somebadsite.com
.somebadsite.com/with/additionsor> .somebadsite.com
.addition.somebadsite.comIs it possible to parse this file with sed to find lines with similarities and delete the longer ones? Keep in mind that I don't know pattern in this case.
Thank you in advance!

---

### Post by unutbu on 2009-08-13
I don't know how to do this with just sed, but here is a solution in python:

[PHP]#!/usr/bin/env python
sites=[site.strip() for site in open('blacklist','r').read().split()]
result=sites[:]
for pattern in open('blacklist','r'):
    pattern=pattern.strip()
    for site in sites:
        if pattern!=site:
            idx=site.find(pattern)
            if idx>-1:
                # pattern is in site
                result.remove(site)
    sites=result
print '\n'.join(result)
[/PHP]
Save it to ~/bin/blacklist_filter.py
Make it executable:```

chmod +x ~/bin/blacklist_filter.py
```

Run it in the directory that contains blacklist like this:
```

blacklist_filter.py > new-blacklist
```

Note that this program requires enough memory to load the entire blacklist twice.
If that is too onerous, I could be modify the program to write partial results to disk.
This could save on memory, at the expense of more disk I/O.

---

### Post by PryGuy on 2009-08-13
Thank you, buddy! Beer's on me if you'll ever happen to visit Russia! :)

---

