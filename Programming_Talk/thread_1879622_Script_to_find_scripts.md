---
title: "Script to find scripts"
date: 2011-11-11
forum: Programming Talk
---

### Post by crownedzero on 2011-11-11
```

#!/bin/bash

#scriptfinder.sh

#check for arguments
if [ ! -z $2 ]; then
	echo "USAGE: Too many arguments"

#if argument is empty
elif [ -z $1 ]; then
	clear
	for i in $(ls -l $1)
		do
			if [ -x $i ]; then
				echo "$i"
				du -sh $i | awk '{print "Size: " $1}'
				file $i | awk '{print "Script type: " $2}'
fi
		done
#if 1 argument exists
elif [ -n $1 ]; then
	clear
	for i in $(ls -l $1)
		do
			if [ -x $i ]; then
				echo "$i"
				du -sh $i | awk '{print "Size: " $1}'
				file $i | awk '{print "Script type: " $2}'
fi
		done

#default
else
	echo "Wasn't able to understand the command line argument"
fi


```

Finds scripts if they are executable, I'm hoping to revise it to find all shell scripts...suppose I use the file filename command, would it be best to set this to a string and then compare it to each file in a directory?

---

### Post by ofnuts on 2011-11-12
[LIST]
[*]To find executable files use```
find -executable
```
[*]To determine if a given file is a script (vs binary) use the file command, or test for shebang ("#!")
[*]Your code tests for a missing $1 but then uses it (a good default value would be ".")
[/LIST]

---

### Post by crownedzero on 2011-11-12
find -executable only looks for those marked +x

file on the other hand will list if it is a shell script, guess the issue I'm having is the logic.

If part of the file returns "shell script", compare to string and then, spit out the info or is there an easier way?

---

### Post by ofnuts on 2011-11-12
> **crownedzero said:**
> find -executable only looks for those marked +x

file on the other hand will list if it is a shell script, guess the issue I'm having is the logic.

If part of the file returns "shell script", compare to string and then, spit out the info or is there an easier way?If you don't filter on "executable", all files are shell scripts...
```

>echo "echo foo" >notascript
>file notascript 
notascript: ASCII text
>. notascript 
foo

```Above, file doesn't consider "notascript"to be a script, while it is one since bash will run it. In fact file relies on the "shebang":
```

>echo "#! /bin/sh" >notascript
>echo "echo foo" >>notascript
>cat notascript 
#! /bin/sh
echo foo
>file notascript 
notascript: POSIX shell script text executable

```But the shebang is only useful for a file marked executable, because it the file is not marked such, you can still call it as an argument to a shell interpreter("bash notascript" or ". notascript")  but in that case the shebang is ignored.

---

### Post by crownedzero on 2011-11-12
Not sure I followed.

So for file in a directory set a variable equal to the whatever the file command returns, then compare this variable to "shell script" or something similar, if yes display, else move on to the next correct?

---

### Post by ofnuts on 2011-11-12
> **crownedzero said:**
> Not sure I followed.

So for file in a directory set a variable equal to the whatever the file command returns, then compare this variable to "shell script" or something similar, if yes display, else move on to the next correct?

Indeed you didn't follow :) Let me rephrase it.

A shell script is a file that is interpreted. There are to ways to have it interpreted: 

[LIST=1]
[*]explicitly designate it as a target to the interpreter ("sh foo" or ". foo"): in this case the execute flag and the shebang are not necessary, so unless you parse the file to attempt to recognize some shell syntax, you can't distinguish such a script from, say, C source code or a shopping list.
[*]call its name and have a shell interpreter use a) the execute flag to determine if it can be executed [SIZE=3]***and***[/SIZE] b) the shebang to see how it is executed. In other words, the shebang is irrelevant is the file is not executable, and the execute flag is useless without a shebang.
[/LIST]
So case 1) is out of your reach, and if you want to cover case 2) filtering on the executable flag isn't going to make you miss any script.

---

