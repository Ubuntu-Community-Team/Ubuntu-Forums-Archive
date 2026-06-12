---
title: "Delete all file and Directories in a folder but not top folder"
date: 2015-11-05
forum: Programming Talk
---

### Post by lance bermudez on 2015-11-05
Using python 3.4

/tmp/1 is the main folder and I want to delete all that is in it without deleting /tmp1.
The names change but below is a basic layout.

root or top is /tmp/1
subfolder of           /folder1
subfolder folder1 has some files in it    /files
subfolder             /folder2
                                    /files

the code I'm using remove every thing even the /tmp/1. So how do I go about fixing this?

I do not use "find" because I need this cross platform for linux and windows

```

#!/usr/bin/python3
import os

emptyDirs = []
path = "/tmp/1"

def deleteFiles(dirList, dirPath):
    for file in dirList:
        print("Deleting " + file)
        os.remove(dirPath + "/" + file)

def removeDirectory(dirEntry):
    print("Deleting files in " + dirEntry[0])
    deleteFiles(dirEntry[2], dirEntry[0])
    emptyDirs.insert(0, dirEntry[0])

#Enumerate the entries in the tree
tree = os.walk(path)
for directory in tree:
    removeDirectory(directory)

#Remove the empty directories
for dir in emptyDirs:
    print("Removing " + dir)
    os.rmdir(dir)

```

---

### Post by TheFu on 2015-11-05
Please review your post. It appears to have inconsistencies that I cannot decipher.
Can't tell if there are subdirs or not, is the first issue.

Output from **find /tmp** would be helpful.

Also, why use python for something easily handled with **find**?

---

### Post by matsuzine on 2015-11-06
If I understand you correctly, you're looking for the following:

```

/tmp/
    1/
      folder1/files
      folder2/files
      file
    2/

```

You want /tmp/1/ to remain when you're done deleting files, but you want folder1, folder2 and all contents of those gone? And you also want any files in 1/ gone as well?

The script below will do what you want:

```
import os

path = "tmp/1"

for root, dirs, files in os.walk(path, topdown=False):
    for f in files:
        to_delete = os.path.join(root, f)
        print("Removing file: {}".format(to_delete))
        os.remove(to_delete)
    for dir in dirs:
        print("Removing {}".format(dir))
        os.rmdir(os.path.join(root, dir))
```

The trick here is the os.walk method's topdown=False parameter, which tells os.walk to start at the bottom of the tree and work its way up. In this way, you can start at the bottom, deleting files and folders as you climb up the tree. It's self-limiting, stopping when the root is the same as path.

---

### Post by TheFu on 2015-11-06
```
/tmp/
    1/
      folder1/files
      folder2/files
      file
    2/
```
If you want to keep any 1, 2, 3, 4, 5, ..... 99999999999 directories at the first level, but remove everything below ... 
```
rm -rf /tmp/[0-9]*/*
```
This leaves the 1, 2, 3, 4 directories alone.
However, I'd probably just remove them all and add the directories I wanted back after.

You could also use a find - but with a directory depth limit of 1 or 2 (I'd have to test/check the manpage). Don't quote me, but something ....
```
find /tmp/ -mindepth 2 -delete
```  For traversal, find is generally faster than other methods.  Be sure to test this somewhere safe first.

---

