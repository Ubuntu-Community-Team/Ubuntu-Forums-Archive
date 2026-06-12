---
title: "Bash help - Renaming"
date: 2008-01-13
forum: Programming Talk
---

### Post by victorbrca on 2008-01-13
Trying to rename files in a folder from lines in a txt file but not able to. What am I doing wrong??  :-s

```
$ cat script.sh
#!/bin/bash

d=1 ;
e=$(cat songs | grep $d) ;

for i in `ls *mp3` ;
   do cp $i $e".mp3" ;
   d=$[d+1] ;
   e=$(cat songs | grep $d) ;
done
```


```
$ cat songs
1-Rotten Apple  
2-Nutshell  
3-I Stay Away  
4-No Excuses  
5-Whale and Wasp  
6-Don't Follow  
7-Swing On This
```


```
$ ls -1
01-Track1.mp3
02-Track2.mp3
03-Track3.mp3
04-Track4.mp3
05-Track5.mp3
06-Track6.mp3
07-Track7.mp3
script.sh
songs
```


```
$ ./script.sh 
cp: target `.mp3' is not a directory
cp: target `.mp3' is not a directory
cp: target `.mp3' is not a directory
cp: target `.mp3' is not a directory
cp: target `.mp3' is not a directory
cp: target `.mp3' is not a directory
cp: target `This.mp3' is not a directory
```

Vic.

---

### Post by ghostdog74 on 2008-01-13
> **victorbrca said:**
> Trying to rename files in a folder from lines in a txt file but not able to. What am I doing wrong??  :-s

```
$ cat script.sh
#!/bin/bash

d=1 ;
e=$(cat songs | grep $d) ;

for i in `ls *mp3` ;
   do cp $i $e".mp3" ;
   d=$[d+1] ;
   e=$(cat songs | grep $d) ;
done
```




do away with the " ls *mp3 " in the for loop. Use shell globbing instead. Put double quotes in your cp command. use open brackets if you want to increment a variable. you can do away with the cat.
eg
```

e=$(grep $d songs) ;
for i in *mp3
do
 cp "$i" "$e.mp3"
 d=$(( d+1 ))
 e=$(grep $d songs) 
done

```
something like that. If you get more experienced in shell scripting, you might find better ways of doing this

---

### Post by victorbrca on 2008-01-14
> **ghostdog74 said:**
> ...something like that. If you get more experienced in shell scripting, you might find better ways of doing this

Thanks a lot. Just by adding the double quotes on the cp from and target already worked, but I did change it to match your code. It looks a lot more versatile....

One thing I noticed to is that the original file names can not contain spaces otherwise the script doesn't work properly.


Vic.

---

