---
title: "csh scripting problem!!"
date: 2008-10-15
forum: Programming Talk
---

### Post by adramalech on 2008-10-15
this csh program will ask the user for a filename then check all the directories and files in the present working directory for anything matching the filename and output it...then ouput the number of directories searched and filename searched...simple right but i get a error before i even start what is in the foreach loop...

```

#!/bin/csh
#
# file name: ~/CSC60/lab4/hunt*
# Author: Jonathan Throne
# Date Written: October 15, 2008
# Date Last Modified: October 15, 2008
#
clear
set COUNT_DIRECTORIES = 0
set COUNT_FILES = 0
set FILE
echo -n "Please enter a file name you wish to search for: "
set FILE_NAME = `head -1`
foreach FILE (`ls`)then
        if(-d $FILE)then
                @COUNT_DIRECTORIES++
                pushd FILE >> ~/dump
                popd >>~/dump
        endif
        else if(-f $FILE)then
                @COUNT_FILES++
                if($FILE =~ $FILE_NAME)then
                        pwd
                endif
        endif
end
rm ~/dump
echo "The number of directories searched: $COUNT_DIRECTORIES"
echo "The number of files searched: $COUNT_FILES"
exit 0

```

this is to show that the csh script file is in my present working directory...

```

> ls
CSC60/  dead.letter  html/  hunt*  huntScript.csh  mail/
>

```

will then clear the screen and this is the actual script program running..

```

Please enter a file name you wish to search for: helloWorld
foreach: Words not parenthesized.
>

```

---

### Post by reality1011 on 2008-10-15
First off, CSH Sucks...  consider using ksh,sh, or bash
<modifying it now>

---

### Post by reality1011 on 2008-10-16
My Version:


```


#!/bin/ksh
echo -n "Please enter a file name you wish to search for: "
FILE_NAME=`head -1`
find . -name "$FILE_NAME" > /tmp/log
set -A dirs_searched `find . -type d -print`
echo " searching for $FILE_NAME"
echo "Number of directories AND SubDirectories searched: ${#dirs_searched[@]}"
echo " results of search : `cat /tmp/log`"
exit

```

---

### Post by geirha on 2008-10-16
You shouldn't use ls to get a list of files to iterate. It will break for files with whitespace. Use *. And the error was just that you shouldn't use the then word.

```
foreach FILE ( * )
```

Though, as reality1011 suggests, check out the find-command.

---

### Post by dwhitney67 on 2008-10-16
> **adramalech said:**
> ...
```

#!/bin/csh
#
# file name: ~/CSC60/lab4/hunt*
# Author: Jonathan Throne
# Date Written: October 15, 2008
# Date Last Modified: October 15, 2008
#
clear
set COUNT_DIRECTORIES = 0
set COUNT_FILES = 0
set FILE
echo -n "Please enter a file name you wish to search for: "
set FILE_NAME = `head -1`
foreach FILE (`ls`)then
        if(-d $FILE)then
                @COUNT_DIRECTORIES++
                pushd FILE >> ~/dump
                popd >>~/dump
        endif
        else if(-f $FILE)then
                @COUNT_FILES++
                if($FILE =~ $FILE_NAME)then
                        pwd
                endif
        endif
end
rm ~/dump
echo "The number of directories searched: $COUNT_DIRECTORIES"
echo "The number of files searched: $COUNT_FILES"
exit 0

```
...


If you are able to use 'find', then I suggest you use it.  Otherwise, try to use the following:
```

...
foreach FILE (`ls --quoting-style=escape`)then
...

```
The quoting-style will prepend a '\' character before any white-space that may exist a file/directory name, thus enabling you to effectively use the name in your script should you need to perform a 'pushd'.

