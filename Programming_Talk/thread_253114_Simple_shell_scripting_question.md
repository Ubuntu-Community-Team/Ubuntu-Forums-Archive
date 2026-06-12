---
title: "Simple shell scripting question"
date: 2006-09-07
forum: Programming Talk
---

### Post by wr0x2 on 2006-09-07
I have a directory which has under it many directories and files with "_20" in the filename in place of a space. I want to go through and rename all these files recursively. What's the easiest way to do this?

---

### Post by goatflyer on 2006-09-07
This doesn't do recursive, but you can supply the directory you want to rename, and keep doing it until you get no more output.

First do this:

```

gedit rename

```

Paste this text into the file and save.

```

#!/bin/bash

for i in `ls $1 | grep _20` ; do
# for all files with _20 in the name,

# first, translate what the new name will look like.
j=`echo $i | sed "s/_20/ /;"`

# show what we're about to do
echo "$i -> $j"

# and do it.
mv $i "$j"

done

```

Then 
```

chmod +x rename

```

To rename all files in the current directory:

```

./rename .

```

Repeat until no more output.


Then each directory you want to rename the contents of: (suppose its mysubdir/deep

```

./rename mysubdir/deep

```

Wash, rinse, repeat.  :)

---

### Post by jrohde on 2006-12-06
Hi,

This doesn't work for me. It seems like the script can't handle spaces in file names, which is a problem because "_20" is replaced with a space.

Any suggestions?

Jakob

---

### Post by -J- on 2006-12-06
Replace this line
```
j=`echo $i | sed "s/_20/ /;"`
```

with this
```
j=`echo $i | sed "s/_20//"`
```

Or, if you have more spaces in the file name use this

```
j=`echo $i | sed "s/_20//" | sed "s/ /\\ /g"`
```

---

### Post by jrohde on 2006-12-10
Hi again,

That was better. Thanks!

Now I would like to take it a little step further...

How do I change the script, so that it isn't removing "_20" but instead removes whatevet I provide in a paramter (eg "rename _20).

The ultimate solution is to create a script that searches for all possible "_xx" combinations and replace them with the correct characters, but the above solution with a parameter will be ok for now.

Is that only a small change?

Jakob

---

### Post by tomj on 2006-12-19
Hi this will be my first attempt at shell scripting under linux or any os for that matter

when i first tried the code i got this error mv: cannot stat 'file name' no such file or directory.

I Then had a look at the code and changed

```
for i in `ls $1 | grep _20` ; do
``` 
to
```
for i in `ls $i | grep _20` ; do
```

When i had done this i got an output of the file showing 
file_20name -> filename

I repeated until all the _20's had been removed. However the actual file name had not been changed but there was a file of 100bytes in the same folder as rename with the correctish name containing the text file_20name -> filename

I fiddled with it a bit more and now when i run it nothing at all happens even though the file names are unchanged. I have tried the variations of j=... . I then went back to the start remaking rename using the original code got the error messages made the change and still nothing happens](*,) .

Any help would be apreciated

---

### Post by TyphoonJoe on 2006-12-22
Try using a combination of three tools: find, xargs, and rename

```

find /directory -name "*_20*" | xargs rename s/\_20//

```
This should find ALL files in specified directory and ALL subdirectories with _20 in the name and rename them to strip that part of the name  out.  

You should be able to make a shell script that takes a parameter rather than hard coding "_20" if you will do this often.

---

### Post by tomj on 2007-01-05
Hi, 
If anyone else has this problem and it is to do with music Amarok has a feature called organise files which does this and a few other neat things. Currently with exams coming up in a week learning about shell scripting got pushed near the bottom of my prioritys. 
Thanks for the suggestion TyphoonJoe when I have more time that will be really usefull and much more powerful.

---

