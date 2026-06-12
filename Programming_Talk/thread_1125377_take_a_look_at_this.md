---
title: "take a look at this"
date: 2009-04-14
forum: Programming Talk
---

### Post by shishir_knit on 2009-04-14
[B]array=('ls -B')
i=0
while [ $i -lt $nof ]; do
	p=`${array[$i]}`
        q="$p"
        n=`du -b -s $q`
        echo "$n">>/home/shishir/read.txt
	let i++
done[/B]

this code is not running properly
what to do

reply will be appreciated

---

### Post by Tony Flury on 2009-04-14
Can you tell us what it is meant to do ? Do you get error messages ?

---

### Post by shishir_knit on 2009-04-14
i wanted to get the total size of directory/file without their subdirectory sizes
this command 
**`du -b -s $q`**
is not working when filename contains space

---

### Post by shishir_knit on 2009-04-14
here **nof** is number of files/directories in current directory

---

### Post by Perfect Storm on 2009-04-14
Moved to Programming Talk, you might get a better respond here.

---

### Post by shishir_knit on 2009-04-14
please reply

---

### Post by shishir_knit on 2009-04-14
thanks

---

### Post by sujoy on 2009-04-14
```
du -bsS * > filename
```
seems to do the job pretty fine, not sure what more you need though

---

### Post by shishir_knit on 2009-04-14
this code too is not working as i want
the common problem with this code and my code is that it shows the size of many directories as **4096** which actually is not

secondly i dont want temporary files(*.*~)in the list
i want the sizes of only files & directories(no need of internal details of subdirectories or files)

---

### Post by shishir_knit on 2009-04-15
please reply

---

