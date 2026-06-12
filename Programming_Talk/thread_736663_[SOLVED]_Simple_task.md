---
title: "[SOLVED] Simple task?"
date: 2008-03-26
forum: Programming Talk
---

### Post by jflaker on 2008-03-26
I have a simple task:

I have 3 folders with files in them.  the file names are SOMETHING.SOMETHING.....so here is what I need to do.

I want to get each file name in these folders and rename them by chopping the "SOMETHING." from the beginning of the name and adding a ".txt" to the end of the name so my windows system can associate notepad and/or wordpad with the file.

There are about 4000 - 5000 files, so manually renaming is not an option.

---

### Post by dashnak on 2008-03-26
You could try [PyRenamer]("http://www.gnomefiles.org/app.php/pyRenamer")

---

### Post by jflaker on 2008-03-26
I found it in synaptic.....going to check it out.

and, oops, there are close to 21,000 files, my last estimate was for a single folder.

---

### Post by scragar on 2008-03-26
rather basic shell script to quickly add ".txt" to the end of all file names in a directory:
```

#!/bin/bash

#
# simle renaming script
#
for i in `ls $1`
do

mv $i $i.txt

done

```

just save, make executable, then run it like so:
```
**path to this script** _path to folder you want to rename contents of_
```

---

### Post by ghostdog74 on 2008-03-26
> **scragar said:**
> rather basic shell script to quickly add ".txt" to the end of all file names in a directory:
```

#!/bin/bash

#
# simle renaming script
#
for i in `ls $1`
do

cp $i $i.txt

done

```

just save, make executable, then run it like so:
```
**path to this script** _path to folder you want to rename contents of_
```

ls is not needed. Instead, use shell expansion.

---

### Post by scragar on 2008-03-26
> 
ls is not needed. Instead, use shell expansion.
forgive me, but I tend not to work with shell scripting(or bash all that much actualy), so how would I do that then?

---

### Post by ghostdog74 on 2008-03-26
> **jflaker said:**
> I have a simple task:

I have 3 folders with files in them.  the file names are SOMETHING.SOMETHING.....so here is what I need to do.

I want to get each file name in these folders and rename them by chopping the "SOMETHING." from the beginning of the name and adding a ".txt" to the end of the name so my windows system can associate notepad and/or wordpad with the file.

There are about 4000 - 5000 files, so manually renaming is not an option.

snippet:
```

# a=test.txt
# echo ${a%.*}
test

```

using a for loop, loop through the directory
```

for files in directory
do
   mv files <fill in the blank>
done

```

---

### Post by ghostdog74 on 2008-03-26
> **scragar said:**
> forgive me, but I tend not to work with shell scripting(or bash all that much actualy), so how would I do that then?

```

for f in dir/*
do
 echo $f
done

```

---

### Post by EvilMarshmallow on 2008-03-26
Question: don't you need to remove the old version?  When I read that script, I see a copy of every file... does cp replace the original file, or will the script leave us with 2 copies of the contents?  If I were writing the script, I'd have added a "rm -f $i" to that.

---

### Post by scragar on 2008-03-26
ah, get you now.

