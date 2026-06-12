---
title: "Replacing spacwe with underscore in file names"
date: 2007-10-17
forum: Programming Talk
---

### Post by coolboarderguy on 2007-10-17
Hi All,

I'm trying to replace the space in file names with an underscore. Someone suggested using tr with ls -Q then piping to mv as below

for i in $(ls -Q); do mv $i $(echo $i | tr ' ' '_');done

bu it gives the following,

mv: cannot stat `"file': No such file or directory
mv: cannot stat `1"': No such file or directory
mv: cannot stat `"file': No such file or directory
mv: cannot stat `2"': No such file or directory
mv: cannot stat `"file': No such file or directory
mv: cannot stat `3"': No such file or directory
mv: cannot stat `"file': No such file or directory
mv: cannot stat `4"': No such file or directory

Why is it looking for the file name separately? A little confused here.

for i in $(ls -Q);do echo $i ;done
"file
1"
"file
2"
"file
3"
"file
4"

---

### Post by cwaldbieser on 2007-10-17
Try:
```

for file in *; do
    newname=$(echo "$file" | tr " " _)
    mv "$file" "$newname"
done

```

Or just use krename.

---

### Post by ape on 2007-10-17
Try this:


```
/bin/ls | while read i; do mv $i `echo $i | tr ' ' '_'`;done
```

--ape--

---

### Post by stylishpants on 2007-10-17
Simpler still:

```
rename 's/ /_/g' *
```

---

### Post by coolboarderguy on 2007-10-29
Thanx guys.

---

### Post by bashologist on 2007-11-01
> **cwaldbieser said:**
> Try:
```

for file in *; do
    newname=$(echo "$file" | tr " " _)
    mv "$file" "$newname"
done

```

Or just use krename.

This thread's getting old, but there's no need for piping the output into tr. 
```
man bash -P 'less -p "Parameter Expansion"'
```
So, using parameter expansion you could do this.
```
mv "$file" "${file/ /_}"
```

---

