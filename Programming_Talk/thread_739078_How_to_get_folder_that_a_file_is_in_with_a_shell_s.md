---
title: "How to get folder that a file is in with a shell script?"
date: 2008-03-29
forum: Programming Talk
---

### Post by maybeway36 on 2008-03-29
I have a shell script that launches kdialog to find a file to open. I want the next program to run in the same directory as that file, so if the file is ~/Documents/file.txt it should run in ~/Documents. I'm sure this can be done by taking off the last slash and everything after it, but how?

---

### Post by dwhitney67 on 2008-03-29
Will something like the following work for you?
```

basename `find . -name someFile.txt`
```

Alternatively,
```
basename /some/path/to/a/file.txt
```

---

### Post by maybeway36 on 2008-03-29
I really want to do the complete opposite of basename, i.e. find the directory.

---

### Post by stroyan on 2008-03-29
The opposite of basename is dirname.
Or, you can just use a bash feature to strip off the last / and trailing chars.
The second way would be  a bit faster.
```

$ F='~/Documents/file.txt'
$ echo $(dirname "$F")
~/Documents
$ echo ${F%/*}
~/Documents

```

---

### Post by WW on 2008-03-29
If you use the bash parameter substitution, you must be sure that the file has at least one slash in it.  Otherwise...
> 
$ F="file.txt"
$ dirname $F
.
$ echo ${F%/*}
file.txt
$ 

dirname gives a correct directory ("."), but ${F%/*} gives the original file name.

---

### Post by maybeway36 on 2008-03-29
Thanks! Since my script gets the file path from kdialog, I think I'll just use ${F%/*} in my script.

---

### Post by ghostdog74 on 2008-03-29
you can also get the path using GNU find
```

find /fullpath -name "file*" -printf "%h\n" 

```

---

### Post by Mr. C. on 2008-04-01
I presume kdialog presents you with a full pathname.  If so, just use dirname as indicated earlier.

If kdialog only gives you a relative path, the job is more difficult.

The find solution presented above is problematic in that a) it takes a very long time, b) does not guarantee file uniqueness.

---

