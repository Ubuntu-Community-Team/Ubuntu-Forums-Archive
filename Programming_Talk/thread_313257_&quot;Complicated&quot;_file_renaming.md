---
title: "&quot;Complicated&quot; file renaming"
date: 2006-12-05
forum: Programming Talk
---

### Post by jaykup on 2006-12-05
Well, its complicated for me at least.  This is what I want to accomplish.

Rename a bunch of file names using a list of file names that is not in the same order as the original files, but the only difference in file names are case sensitivity.

For example

me@computer:~$ ls

fileone.new
fileseven.old.new
thridfile
anotherfile
anotherfile2
lastfile

my list:

FileSeven.olD.new
FileOne.New
LastFile
AnotherFILE
AnotherFILE2
ThriDfilE

My real list of course is VERY long which is why I don't want to do this by hand, and all the original files are in lower case.  The new file names are in a mix of lower and upper case, but contain the same letters and numbers.

What can I do?

---

### Post by Steveire on 2006-12-05
```

stephen@ubuntu:~/somedir$ ls
RtfT4  weEhJ6i8
stephen@ubuntu:~/somedir$ for file in $(ls); do mv $file $(echo $file | tr 'A-Z' 'a-z'); done
stephen@ubuntu:~/somedir$ ls
rtft4  weehj6i8
stephen@ubuntu:~/somedir$  

```

---

### Post by duff on 2006-12-05
```
# cat name-list 
FileSeven.olD.new
FileOne.New
LastFile
AnotherFILE
AnotherFILE2
ThriDfilE

# ls rename
anotherfile  anotherfile2  fileone.new  fileseven.old.new  lastfile  thridfile

# cat rename/*
anotherfile
anotherfile2
fileone.new
fileseven.old.new
lastfile
thridfile

# ./weird-rename.py name-list rename
mv rename/anotherfile rename/AnotherFILE
mv rename/anotherfile2 rename/AnotherFILE2
mv rename/fileone.new rename/FileOne.New
mv rename/fileseven.old.new rename/FileSeven.olD.new
mv rename/thridfile rename/ThriDfilE
mv rename/lastfile rename/LastFile

# ./weird-rename.py name-list rename | sh

# ls rename
AnotherFILE  AnotherFILE2  FileOne.New  FileSeven.olD.new  LastFile  ThriDfilE

# cat rename/*
anotherfile
anotherfile2
fileone.new
fileseven.old.new
lastfile
thridfile

# cat weird-rename.py 
#!/usr/bin/env python

import sys
import os

thelist = { }
f = open (sys.argv[1])
for word in f:
   thelist[word.lower()[:-1]] = word[:-1]
f.close()

for file in os.listdir(sys.argv[2]):
   print 'mv %s/%s %s/%s' % (sys.argv[2], file, sys.argv[2], thelist[file])


```

I have the script print out shell commands so you can make sure it's correct before you run it.

---

### Post by ghostdog74 on 2006-12-05
Python alternative:
```

#!/usr/bin/python
import os
thelist = open("filelist").read().split()
lowerlist = [items.lower() for items in thelist]
for file in os.listdir(os.getcwd()):
        if file in lowerlist:
                newfile = thelist[lowerlist.index(file)]
                os.rename(file, newfile)

```

---

### Post by jaykup on 2006-12-07
The python code was amazing, it worked wonderfully.  Thanks, I am always amazed at how simple python can be.  I really need to pick up on it more.

---

