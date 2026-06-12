---
title: "Bash User and File Input"
date: 2007-09-08
forum: Programming Talk
---

### Post by Blazeix on 2007-09-08
Hi, I'm writing a bash script where I read in a bunch of filenames from a list and then ask the user a question about each file. I've googled around, and I have it almost working; I can't get the last step. I'm using the read command to read from a file, and then I am trying to 'read' user input. The problem is that the script obviously doesn't know that I want user input instead of file input. How to I tell the script that I want to have the input be user input?

Here is my program so far. This is just a small pointless program that I'm using to get the basics of what I need to do for the larger program. 
```

#!/bin/bash
exec < $1
read file            [color=red]<----This line reads the first line from the file specified at the command line[/color]
echo "What would you like to do for file $file?"
read action          [color=red]<----This line *should* get user input.[/color]
if [ "$action" = "d" ]; then
        echo "d key pressed"
elif [ "$action" = "k" ]; then
        echo "k key pressed"
else
        echo "Error"
fi

```

Thanks for any help!

---

### Post by dwhitney67 on 2007-09-08
I get these errors when I run your script.  Seems like the problem occurs way before you prompt for input from the user.

[FONT="Courier New"]> bash script 
script: line 2: $1: ambiguous redirect
script: line 3: ----This: No such file or directory
What would you like to do for file ?
script: line 5: ----This: No such file or directory
Error[/FONT]

Consider inserting a check at the beginning to ensure you have your command line arg:
```

if [ $# != 1 ]; then
  # show script 'usage'
  exit
fi
```

---

### Post by dwhitney67 on 2007-09-08
Sorry, I ran your script without removing your comments/questions.  That's why I got those errors. But now I understand what your asking.

Here's a clue from this [web page]("http://www.tldp.org/LDP/abs/html/index.html"):

```
#!/bin/bash

exec echo "Exiting \"$0\"."   # Exit from script here.

# ----------------------------------
# The following lines never execute.

echo "This echo will never echo."

exit 99                       #  This script will not exit here.
                              #  Check exit value after script terminates
                              #+ with an 'echo $?'.
                              #  It will *not* be 99.
```

---

### Post by dwhitney67 on 2007-09-09
Try this:

[PHP]#!/bin/bash

if [ $# != 1 ]
then
        echo "Usage: $0 <file>"
        exit
fi

FILES=`cat $1`

for file in $FILES
do
        echo "What do you want to for $file"
        read action

        case "$action" in
                [dD])   echo "d key pressed";;
                [kK])   echo "k key pressed";;
                *)      echo "Illegal input... bye!"; exit;;
        esac
done[/PHP]

Hope this helps.  I got my "Red Hook ESB" hat on tonight.

---

### Post by gnusci on 2007-09-09
Try changing the way of reading the input file

[PHP]
#!/bin/bash

#exec < $1
#read file   #<----This line reads the first line from the file specified at the command line

file=`cat $1`



echo "What would you like to do for file $file?"
read action  #<----This line should get user input. 


if [ "$action" = "d" ]; then
        echo "d key pressed"
elif [ "$action" = "k" ]; then
        echo "k key pressed"
else
        echo "Error"
fi
[/PHP]

---

### Post by dwhitney67 on 2007-09-09
> **gnusci said:**
> Try changing the way of reading the input file

[PHP]
#!/bin/bash

#exec < $1
#read file   #<----This line reads the first line from the file specified at the command line

file=`cat $1`



echo "What would you like to do for file $file?"
read action  #<----This line should get user input. 


if [ "$action" = "d" ]; then
        echo "d key pressed"
elif [ "$action" = "k" ]; then
        echo "k key pressed"
else
        echo "Error"
fi
[/PHP]

Your comments leave me with a hanging question... Huh???

---

### Post by Blazeix on 2007-09-09
Those are all good ideas. I hadn't thought of simply using cat to read in the file contents, although that makes perfect sense. I used the method in the link that dwhitney67 provided in his second post. This is how I ended up doing it:

```

#!/bin/bash
#User provides a file that contains a list of filenames, one per line

#save current stdin
exec 6<&0

# make stdin the file that the user provided, and then read each line in the
# file into an array
exec < $1
numLines=`wc -l < $1`
for i in `seq 1 "$numLines"`
do
        read filename
        files["$i"]="$filename"
done

#Now that we're done loading the data into the array, restore stdin
exec 0<&6 6<&-

#iterate through the array, asking a question about each file
for file in ${files[@]}
do
        echo "What would you like to do for file $file?"
        read action
        if [ "$action" = "d" ]; then
                echo "d key pressed"
        elif [ "$action" = "k" ]; then
                echo "k key pressed"
        else
                echo "Error"
        fi
done

```

Thanks for everyone's help!

---

### Post by jpkotta on 2007-09-09
You may also want to try select, because this is exactly what it was designed to do.

```
#!/bin/bash

PS3="Please choose a number: "

select response in yes no maybe ; do
    if [[ $response = "yes" ]] ; then
	echo "yes"
	break
    elif [[ $response = "no" ]] ; then
	echo "no"
	break
    elif [[ $response = "maybe" ]] ; then
	echo "maybe"
	break
    else
	echo "Invalid choice, try again."
    fi
    echo
done

exit
```

---

