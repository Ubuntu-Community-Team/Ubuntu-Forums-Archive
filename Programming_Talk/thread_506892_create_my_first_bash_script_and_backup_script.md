---
title: "create my first bash script and backup script"
date: 2007-07-22
forum: Programming Talk
---

### Post by cazz on 2007-07-22
Hi
I try to create my first bash script and that is a backup script that use rsync
That maybe dont look so good and maybe someone have any tips to give me to make my backup script better then just write :)


The code look like this
```
#!/bin/bash
SOURCE=/from/a/directory/
TARGET=/to/a/directory/
DATE=`date +'%m-%d-%Y'`
CHANGE=/to/a/directory/temp/
OLDBACKUP=/to/a/directory/old/


rsync -az  $SOURCE $TARGET -b --backup-dir=$CHANGE

if test -a /to/a/directory/old/* 
then 
 tar -cvvf  $OLDBACKUP$DATE.tar $CHANGE
 rm $OLDBACKUP*
fi
```

I going to create a backup script that run every night and see if that have change from a directory and if it have it going update my backupfile and take the old file and compress it to a file that have the date on.
So I can go back if I have write something or mistake delete some file.

Now to my problem

I have try so I have in the if file 
```
if test -a $CHANGE* 
```
but that give me a error "too many arguments" at line 11

---

### Post by nitro_n2o on 2007-07-22
AFAIK -a is an AND to test two expressions.. is that wht r u trying to do

---

### Post by cazz on 2007-07-22
I want to see if the is any file in that directory and if that is any file it do the compress and delete the file

I have ask that in another post and get this

```
if [ $(ls -1A | wc -l) -eq 0 ]; then
    echo Empty
fi
```

but I have no idea what the code mean :redface:
[http://ubuntuforums.org/showthread.php?t=506364](http://ubuntuforums.org/showthread.php?t=506364)

---

### Post by cazz on 2007-07-22
Strange
When I remove the if and that so it run anyway nothing happen.
The script dont delete the file or compress to one single file at all.

---

### Post by Mr. C. on 2007-07-22
Cazz,

If you are having trouble with the basic if statement, maybe you should start with some fundamentals first ?

Do you have any good scripting tutorials or books ?

MrC

---

### Post by cazz on 2007-07-23
Yes I have some that I have read on the internet.
I have program in other language some years now but never in bash.

But I think I now understand the code you have give me.

I have now create my backup script and that look that work fine

```
#!/bin/bash
SOURCE=/from/a/directory/
TARGET=/to/a/directory/
DATE=`date +'%m-%d-%Y'`
CHANGE=/to/a/directory/temp/
OLDBACKUP=/to/a/directory/old/


rsync -azv  $SOURCE $TARGET -b --backup-dir=$CHANGE >> $DATE.txt

if [ $(( 3 >= $(ls -la $CHANGE |wc -l) )) = 0 ]
then
 tar -cvvf  $OLDBACKUP$DATE.tar $CHANGE
 rm $CHANGE*
fi
```

find the if code from
[http://www.issociate.de/board/goto/866027/checking_if_a_directory_is_empty.html](http://www.issociate.de/board/goto/866027/checking_if_a_directory_is_empty.html)

---

### Post by Mr. C. on 2007-07-23
This line of code makes no sense:

```
if [ $(( 3 >= $(ls -la $CHANGE |wc -l) )) = 0 ]
```

It says of 3 is greater that or equal that the number of files in the directory and that equals the *string* 0 ...

Use the -A option to ls instead of -a.  The -A options prevents . and .. from being listed, which you don't want anyway.  You are really trying to see if the number of files is greater than 0.

MrC

---

### Post by cazz on 2007-07-23
yes I now but when I write 

```
echo $(( 3 >= $(ls -la $CHANGE |wc -l) ))
```

It show 0 if that is something inside the directory
If that is nothing in the directory it show 1


But that directory never going to have . or .. file so that maybe is a better script that I can do but it work :)

---

### Post by Mr. C. on 2007-07-23
I think you're misunderstanding.  Look at the two if tests here; try them, and compare them to yours:

```
if [ $(ls -1A $CHANGE | wc -l) -eq 0 ]; then
   echo directory is empty
else 
   echo directory is not emtpy
fi
```

or the reverse case :

```
if [ $(ls -1A $CHANGE | wc -l) -ne 0 ]; then
   echo directory is not empty
else 
   echo directory is emtpy
fi
```

Use the -A option to ls !
MrC

---

### Post by cazz on 2007-07-23
ohh thanks that was very interesting

---

