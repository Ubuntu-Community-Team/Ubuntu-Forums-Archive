---
title: "shell script with case statements"
date: 2010-10-31
forum: Programming Talk
---

### Post by Reddoug on 2010-10-31
Hi All

I am working on my scripting with case statements. Is there away to call out any file and list its contents? The first four work ok. I am not sure about the last two. The 5th one, after entering file name should respond with a listing of the file and the exit. The 6th on should respond with the ls -l of that directory. I only have one directory. Can you change to the directory and list contents with case statements? Enter a valid dir name and list contents. Just wanting to know if I am close to being right or not. I have  spent a lot of time today trying to figure this out.

Thanks, Doug

#!/bin/sh

echo "\n Please enter function: \c"
read function
echo "You entered $function"
case $function in
   Author)
     echo "Doug"
      ;;
    date)
        date +"%b %d %Y"
      ;;
    time)
       date +%l:%M
      ;;
 current)
       pwd
      ;;
    type)
      echo " Enter file name: "
      read filename
      ls -l | grep "^-" 
      ;; 
     dir)
     echo "Enter directory name"
      read dirname
      ls -l wild
      ;;
esac

---

### Post by epicoder on 2010-10-31
Assuming you are showing the contents of a text file (anything else will print loads of jargon) that is in the working directory:
```
type)
echo "Enter file name: "
read filename
ls -l $filename
cat $filename
;; 
```As for the directory listing:
```
dir)
echo "Enter directory name: "
read dirname
ls -l $dirname
;;
```Also, for making a script with a prompt, it's a good idea to add case insensitivity and a handler for anything else.
To add the case insensitivity, simply change all the match patterns to lowercase and use sed to transform the input:
```
function=$(echo $function | sed "s/[A-Z]/\L&/g")
case $function in
author) #instead of Author
```To add the handler, you add a "*)" after all of the other choices:
```
*)
echo "Unrecognized function"
;;
esac
```

---

### Post by Reddoug on 2010-10-31
Hi and thanks for the info. I have not used sed yet. I will have to start working with it and figure out how it works. Been having fun learning scripting. 

Thanks again, Doug

---

