---
title: "Problem with 'greater than' bash script"
date: 2010-04-30
forum: Programming Talk
---

### Post by mhouston100 on 2010-04-30
Hi guys, first script and I'm a little stuck.  Basically this script will run periodically on my recorded TV directory and if the space left is under 10% remove the last folder in the dir.

What I'm stuck on is getting the 'if' conditions right.  I'm trying to say "If the percent used is greater than 90, then do the task"

It keeps reporting:

```
[: 28: Illegal number: 

```

I've tried with '>' and also with '-qt' but I'm not really sure on the syntax of it.  All the variables return correctly.

```
#!/bin/bash

var=olddir
var=tvdir
var=usedperc
var=highperc

##Declare tv recording directory and percentage
highperc=90
tvdir=/media/TV/TV

## Get oldest directory read it into var ldir

olddir=`ls -lt $tvdir | grep "^d" | tail -1 | cut -f 9 -d ' '`

## Find used percent Read into usedperc

usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`

## test make sure variables are correct
echo $highperc
echo $tvdir"/"$olddir
echo $usedperc

## If used percentage is greater then 90% then remove last directory
if [ "$usedprc" -gt "$highperc" ];	then
	`rm -R $tvdir"/"$olddir`
fi
```

This is pretty much just a learning exercise for me and ill be adding a condition so that if removing the dir doesn't bring it under 90% then go again.

Any help is, as alway's, greatly appreciated!

---

### Post by mhouston100 on 2010-04-30
Well, once again I jumped the gun, seems I had some quotation marks in the wrong place.

All good now!

```
if [ $usedprc > $highperc ]; then
	`rm -R $tvdir"/"$olddir`
fi
```

For anyone else with the same issue

---

### Post by mhouston100 on 2010-04-30
Well, I guess I hadn't solved it.  I'm no longer getting any errors, but the expression is still not returning the correct answer. 

This is what I have so far :

```
#!/bin/bash

var=olddir
var=tvdir
var=usedperc
var=highperc
var=leftperc

##Declare tv recording directory and percentage
highperc=90
tvdir=/media/TV/TV

## Get oldest directory read it into var ldir

olddir=`ls -lt $tvdir | grep "^d" | tail -1 | cut -f 9 -d ' '`

## Find used percent Read into usedperc

usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`

## While the used space is greater then 90%, remove the last directory

while [ $usedprc > $highperc ]
do
	`rm -R $tvdir"/"$olddir`
	usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`
done
```

So the issue is still with the section :

```
while [ $usedprc > $highperc ]
do
	`rm -R $tvdir"/"$olddir`
	usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`
done
```

I am officially completely stuck now, tried that many different combinations I've lost myself!

---

### Post by Vox754 on 2010-04-30
> **mhouston100 said:**
> Well, I guess I hadn't solved it.  I'm no longer getting any errors, but the expression is still not returning the correct answer. 

This is what I have so far :

```

So the issue is still with the section :

[CODE]while [ **$usedprc > $highperc** ]
do
	**`rm -R $tvdir"/"$olddir`**
	usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`
done
```

I am officially completely stuck now, tried that many different combinations I've lost myself!

From the bash(1) manual
```

       string1 > string2
              True if string1 sorts after  string2  lexicographically  in  the
              current locale.

       arg1 OP arg2
              OP  is one of -eq, -ne, -lt, -le, -gt, or -ge.  These arithmetic
              binary operators return true if arg1 is equal to, not equal  to,
              less  than, less than or equal to, greater than, or greater than
              or equal to arg2, respectively.  Arg1 and arg2 may  be  positive
              or negative integers.

```

The string comparison most likely will never fail but will give you incorrect results. Use "-gt" for arithmetic comparison.

Also, remove the backquotes in the remove command. Otherwise, you are performing Command Substitution, that is, you are trying to execute the result of "rm". Watch out for the quotes.

```
while [ **$usedprc -gt $highperc** ]
do
	**rm -Rf $tvdir/$olddir**
	usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`
done
```

---

### Post by sujoy on 2010-04-30
use (()) for arithmetic operations.

(( $usedprc > $highperc ))

---

### Post by mhouston100 on 2010-05-01
Thanks a lot guys, seems to be working fine now.

Anyone care to run over it and see if I have made any glaring mistakes?

```
#!/bin/bash

var=olddir
var=tvdir
var=usedperc
var=highperc
var=leftperc

##Declare tv recording directory and percentage
highperc=90
tvdir=/media/TV/TV

## Get oldest directory read it into var ldir

olddir=`ls -lt $tvdir | grep "^d" | tail -1 | cut -f 9 -d ' '`

## Find used percent Read into usedperc

usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`

## While the used space is greater then 90%, remove the last directory

while [ $usedperc -gt $highperc ]
do
	rm -R $tvdir"/"$olddir
	usedperc=`df $tvdir -h | tail -1 | cut -c 41-42`
done
```

And once again thats a lot!

---

