---
title: "combining text files in bash"
date: 2008-11-08
forum: Programming Talk
---

### Post by dunryc on 2008-11-08
Hi guys thanks for all your help in the past and hopefully with this one as well :-)

i have two text files file1 and file2 both files have 40 lines what i want to do is create on file with one line from each file combined. for example

file1

> 
the quick brown fox 
jack and jill 
humptey dumptey 



file2

> 
jumped over the lazy dog 
ran up the hill 
sat on a wall 



the results i want ! 

> 
the quick brown fox - jumped over the lazy dog 
jack and jill - ran up the hill 
humpty dumpty - sat on a wall 



does any one know of a way of achieving this ?? any help at all would be appreciated I've been looking at the tail and head command and passing them to variables but feel i may be missing a trick somewhere

---

### Post by Mr.Macdonald on 2008-11-08
Not in bash but here the solution in python

first go to directory with files
then type python into terminal (you should see >>> for the python prompt)
no copy and paste this into the python

replace path to file with the actual path (just the file name if you are in that directory)

this code will put a " - " in between the lines of each file, as in your example, if you don't want this then remove the ' + " - "'

copy everything in the PHP box (even newlines) use Ctrl - Shift - v to paste in terminal
[PHP]
def mergeFile(f1, f2, f3):
	f1 = open(f1, "r")
	f2 = open(f2, "r")
	f3 = open(f3, "w")
	for i in f1:
		s = i.replace("\n", "") + " - " + f2.readline().replace("\n", "")
		f3.write(s+"\n")


mergeFile("path to file1", "path to file2", "path to output file")


[/PHP]

---

### Post by unutbu on 2008-11-08
```

%  paste file1 file2 | sed -e 's/\s*\t\s*/ - /g'
the quick brown fox - jumped over the lazy dog
jack and jill - ran up the hill
humptey dumptey - sat on a wall


```

---

### Post by WW on 2008-11-08
The **paste** command does almost what you want:
```

$ paste -d- file1 file2

```
will combine corresponding lines, separated by a dash.  The -d option doesn't handle separators with multiple characters (at least not the way you want).

---

### Post by Sub101 on 2008-11-08
```
#!/bin/bash
echo "What is the name of the first file?"
read filename1
echo "What is the name of the second file?"
read filename2
n=(1)
while (n <= 40); do
line[${n}]=$(sed -n ${n}{p} $filename1.lst)
line[${m}]=$(sed -n ${n}{p} $filename2.lst)
echo ${line[$n]}" - "${line[$m]}>>Joinedfile.lst
n=$((1+$n))
done

```

Something like this should work.

---

### Post by dunryc on 2008-11-08
> **unutbu said:**
> ```

%  paste file1 file2 | sed -e 's/\s*\t\s*/ - /g'
the quick brown fox - jumped over the lazy dog
jack and jill - ran up the hill
humptey dumptey - sat on a wall


```

thanks unutbu this worked great for what i wanted and thanks every one else for all your ideas

---

### Post by conscious on 2008-11-09
Actually, there are commands for it, **lam** and **paste**.

---

