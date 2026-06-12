---
title: "What is the best way to do this in python?"
date: 2005-09-02
forum: Programming Talk
---

### Post by SGC on 2005-09-02
If I have a large text file that has something like this:
```

text=Kubuntu
color=Red
font=Arial
...

```

What the best way to know the value of color,text,font,etc?
I usually uses string.find to locate "color=" then save the text after that in a variable, but I think this is not an effient way to do it.

---

### Post by vasdee on 2005-09-02
i reckon use a while loop on each line, something like this
```

vals = {}
for line in inputfile.readlines():
    info = line.split('=')
    vals['info[0]'] = info[1]

```

then you should be able to look up the values by vals['color'], vals['font'] etc

---

### Post by SGC on 2005-09-02
[QUOTE=vasdee]i reckon use a while loop on each line, something like this
```

vals = {}
for line in inputfile.readlines():
    info = line.split('=')
    vals['info[0]'] = info[1]

```

then you should be able to look up the values by vals['color'], vals['font'] etc[/QUOTE]
 Thank you very much for your help

---

### Post by wtd on 2005-09-05
[QUOTE=vasdee]i reckon use a while loop on each line, something like this
```

vals = {}
for line in inputfile.readlines():
    info = line.split('=')
    vals['info[0]'] = info[1]

```

then you should be able to look up the values by vals['color'], vals['font'] etc[/QUOTE]
 If you're using Python 2.4 or later that can be simplified a tad.

```
vals = {}
for line in inputfile:
    info = line.split('=')
    vals[info[0]] = info[1]
```

Or perhaps:

```
vals = dict(line.split('=', 2) for line in inputFile)
```

:)

---

### Post by SGC on 2005-09-07
[QUOTE=wtd]```
vals = dict(line.split('=', 2) for line in inputFile)
```[/QUOTE]
Thanks, I like this one.

---

### Post by wtd on 2005-09-07
Just one note... I'm fairly sure the 2 should be 1 in that call of split.

Also worth noting is that there's more than simply a stylistic difference between:

```
for line in inputFile.readlines()
```

And:

```
for line in inputFile
```

The former reads in all lines, then iterates over them.  The latter reads through them one at a time without creating an intermediate list.  This can be very useful if you're dealing with very large files, and especially if at some point you plan to break out of the loop before you get to the end of the file.

---

### Post by ArBaDaCarBa on 2005-09-09
[QUOTE=wtd]Just one note... I'm fairly sure the 2 should be 1 in that call of split.

Also worth noting is that there's more than simply a stylistic difference between:

```
for line in inputFile.readlines()
```

And:

```
for line in inputFile
```

The former reads in all lines, then iterates over them.  The latter reads through them one at a time without creating an intermediate list.  This can be very useful if you're dealing with very large files, and especially if at some point you plan to break out of the loop before you get to the end of the file.[/QUOTE]

Very usefull info. I'll remember this, thanks !

---

### Post by UbuWu on 2005-10-01
What does info = line.split('=') do when there is no '=' in the line? Is the line ignored or is it also stored in memory?

---

### Post by jrbj on 2005-10-01
[QUOTE=UbuWu]What does info = line.split('=') do when there is no '=' in the line? Is the line ignored or is it also stored in memory?[/QUOTE]

The line is not ignored.  It is just not split becaused the specified delimiter is not present in that line.

For example:

>>> line1 = 'font=Verdana'
>>> line1.split('=')
['font', 'Verdana']


>>> line2 = 'font Monaco'
>>> line2.split('=')
['font Monaco']

---

