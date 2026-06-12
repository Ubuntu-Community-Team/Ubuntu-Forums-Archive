---
title: "Script writing in sed"
date: 2009-08-20
forum: Programming Talk
---

### Post by BufordPants on 2009-08-20
Can someone show me a script written using sed:

a)There is no trailing white space
b)Every comma is followed by one space
c) Every period is followed by two spaces
d)consecutive words are separated by one space
e)except for the above the file is otherwise unchanged

---

### Post by geirha on 2009-08-20
Do it one step at a time, then combine all commands. An example with your a and d:

a) remove trailing whitespace, s/ *$//
d) squeze spaces s/ \{1,\}/ /g

```

sed 's/ *$//; s/ \{1,\}/ /g' file > newfile

```

---

### Post by DaithiF on 2009-08-21
and just to round this out ... the other 2 pieces you wanted added here:
```
sed 's/ *$//; s/ \{1,\}/ /g; s/, */, /g; s/\. */.  /g' somefile > newfile
```

---