I was wondering why trying to fit everything on one line was causing errors(origional source said something along lines of:
```
for i in `ls`; do; echo $i; done;
```
but I couldn't get this to work :P

---

### Post by YldGuy on 2008-03-26
forgive me if i say something stupid but isnt there a way to change the file association in Windows?. I can say the file of ".SOMETHING" extension be opened only by notepad/wordpad in Windows. Won't this solve the problem?

---

### Post by scragar on 2008-03-26
> **EvilMarshmallow said:**
> Question: don't you need to remove the old version?  When I read that script, I see a copy of every file... does cp replace the original file, or will the script leave us with 2 copies of the contents?  If I were writing the script, I'd have added a "rm -f $i" to that.

yeah, it was a testing failsafe that didn't work, just replace **cp** with **mv** and it's all good.


final working code then:
```
$ for i in `ls`
> do
> mv $i $i.txt
> done
```or you could try:```
for i in `ls`; do mv $i $i.txt; done
```

---

### Post by jflaker on 2008-03-26
> **YldGuy said:**
> forgive me if i say something stupid but isnt there a way to change the file association in Windows?. I can say the file of ".SOMETHING" extension be opened only by notepad/wordpad in Windows. Won't this solve the problem?

The file names are like this

xxxx.AllDifferentNames

Which is why I asked.  So, Looking at the replies, I think there are details that were missed....

I want to strip away everyhing from the the beginning of the file name, up to and including the dot.  I then want to append a ".txt" to the end of the name so windows knows it is a text file.

All good information either way..........

I dowloaded PyRenamer, which worked very well.  It would still be interesting to see some code either way

---

### Post by pmasiar on 2008-03-26
> **scragar said:**
> forgive me, but I tend not to work with shell scripting(or bash all that much actualy), so how would I do that then?

What about Python scripting? That would be easy.

Seems like you want specialized renaming tool - but writing customized solution (exactly what you need) in Python should take not more than an hour, faster than researching/downloading/installing/learning tool, IMHO.

---

### Post by ghostdog74 on 2008-03-27
> **scragar said:**
> ah, get you now.

I was wondering why trying to fit everything on one line was causing errors(origional source said something along lines of:
```
for i in `ls`; do; echo $i; done;
```
but I couldn't get this to work :P

like i said, use shell expansion to avoid errors due to the complication of file names with spaces.
```

# ls -1
file with spaces
filewithnospaces
# for i in `ls`; do echo "$i"; done
file
with
spaces
filewithnospaces
# for i in *; do echo "$i"; done
file with spaces
filewithnospaces
# for i in `ls`; do cp "$i" "$i".txt; done
cp: cannot stat `file': No such file or directory
cp: cannot stat `with': No such file or directory
cp: cannot stat `spaces': No such file or directory
cp: cannot stat `file': No such file or directory
cp: cannot stat `with': No such file or directory
cp: cannot stat `spaces.txt': No such file or directory
# for i in *; do cp "$i" "$i".txt; done
# ls -1
file with spaces
file with spaces.txt
filewithnospaces
filewithnospaces.txt



```

---

### Post by scragar on 2008-03-27
blast, spaces in file names, never thought about that.

---

### Post by WW on 2008-03-27
**rename** could also work:
> 
$ ls -1
asdf.Bfile
not_this
qwer.Afile
s p a c e s.Dfile
uiop.E file with spaces
zxcv.Cfile
$ [color="blue"]rename 's/.*\.([^.]+)/$1.txt/' *[/color]
$ ls -1
Afile.txt
Bfile.txt
Cfile.txt
Dfile.txt
E file with spaces.txt
not_this
$ 


---

### Post by mssever on 2008-03-27
> **scragar said:**
>  ```
$ for i in `ls`
```

The ls command is meant to be human-readable. Its output isn't safe for parsing (filenames can contain spaces and newlines). Use ```
for i in *
``` instead.

---

### Post by lloyd_b on 2008-03-27
> **jflaker said:**
> The file names are like this

xxxx.AllDifferentNames

Which is why I asked.  So, Looking at the replies, I think there are details that were missed....

I want to strip away everyhing from the the beginning of the file name, up to and including the dot.  I then want to append a ".txt" to the end of the name so windows knows it is a text file.

All good information either way..........

I dowloaded PyRenamer, which worked very well.  It would still be interesting to see some code either way

```
#!/bin/bash

# Loop through all files in the current directory
for FILE in *; do

     # Take everything after the period, and move it to EXT
     EXT=`echo "$FILE" | cut -d '.' -f 2`

     # Concatenate ".txt" onto EXT to create the new filename
     NEWFILE="$EXT.txt"

     # Move the old file to the new name
     mv "$FILE" "$NEWFILE"

done
```

Note that this is a pretty simple script, and lacks a lot of error checking.  For instance, it doesn't verify that actually is a period in the filename, that there is actually something after the period, and that we aren't accidentally overwriting an existing file.  But for your situation it would probably have done the job.

Note: If you consider this solved, then please go to the "Thread Tools" and mark it as such.

Lloyd B.

---

### Post by ghostdog74 on 2008-03-27
> **lloyd_b said:**
> [CODE]#!/bin/bash
...
     # Take everything after the period, and move it to EXT
     EXT=`echo "$FILE" | cut -d '.' -f 2`
...



if the filename is like blah.blah.ext, then using  the cut method with -f 2 might not get the desired results

---

### Post by lloyd_b on 2008-03-27
> **ghostdog74 said:**
> if the filename is like blah.blah.ext, then using  the cut method with -f 2 might not get the desired results

True.  I mentioned the possibility of no period, but too many periods would be just as bad.

```
     EXT=`echo "$FILE" | awk -F"." '{print $NF}'`
```
would be a good solution - it grabs the last field, regardless of the number of periods, and as an added bonus if there are no periods, it returns the entire input string (where cut would return an empty string).

Lloyd B.

---

### Post by Wybiral on 2008-03-27
Python:
```

import os
for fullname in os.listdir("./"):
    name, extension = fullname.split(".")
    os.rename(fullname, name + ".txt")

```

---

### Post by lloyd_b on 2008-03-27
> **Wybiral said:**
> Python:
```

import os
for fullname in os.listdir("./"):
    name, extension = fullname.split(".")
    os.rename(fullname, name + ".txt")

```

Actually, for the original question it would be
```
os.rename(fullname, **extension** + ".txt")
```

One issue (basically, the same one Ghostdog brought up in regards to my script) - the script crashes if there is more than one period in a filename, or if there is no period in the filename.

Lloyd B.

---

### Post by Wybiral on 2008-03-27
> **lloyd_b said:**
> Actually, for the original question it would be
```
os.rename(fullname, **extension** + ".txt")
```

One issue (basically, the same one Ghostdog brought up in regards to my script) - the script crashes if there is more than one period in a filename, or if there is no period in the filename.

Lloyd B.
Ah, I didn't realize you needed the right side. What should it do if there are more than one (or zero) periods?

EDIT:

Oh, something like this then?
```
import os
for name in os.listdir("./"):
    os.rename(fullname, name.split(".")[-1] + ".txt")
```

---

### Post by ghostdog74 on 2008-03-27
> **Wybiral said:**
> Ah, I didn't realize you needed the right side. What should it do if there are more than one (or zero) periods?


```

>>> s="file.file.txt"
>>> import os
>>> os.path.splitext(s)
('file.file', '.txt')
>>>

```

---

### Post by ghostdog74 on 2008-03-27
> **lloyd_b said:**
> 
```
     EXT=`echo "$FILE" | awk -F"." '{print $NF}'`
```

if using bash , no need to call external command.
```

# s="file.file.txt"
# echo ${s##*.}
txt
# s="file"
# echo ${s##*.}
file

```
of course, using awk is almost always guaranteed to work in different *nixes.

---

### Post by jflaker on 2008-03-27
Thanks for all the input.  I am a programmer, but I am not that familiar with Python so........as always, there are MANY ways to skin a cat.

As I said earlier, PyRename worked wonders but I wanted to see some good code......

Thanks EVERYONE who answered

---

### Post by dashnak on 2008-03-27
Glad to know PyRename worked

---

