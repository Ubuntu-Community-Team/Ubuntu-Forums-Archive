---
title: "grep"
date: 2009-08-05
forum: Programming Talk
---

### Post by dunryc on 2009-08-05
Hi guys sorry if this sounds like a newb question but it probably is !

does any on know how to use grep to find the last instance of a string in a text file ?? 


any help would be gratefully appreciated 

many thanks dunryc

---

### Post by willjcroz on 2009-08-05
This may work for you:
```
grep string file | tail -1
```

or else you can use sed:
```
sed -n "/string/h;$ {x;p;}" file
```

---

### Post by Lampi on 2009-08-05
Let's say the text file is called foo.txt and you search dunryc inside of it:
```
cat <filename> | grep <searchstring>
```
so this makes it:
```
cat foo.txt | grep dunryc
```

---

### Post by dunryc on 2009-08-05
Wow thanks for the quick response ill give them a try and let you know how i get on with them

---

### Post by ahmatti on 2009-08-05
Yeah, these guys beat me to it while I was testing :) You could also do:

```

tac file | grep -m 1 pattern

```

This prints out the whole last line, but you can also make grep e.g. to give you the line number.

---

