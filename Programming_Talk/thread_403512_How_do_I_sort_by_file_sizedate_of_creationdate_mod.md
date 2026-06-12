---
title: "How do I sort by file size/date of creation/date modified etc in python?"
date: 2007-04-07
forum: Programming Talk
---

### Post by slimdog360 on 2007-04-07
I want to make a small script that picks out every 100th (or whatever) photo, by the creation date, from a folder and put the photos in a new folder. I don't think there will be any trouble copying over the files etc, but being able to sort through them via their properties has me stumped.

So is there some function, or some other way, which lets me find and read the properties of each file?

thanks

---

### Post by duff on 2007-04-07
You need os.stat

```
#!/usr/bin/env python

import os
import sys
import glob
import operator

flist = glob.glob(sys.argv[1])
for i in range(len(flist)):
	statinfo = os.stat(flist[i])
	flist[i] = flist[i],statinfo.st_size,statinfo.st_ctime

flist.sort(key=operator.itemgetter(1))
print 'sorted by size:',flist

print

flist.sort(key=operator.itemgetter(2))
print 'sorted by creation date:',flist
```

---

### Post by slimdog360 on 2007-04-07
beautiful, thanks for that. Now I just have to figure out the easiest way to sort 30-40 thousand photos.

---

