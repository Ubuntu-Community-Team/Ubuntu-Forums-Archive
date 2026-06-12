---
title: "A question about sed"
date: 2011-03-09
forum: Programming Talk
---

### Post by CaptainMark on 2011-03-09
Im having trouble with the sed command,
im trying to pass file names which are strings to the rm command 
anytime i hit a file with white space in it im coming unstuck, for example

a string of file_name='new file' is being passed to rm
but its trying to remove a file named 'new' and a file named 'file' which dont exist,
im trying to pipe it through sed to change the string with this

| sed  's: :\\ :g'

but i still get the error the same so obviously rm is still getting two seperate arguments,

the idea came from [this thread]("http://ubuntuforums.org/showthread.php?t=1692800&page=2"), they had the same problem of white space but i didnt understand

---

### Post by DaithiF on 2011-03-09
Hi, rather than trying to escape spaces, just enclose the filename in quotes:
```

file_name="new file"
rm "$file_name"

```

---

### Post by CaptainMark on 2011-03-09
i was just playing around with this idea when i read your post, i keep getting syntax errors on that perhaps if you see the whole file you could help me more ```
#!/bin/bash

echo 'Updating new files....'
rsync -aE ./ ../passport
echo 'New files copied.'

num_files=`rsync -avn --delete ./ ../passport | grep deleting | sed 's/deleting / /' | wc -l`
if [ $num_files != 0 ]; then
    echo -e '\nThe following files/folders will be deleted:\n'
    rsync -avn --delete ./ ../passport | grep deleting | sed 's/deleting / /'
    
    echo -en '\nDo you want these files to be erased? (y/n): '
    read choice1;
    yes='y'
    no='n'
    
    if [ $choice1 = $yes ]; then
        echo -e '\nPlease wait'
        echo -n '5 ' && sleep 1
        echo -n '4 ' && sleep 1
        echo -n '3 ' && sleep 1
        echo -n '2 ' && sleep 1
        echo '1' && sleep 1
        
        echo -en '\nAre you sure you want to delete? (y/n): '
        read choice2
        
        if [ $choice2 = $yes ]; then
            echo ''
            rsync -av --delete ./ ../passport | grep deleting | sed 's/deleting/Deleting - /'
        else 
            echo 'No files deleted'
        fi
    
    else
        
        echo -en '\nWould you like to delete interactivly? (y/n): '
        read inter
        
        if [ $inter == $yes ]; then
            echo 'Interactive Removal:'
            for file in $(rsync -avn --delete ./ ../passport | grep deleting | sed -e 's:deleting ::')
            rm -ir "$file"
    
        else
            echo 'No files deleted'
            
        fi
    fi 
else
    echo -e '\nNo files to delete'
    
fi

echo -e '\nExiting.' && sleep 5
    
    

```The problem lies after the line echo 'Interactive Removal' about 10 lines from the end
basically i need to take the results of rsyncs verbosive output use grep to pick out only lines that contain 'deleting ', ive used sed to remove the word deleting and the trailing space i then need to pass that output to the rm command, im missing something small thats stopping that line working.

---

### Post by Vaphell on 2011-03-09
```
IFS=$'\n'
``` to delimit with newlines only (space becomes an ordinary char)

or try
```
rsync -avn --delete ./ ../passport | grep deleting | sed -e 's:deleting ::' | while read file
do
  rm -ir "$file"
done
```

---

### Post by CaptainMark on 2011-03-09
I felt optimisic about this second option, i would have expected it to work but it doesnt. it doesnt wait for any interactivity but just skips and quits, hmmm, 

could i put the output of rsync into an array and iterate over each file with a for loop, i have the variable $num_file to use already, i dont know how to so this in bash

heres my output this time
```
Updating new files....
New files copied.

The following files/folders will be deleted:

 new file (copy)
 new file

Do you want these files to be erased? (y/n): n

Would you like to delete interactivly? (y/n): y

Interactive Removal:
rm: remove regular empty file `../passport/new file (copy)'? 
Exiting.


```Where would i place IFS=$'\n'

---

### Post by Vaphell on 2011-03-10
put IFS where you need it, if you have a lot of space handling you can put at the beginning
look at this example, maybe you'll figure out what you need
```
#!/bin/bash

str="a b
c d"

for t in $str; do echo :::"$t"; done
echo --------
IFS=$'\n'
for t in $str; do echo :::"$t"; done
echo --------
unset IFS
for t in $str; do echo :::"$t"; done
echo --------
for t in "$str"; do echo :::"$t"; done
echo --------

IFS=$'\n'
#output of example command to array
array=( $( ls ) )

# approach #1
i=0
for item in ${array[@]}
do
  (( i++ ))
  echo \#$i $item
done
echo --------

# approach #2, ${#array[@]} = number of elements
for (( i=0; i<${#array[@]}; i++ ))
do
  echo \#$(( i+1 )) ${array[i]}
done

```

output:
```

:::a
:::b
:::c
:::d
--------
:::a b
:::c d
--------
:::a
:::b
:::c
:::d
--------
:::a b
c d
--------
#1 a.out
#2 arrays.sh
...
#33 test test
...
--------
#1 a.out
#2 arrays.sh
...
#33 test test
...
```
first loop uses default delimiter of any whitespace, second only newline, third again default one, 4th - default one, but string is quoted. 2 last loops showcase arrays.

---

### Post by CaptainMark on 2011-03-10
Aw thank you soo much, ive been pondering over this for 2 days at work, this was a huge help, ill buy you an imaginary beer for that

---

