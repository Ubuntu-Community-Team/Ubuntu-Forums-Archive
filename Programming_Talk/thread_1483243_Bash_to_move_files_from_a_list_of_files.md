---
title: "Bash to move files from a list of files"
date: 2010-05-14
forum: Programming Talk
---

### Post by pmorton on 2010-05-14
Can any one kindly sort me out here. I have a text file containing file paths/names, one per line, and I want to move these files from one directory to another. My bash scripting syntax is terrible. Can anyone give me a one-liner or script?

---

### Post by kaibob on 2010-05-14
The following should do what you want:

```
while read file ; do cp "$file" /destination/directory ; done < list.txt
```

The file list.txt contains the listing of the files to be moved. I used cp rather than mv as a precaution.

---

### Post by iponeverything on 2010-05-14
```
cat file |awk '{print "cp "$1" /destiniation"}'|sh
```

---

### Post by pmorton on 2010-05-16
Very grateful, Kaibob and IPoneverything.

---

### Post by Cracauer on 2010-05-16
Looks like classic backtick use to me:

```

mv `cat myfile` mydestination/.

```

It is not safe against filenames with special characters (shell special, e.g. spaces).  To be safe you'd need something like this"
```

cat myfile | while read foo ; do
    mv "$foo" mydestination/.
done

```

Useless use of cat left in for clarity.

---

