---
title: "I need to delete newer copies"
date: 2012-07-09
forum: Programming Talk
---

### Post by wdtd on 2012-07-09
So I have a very big mess.

I have lots of broken copies and backups of several directory trees. I have corrupted files, missing files, and bad file dates. I have filenames with funny characters.

After much effort, I hope I can deal with everything but the bad (newer) file dates.

To simplify:  I need to take 2 non-identical directory trees (that only have missing files, no bad copies)  then end up with just 1 directory tree where the files' dates were  the oldest files' dates.

```
dir1/file1 #older date
dir1/file2 #newer date
dir1/file3 #only copy
dir1/file4 #same date
dir2/file1 #newer date
dir2/file2 #older date
dir2/file4 #same date
dir2/file5 #only copy

to

dir/file1 #older date
dir/file2 #older date
dir/file3
dir/file4
dir/file5 #same date

```I don't know how to make this happen especially with  filenames with funny characters.

I think the script would loop, (compare the equivalent file md5sums), compare the equivalent file dates, and fix or delete the newer copies.

I have done a lot of searching, downloaded a bunch of programs, but haven't found anything I could use and I need to get this done sooner rather than later.

_*[COLOR=DarkRed]**WARNING: You need to backup your files and test your script heavily before deleting (using the command rm) or changing anything important even if you think it should work!**[/COLOR]*_

---

### Post by wdtd on 2012-07-09
So, do you think this would this work? Is there a better way to do it?

```
#!/bin/bash
FILES1=/path/to/dir1
FILES2=/path/to/dir2

cd $FILES1
for f1 in `find -type f`; do
  f2=$FILES2/$f1
  if [ ${f1} -nt ${f2} ] 
  then
     echo "$FILES1 $f1 is newer"
  else
     rm -i $f2
  fi
done
```

I really don't want to lose files because of a goof.

---

### Post by Vaphell on 2012-07-10
> I really don't want to lose files because of a goof.
so you have to test it heavily without rm-ing

always quote your variables if you don't want surprises
if [ [COLOR="Red"]${f1}[/COLOR] -nt [COLOR="Red"]${f2}[/COLOR] ]
rm -i [COLOR="Red"]$f2[/COLOR]

i'd go with
```
while read -d $'\0' f1; do echo "$f1"; done < <( find -type f -print0 )
```
instead of *for*

---

### Post by wdtd on 2012-07-10
Thank you for the VERY IMPORTANT :p reminder about testing. I am going to pre-run the script with **ls** instead of **rm** before I start deleting files.

I am not sure how to quote my variables. Would using **find** with **-fls** instead of **-print0** be enough for my unusual characters? Including ```
{ } ( )  _ extended-char-sets
```Unfortunately,  I don't think I understand how to incorporate your suggestion below because I keep getting errors.

```
while read -d $'\0' f1; do echo "$f1"; done < <( find -type f -print0 )
```Thank you!

---

### Post by Vaphell on 2012-07-10
what kind of errors do you get?

that while loop iterates over find just like your for loop but uses NULL character as a delimiter (-print0/read -d $'\0') - NULL is illegal in filenames so it's perfect for that purpose. Everything else is put into f1 variable (read f1). You need more or less copy do-done block, echo in mine was just for illustrative purposes.

```
while read -d $'\0' f1
do
  f2="$FILES2/$f1"
  if [ "${f1}" -nt "${f2}" ] 
  then
     echo "$FILES1 $f1 is newer"
  else
     rm -i "$f2"
  fi
done < <( find -type f -print0 )
```

[ ${f1} -nt ${f2} ] this needs quotes, otherwise you'll get 'too many arguments' error thrown by the [ command every time you get whitespace
```
$ x='a b'; y='a b'
$ [ ${x} = ${y} ]  [COLOR="DarkRed"]# equivalent to [ a b = a b ][/COLOR]
bash: [: too many arguments
$ [ "${x}" = "${y}" ]
$
```

---

### Post by wdtd on 2012-07-10
I was getting syntax errors trying to use the while loop.  Using this code, I don't get syntax errors but it doesn't seem to get iterating (and only compares 2 pairs of files) and I don't know what I am doing wrong.

```
#!/bin/bash 
FILES1=/path/to/dir1 
FILES2=/path/to/dir2

cd "$FILES1"
while read -d $'\0' f1
do
  f2="$FILES2/$f1"
  if [ "${f1}" -nt "${f2}" ] 
  then
     echo "$FILES1 $f1 is newer"
  else
     rm -i "$f2"
  fi
done < <( find -type f -print0 )
```

---

### Post by Vaphell on 2012-07-10
strange
let's see what the loop does exactly, copy-paste this into terminal in proper directory (ctrl+c/ctrl+shift+v)

```
c=1; while read -d $'\0' f1; do echo "$((c++)) $f1"; done < <( find -type f -print0 )
```
does this produce different results than
```
find -type f
find -type f -printf "x" | wc -c
```

how do you run your script?

---

### Post by wdtd on 2012-07-10
**c=1** code
```

1 ./filed
2 ./fileb
3 ./filea
4 ./filec

```[B]find -type f
[/B]```

./filed
./fileb
./filea
./filec

```**find -type f -printf "x" | wc -c**
```

4

```I get the same results with either:
```

bash script.sh
bash ./script.sh
./script.sh

```Here is what I get when I run the script  
(filed and fileb are newer in dir1 while filec and filea are older in dir1)
```

[COLOR=Blue]$[/COLOR] bash script.sh
/path/to/dir1 ./filed is newer
/path/to/dir1 ./fileb is newer
rm: remove regular empty file `/path/to/dir2./filea'? [COLOR=Blue]$[/COLOR]
```Thank you again for all of your help. I am still learning and hopefully this thread will also be of help to others who need this kind of script.

---

### Post by wdtd on 2012-07-10
I think **rm[COLOR=Magenta] [COLOR=DarkRed]-i[/COLOR][/COLOR]** is the problem. 

For some reason, the **while** loop version does not want to let me confirm my deletion when the **for** loop does not have that problem.

---

### Post by Paddy Landau on 2012-07-10
Please back up both folders before proceeding.

---

### Post by Vaphell on 2012-07-10
indeed, i haven't thought of that.
try this:
```
while read -r -d $'\0' f1
do
  f2="$FILES2/$f1"
  if [ "${f1}" -nt "${f2}" ] 
  then
     echo "$FILES1 $f1 is newer"
  else
     rm -i "$f2" **< /dev/tty**
  fi
done < <( find -type f -print0 )
```

---

### Post by wdtd on 2012-07-10
Thank you very much! That did it. Here is a complete copy of the code in case it can be of use to others. :D

```
#!/bin/bash
#Delete files in FILES2 which are newer than or the same age as FILES1
FILES1=/path/to/dir1
FILES2=/path/to/dir2

cd "$FILES1"
while read -r -d $'\0' f1
do
  f2="$FILES2/$f1"
  if [ "${f1}" -nt "${f2}" ] 
  then
     echo "$FILES1   $f1 is newer"
  else
     rm -i "$f2" < /dev/tty
  fi
done < <( find -type f -print0 )
```[U][I][COLOR=DarkRed][B]

WARNING: You need to backup your files  and test your script heavily before deleting (using the command rm) or  changing anything important even if you think it should work![/B][/COLOR][/I][/U]

---

### Post by Paddy Landau on 2012-07-11
> **wdtd said:**
> Thank you very much! That did it. Here is a complete copy of the code in case it can be of use to others.
Excellent, and thank you for the code.

To help others find the code, please [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

