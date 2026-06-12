---
title: "Help with simple BASH Script"
date: 2007-06-11
forum: Programming Talk
---

### Post by brennydoogles on 2007-06-11
I am trying to learn BASH scripting, and the script that I am working on is a script to copy DVD's through the command line (I know this is a simple enough task to do without a script, but i am trying to learn how!!) Here is the script so far:
```
#!/bin/bash
	echo -e "Where would you like the ISO created?"
           OPTIONS="Home Other"
           select opt in $OPTIONS; do
               if [ "$opt" = "Home" ]; then
                DIRECTORY=/home/$(USER)/
               elif [ "$opt" = "Other" ]; then
                echo -e "Please enter the directory into which you would like to create your ISO: " 
		read  DIRECTORY
               else
                clear
                echo "bad option"
               fi
           done
	echo -e "Please enter the desired filename for your ISO (and please remember to precede " 
	echo -e "any SPACES or ' with a \) :" 
	read FILENAME
	dd if=/dev/cdrom of=$DIRECTORY/"$FILENAME".iso
	exit 0
```

and here is the error I get when running it:
```
brendon@linux:~$ sh test1.sh 
-e Where would you like the ISO created?
test1.sh: 4: select: not found
bad option
test1.sh: 14: Syntax error: "done" unexpected

```

Where have I Gone wrong?? This is my first time trying to create a menu in a script, and I also don't know if the $(USER) variable will work. Any help would be greatly appreciated!!

---

### Post by leibowitz on 2007-06-11
I think that you are using dash, and not bash. As I tried your script (with little modification) and it seems to work using Bash.

But using dash, it's reporting the same error as you get.

```
#!/bin/bash
	echo -e "Where would you like the ISO created?"
           OPTIONS="Home Other"
           select opt in $OPTIONS; do
               if [ "$opt" = "Home" ]; then
                ## no, $(USER) is not the same as $USER (and the last slash "/" is not needed here)
                DIRECTORY=/home/$USER
               elif [ "$opt" = "Other" ]; then
                echo -e "Please enter the directory into which you would like to create your ISO: " 
		read  DIRECTORY
               else
                clear
                echo "bad option"
               fi
               ## break otherwise it will loop ... 
               break
           done
	echo -e "Please enter the desired filename for your ISO (and please remember to precede " 
	echo -e "any SPACES or ' with a \) :" 
	read FILENAME
	dd if=/dev/cdrom of=$DIRECTORY/"$FILENAME".iso
	exit 0
```

This is it. Try installing bash (I think it was in Edgy that dash replaced bash)

---

### Post by slightcrazed on 2007-06-11
You could get away with doing a case statement instead of the 'select' that you are using. Case is going to be a lot more portable (bash, ksh etc....) but I don't know if portability is important to you.

---

### Post by brennydoogles on 2007-06-11
> **leibowitz said:**
> I think that you are using dash, and not bash. As I tried your script (with little modification) and it seems to work using Bash.

But using dash, it's reporting the same error as you get.

```
#!/bin/bash
	echo -e "Where would you like the ISO created?"
           OPTIONS="Home Other"
           select opt in $OPTIONS; do
               if [ "$opt" = "Home" ]; then
                ## no, $(USER) is not the same as $USER (and the last slash "/" is not needed here)
                DIRECTORY=/home/$USER
               elif [ "$opt" = "Other" ]; then
                echo -e "Please enter the directory into which you would like to create your ISO: " 
		read  DIRECTORY
               else
                clear
                echo "bad option"
               fi
               ## break otherwise it will loop ... 
               break
           done
	echo -e "Please enter the desired filename for your ISO (and please remember to precede " 
	echo -e "any SPACES or ' with a \) :" 
	read FILENAME
	dd if=/dev/cdrom of=$DIRECTORY/"$FILENAME".iso
	exit 0
```

This is it. Try installing bash (I think it was in Edgy that dash replaced bash)

That was the issue for sure. Thanks so much for your help!! I will have to post back soon with one other script i am having a hard time with. Thanks!!!!!

---

