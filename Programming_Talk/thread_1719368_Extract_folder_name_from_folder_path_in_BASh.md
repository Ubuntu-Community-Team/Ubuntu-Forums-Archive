---
title: "Extract folder name from folder path in BASh"
date: 2011-04-01
forum: Programming Talk
---

### Post by jamesisin on 2011-04-01
I am writing a script for bash wherein I need to use the containing folder name from a path:

```
/path/to/folder
extract "folder"
```

I did something similar when I needed to extract the folder path from a file path using this bit of code:

```
for (( i=0 ; i < ${#albumfind[@]} ; i++ )) ; do
   # path is cue iteration less file name
   albumfolder="${cuefind[i]%/*.*}"
```

(Where albumfind and cuefind are arrays containing paths.)

This problem is a little different and I'm a little stumped (read: stupid) today.

---

### Post by MadCow108 on 2011-04-01
```
$ basename /path/to/folder
folder
$ dirname /path/to/folder
/path/to
$ fold=`basename /path/to/folder`
$ echo $fold
folder

```

---

### Post by jamesisin on 2011-04-01
Hmmm...  I was making this really hard.  Thanks.

---

### Post by jamesisin on 2011-04-02
Recursive Prepending Script

[http://soundunreason.com/inkwell/index.php/2011/04/recursive-prepending-script/](http://soundunreason.com/inkwell/index.php/2011/04/recursive-prepending-script/)

... for what it's worth.

---

