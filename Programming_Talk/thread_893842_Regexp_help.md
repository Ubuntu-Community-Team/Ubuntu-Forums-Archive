---
title: "Regexp help?"
date: 2008-08-18
forum: Programming Talk
---

### Post by linuxgeekery on 2008-08-18
Like many, I'm a regex noob and I need a little sed (or possibly awk) help.

I have a bunch of data formatted like:

This 01 Is 02 An 03 Example 04 

and I need it formatted like:
This 01
Is 02
An 03
Example 04

I would be able to figure this out myself, but sed doesn't seem to want to work with newlines.

Thanks!

---

### Post by mssever on 2008-08-18
> **linuxgeekery said:**
> Like many, I'm a regex noob and I need a little sed (or possibly awk) help.
How about Ruby?
```
echo 'This 01 Is 02 An 03 Example 04' | ruby -pe "gsub(/([0-9]+) /,'\1' + \"\n\")"

```

---

### Post by pdwerryhouse on 2008-08-18
This works for me:

```
echo "This 01 Is 02 An 03 Example 04" | sed 's/\([0-9]\+\) \?/\1\n/g'
```

---

### Post by ghostdog74 on 2008-08-18
things can be done easily without regexp
```

awk '{  for(i=1;i<NF;i=i+2) {   print $i,$(i+1)   }}' file

```

---

### Post by linuxgeekery on 2008-08-18
> **pdwerryhouse said:**
> This works for me:

```
echo "This 01 Is 02 An 03 Example 04" | sed 's/\([0-9]\+\) \?/\1\n/g'
```

Weird.  Both the awk and ruby examples work, but yours doesn't.

Thanks!

---

### Post by ghostdog74 on 2008-08-18
unless your data is really structured like that, using regexp and checking for digits is less flexible than going over the fields and implementing a newline for every 2 words.

---

