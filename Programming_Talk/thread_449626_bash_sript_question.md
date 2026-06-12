---
title: "bash sript question"
date: 2007-05-20
forum: Programming Talk
---

### Post by finer recliner on 2007-05-20
hey i'm writing a fairly simple bash script to back up selected file on my external drive

```
#!/bin/bash


#set destination variable to be used throughout the script
#note: do not add a trailing slash!
D="/media/External_HDD/Backup/linux"

#if destination does not exist, create it
if [[ ! -e $D ]]
	then mkdir $D
fi

echo All files will be saved to: $D


#instantiate array of files to backup
#always type the full path starting with "/" !
Arr=( 
/etc/fstab 
/etc/X11/xorg.conf
)

#iterate through the array of files. copy them to destination
for (( i = 0 ; i < ${#Arr[@]} ; i++ )) do

	FILE="${Arr[i]%\/*}/"
	PATH="${Arr[i]##\/*\/}"

	echo $FILE
	echo $PATH

#if the path does not already exist in destination, create it
	if [[ ! -d $D$PATH ]]
		then mkdir $D$PATH
	fi

#if the file does not already exist in destination, create it
	if [[ ! -e $D$PATH$FILE  ]]
		then touch $D$PATH$FILE
	fi

#copy file recursively WITHOUT prompting for overwrite.
#use cp -ir to prompt before overwriting.
	cp -r $PATH$FILE $D$PATH$FILE

done



echo backup is complete.
exit 0
```



but i always get the follow errors:
```
$ bash backup.sh
All files will be saved to: /media/External_HDD/Backup/linux
/etc/
fstab
backup.sh: line 34: mkdir: command not found
backup.sh: line 39: touch: command not found
backup.sh: line 44: cp: command not found
/etc/X11/
xorg.conf
backup.sh: line 34: mkdir: command not found
backup.sh: line 39: touch: command not found
backup.sh: line 44: cp: command not found
backup is complete.

```

i'm probably missing a closing bracket somewhere or something simple like that. anyone see what's wrong?
thanks

---

### Post by qix on 2007-05-20
I have a question. You do
```
echo $FILE
echo $PATH
```
and you say that your output for that is
```
/etc/
fstab
```
right?

Shouldn't it be reversed?

EDIT: read the poster below me!

---

### Post by jyba on 2007-05-20
The problem is that you've overwritten the PATH variable. 

```
	PATH="${Arr[i]##\/*\/}"
```

PATH is used by bash to locate commands such as mkdir, touch and cp. Luckily when your script exits the PATH variable reverts to its old value.

Anyway, the solution is to call your variable anything other than PATH, and then your script will work because bash will be able to find the commands that you call upon later in the script.

---

### Post by finer recliner on 2007-05-20
thanks jyba, i renamed that variable and now it works.


thank you qix as well. i did accidentally mix up the variables ;)

---

