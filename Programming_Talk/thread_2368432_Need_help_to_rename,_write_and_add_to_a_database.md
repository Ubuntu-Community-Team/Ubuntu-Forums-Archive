---
title: "Need help to rename, write and add to a database"
date: 2017-08-10
forum: Programming Talk
---

### Post by cazz on 2017-08-10
It does not need to be one script but I need some help

I have some files that I like to trim the filename

filename_(2000)_001.jpg
filename_(2011)_002.jpg
filename_(2012)_005.jpg
....

I have to trim 11 from right so I just have filename.jpg
I was thinking maybe use bach but is that any trim function inside that I can use?


Next is time to rename all the filesname to random letters and numbers but it have to be unique or it going to be error if it is a file with same name
like dsdfsf89w4.jpg

but I have to someone still have information what the filename it have before and maybe save it in a text file
like this

filename.jpg dsdfsf89w4.jpg


Later I was thinking import the file to a MySQL database


/Update
Have find this code
ls | awk -F. '{printf "mv \"%s\" \"%s.%s\"\n",$0,substr($1,1,length($1)-11),$2 ;}' | ksh 
from here [https://unix.stackexchange.com/questions/154771/rename-hundreds-of-file-by-removing-last-few-characters](https://unix.stackexchange.com/questions/154771/rename-hundreds-of-file-by-removing-last-few-characters)

so now step one is finnish, have nice filenames now.

but I have no idea how to continue

/Update 2
After a little sleeping I have got everything to work
I did use a loop, save it in csv file and use mv to rename the file.
I also use Random and use a number that loop to make sure I get it right :)

---

### Post by TheFu on 2017-08-13
Using 'ls' in a script is very dangerous.  You might want to google a little for when and why that files.  Better to use file globbing methods provided in the scripting language you use.  All the major scripting languages have safe globbing tools/methods.  Plus those are usually faster.

I would have used rename, mktemp  and simple bash globbing. 
*        rename - renames multiple files
*        mktemp - create a temporary file or directory
* Bash manpage explains the globbing nicely, 
```
              ?(pattern-list)
                     Matches zero or one occurrence of the given patterns
              *(pattern-list)
                     Matches zero or more occurrences of the given patterns
              +(pattern-list)
                     Matches one or more occurrences of the given patterns
              @(pattern-list)
                     Matches one of the given patterns
              !(pattern-list)
                     Matches anything except one of the given patterns
```

Just to prove that I can write C in any language ... ;)
```
#!/bin/sh
#script
for filename in "$@"; do
   ROOT=`echo "$filename"| sed -e 's/\(.*$//' ` # this will retain everything up to the first '('
   OUT="$ROOT-$RANDOM.jpg"
   echo mv "$filename" "$OUT"
done
```

As an example. My script won't work with filenames that contain spaces, because a {space} is a globbing delimiter when using "$@"

So, *./script {glob pattern}* is the way to use it.   **./script  *jpg** or  **./script  *01* **

---

