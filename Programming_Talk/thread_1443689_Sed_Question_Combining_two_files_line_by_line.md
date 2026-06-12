---
title: "Sed Question: Combining two files line by line"
date: 2010-03-31
forum: Programming Talk
---

### Post by ajlee on 2010-03-31
I've done some google searching but no one has given an example of what I am looking for.  I have two files:


File 1
======
AAAA
BBBB
CCCC

File 2
======
XXXX
YYYY
ZZZZ


What I want to end up with is:

AAAA
XXXX
BBBB
YYYY
CCCC
ZZZZ

Anyone know how to do this with sed?  Also, if you can point me to any good sed tutorials/books that would be great.

Thanks!

---

### Post by sisco311 on 2010-03-31
Is this a homework? Do you have any reason to use sed instead of awk?

---

### Post by ajlee on 2010-03-31
No it's something I am trying to accomplish at work.  I can use any program that will get the job done.  What I am actually doing is generating database commands out of the system catalog and I want to combine two lists of commands into one file (ie. count (*) from TABLE followed by the export from the table so I can see if the counts match without having to go back and forth between two files).

Thanks!

---

### Post by DaithiF on 2010-03-31
Hi, you could use paste.
e.g.

```
$ cat file1
AAAA
BBBB
CCCC

$ cat file2
XXXX
YYYY
ZZZZ

$ paste -d'\n' file1 file2
AAAA
XXXX
BBBB
YYYY
CCCC
ZZZZ


```

---

### Post by geirha on 2010-03-31
```
paste -d '\n' file1 file2
```

EDIT: D'oh, beaten to the punch.

---

### Post by sisco311 on 2010-03-31
2xd'oh, of course, paste... I completely forgot it. :redface:

I was playing with awk:
```
awk 'OFS="";NR==FNR{a[FNR]=$0;next} {print a[FNR],"\n","\b",$0}' file1 file2
```

It works, but of course *paste* is preferable.

---

### Post by cdiem on 2010-03-31
As a python script:

```

try:
	file1 = open("file1.txt")
	file2 = open("file2.txt")
	for line_f1 in file1:
		for line_f2 in file2:
			print line_f1, line_f2,
			break
except IOError:
	print "One or more of the files does not exist"

```

```

cdiem@cdiemst:~/Desktop$ cat file1.txt
AAAA
BBBB
CCCC
cdiem@cdiemst:~/Desktop$ cat file2.txt
XXXX
YYYY
ZZZZ
cdiem@cdiemst:~/Desktop$ python play.py
AAAA
XXXX
BBBB
YYYY
CCCC
ZZZZ

```

Of course, the one-liner with paste is better.

---

### Post by ajlee on 2010-03-31
Thanks everyone.  I had looked at paste - but I guess I was leaving off the '' around the \n.  Ran the command as you guys described it and it worked perfectly.

Thanks again!

---

### Post by kaibob on 2010-03-31
Because this issue arose for me in a different context, I was curious how the OP's question might be addressed with bash but without the use of an external command (awk, sed, paste, and so on). I came up with the following, which works. Is it possible to do this without the use of an array. What I had in mind was some sort of nested loops. Thanks!

```
#!/bin/bash

IFS=$'\n'

list1=( $(<file1) )
list2=( $(<file2) )

for i in ${!list1[@]} ; do
   echo ${list1[${i}]}
   echo ${list2[${i}]}
done
```

---

### Post by geirha on 2010-03-31
> **kaibob said:**
> Because this issue arose for me in a different context, I was curious how the OP's question might be addressed with bash but without the use of an external command (awk, sed, paste, and so on). I came up with the following, which works. Is it possible to do this without the use of an array. What I had in mind was some sort of nested loops. Thanks!

```
#!/bin/bash

list1=( $(<file1) )
list2=( $(<file2) )

for i in ${!list1[@]} ; do
   echo ${list1[${i}]}
   echo ${list2[${i}]}
done
```

That will not output line by line, it will output word by word.  Furthermore, if any of those words were to be a glob (pattern) like * for instance, that would be expanded to all files in the current directory. 

But, to your question, yes, it can be done safely in bash, and without using arrays.

```
#!/bin/bash

while IFS= read -r -u3 line1 && IFS= read -r -u4 line2; do
  printf "%s\n" "$line1" "$line2"
done 3< file1 4< file2

```

---

### Post by kaibob on 2010-03-31
geirha

Thanks for the response. It answers my question and opens a new area of study for me. I was not familiar with what I believe are called file descriptors or that they could be used in scripts in this manner.  

I have modified the script in my earlier post to change the IFS to a newline. When I wrote this script I was working with the OP's source files, which only contained one word per line. So, the script worked fine.

Thanks again.

kaibob

---

