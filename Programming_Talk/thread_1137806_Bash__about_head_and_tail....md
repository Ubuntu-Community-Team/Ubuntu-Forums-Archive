---
title: "Bash ? about head and tail..."
date: 2009-04-25
forum: Programming Talk
---

### Post by Barriehie on 2009-04-25
Hey,  I've got a dir. with files in it that I'ld like to move the first 100 out of every so often.  The files are numerically named and I've been doing it with:
```

mv ./??.* ~/somedir

```This works but it will be more usefull if I can use head or tail to move the files.  I've tried
using ls and piping to head/tail and that works fine but how do I then pipe/redirect to the mv command???

Thank You,
Barrie

---

### Post by Peasantoid on 2009-04-25
Try this:

```
for file in $(ls | head -n 100); do mv $file ~/somedir; done
```
Multiple-line version:

```
for file in $(ls | head -n 100); do
    mv $file ~/somedir
done
```

---

### Post by Dougie187 on 2009-04-25
You could look into awk. Not sure if it helps or not. but try to man awk, and look for -exec

---

### Post by Peasantoid on 2009-04-25
Awk seems like it would be overkill...?

---

### Post by ghostdog74 on 2009-04-25
> **Peasantoid said:**
> Try this:

```
for file in $(ls | head -n 100); do mv $file ~/somedir; done
```
Multiple-line version:

```
for file in $(ls | head -n 100); do
    mv $file ~/somedir
done
```

use while loop instead to take care of spaces in file names
```

ls | head -100 | while read FILE
do
 ....
done

```

and no, using awk is definitely not overkill.
```


ls | awk 'BEGIN{q="\047"}NR<=100{cmd="mv "q $0 q " /destination"; system(cmd)}' 

```

---

### Post by Peasantoid on 2009-04-25
Mhm. Quick modification to fix spaces and special chars:

```
for file in $(ls | head -n 100); do mv "$file" ~/somedir; done
```
This will still be broken by double quotes in filenames, but if you do that, you're weird. :P

---

### Post by ghostdog74 on 2009-04-25
> **Peasantoid said:**
> Mhm. Quick modification to fix spaces and special chars:

```
for file in $(ls | head -n 100); do mv "$file" ~/somedir; done
```
This will still be broken by double quotes in filenames, but if you do that, you're weird. :P
it will still not work. you have to modify IFS. instead of doing that, use a while loop.

---

### Post by Peasantoid on 2009-04-25
What are/is IFS...?

---

### Post by ghostdog74 on 2009-04-26
> **Peasantoid said:**
> What are/is IFS...?

Input Field Separator.

---

### Post by Peasantoid on 2009-04-26
Okay, not too sure what that means, but I'm guessing it's something to do with how *for* separates the iterated string into individual items?

Works for me anyway.

---

### Post by ghostdog74 on 2009-04-26
> **Peasantoid said:**
> Okay, not too sure what that means, but I'm guessing it's something to do with how *for* separates the iterated string into individual items?

Works for me anyway.
i am very curious how it can work for you. can you show your output by creating file names with spaces and execute your code.

---

### Post by Peasantoid on 2009-04-26
Ah, you're right. Each piece of the filename shows up as its own file.
Still, it's an okay solution if you don't have any files with spaces in their names (I don't).

---

### Post by slavik on 2009-04-26
man xargs

---

### Post by Barriehie on 2009-04-26
> **Peasantoid said:**
> Try this:

```
for file in $(ls | head -n 100); do mv $file ~/somedir; done
```Multiple-line version:

```
for file in $(ls | head -n 100); do
    mv $file ~/somedir
done
```

The one liner worked perfectly!  Thank you Peasantoid!

Barrie

---

### Post by Barriehie on 2009-04-26
Thank you everyone for your replies.  I don't do whitespace in filenames so that's never an issue.  After looking at the manpage for awk that could be useful down the road.  I've got a python program that generates filenames like 000000, 000001, 000002, etc. but since I'm in the business of repairing HVAC equip. computer time is getting way short these days!

Thanks All,
Barrie
:)

---

### Post by Peasantoid on 2009-05-09
Hey, sorry for reviving this, but I found another way:
```
ls | head -n 100 | while read file; do mv "$file" ~/somedir; done
```
Not broken by spaces in filenames.

---

### Post by Barriehie on 2009-05-09
> **Peasantoid said:**
> Hey, sorry for reviving this, but I found another way:
```
ls | head -n 100 | while read file; do mv "$file" ~/somedir; done
```Not broken by spaces in filenames.

:o   ... :) Improvements are always good !

Barrie

---

