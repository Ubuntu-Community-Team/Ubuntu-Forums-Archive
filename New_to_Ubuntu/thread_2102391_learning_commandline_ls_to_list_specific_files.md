---
title: "learning commandline ls to list specific files"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by anshuhim20 on 2013-01-07
Hello,
I want to make a bash script for entering all the folders of a directory and rename that one particular file with their respective folder name and move these renamed files to the current directory.
I am using the ls command to imply 
#!/bin/bash
path=/home/mv/Desktop/3x3s/test

export SUBJECTS_DIR=$path

cd $path
#ls | sed 's/.nii.gz//g'>list
ls >list
echo "Making list"

cd $path/$list

for y $(cat list)

do
mv mprage.nii.gz y.nii.gz
echo "renaming data file"  
for x in .$list*
do 
mv $x /home/mv/Desktop/3x3s/test
echo "moving"
if [ "$?" -eq "0" ]
then
 /call/the/script/here
 wait
fi
done

please rectify the errror is $path/list doesnot exist

---

### Post by steeldriver on 2013-01-07
Your specific problem seems to be that list is neither a variable ($list) nor a directory (so you can't cd to it)

> **anshuhim20 said:**
> Hello,
I want to make a bash script for entering all the folders of a directory and rename that one particular file with their respective folder name and move these renamed files to the current directory.
I am using the ls command to imply 
```
#!/bin/bash
path=/home/mv/Desktop/3x3s/test

export SUBJECTS_DIR=$path

cd $path
#ls | sed 's/.nii.gz//g'>list
**[COLOR=Red]ls >list[/COLOR]**
echo "Making list"

[COLOR=Red]**cd **[/COLOR]$path/[COLOR=Red]**$list**[/COLOR]

for y $(cat list)

do
mv mprage.nii.gz y.nii.gz
echo "renaming data file"  
for x in .$list*
do 
mv $x /home/mv/Desktop/3x3s/test
echo "moving"
if [ "$?" -eq "0" ]
then
 /call/the/script/here
 wait
fi
done
```please rectify the errror is $path/list doesnot exist

However there are lots of other issues - for example you don't need to use ls to a file (with sed?) to make a  list of files to work on - if you want to do something to all the .nii.gz files in dir you can just do

```
for file in path/to/dir/*.nii.gz
do
```

---

### Post by Impavidus on 2013-01-07
Please enclose your code in code tags or php tags (for syntax highlighting; it's a different language but results are reasonable) the next time you post code for better readability. Select the code and click on the # above the input field.

I see more than one problem in your code.

[FONT=Courier New]cd $path[/FONT]: change current directory to /home/mv/Desktop/3x3s/test. This is correct.

[FONT=Courier New]ls >list[/FONT]: store a list of the contents of this directory in the file "list" in this same directory. This is syntactically correct, but maybe not what you want.

[FONT=Courier New]cd $path/$list[/FONT]: error, "list" is a file in the current directory, not a variable in your script.

[FONT=Courier New]for y $(cat list)[/FONT]: incorrect syntax. Correct syntax would be: [FONT=Courier New]for y in $(cat list)[/FONT], however, as "list" contains only the output of ls, this is equivalent to omitting the ls >list statement and changing this into [FONT=Courier New]for y in $(ls)[/FONT]. This will fail if there are file names or directories containing whitespace, so [FONT=Courier New]for y in *[/FONT] is considered better.

[FONT=Courier New]echo "moving"
if [ "$?" -eq "0" ][/FONT]: echo should never fail and therefore always returns 0. $? on the next line contains the return value of echo. The test on that line therefore always evaluates to true, which is probably not what you want.

I'm not sure what you intend to do with the other statements in your script, but I recommend reading a scripting guide. No offence, but you are clearly a complete beginner. We all were at one point. The *advanced bash scripting guide* (ask google, first hit) starts with a nice introduction before things get complicated.

If you add some explanatory comments to your code or write some pseudo-code we may be able helping you writing a script that does what you want.

---

### Post by anshuhim20 on 2013-06-11
Thanks for your sugessions

I have to make a list of names which start with letter abc in the directory as provided in path 
and I want to call individual member of the list using for 
Please find the script below and kindly assist me.

#!/bin/bash

path=/home/coiproject/Desktop/Himanshu

ls | sed 's/abc*//g'>list

echo "Making list"

for y $(cat list);

do
use the specific members of list by using ${y} 

done

> **Impavidus said:**
> Please enclose your code in code tags or php tags (for syntax highlighting; it's a different language but results are reasonable) the next time you post code for better readability. Select the code and click on the # above the input field.

I see more than one problem in your code.

[FONT=Courier New]cd $path[/FONT]: change current directory to /home/mv/Desktop/3x3s/test. This is correct.

[FONT=Courier New]ls >list[/FONT]: store a list of the contents of this directory in the file "list" in this same directory. This is syntactically correct, but maybe not what you want.

[FONT=Courier New]cd $path/$list[/FONT]: error, "list" is a file in the current directory, not a variable in your script.

[FONT=Courier New]for y $(cat list)[/FONT]: incorrect syntax. Correct syntax would be: [FONT=Courier New]for y in `cat list`[/FONT], however, as "list" contains only the output of ls, this is equivalent to omitting the ls >list statement and changing this into [FONT=Courier New]for y in `ls`[/FONT]. This will fail if there are file names or directories containing whitespace, so [FONT=Courier New]for y in *[/FONT] is considered better.

[FONT=Courier New]echo "moving"
if [ "$?" -eq "0" ][/FONT]: echo should never fail and therefore always returns 0. $? on the next line contains the return value of echo. The test on that line therefore always evaluates to true, which is probably not what you want.

I'm not sure what you intend to do with the other statements in your script, but I recommend reading a scripting guide. No offence, but you are clearly a complete beginner. We all were at one point. The *advanced bash scripting guide* (ask google, first hit) starts with a nice introduction before things get complicated.

If you add some explanatory comments to your code or write some pseudo-code we may be able helping you writing a script that does what you want.

---

### Post by Impavidus on 2013-06-11
Try```

cd $path
for y in abc*
do
whatever
done

```

---

### Post by anshuhim20 on 2013-06-12
Thanks a lot :)

---

### Post by claracc on 2013-06-12
As you got fixed your problem, please, mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

