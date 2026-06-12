---
title: "BaSH script to rename files recursively"
date: 2012-02-14
forum: Programming Talk
---

### Post by mrphud on 2012-02-14
Hello all,

I have written my first bash script that allows me to go through the files in a folder and rename them to a line that I have in a text file. The problem is, the program now skips files even though they are in the proper (alphabetical) order. I believe the for loop (see below) sorts the list by name. I have attached a copy of the script. If I just use echo, then everything is fine. But, if I try to use the mv command then the order gets all jacked up.

```

#!/bin/bash
#This script recursively renames files in a folder to
#a name that is the line of a text file.
IFS='
'
count=1
files=/media/Extra\ 250/try/   #where my files are located
newpath=/home/jordan/Desktop/complete/    #where my files are going
cat lecture\ names | while read line; do   #list all names
	check=1
	for f in $files*; do	
		if [ "$check" = "$count" ]		
			then 					 
			mv -v $f $newpath$line #move the file and rename it
		fi		
		let "check += 1"
	done
	let "count += 1"
done

```

What is wrong with this?

---

### Post by nothingspecial on 2012-02-14
Well at a glance you have bash pitfall #2

[http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)

---

### Post by Vaphell on 2012-02-14
+1

minor nitpicks
also *cat input | while read; do ... done* is not necessary when you can do
*while read; do .... done < input*
running external commands when builtin alternative exists only adds overhead.

in bash you can do integer math and conditions inside (()) - $ is not necessary inside, all text is automatically treated as a variable name
(( i++ ))
if (( i>4 ))
echo $(( a+b+1 ))  $ is required to access the calculated value

---

### Post by mrphud on 2012-02-15
I appreciate the replies an all, but neither really addressed the program issue. If you need more details I will be happy to supply them, but the program is not working as expected. I would like to figure out why.

I am adding an updated script that hopefully fixes some of the nitpicks.

```

#!/bin/bash -x
#This script recursively rename files in a folder to
#a name that is the line of a text file.
#This script will not work without the internal field separator (IFS)
#set to a new line instead of just a space.
#without the IFS definition the script will not recognize files that have
#a space in the name. It will not recognize the character. 
IFS='
'
count=1
files=/media/Extra\ 250/try/
newpath=/home/jordan/Desktop/complete/
cat lecture\ names | while read line; do
	check=1
	for f in $files*; do			
		if [ "$check" = "$count" ]		
			then 					 					
			mv -v "$f" "$newpath$line"			#move the file and rename it
			((check++))		
		fi						
		((check++))
	done	
	check=1	
	((count++))
done

```

Thanks

---

### Post by emiller12345 on 2012-02-15
I'm not sure this is completely correct, but this was what I was thinking
```
#!/bin/bash
#This script recursively renames files in a folder to
#a name that is the line of a text file.
count=1
files="/media/Extra 250/try"   #where my files are located
newpath="/home/jordan/Desktop/complete"    #where my files are going
cat "lecture names" | while read line; do   #list all names
    check=1
    for f in "$files"/*; do    
        if [ "$check" = "$count" ]        
            then                      
            mv -v "$f" "$newpath/$line" #move the file and rename it
        fi        
        check=$(($check + 1))
    done
    count=$(($count + 1))
done
```

---

### Post by ofnuts on 2012-02-15
> **emiller12345 said:**
> I'm not sure this is completely correct, but this was what I was thinking
```
#!/bin/bash
#This script recursively renames files in a folder to
#a name that is the line of a text file.
count=1
files="/media/Extra 250/try"   #where my files are located
newpath="/home/jordan/Desktop/complete"    #where my files are going
cat "lecture names" | while read line; do   #list all names
    check=1
    for f in "$files"/*; do    
        if [ "$check" = "$count" ]        
            then                      
            mv -v "$f" "$newpath/$line" #move the file and rename it
        fi        
        check=$(($check + 1))
    done
    count=$(($count + 1))
done
```
Looks awfully complicated for the job, and any extra file is going to break it.

Read current files in array (sources=($(ls *)), read new names in array (targets=($cat $targetnames)), check that array sizes match, loop over array index and rename from source array item to target array item.

---

### Post by sisco311 on 2012-02-15
You have to specify the full path to the "lecture names" file otherwise your script will only work if you invoke it from the directory where the "lecture names" file is located.

+1 for quoting your expansions instead of reseting the IFS to a newline.

I'd try something like:
```

#!/bin/bash

shopt -s nullglob

source="/path/to/source"
dest="/path/to/dest"
names="/path/to/file names"

for file in "$source"/*; do
    read -r name || { printf '%s\n' "no more file names in $names";  break; } >&2
    mv -v -i -- "$file" "$dest/$name"
done < "$names"

```

---

### Post by emiller12345 on 2012-02-15
> **ofnuts said:**
> Looks awfully complicated for the job, and any extra file is going to break it.


I was trying to work with his program in mind, so that he can learn what syntax mistakes he is making.

---

### Post by mrphud on 2012-02-16
OK. Thanks for the replies. It will take some time to mull these over.

Cheers

---

### Post by ofnuts on 2012-02-16
> **emiller12345 said:**
> I was trying to work with his program in mind, so that he can learn what syntax mistakes he is making.Sorry, I wasn't really quoting you :)

---

