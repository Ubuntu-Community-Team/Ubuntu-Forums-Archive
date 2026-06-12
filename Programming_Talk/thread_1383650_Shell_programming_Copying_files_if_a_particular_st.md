---
title: "Shell programming: Copying files if a particular string is present in the filename"
date: 2010-01-17
forum: Programming Talk
---

### Post by vinayg18 on 2010-01-17
Hi,

Consider this: 
I have a set of files in a directory. Let the names of the files be abcde.txt, pqrst.txt, mnabcop.txt and so on.
I want to copy to another directory only those files which have "abc" in their file name. I realise I can simply use the metacharacter * and select such files with *abc*.txt, but I want to try it using ls and grep.

I know one part of the command would be ls | grep abc, but I can't seem to link it with the cp command. 
Do I use '>' or do I use another pipe? I tried 
```
ls | grep abc | cp foldername
```
but I get an error saying the destination directory is missing. I also tried 
```
cp <ls|grep abc foldername
```
but it doesn't work either.
Can someone help me? Thank you. I'm a n00b to shell programming, among other things :)

---

### Post by matchett808 on 2010-01-17
erm.....I think something along the lines of:

cp ./$(ls | grep abc) /destination

but if there are multiple files it may not work, it may be more prudent to do a loop or a for funciton copying one at a time (remeber if the transfers may take some time you could run them "in the background" and redirect the output to somewhere....

let me know if this helps....

EDIT: 

it may be possible (I cant remember if wildcards will work but its worth a check) 

cp ./*abc*.* /destination

but you will have to chec what the wildcards are in the cp man pages (i would but i need to go the now...)

---

### Post by phrostbyte on 2010-01-17
```

for i in $(ls | grep abc) do
  cp $i /dest/to/copy
done

```

---

### Post by matchett808 on 2010-01-17
yeah i reckon phrostbytes code is the way to go...

---

### Post by denarced on 2010-01-17
personally I'd use find for this:
```
find . -type f -iregex '.*abc.*' -exec cp '{}' /to/folder/where.ever \;
```
find doesn't have problems with filenames that contain spaces or other whitespace
example command works if you're in the same directory
also note that in this form it'll find files also from subdirectories

---

### Post by denarced on 2010-01-17
> **phrostbyte said:**
> ```

for i in $(ls | grep abc) do
  cp $i /dest/to/copy
done

```

I'm thinking this might have problems with space containing filenames

---

### Post by Hellkeepa on 2010-01-17
HELLo!

Add quotes around the "$i" then, it's that easy. ;-)

Happy codin'!

---

### Post by falconindy on 2010-01-17
> **Hellkeepa said:**
> HELLo!

Add quotes around the "$i" then, it's that easy. ;-)

Happy codin'!

It's not that easy, actually, because the problem occurs when the results of the command are iterated over in addition to when the copy is done. To use a foreach loop, you'd need to do the following:

```
#!/bin/bash

files=($(ls | grep abc))
for file in "${files[@]}"; do
    cp "$file" /to/dest
done
```
The combination of the @ operator to return all the elements plus quoting the array reference will give you the functionality you want. Find is probably a better/simpler option here.

---

### Post by Hellkeepa on 2010-01-17
HELLo!

Ah, thanks for correcting me. I'll keep it in mind. :-)

Happy codin'!

---

### Post by matchett808 on 2010-01-17
a non recursive way in one line:

cp ./$(ls | grep abc) /absoloute/path/to/dest

unfortunatle ls does a recursive find (-R) but it doesnt report absoloute path names....(as far as i know, if you could find the absoloute switch from ls then this would give it in one line)

---

### Post by phrostbyte on 2010-01-17
> **denarced said:**
> I'm thinking this might have problems with space containing filenames

Yes this is true. Whitespace seems to delimit the output.

I also recommend going with the *find* command, in the limited times I have had to do something similar, the find command worked really well. I am not sure why ls/grep is really needed, but the OP said it was.

---

### Post by lostinxlation on 2010-01-17
cp `ls . | grep abc` <target directory>

---

### Post by vinayg18 on 2010-01-18
Thank you for all the replies.
I tried them all, and learnt some new things, but the last solution by lostinxlation is the one I was looking for. The backquote, of course! :)

---

