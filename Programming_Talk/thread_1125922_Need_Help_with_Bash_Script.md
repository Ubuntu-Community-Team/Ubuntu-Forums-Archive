---
title: "Need Help with Bash Script"
date: 2009-04-14
forum: Programming Talk
---

### Post by leroylim on 2009-04-14
Hi all.

I'm quite new to bash scripting.

I have some queries with a bash script I wrote. I'm writing a bash script to automate file uploading to Amazon S3 since I have thousands of file, and it's sorta tiring & impossible to specify every of them as a filename.

I was wondering how to limit the number of s3-put it ran, etc 5 number of s3-put at one time. Since thousands of files would just die off with Can't allocate memory. Would appreciate it if you guys could help, Thanks.

```

#! /bin/bash

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")


mfiles=`ls -1`

for i in $mfiles ; do
        s3-put -k XXXXX -s /root/s3-key.secret -T $i /leroy-anime/$i &
done

IFS=$SAVEIFS

```

---

### Post by Jesdisciple on 2009-04-14
Only doing 5 at a time would be pretty easy with the three-expression header described [here]("http://www.cyberciti.biz/faq/bash-for-loop/").  As for picking up where you left off, do you want to exit the shell or just pause it before doing the next 5 s3-puts?

---

### Post by leroylim on 2009-04-14
Well. I want it to pick up from where it left off. Any ideas how to do so? Thanks

---

### Post by croto on 2009-04-14
How about something like this?
```

#!/bin/bash

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")


mfiles=`ls -1`

counter=0
for i in $mfiles ; do
        s3-put -k XXXXX -s /root/s3-key.secret -T $i /leroy-anime/$i &
	counter=$(($counter+1))
	if [[ $counter -eq 5 ]]; then
	    wait
	    counter=0
	fi
done

IFS=$SAVEIFS

```

You can get help on bash's "wait" command in "man bash", or "help wait".

---

### Post by leroylim on 2009-04-15
Thanks. by the way. I was wondering how handle white spaces in bash. Somehow when I try to upload files with white spaces in between their filename, it doesn't work

---

### Post by lloyd_b on 2009-04-15
As a general rule, whenever passing a filename with spaces in it as an argument to a program, enclose it in quotation marks.  That way it's treated as a single argument, rather than multiple arguments.

Lloyd B.

---

### Post by leroylim on 2009-04-15
I've done that, yet it's still spitting errors due to whitespace. Somewhat. I've read about using IFS for white-space handling in bash for filenames, but it doesn't quite work in this case, so I've commented it out.

I was wondering about how to go about using this in the bash script
```
sed -e "s/ /\\\ /g"
```

```

#! /bin/bash

#SAVEIFS=$IFS
#IFS=$(echo -en "\n\b")


mfiles=`ls -1`

counter=0

for i in $mfiles ; do
        s3-put -k AKIAIJVEZHFK7SWOQO7A -s /root/s3-key.secret -T "$i" "/leroy-anime/$i" &
        counter=$(($counter+1))
        if [[ $counter -eq 5 ]]; then
                wait
                counter=0
        fi
done

#IFS=$SAVEIFS

```

---

### Post by ghostdog74 on 2009-04-15
why are you using ls -1? its called useless use of ls
```

for i in * ; do
        s3-put -k AKIAIJVEZHFK7SWOQO7A -s /root/s3-key.secret -T "$i" "/leroy-anime/$i" &
        counter=$(($counter+1))
        if [[ $counter -eq 5 ]]; then
                wait
                counter=0
        fi
done

```

---

### Post by leroylim on 2009-04-15
> **ghostdog74 said:**
> why are you using ls -1? its called useless use of ls
```

for i in * ; do
        s3-put -k AKIAIJVEZHFK7SWOQO7A -s /root/s3-key.secret -T "$i" "/leroy-anime/$i" &
        counter=$(($counter+1))
        if [[ $counter -eq 5 ]]; then
                wait
                counter=0
        fi
done

```

Ah. So I guess thats a nicer simpler way to do stuff. Thanks

---

### Post by lloyd_b on 2009-04-15
> **leroylim said:**
> I've done that, yet it's still spitting errors due to whitespace. Somewhat. I've read about using IFS for white-space handling in bash for filenames, but it doesn't quite work in this case, so I've commented it out.

I was wondering about how to go about using this in the bash script
```
sed -e "s/ /\\\ /g"
```

```

#! /bin/bash

#SAVEIFS=$IFS
#IFS=$(echo -en "\n\b")


mfiles=`ls -1`

counter=0

for i in $mfiles ; do
        s3-put -k AKIAIJVEZHFK7SWOQO7A -s /root/s3-key.secret -T "$i" "/leroy-anime/$i" &
        counter=$(($counter+1))
        if [[ $counter -eq 5 ]]; then
                wait
                counter=0
        fi
done

#IFS=$SAVEIFS

```

First off, there's no reason to "save" the IFS setting.  Like all environment variables, it'll revert back to normal when the script exits.

Second, try this for IFS: IFS=$'\n'

I honestly don't understand why you wanted '\b' (backspace) as a field separator.

As for your sed command - the "-e" option is to read a script and get the expression from it, which you don't need in this case.  If you just want to edit a variable with sed:```
SOMETHING=`echo $SOMETHING | sed "s/ /\\\ /g"`
```

Lloyd B.

---

### Post by ericdube on 2010-05-19
> **lloyd_b said:**
> First off, there's no reason to "save" the IFS setting.  Like all environment variables, it'll revert back to normal when the script exits.

Second, try this for IFS: IFS=$'\n'

I honestly don't understand why you wanted '\b' (backspace) as a field separator.

As for your sed command - the "-e" option is to read a script and get the expression from it, which you don't need in this case.  If you just want to edit a variable with sed:```
SOMETHING=`echo $SOMETHING | sed "s/ /\\\ /g"`
```

Lloyd B.


Can someone explaine the difference between :

IFS=$'\n'
and
IFS=$'\n\b'

Why use "\b" in the IFS ???

---

