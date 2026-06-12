---
title: "inserta a carriage return from a word"
date: 2008-02-26
forum: Programming Talk
---

### Post by davidtuti on 2008-02-26
Hi,
 

I have a long text without carriage return, How could I insert a 
carriage return from a certain word. 



for instance

one line: Los estados unidos de norteamerica no han podido conseguir el objetivo de convertir

"command ... objetivo"

one line: Los estados unidos de notemaerica no han podido conseguir el 
two line: objetivo de convertir

Thanks a lot and sorry for my english.

---

### Post by lloyd_b on 2008-02-26
> **davidtuti said:**
> Hi,
 

I have a long text without carriage return, How could I insert a 
carriage return from a certain word. 



for instance

one line: Los estados unidos de norteamerica no han podido conseguir el objetivo de convertir

"command ... objetivo"

one line: Los estados unidos de notemaerica no han podido conseguir el 
two line: objetivo de convertir

Thanks a lot and sorry for my english.

If you're just trying to modify text files from the command line (or in a script):
```
sed -i "s/objetivo/\nobjetivo/g" filename.txt
```
will insert a "newline" (carriage return) before every instance of "objetivo" in the file "filename.txt".

If this is a programming question, we really need to know what programming language you're using...

Lloyd B.

---

### Post by davidtuti on 2008-02-26
Hi,

Sorry I use ksh.

The command sed -i don't work

I try 
sed -e "s/title/\ntitle/g" hol > hols2

These also don't works it writes: ntitle

Any help?

---

### Post by ghostdog74 on 2008-02-26
```

awk '{sub("objetivo","\nobjetivo")}1' file

```

---

### Post by davidtuti on 2008-02-26
it gives me some errors:

awk '{sub("title","\ntitle")}1' tufo

awk: syntax error near line 1
awk: illegal statement near line 1
awk: syntax error near line 1
awk: bailing out near line 1

Any help?
Thansk

---

### Post by ghostdog74 on 2008-02-26
try this
```

awk '{sub("title","\ntitle")}{print}' tufo

```
if you are on another platform, like solaris, you can use nawk instead of awk.

---

### Post by davidtuti on 2008-02-26
Thanks, in Solaris it's ok.

But... I don't have Ubuntu at this moment, do you think that in ubuntu also works? Ubuntu have nawk?

Thanks a lot

---

### Post by ghostdog74 on 2008-02-26
> **davidtuti said:**
> Thanks, in Solaris it's ok.

But... I don't have Ubuntu at this moment, do you think that in ubuntu also works? Ubuntu have nawk?

Thanks a lot

no need. use awk or gawk will do

---

### Post by davidtuti on 2008-02-27
Thanks a lot 

I 've tryed with nwak and i'ts ok all.

:):):):):):):)

---

### Post by Mr. C. on 2008-02-27
And for documents with many long lines, the **fmt** command is nice and handy:
```

$ cat long

Los estados unidos de norteamerica no han podido conseguir el objetivo de convertir

``````

$ fmt long
Los estados unidos de norteamerica no han podido conseguir el objetivo
de convertir
```

MrC

---

