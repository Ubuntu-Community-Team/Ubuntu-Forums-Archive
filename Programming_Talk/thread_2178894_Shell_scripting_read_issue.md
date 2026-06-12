---
title: "Shell scripting read issue"
date: 2013-10-05
forum: Programming Talk
---

### Post by aadil7 on 2013-10-05
hi everyone

i am trying to read in a file and move it to a new location which is specified in the script. 
i want this to work like all other commands (rm, mv, ls...)
I am having trouble as I cannot get the script to read or locate the file!

```

#!/bin/bash


for TOKEN in $@
do


echo $TOKEN


echo "file name: $1"


filename=$TOKEN


if [-f $filename]
then
	echo "File $filename exists"
	else
	echo "File $filename does not exist"
fi
done

```

further explaination
i ensure i have a file called file1 in the same location as the script.. /home/user/
i start the script in terminal with sh exist file1
I get an error saying "exist: 12: exist: [-f: not foundFile  does not exist"

am i going about this in the right way?
does it not know the directory of the file?
why can it not find it?

all help is much appreciated thank you

---

### Post by aadil7 on 2013-10-05
Okay after further looking into this I understand the for loop is un-necessary..
but the problem still persists I cannot find the file!

---

### Post by Vaphell on 2013-10-05
tests in [ ] require spaces separating everything. [] is not a flavor of parentheses, but a command "[" and the rest are its parameters "-f" "$file" "]"
bash tells you there is no **[-f** because it got this in one piece and tried to find a command with that name.

---

### Post by aadil7 on 2013-10-05
right so i discovered something new
as I was baffled at why it couldnt find the file i did a little test:

```

#!/bin/bash


[ -d /var/logs ] && echo "works" || echo "dont work"

```

this would simply confirm if the could see the directory /var/logs but this did not work either!
how do I go about fixing this I feel as though im missing something

---

### Post by aadil7 on 2013-10-05
rightfully so.. but in the test to see if it notices the directory.. it still showed up as not detectable!

---

### Post by Vaphell on 2013-10-05
```
$ [ -d /var/log[COLOR="#FF0000"]s[/COLOR] ] && echo "works" || echo "dont work"
dont work
$ [ -d /var/log ] && echo "works" || echo "dont work"
works
```

---

### Post by aadil7 on 2013-10-05
okay brill.. sorry for that silly error.. i tried 

```

#!/bin/bash
FILE=$1
 
if [ -f $FILE ];
then
   echo "File $FILE exists"
else
   echo "File $FILE does not exists"
fi

```

and it worked also but how can i get it so I do not have to input the whole location? i want to use it like an ls command. is that to do with aliases?

---

### Post by Vaphell on 2013-10-05
i don't understand what you want to achieve. What is the script supposed to do to be like ls?

Btw try your script with a quoted param like this "some file with spaces in its name" to find out why wrapping variables with "" is a good idea ;-)

---

### Post by aadil7 on 2013-10-05
im sorry youve confused me I want to learn but just dont know where to put the ""

and what i want to do is make my own move command.. first i need it to verify the file exists and that is this stage.. the thing is i dont want to put in the whole path to the file so:
instead of
sh move /home/user/file1

i want to do:
sh move file1

just like with the mv command you can find the file anywhere.. call the command and execute the command

---

### Post by Vaphell on 2013-10-05
```
$ f="omg wtf bbq"
$ [ -f $f ] && echo true
bash: [: too many arguments
$ [ -f "$f" ] && echo true
$
```
why is there an error? because [ sees "-f" "omg" "wtf" "bbq" "]" and -f requires only 1 + ]. If you want to prevent fragmentation of the contents of the variable (and you want, trust me), quote it.


mv command doesn't find stuff anywhere. You can use only name if you are exactly where the object of interest is, but if it's somewhere else you need to use path, either absolute or relative. If you run your script from $HOME and file1 is there, file1 should be enough.

```
$ cd ~
$ touch file1.txt
$ f=file1.txt 
$ [ -f "$f" ] && echo "'$f' exists" || echo "'$f' doesn't exist"
'file1.txt' exists
$ f=~/file1.txt 
$ [ -f "$f" ] && echo "'$f' exists" || echo "'$f' doesn't exist"
'/home/me/file1.txt' exists
```

---

### Post by aadil7 on 2013-10-05
thanks a million you have been such a great help!
i cant wait to have sufficient scripting skills *sigh*

---

