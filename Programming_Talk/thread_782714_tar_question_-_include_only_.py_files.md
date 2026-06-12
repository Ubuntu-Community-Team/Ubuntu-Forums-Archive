---
title: "tar question - include only *.py files"
date: 2008-05-05
forum: Programming Talk
---

### Post by wrightee on 2008-05-05
Hi - sorry, this isn't really programming talk but I couldn't figure out where else to put it.. I have a bit of a crisis going on and need to tar up all files that match a pattern in a directory tree; I figured out excluding stuff but aren't sure on including only files that match a pattern.  Could someone please put me out of my misery!  Thanks in advance.

---

### Post by tseliot on 2008-05-05
Try this:
```
tar -cvvf foo.tar ~/*.py
```

or 
```
tar -cvvf foo.tar your_directory/*.py
```

---

### Post by wrightee on 2008-05-05
That half worked.. though I need to go down into the directory tree and find all the *.py's there too; this restricts to current directory.. how can I make it descend?  Thanks for your help so far.

---

### Post by wrightee on 2008-05-05
```
find . -name \*.py|xargs tar cvfz osp.tar.gz
```

That worked.

---