Btw, you also have an unneeded 'endif' before and after the 'else if'; remove it; you only need one for an if-else if block.  For unwanted data (such as is produced by 'pushd'), do not write it to a file; instead write it to /dev/null.  (I'd be pissed if I ran you script and it overwrote/appended the precious information I had in my '~/dump' file!)

P.S.  I do not have csh installed on my system, so I was unable to test the suggestion concerning the foreach I presented above.  I hope it works for you.

---

### Post by dwhitney67 on 2008-10-16
> **dwhitney67 said:**
> If you are able to use 'find', then I suggest you use it.  Otherwise, try to use the following:
```

...
foreach FILE (`ls --quoting-style=escape`)then
...

```
...
I tried to use something similar to the above in a bash script, and it failed miserably.

Apparently the issue is not so much with 'ls', but with the 'for'.  Not to be beaten by the (bash) shell, I came up with this not-so-pretty script that works around the problem.  Like it was mentioned earlier, use 'find' if at all possible.

```

#!/bin/bash

filename=""

for file in `ls -1 --quoting-style=escape`
do
	declare -i len=${#file}-1

	# check if dealing with partial result
	if [ "${file:$len:1}" == "\\" ]
	then
		declare -i i=0
		tmp=""
		while [ $i -lt $len ]
		do
			tmp="$tmp${file:$i:1}"
			i=$i+1
		done
		if [ "$filename" == "" ]
		then
			filename="$tmp"
		else
			filename="$filename $tmp"
		fi
	else
		# reached end of filename (could happen on first pass)
		if [ "$filename" == "" ]
		then
			filename=$file
		else
			filename="$filename $file"
		fi

		# do something with complete filename
		file "$filename"

		# clear for next evolution
		filename=""
	fi
done

```

P.S.  The only time 'find' would not be a viable option is if you have a professor that "sucks".  He/she may want students to think of an original solution, rather than rely on a built-in tool.

---

### Post by geirha on 2008-10-16
As I mentioned earlier, foreach should not have a then at the end.

```
foreach FILE (`ls --quoting-style=escape`)
```
will work, but
```
foreach FILE ( * )
```
should be the preferred way.

---

### Post by adramalech on 2008-10-16
well getting rid of the then helped:lolflag:...but it doesn't search well i need to fix some stuff...

what is the difference from

set FILE_NAME = "$<"

and...

set FILE_NAME = "head-1":confused:

also how do i increment counters...

i said @ COUNT_DIRECTORIES ++ thats wrong i know it threw an error is there a way to and how??

---

### Post by adramalech on 2008-10-16
okay so i tried the star and i tried the foreach FILE (`ls --quoting-style=escape`) and both failed i don't what happened but every time i ran it it wouldn't find the file!!!

second thing, this isn't for pleasure this is an assignment, i cannot use search or find can only use popd pushd and i use the ~/dump file because i am dealing with ssh server not ubuntu....i have to use csh because that is all my school has to use...don't ask me why i think bash would be better!!!

i would like to ask though if the variable FILE was to get the list of files and store them theoretically my conditions should work right??? because if my logic isn't correct neither will my code ever be!!

---

### Post by geirha on 2008-10-16
The man page says that @ name++ will increment name, it does not say anything about @name++ ...

Also make sure to quote variables containing filenames. "$FILE" not $FILE

---

### Post by dwhitney67 on 2008-10-16
> **adramalech said:**
> well getting rid of the then helped:lolflag:...but it doesn't search well i need to fix some stuff...

what is the difference from

set FILE_NAME = "$<"

and...

set FILE_NAME = "head-1":confused:

also how do i increment counters...

i said @ COUNT_DIRECTORIES ++ thats wrong i know it threw an error is there a way to and how??
You must hate Google?

Go here:  [http://www.kingston.ac.uk/support/unix/Scripts.html](http://www.kingston.ac.uk/support/unix/Scripts.html)
and scroll down to "Reading user input".

There is also information (at the top of the webpage) concerning Expressions (just follow the link at the bottom of the section).

---

### Post by adramalech on 2008-10-16
okay this is the code as it looks right now!! it will execute and print out how many directories and how many files searched, but it will only check the current directory will not go into any sub directories of the current directory..

```

#!/bin/csh
#
# file name: ~/CSC60/lab4/hunt*
# Author: Jonathan Throne
# Date Written: October 15, 2008
# Date Last Modified: October 15, 2008
#
clear
set COUNT_DIRECTORIES = 0
set COUNT_FILES = 0
set FILE
echo -n "Please enter a file name you wish to search for: "
set FILE_NAME = `head -1`
foreach FILE (`ls --quoting-style=escape`)
        if(-d "$FILE")then
                @ COUNT_DIRECTORIES++
                pushd "$FILE" >> ~/dump
                popd >>~/dump
        else if(-f "$FILE")then
                @ COUNT_FILES++
                if("$FILE" =~ "$FILE_NAME")then
                        pwd
                endif
        endif
end
#rm ~/dump
echo "The number of directories searched: $COUNT_DIRECTORIES"
echo "The number of files searched: $COUNT_FILES"
exit 0

```

see that this is the dump file where it will right the pops and pushs..

```

> cat dump
~/CSC60 ~
~
~/html ~
~
~/mail ~
~
~/CSC60 ~
~
~/html ~
~
~/mail ~
~
~/CSC60 ~
~
~/html ~
~
~/mail ~
~
>

```

this is the current working directory where i have the script file and where i execute it...it is my home directory..

```

~> ls
CSC60/  dead.letter  dump  html/  [COLOR="Red"]hunt*[/COLOR]  huntScript.csh  mail/
~>

```

but in CSC60 there are 4 more directories and in the other directories html and mail there are some more files...

so should be more than 4 files and at least 7  directories but this is the output when i run the code...

```

Please enter a file name you wish to search for: helloWorld
The number of directories searched: 3
The number of files searched: 4
~>

```

this is showing me that i don't evaluate the files and i don't do the pops!!!

maybe i should switch up how i evaluate the conditions....

what i mean is that:

if(-f "$FILE") then
       .....
else 
     .....
end

---

### Post by geirha on 2008-10-16
You'll need to use recursion. That seems to be a bit difficult with csh though, as apparently you can't make functions in it !?

I guess your best bet is to take input as an argument, and then call the script for each directory.

---

### Post by dwhitney67 on 2008-10-16
> **adramalech said:**
> ...
but in CSC60 there are 4 more directories and in the other directories html and mail there are some more files...

so should be more than 4 files and at least 7  directories but this is the output when i run the code...

```

Please enter a file name you wish to search for: helloWorld
The number of directories searched: 3
The number of files searched: 4
~>

```
...
Two suggestions... and the first may not be enough:

1.  Use the -R option with 'ls' (to recursively delve into subdirectories)

2.  Augment your output statements so that you see exactly what is being "worked"/"looked" upon.

---

### Post by reality1011 on 2008-10-17
You probably need to loop through this command to find sub-directories

```

**** List current sub-directories ****
ls -al | grep ^d


*** To count the number of files: 
cappetta@Linux-Box:~/public_html$ ls -lRt | grep ^- | wc -l
7054

*** To Count the number of directories
cappetta@Linux-Box:~/public_html$ ls -lRt | grep ^d | wc -l
290

****To find the file: 
cappetta@Linux-Box:~/public_html$ ls -lRt | awk ' {if ($8 == "zoom.htm") {print "Found: " $0}}'
Found: -rw-r--r-- 1 cappetta cappetta 23432 2008-02-23 11:20 zoom.htm
Found: -rw-r--r-- 1 cappetta cappetta 23432 2008-01-15 07:28 zoom.htm


** OR **

cappetta@Linux-Box:~/public_html$ ls -lRt | grep  zoom
-rw-r--r-- 1 cappetta cappetta 23432 2008-02-23 11:20 zoom.htm
-rw-r--r-- 1 cappetta cappetta 23432 2008-01-15 07:28 zoom.htm





```

---

