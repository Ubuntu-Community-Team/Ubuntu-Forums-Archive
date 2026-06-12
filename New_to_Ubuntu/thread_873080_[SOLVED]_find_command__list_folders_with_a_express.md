---
title: "[SOLVED] find command // list folders with a expression"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Plexus81 on 2008-07-28
How can I list all folders/subfolders with a spesific expression and a size bigger than 500 mb?

ex
want to find all folders / subfolder that have iso in their foldername and have a size bigger then 500 mb?

---

### Post by raptor2552 on 2008-07-28
Hello

You could use something like:
```
find / -size +500M -name *.iso
```

this will find starting at root all files 500meg or greater containing .iso

you may find all your looking for with man find

---

### Post by Plexus81 on 2008-07-28
I've tried many times but I can't get it to worp propebly.. I want:

total foldersize bigger than 500 MB
foldername with ex *iso*  *ISO*  like ignore case
and I want to list all the folder in the folder include subfolder like /../../test_iSo/

big thanx

---

### Post by sdennie on 2008-07-28
If I understand you correctly, this should work:

```

find . -type d -size +500M | grep -i iso

```

---

### Post by raptor2552 on 2008-07-28
Sorry it took me so long to get back to you, but I had to eat + errands

This will find all directories 500MBytes or greater and list all the .iso under that directory if any
```

du -bS |awk '$1 > 500000000 {print "Size: " $1, "\tDir: " $2; system("ls -R "$2 "|grep -i iso") }'

```

if you would like to keep this in a script:
start gedit and then copy and paste this into the editor;
```

#!/bin/bash
du -bS |awk '$1 > 500000000 {print "Size: " $1, "\tDir: " $2; system("ls -R "$2 "|grep -i iso") }'

```
then save it to a directory in your path with a name you'll remember, home dir is preferable. Finally make it executable by typing:
```

chmod a+x yourscriptname

```
Let us know how/if this is what you're looking for:)

---

### Post by ghostdog74 on 2008-07-28
> **vor said:**
> If I understand you correctly, this should work:

```

find . -type d -size +500M | grep -i iso

```

this should be equivalent to 
```

find . -type d -size +500M -iname *iso*

```

---

### Post by sdennie on 2008-07-28
> **ghostdog74 said:**
> this should be equivalent to 
```

find . -type d -size +500M -iname *iso*

```

That's not an equivalent command.  My command is also not correct in that it won't report subdirectories under an iso directory that are smaller than 500M though.

---

### Post by raptor2552 on 2008-07-28
Vor and ghostdog, I beg to differ with your solutions

Directories themselves have no real size except for the inode that describes the directory (4096 bytes). The files contained in the directories, the sum of their size, is what gives the directory their size.

---

### Post by Plexus81 on 2008-07-29
> **raptor2552 said:**
> Sorry it took me so long to get back to you, but I had to eat + errands

This will find all directories 500MBytes or greater and list all the .iso under that directory if any
```

du -bS |awk '$1 > 500000000 {print "Size: " $1, "\tDir: " $2; system("ls -R "$2 "|grep -i iso") }'

```

if you would like to keep this in a script:
start gedit and then copy and paste this into the editor;
```

#!/bin/bash
du -bS |awk '$1 > 500000000 {print "Size: " $1, "\tDir: " $2; system("ls -R "$2 "|grep -i iso") }'

```
then save it to a directory in your path with a name you'll remember, home dir is preferable. Finally make it executable by typing:
```

chmod a+x yourscriptname

```
Let us know how/if this is what you're looking for:)

This is working perfect! Thanks alot! :)

---

### Post by sdennie on 2008-07-29
Glad you were able to find a solution.  :)

---

