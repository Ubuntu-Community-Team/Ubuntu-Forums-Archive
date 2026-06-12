---
title: "Bash script"
date: 2012-05-06
forum: Programming Talk
---

### Post by RaHorakhty on 2012-05-06
is there an online repository of bash scripts for ubuntu? I want to develop a script that can move a file within a directory to the parent directory, recursively.  For example, if the directory  "Ubuntu" is filled with sub directories that start with "temp," the script must copy all the files out of each temp directory and move it in to the parent directory.  any suggestions?](*,)]

---

### Post by hakermania on 2012-05-06
Welcome to the forums :D

Well, most bash scripts are made for personal use, for doing jobs as the one you told about, so while there are (somewhere in the web, lol) collections of scripts (like nautilus scripts), there aren't bash scripts for everything, as it's very easy to create your own script.
I will try to explain you some basic things so as to understand what you're doing, because bash scripts can become very dangerous, especially with the use of the 'rm' command, when it's not used properly.

Ok, a bash script is a program that uses commands so as to do a specific job.
The 'mv' command moves recursively folders and files everywhere you tell it to do so.
The 'cd' command stands for Change Directory.
And here's a simple script that does what you want to:
Every line starting with a '#', except from the 1st one, is a comment.
```

#!/bin/bash
#Going to the parent directory, let's call it 'Ubuntu', placed under the Documents folder
cd ~/Documents/Ubuntu/
# The '~' sign stands for /home/myusername
#Now, let's say that inside the 'Ubuntu' folder there are 3 directories, called DirA, DirB and DirC, and 1 file, let's say hi.txt
#We will have to 'cd' to every directory and 'mv' the files up one directory, namely under the 'Ubuntu' directory
#loop between all the files (the '*' means all the files under the current directory, remember we have 'cd'ed to ~/Documents/Ubuntu
for object in *; do
   #Now the variable $object is either one of the folders (DirA etc) or the file hi.txt, we have to do the actions we want only to the folders, though!
   #Checking to see if $object is a folder or not:
   if [ -d "$object" ]; then #It is a directory! Now 'mv' everything from it, up one level
      mv "$object"/* ./   # '*' means everything and "." (dot) stands for the current directory
   fi
done

```

---

### Post by codemaniac on 2012-05-06
> **RaHorakhty said:**
> is there an online repository of bash scripts for ubuntu? I want to develop a script that can move a file within a directory to the parent directory, recursively.  For example, if the directory  "Ubuntu" is filled with sub directories that start with "temp," the script must copy all the files out of each temp directory and move it in to the parent directory.  any suggestions?](*,)]
RaHorakhty , what have you tried so far ?

---

### Post by RaHorakhty on 2012-06-30
Thanks for the code.  I'll try it out later.  You're right. Bash isn't really meant to handle programming techniques like recursion, although it is possible.  I have another issue that I'm dealing with at the moment which deserves more attention.  I'll follow up with you asap.  sorry for the late reply btw us...):P

---

### Post by Habitual on 2012-06-30
Another resource - [http://ubuntuforums.org/showpost.php?p=11611291&postcount=1](http://ubuntuforums.org/showpost.php?p=11611291&postcount=1)

---

### Post by steeldriver on 2012-06-30
you could do it with 'find -exec' 

I'm not clear from your original post whether you want to move all of the files in each temp dir up to the root directory of the search (**the** parent)
```
find . \( -type d  -name 'temp*' \) -exec sh -c "cp {}/* ." \;
```or move each set of temp/* files up one level (to **its** parent)
```
find . \( -type d  -name 'temp*' \) -exec sh -c "cp {}/* {}/.." \;
```or maybe neater 
```
find mydir \( -type d  -name 'temp*' \) -execdir sh -c "cp {}/* ." \;
```

---

