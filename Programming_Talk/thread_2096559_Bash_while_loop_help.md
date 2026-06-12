---
title: "Bash while loop help"
date: 2012-12-20
forum: Programming Talk
---

### Post by black_ice on 2012-12-20
Hi Guys, 

I'm currently working on a simple bash script that will check the current size of files inside directory and if it's larger than specific value .. the script should remove the files until it reached to specific value .. but it seems it's not working "The script always going outside the loop which is weird for me "

```

#!/bin/bash
CURR_DIR_SIZE=`du -sk /opt/test/ | cut -f1`
MAX_SIZE=81920

#echo $CURR_DIR_SIZE


while [[ $CURR_DIR_SIZE -gt $MAX_SIZE ]]

do
echo $CURR_DIR_SIZE

FILE=`ls -1tra test/ | head -1`
rm -rf $FILE

CURR_DIR_SIZE=`du -sk /opt/test/ | cut -f1`
done
exit 0


```

Any help  

Thanks in advance

---

### Post by sudodus on 2012-12-20
Did you try with single brackets:

```
while [ $CURR_DIR_SIZE -gt $MAX_SIZE ]
```

---

### Post by black_ice on 2012-12-20
Thanks for reply back : 

I have tried it, but it's entering endless loop !! without removing any files

---

### Post by sudodus on 2012-12-20
Do you have write permission (and hence remove permission in that directory)? Maybe rm cannot do its job.

Edit: and are you in the right directory doing it? Maybe you should use absolute path in the FILE= statement

```
FILE=`ls -1tra /opt/test/ | head -1`
```
```
rm -rf /opt/test/$FILE
```

---

### Post by drmrgd on 2012-12-20
You might consider using stat for this.  something along the lines of:

```

MAX_SIZE=81920
while [[ $(stat -c%s $CURR_DIR_SIZE) -gt $MAX_SIZE ]]; then
    do ......

```

You might play with the formatting of the stat output and make sure that $MAX_SIZE matches the units correctly.

---

### Post by black_ice on 2012-12-20
Yes I do, I'm executing the script as a root ..

---

### Post by sudodus on 2012-12-20
I think the solution is absolute paths. See my previous post, it is edited twice.

---

### Post by steeldriver on 2012-12-20
I second using 'stat' instead of 'ls' 

You appear to be testing the size of /opt/test but attempting to remove files from the current directory

You should also quote your $file variable in case it has spaces

I don't think there is anything wrong with your loop syntax itself (although it would be more idiomatic to use < > operators instead of -lt -gt in an extended test [[ ]] I think)

---

### Post by sudodus on 2012-12-20
> **steeldriver said:**
> i second using 'stat' instead of 'ls' 

you appear to be testing the size of /opt/test but attempting to remove files from the current directory

[color="red"]you should also quote your $file variable in case it has spaces[/color]

i don't think there is anything wrong with your loop syntax itself (although it would be more idiomatic to use < > operators instead of -lt -gt in an extended test [[ ]] i think)
+1

---

### Post by black_ice on 2012-12-20
Thanks guys for your valuable input, but the script didn't do the desired function , here is the new code 

```

#!/bin/bash
CURR_DIR_SIZE=`du -sk /opt/test/ | cut -f1`
MAX_SIZE=81920

#echo $CURR_DIR_SIZE


while [[ $CURR_DIR_SIZE > $MAX_SIZE ]]
do
#echo $CURR_DIR_SIZE

FILE=`ls -1htr /opt/test/ | head -1`
rm -rf /opt/test/$FILE

done
exit 0


```


Bash -x 

# bash -x RemoveFiles.sh
++ du -sk /opt/test/
++ cut -f1
+ CURR_DIR_SIZE=164020
+ MAX_SIZE=81920
+ [[ 164020 > 81920 ]]
+ exit 0

---

### Post by rnerwein on 2012-12-20
> **black_ice said:**
> Thanks guys for your valuable input, but the script didn't do the desired function , here is the new code 

