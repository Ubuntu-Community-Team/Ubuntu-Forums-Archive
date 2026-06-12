---
title: "Is there a Shell Script program to delete one line of a file on the command line?"
date: 2008-02-28
forum: Programming Talk
---

### Post by kevdog on 2008-02-28
Looking for a one line shell script on the command line I could use to remove a line in a config file (for example the first or last line or line that contains xxxxx).  Here are the examples Ive found thus far.  Any better methods?

```


awk 'NR!=4' file1 > file2

cp /etc/apt/sources.list /etc/apt/sources.list_backup
grep -v “line you want to remove” /etc/apt/sources.list_backup > /etc/apt/sources.list
```

---

### Post by ghostdog74 on 2008-02-28
if they suit your purpose, then use them.
other method
```

head -3 file > newfile
more +5 file >> newfile


```
using sed
```

sed '4d' file

```

---

### Post by erginemr on 2008-02-28
Hi kevdog,

I think, your solution:
```
grep -v "line you want to remove" /etc/apt/sources.list_backup > /etc/apt/sources.list
```
is the most elegant way to do it. 

Alternatively, you can use:
```
sed "/line you want to remove/d" /etc/apt/sources.list_backup > /etc/apt/sources.list
```
Kindly see the attached example...

---

### Post by kevdog on 2008-02-28
Just for my reference -- there is no way to avoid use of a temporary file (at least specifying one on the command line -- what happens internally within a buffer is different) other than with something similar to 

sed '4d' file


Im not familar with the +5 part of this command:
more +5 file >> newfile

I read the man pages but they dont list this as an option.  What exactly does this do?

---

### Post by scruff on 2008-02-28
GNU sed includes a -i option for "inline" edits. No need for a temp backup file :)

---

### Post by kevdog on 2008-02-28
So it would be something like this??:

sed -i "/line you want to remove/d" /etc/apt/sources.list

So hence the sources.list would be the same as the original, minus the line you removed?

---

### Post by scruff on 2008-02-28
Yes that is correct.

---

### Post by ghostdog74 on 2008-02-28
> **kevdog said:**
> 
I read the man pages but they dont list this as an option.  What exactly does this do?

please read the man page again. you should see +num
it just simply means start from that line number (num)

---

### Post by Roguebantha on 2012-07-31
I accomplished deleting the last line of a file like this:
$cp Example1 ./tmp
$head --lines=-1 tmp > Example1

In which running head --lines=-1 shows all of the lines except the last one.

---

### Post by Bachstelze on 2012-07-31
> **scruff said:**
> GNU sed includes a -i option for "inline" edits. No need for a temp backup file :)

And even without GNU sed, the same thing can be achieved with ed (this is why POSIX sed does not include a similar functionality: it would be redundant since it's already in ed).

---

### Post by nothingspecial on 2012-07-31
Old thread.

Closed.

---

