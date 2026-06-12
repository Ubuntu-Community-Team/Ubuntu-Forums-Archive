---
title: "script to create soft links."
date: 2011-05-30
forum: Programming Talk
---

### Post by Blackbug on 2011-05-30
hello,
 
i need to write a script which will create softlinks in a directory using by just making a copy of existing softlinks but with different name.
 
for example:
 
DIR contains:
 
abcinfu.txt -> ../../bin/files/abcinfu.txt
xyzinfu.txt -> ../../bin/files/xyzinfu.txt
123infu.txt -> ../../bin/files/123infu.txt
 
now new DIR structure should be:
 
abcinfu.txt -> ../../bin/files/abcinfu.txt
xyzinfu.txt -> ../../bin/files/xyzinfu.txt
123infu.txt -> ../../bin/files/123infu.txt
abctemp.txt -> ../../bin/files/abctemp.txt
xyztemp.txt -> ../../bin/files/xyztemp.txt
123temp.txt -> ../../bin/files/123temp.txt
 
I was trying to write something below:
 
```

 
fileName=""
location=""
for file in `ls -ltr *infu*`
do
 renamedFile=`ls -ltr *infu* | awk '{fileName=$8}' | sed s/infu/temp/`
 renamedLoca=`ls -ltr *infu* | awk -F"> " '{location=$2}' | sed s/infu/temp/`
 echo "Creating softlinks for $renamedFile file from $renamedLoc"
done

 

```
 
but the ls -ltr is not working, i have no clue why, on console if i run each command individually its workin as required, but from script its not

---

### Post by dwhitney67 on 2011-05-30
Here's some ideas that perhaps you can use:
```

#!/bin/bash

newfile=""
DIR1=$HOME/tmp/dir1
DIR2=$HOME/tmp/dir2


function CreateCopy()
{
   newfile=`echo $1 | sed -e s/infu/temp/`

   if [ ! -f $newfile ]
   then
        cp -p $1 $newfile
   fi
}

function CreateLink()
{
   target=$2/`basename $1`

   if [ ! -f $target ]
   then
        echo "Existing link NOT found for file $target; creating it..."
        ln -s $1 $target
   else
        echo "Existing link found for file $target."
   fi
}

for file in `ls $DIR1/*infu*`
do
        CreateCopy $file
        CreateLink $file $DIR2
        CreateLink $newfile $DIR2
done

```

---

### Post by Arndt on 2011-05-30
> **Blackbug said:**
> hello,
 
i need to write a script which will create softlinks in a directory using by just making a copy of existing softlinks but with different name.
 
for example:
 
DIR contains:
 
abcinfu.txt -> ../../bin/files/abcinfu.txt
xyzinfu.txt -> ../../bin/files/xyzinfu.txt
123infu.txt -> ../../bin/files/123infu.txt
 
now new DIR structure should be:
 
abcinfu.txt -> ../../bin/files/abcinfu.txt
xyzinfu.txt -> ../../bin/files/xyzinfu.txt
123infu.txt -> ../../bin/files/123infu.txt
abctemp.txt -> ../../bin/files/abctemp.txt
xyztemp.txt -> ../../bin/files/xyztemp.txt
123temp.txt -> ../../bin/files/123temp.txt
 
I was trying to write something below:
 
```

 
fileName=""
location=""
for file in `ls -ltr *infu*`
do
 renamedFile=`ls -ltr *infu* | awk '{fileName=$8}' | sed s/infu/temp/`
 renamedLoca=`ls -ltr *infu* | awk -F"> " '{location=$2}' | sed s/infu/temp/`
 echo "Creating softlinks for $renamedFile file from $renamedLoc"
done

 

```
 
but the ls -ltr is not working, i have no clue why, on console if i run each command individually its workin as required, but from script its not

I don't quite understand your loop logic. The variable 'file' will get set to each individual "word" in the output from "ls -ltr", including date, owner, etc. And the variables fileName and location set by awk don't get communicated to the shell.

Here is my attempt:

```
ls -ltr *infu* | while read file
do
  cmd0=`echo $file | sed 's/.* \([^ \t]*\) -> \(.*\)/ln -s \2 \1/'`
  cmd=`echo $cmd0 | sed s/infu/temp/g`
  echo $cmd
done
```

If it's just a one-shot thing, one may just as well use the sed commands to produce a file of commands, then run that file through bash, without any "while" and "echo" and stuff:

```
ls -ltr *infu* | sed 's/.* \([^ \t]*\) -> \(.*\)/ln -s \2 \1/' | sed s/infu/temp/g
```

---

### Post by Blackbug on 2011-05-30
thanks for replyin both of you.
well script serves the purpose just i want to do things without creating extra copy 
 
> 
function CreateCopy()

but its useful, so thanks
 
 
about the post below, well yes you are right, file variable was gettin set by all 'word'
the modification in loop is useful and works.
 
> **Arndt said:**
> I don't quite understand your loop logic. The variable 'file' will get set to each individual "word" in the output from "ls -ltr", including date, owner, etc. And the variables fileName and location set by awk don't get communicated to the shell.
 
Here is my attempt:
 
```
ls -ltr *infu* | while read file
do
  cmd0=`echo $file | sed 's/.* \([^ \t]*\) -> \(.*\)/ln -s \2 \1/'`
  cmd=`echo $cmd0 | sed s/infu/temp/g`
  echo $cmd
done
```
 
If it's just a one-shot thing, one may just as well use the sed commands to produce a file of commands, then run that file through bash, without any "while" and "echo" and stuff:
 
```
ls -ltr *infu* | sed 's/.* \([^ \t]*\) -> \(.*\)/ln -s \2 \1/' | sed s/infu/temp/g
```
 
But best one is sed use, although i am too weak in usin sed i just know the basic use.
can you explain this part ```
 sed 's/.* \([^ \t]*\) -> \(.*\)/ln -s \2 \1/'  
```
 
thanks

---

### Post by Arndt on 2011-05-30
> **Blackbug said:**
> thanks for replyin both of you.
well script serves the purpose just i want to do things without creating extra copy 
 

but its useful, so thanks
 
 
about the post below, well yes you are right, file variable was gettin set by all 'word'
the modification in loop is useful and works.
 

 
But best one is sed use, although i am too weak in usin sed i just know the basic use.
can you explain this part ```
 sed 's/.* \([^ \t]*\) -> \(.*\)/ln -s \2 \1/'  
```
 
thanks

The pieces delimited by \( and \) get assigned to the replacement texts 1 and 2, which are accessed by writing \1 and \2. Other than that, we match the things closest to the ->, matching the biggest pieces that don't contain a space.

---

