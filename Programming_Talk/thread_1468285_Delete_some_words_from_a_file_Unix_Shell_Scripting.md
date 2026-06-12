---
title: "Delete some words from a file Unix Shell Scripting"
date: 2010-05-01
forum: Programming Talk
---

### Post by hakermania on 2010-05-01
Let's say that we have a text file "test":
[B]a
b
c
d
e
f
g
default:f[/B]

And we want to remove the** default:** (without removing "f" after it). How can i do this with unix scripting?

---

### Post by s1ightcrazed on 2010-05-01
```
cat file | sed 's/default//g' > newfile
```

Read (cat) the file, pass the output to sed, substituting every instance of 'default' with nothing, globally. Output to file 'newfile'. 

Hope that helps.

---

### Post by tookyourtime on 2010-05-01
```
#!/bin/bash
mv text text.old
sed 's/default://g' text.old > text

```

---

### Post by red_Marvin on 2010-05-01
s1ghtcrazed: cat is not needed:
```
sed 's/default//g' <file >newfile
```

***

If you want to input and output to the same file check out sed's **-i** flag

eg
```
sed 's/foo/bar/' -i file
```

---

### Post by slavik on 2010-05-01
with -i you can give it a backup extension ...

sed -i.original 'blah' file

---