```

#!/bin/bash
CURR_DIR_SIZE=`du -sk /opt/test/ | cut -f1`
MAX_SIZE=81920

#echo $CURR_DIR_SIZE


while [[ $CURR_DIR_SIZE > $MAX_SIZE ]]
do
#echo $CURR_DIR_SIZE

FILE=`ls -1htr /opt/test/ | head -1`
rm -rf /opt/test/$FILE

done
exit 0


```
Bash -x 

# bash -x RemoveFiles.sh
++ du -sk /opt/test/
++ cut -f1
+ CURR_DIR_SIZE=164020
+ MAX_SIZE=81920
+ [[ 164020 > 81920 ]]
+ exit 0
hi
a directory is just a file. and i think that the syscall using TRUNCATE is not used. that means the size "CURR_DIR_SIZE never changed. you can only change it by deleting files
than move the files to a directory e.g. mv * ../blablu
then delete the orginal directory entry, make it again and move the files back.
the directory (it a file) is grown page-size as i know.
bad trap ?
cheers

---

### Post by black_ice on 2012-12-20
Pardon me, But I didn't get it .. it would be nice if you can elaborate more .. 

Thanks

---

### Post by sudodus on 2012-12-20
This script works for me

```

#!/bin/bash

DIRECTORY="/home/$USER/test/black_ice/sub"
MAX_SIZE=81920
CURR_DIR_SIZE=`du -sk "$DIRECTORY" | cut -f1`

#echo $CURR_DIR_SIZE

while [ $CURR_DIR_SIZE -gt $MAX_SIZE ]
do
 echo $CURR_DIR_SIZE
 FILE=`ls -1htr  "$DIRECTORY" | head -1`
 rm -rf "$DIRECTORY"/"$FILE"
# echo $?
 CURR_DIR_SIZE=`du -sk "$DIRECTORY" | cut -f1`
done
echo "final dir size: $CURR_DIR_SIZE"
exit 0

```

What you need is to adjust the directory.

---

### Post by black_ice on 2012-12-20
you really offered a great help thanks , the script finally executed without any errors but the script deleted all files which were (161 M) under test directory ... What I need to do is stop deleting files when the directory size is less than 80 M or less

---

### Post by sudodus on 2012-12-20
It worked for me, stopping when the content of the directory was less than MAX_SIZE. But of course, if the last remaining file is too big, it will also be deleted. Try with files smaller than MAX_SIZE!

---

### Post by rnerwein on 2012-12-20
> **black_ice said:**
> Pardon me, But I didn't get it .. it would be nice if you can elaborate more .. 

Thanks
hi
ok give me another try.
1. mkdir tst          (in your home)
2. cd tst
3. mkdir tmp
4. du -sk tmp            ---->    4    tmp  (initial size for a directory
5. cd tmp
6. vi bla.sh
      a=1
      while :; do touch bla$a; ((a++)); echo $a; done
save that script
7. at, lets say at 5000 hit CTRL C to stop that loop
8. cd ..
9. du -sk ./tmp         ---->   136    tmp
in your scrip you say: MAX_SIZE=130       
e.g.  CURR_DIR_SIZE= 120
the script will never run: 120 > 130
10. cd tmp
11. rm bla*
12. cd ..
13. du -sk ./tmp     ---->  136  tmp        as you see even if your script will run (CUR.. > MAX.
it will run forever even all the files bla* deletet the directory have the same size.
atention ! the file is not deleted only the inode entry is. the file is still on disk but the former disk block of the file is added to the free list  and the
system don't shrink the directory (wich is only a file in sense of unix)

did we come together now ?
cheers

---

### Post by black_ice on 2012-12-20
@sudodus, You are right thanks for your dedication and your fast responses .. My Problem Solved 

@rnerwein, This is super . Appreciate your detailed steps it helped me getting the full picture .. 

Thanks Guys :)

---

