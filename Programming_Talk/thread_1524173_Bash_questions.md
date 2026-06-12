---
title: "Bash questions"
date: 2010-07-04
forum: Programming Talk
---

### Post by unrealer on 2010-07-04
Hello all, I'm pretty new to programming, and I'm in the process of writing/updating a script for some research work. 

I was wondering, what is the simplest way of getting total number of files in a directory and save that number to a variable within bash.

Second question is, how to process the file names in a directory, and save them into a variable in bash..

Thanks.

---

### Post by stderr on 2010-07-04
Haven't tested, but this should give you an idea:

```
FCOUNT=0 
for f in **path/to/your/directory/*** ; do 
  if [ -f "$f" ] ; then 
    FCOUNT=`expr $FCOUNT + 1` 
  fi 
done 
echo $FCOUNT

```

For the filenames, you've got them already in the for loop - the variable $f holds each one. Do with them as you wish. E.g. to append each to a variable with a delimeter of, say, a colon (a bad idea, granted), add a line like this in the for loop:

```
FNAMES=$FNAMES:$f;
```

Note that some people would go nuts seeing the antiquated `expr .. + 1` in there to increment a variable ;) You should be able to do something like this instead:

```
FCOUNT=$[FCOUNT+1]
```

---

### Post by kaibob on 2010-07-05
> **unrealer said:**
> Hello all, I'm pretty new to programming, and I'm in the process of writing/updating a script for some research work. 

I was wondering, what is the simplest way of getting total number of files in a directory and save that number to a variable within bash.

Second question is, how to process the file names in a directory, and save them into a variable in bash..

Thanks.

There are a lot of ways to get a count of the number of files in a directory. Probably the simplest--which works if the target directory does not contain any subdirectories--is:

```
number=$(ls -1 | wc -l) ; echo $number
```

If the target directory contains subdirectories, then the find command can be used:

```
number=$(find . -maxdepth 1 -type f | wc -l) ; echo $number
```

As mentioned by stderr, the best way to process the files in a directory is by way of a for loop:

```
for files in * ; do
  echo "$files"
done
```

If you actually want to assign the names of all files in a directory to a variable, then it's best to use an array variable:

```
files=( * )
```

If you use an array, then you can get a count of the files by:

```
files=( * ) ; echo ${#files[@]}
```

Which of the above (if any) are applicable depends on what you are doing in the shell script.

---

### Post by unrealer on 2010-07-05
Thank you for your help, I will take those examples and see what I can do with them.

---

### Post by ju2wheels on 2010-07-05
Options, options, options...

Heres another:

```

#!/bin/bash
COUNT=`ls -al | wc -l`;
COUNT=$[ ${COUNT} - 2 ];

```

[edit] *it counts folders in current directory as well by the way (thats what I get for answering at 4 in the morning, and not reading all posts)

---

### Post by unrealer on 2010-07-05
[kaibob]("http://ubuntuforums.org/member.php?u=595193")

can you elaborate a bit more for getting the file name into variables? for example, what if there are 3 files in directory, called "sushi" , "is", "good"  now I want to somehow read that into different variables such as a1 a2 and a3, or a 2d variable of some sort, so i can do some string manipulation on them... 

Thanks

---

### Post by kaibob on 2010-07-05
The following illustrates:

> $ ls -1
good
is
sushi

$ files=( * ) ; echo ${files[0]}
good

$ files=( * ) ; echo ${files[1]}
is

$ files=( * ) ; echo ${files[2]}
sushi

$ files=( * ) ; echo ${files[@]}
good is sushi

$ files=( * ) ; echo ${#files[@]}
3


The following is a good general discussion of bash arrays:

[http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005)

---

### Post by juancarlospaco on 2010-07-05
Attention for :

**N**ames L**í**ke**_**Th**ì**s

:)

---

