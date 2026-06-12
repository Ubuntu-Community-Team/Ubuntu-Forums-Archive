---
title: "[SOLVED] shell script extension changer"
date: 2008-08-26
forum: Programming Talk
---

### Post by king vash on 2008-08-26
I am working on a shell script that takes an old extension, a new extension and a directory and renames all the old extension to new extension in the directory (and subdirectories)

so far I have this.

```
#!/bin/sh
if [ $# = 3 ]
then
	if [ ! $2:~0,1 = "." ]
	then
		oldext="."$2
	else
		oldext=$2	
	fi

	if [ ! $3:~0,1 = "." ]
	then
		newext="."$3
	else
		newext=$3	
	fi	

	filelist=$(find "$1" -name *$2)
	echo $filelist
	for name in "$filelist"
	do
#		echo "$name"
		name2=`echo "$name" | sed -n -e "s!$oldext!$newext!gp"`
#		mv "$name" "$name2"
#		echo "$name2"
	done
else
	echo "takes three parameters : location old extention and new extention"
fi
```

The problem is because I am ignoring spaces in $filelist in the for loop it only sends one long filename (all the file names seperated by a space)

---

### Post by yabbadabbadont on 2008-08-26
```
man rename
```
;)

---

### Post by ghostdog74 on 2008-08-26
> **king vash said:**
> 
```

	filelist=$(find "$1" -name *$2)
	echo $filelist
	for name in "$filelist"
	do
#		echo "$name"
		name2=`echo "$name" | sed -n -e "s!$oldext!$newext!gp"`
#		mv "$name" "$name2"
#		echo "$name2"
	done
else
```


use a while read loop instead of for loop
```

....
find "$1" -name *$2 | while read name
do
  #mv file...
done
....

```
also , in bash, don't have to use external commands like sed to change extension. for eg
```

# file="test.txt"
# echo ${file/.txt/.jpg}
test.jpg


```
see my sig for bash link

---

### Post by king vash on 2008-08-27
The while read loop fixed the problem thanks!

but now I have a different problem. I wanted it to count the files changes and if it changed more than one file to return a successful message.

```
	j=0;
	find "$1" -name *$oldext | while read name
	do
  		oldname=$name 
		newname=`echo $name | sed -e "s!$oldext!$newext!"`
		j=`expr $j + 1`
		echo $j
	done
	echo $j
	if [ $j -gt 2 ]
	then
		echo "Yeah! "$j" files extensions changed" 
	fi
```

how ever this returns 
```
1
2
3
4
.
.
.
47
0

```
any variable gets reset after the script. how ever if I change the initialization to "10" then 10 will be returned at the end.

---

### Post by ghostdog74 on 2008-08-27
i don't understand.

---

### Post by king vash on 2008-08-27
if i use the line 
```

	find "$1" -name *$oldext | while read name

```
then any variables set or changed in my loop get reset to the values they had before the loop.

If j=0 coming into the loop, and then I add 1 to it a couple of times and exit the loop, j will be reset to 0. If j=10 coming into the loop I can change it and do anything I want but the second I exit the loop j will be reset to 10.

I tried a couple of variations to see it they had the same problem.
this still has the problem
```

	find "$1" -name *$oldext | while [ $j -lt 20 ]

```
this didn't
```

	while [ $j -lt 20 ]

```
this did
```

	find "$1" -name *$oldext | for name in "a as asd asdf"

```

so you can see anything that has the 
```
find "$1" -name *$oldext 
```
exhibits this problem

---

### Post by dwhitney67 on 2008-08-27
The value does not change when you complete the while-loop because when you pipe the results from 'find' to the 'while', you are in essence creating a sub-shell which will have a copy of your variable 'j'.  Upon returning to the top-level shell, 'j' is still at the same value it originally held.

If there is a way around this, I am not aware of it.

I did some Googling and found a document that provides a better explanation from what I provided above.
[http://www.cs.cornell.edu/Courses/cs114/2002fa/lect9.pdf](http://www.cs.cornell.edu/Courses/cs114/2002fa/lect9.pdf)

---

