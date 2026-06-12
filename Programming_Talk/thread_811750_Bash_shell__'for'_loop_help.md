---
title: "Bash shell  'for' loop help"
date: 2008-05-29
forum: Programming Talk
---

### Post by akvino on 2008-05-29
Hello all!

I need few suggestions how to overcome a problem with feeding entries from a file to a 'for' loop and accounting for the space in the file name. Here is my script counting number of files from the $path or indicated directory. When 'find' command is done it will store all of the directory names to the file named 'junk'. Afterwards I feed the directory name to the 'for' loop and it counts the number of files in that directory. The only problem is when the directory name is something like /home/user/New Folder and the 'for' loop does not know how to interpret space in the 'New Folder' , so it generates an error since it is trying to read directory by the name /home/user/New and the directory Folder. How do I tell it this is all one line, the name of the directory.

echo "Please enter the path to START directory: ";
read path

echo ..
echo ..
echo "You entered $path as you start directory!"
echo ..
echo ..

#getting the list of directories to file 'junk'
find $path -mount -type d  -print > junk;

for directory in $(cat $'./junk') 
do
        let number=`ls -1 $directory | wc -l`;

        if [ $number -gt 1000 ]
        then
                echo "........................................................"
                echo   
                echo "the number of files in"
                echo "$directory:"
                echo "$number"
        fi
done

/bin/rm junk

---

### Post by ghostdog74 on 2008-05-29
use while loop
```


....
find ...... | while read directory
do
 ls -1 "$directory" | wc -l 
 blah
 blah
done

```

---

### Post by akvino on 2008-05-29
> **ghostdog74 said:**
> use while loop
```


....
find ...... | while read directory
do
 ls -1 "$directory" | wc -l 
 blah
 blah
done

```



Still the same problem - it reads the directory name but uses 'space' in the directory name as a delimiter. So if anyone created a directory via Samba called New Folder - it will try to find /path/New and Folder as two separate directories.

---

### Post by geirha on 2008-05-29
> **akvino said:**
> Still the same problem - it reads the directory name but uses 'space' in the directory name as a delimiter. So if anyone created a directory via Samba called New Folder - it will try to find /path/New and Folder as two separate directories.

You mean the $path variable? just quote it with soft-quotes:

```
find "$path" -type d | while read dir; do
  echo "$dir contains $(ls "$dir"|wc -l) files"
done
```

---

### Post by akvino on 2008-05-29
> **geirha said:**
> You mean the $path variable? just quote it with soft-quotes:

```
find "$path" -type d | while read dir; do
  echo "$dir contains $(ls "$dir"|wc -l) files"
done
```

I tried and still am getting chopped directory structure when reading in or piping to it.

Output Example:
ls: /home/admin/.wine/drive_c/windows/profiles/admin/Local: No such file or directory
ls: Settings/Temporary: No such file or directory
ls: Internet: No such file or directory
ls: Files: No such file or directory

In essence the read in directory should have been "/home/admin/.wine/drive_c/windows/profiles/admin/Local Settings/Temporary Internet Files".

---

### Post by johnl on 2008-05-29
This worked for me:

```

find ./ -type d | while read directory
do
    count=$(ls "$directory" | wc -l)
    echo "$directory has $count"
done

```

If you can echo the directory or filename inside your loop, from there you know the problem is with the quoting inside the loop, not the loop itself.

---

### Post by akvino on 2008-05-29
> **johnl said:**
> This worked for me:

```

find ./ -type d | while read directory
do
    count=$(ls "$directory" | wc -l)
    echo "$directory has $count"
done

```

If you can echo the directory or filename inside your loop, from there you know the problem is with the quoting inside the loop, not the loop itself.

It generates error on the ls command. Possible resolutions: 
1)How do I feed the line to the 'ls' command and tell it to ignore 'space' in the name of the direcoty 

2) Is there a switch for the 'find' command that would insert '\' before the space

---

### Post by geirha on 2008-05-29
> **akvino said:**
> It generates error on the ls command. Possible resolutions: 
1)How do I feed the line to the 'ls' command and tell it to ignore 'space' in the name of the direcoty 

by putting double-quotes (soft-quotes) "" around the directory.
> **akvino said:**
> 
2) Is there a switch for the 'find' command that would insert '\' before the space
Not to my knowledge.

If you paste the code you are using now, someone will probably be able to spot the error.

---

### Post by akvino on 2008-05-29
> **geirha said:**
> by putting double-quotes (soft-quotes) "" around the directory.

Not to my knowledge.

If you paste the code you are using now, someone will probably be able to spot the error.

Code is posted in the top post. I tried variations per suggestions in this thread. 

#!/bin/bash

echo "Please enter the path to START directory: ";
read path

echo ..
echo ..
echo "You entered $path as you start directory!"
echo ..
echo ..

#getting the list of directories to file 'junk'
find $path -mount -type d -print > junk;

for directory in $(cat $'./junk')
do
let number=`ls -1 $directory | wc -l`;

if [ $number -gt 1000 ]
then
echo "................................................. ......."
echo
echo "the number of files in"
echo "$directory:"
echo "$number"
fi
done

/bin/rm junk

---

### Post by geirha on 2008-05-29
Here's your code above, modified to use while instead of for, and with proper quoting.

```

#!/bin/bash

echo "Please enter the path to START directory: ";
read path

echo ..
echo ..
echo "You entered $path as you start directory!"
echo ..
echo ..

find "$path" -mount -type d -print | 
while read directory; do
  number=`ls -1 "$directory" | wc -l`
  if [ $number -gt 1000 ]; then
    echo "................................................. ......."
    echo
    echo "the number of files in"
    echo "$directory:"
    echo "$number" 
  fi
done

```

---

### Post by akvino on 2008-05-29
That did the trick, thanks a lot guys and girls.:guitar:

---

### Post by dtmilano on 2008-05-29
You should use 'find -print0', see **UNUSUAL FILENAMES** section in man find(1).

---

### Post by HalPomeranz on 2008-05-29
May I suggest the following instead:

```

#!/bin/bash
# A script for counting the number of files in a set of directories.
# Usage: filecount dir1 [dir2 ...]

# The line below must be "IFS='<newline>".  DO NOT ADD OTHER WHITESPACE!
IFS='
'

for dir in $(find $* -type d); do
    echo $(ls -a $dir | wc -l) $dir
done

```

Some commentary:

-- The trick with IFS is what you do to make sure that spaces in file names don't mess up the other commands in the script.  IFS stands for "Intra-Field Separator" and is normally set to the list of characters the shell uses to delimit command line arguments: space, tab, and newline.  If you don't want the shell script to treat spaces in file names as special, then just set IFS to newline only as we do here.

-- $(...) is essentially the same thing as `...` but is generally the "safer", more correct syntax to use.

-- Notice that I don't read the search directory in interactively as previous scripts in this thread have done.  Instead I use $* in the find command in the for loop, which will use the list of directories you specify on the command line of the shell script.  This is much cleaner, allows you to specify multiple directories to seach, and much more like the normal Unix command-line standards.

-- Notice also that I'm using "ls -a" to get the directory listing.  You don't want to forget about the dot files in the directories. 

-- Don't use the "-l" option on the ls command because it introduces an extra header line in the output you're counting with "wc -l".  If you were doing the "-l" because you were worried about having "one file per line" in the ls output, remember that when the output of ls is being piped into another program you get "one file per line" output automatically (you can test this by doing "ls /dev | less").

When run the script output looks like this:

```

$ sudo filecount /dev
325 /dev
3 /dev/disk
6 /dev/disk/by-path
6 /dev/input
3 /dev/net
4 /dev/VolGroup00
5 /dev/mapper
2 /dev/shm
6 /dev/pts

```

Again, this kind of output is much more in line with the standard Unix design "religion"-- you're supposed to write simple programs that can be easily pipelined together.  Somebody might want to use this program to get the file counts for all directories, not just the directories with lots of files.

Since you only care about directories with lots of files, you could do something like:

```

# prints the names of directories with 1000 or more files
sudo filecount /dev | awk '($1 >= 1000) { print $2 }'

# shows the 10 largest directories
sudo filecount /dev | sort -n | tail

```

This is the power of the Unix command shell.  Embrace it!

---

### Post by mssever on 2008-05-30
Note also that ls is designed to provide human-readable output, not machine-parsable output. It is impossible to reliably parse the output from ls because ls uses no delimiters to separate filenames from formatting. Using ls -1 is the best you can get, but even that fails for filenames containing \n (and possibly other characters, as well).

---

### Post by dtmilano on 2008-05-30
I would use something along these lines

```
#! /bin/bash

if [ "$1" = '-c' ]
then
   echo $(ls -a "$2" | wc -l) $2
else
   find "$@" -type d -print0 | xargs -0 -I '{}' $0 -c {}
fi

```

it could handle some cases (i.e.: nl in dirnames) that previous couldn't.

---

### Post by geirha on 2008-05-30
A recursive version :)

Might as well use just find, instead of find|xargs
```
find "$@" -type d -exec $0 -c {} \;
```

What happens if a dir is called "-c" though?

---

### Post by dtmilano on 2008-05-30
Very good point.
And with regards to a dir called '-c' there's no problem because dir name is always the second arg (.i.e: $0 -c -c).
A check for more than one args should be added.
Still, there's the case where you invoke it with the same dir (-c) twice, and moreover you need to protect find from interpreting any dir starting with '-' as options.

---

### Post by akvino on 2008-05-30
> **dtmilano said:**
> I would use something along these lines

```
#! /bin/bash

if [ "$1" = '-c' ]
then
   echo $(ls -a "$2" | wc -l) $2
else
   find "$@" -type d -print0 | xargs -0 -I '{}' $0 -c {}
fi

```

it could handle some cases (i.e.: nl in dirnames) that previous couldn't.

Can you give me description to what xargs -0 -I '{}' $0 -c {} does.

---

### Post by akvino on 2008-05-30
> **HalPomeranz said:**
> May I suggest the following instead:

```

#!/bin/bash
# A script for counting the number of files in a set of directories.
# Usage: filecount dir1 [dir2 ...]

# The line below must be "IFS='<newline>".  DO NOT ADD OTHER WHITESPACE!
IFS='
'

for dir in $(find $* -type d); do
    echo $(ls -a $dir | wc -l) $dir
done

```

Some commentary:

-- The trick with IFS is what you do to make sure that spaces in file names don't mess up the other commands in the script.  IFS stands for "Intra-Field Separator" and is normally set to the list of characters the shell uses to delimit command line arguments: space, tab, and newline.  If you don't want the shell script to treat spaces in file names as special, then just set IFS to newline only as we do here.

-- $(...) is essentially the same thing as `...` but is generally the "safer", more correct syntax to use.

-- Notice that I don't read the search directory in interactively as previous scripts in this thread have done.  Instead I use $* in the find command in the for loop, which will use the list of directories you specify on the command line of the shell script.  This is much cleaner, allows you to specify multiple directories to seach, and much more like the normal Unix command-line standards.

-- Notice also that I'm using "ls -a" to get the directory listing.  You don't want to forget about the dot files in the directories. 

-- Don't use the "-l" option on the ls command because it introduces an extra header line in the output you're counting with "wc -l".  If you were doing the "-l" because you were worried about having "one file per line" in the ls output, remember that when the output of ls is being piped into another program you get "one file per line" output automatically (you can test this by doing "ls /dev | less").

When run the script output looks like this:

```

$ sudo filecount /dev
325 /dev
3 /dev/disk
6 /dev/disk/by-path
6 /dev/input
3 /dev/net
4 /dev/VolGroup00
5 /dev/mapper
2 /dev/shm
6 /dev/pts

```

Again, this kind of output is much more in line with the standard Unix design "religion"-- you're supposed to write simple programs that can be easily pipelined together.  Somebody might want to use this program to get the file counts for all directories, not just the directories with lots of files.

Since you only care about directories with lots of files, you could do something like:

```

# prints the names of directories with 1000 or more files
sudo filecount /dev | awk '($1 >= 1000) { print $2 }'

# shows the 10 largest directories
sudo filecount /dev | sort -n | tail

```

This is the power of the Unix command shell.  Embrace it!

Thanks for the pointers, I am still learning my ways around bash and c shell.

This 
# The line below must be "IFS='<newline>".  DO NOT ADD OTHER WHITESPACE!
IFS='
'
the IFS has to be broken on two lines? Why?

---

### Post by geirha on 2008-05-30
> **akvino said:**
> Thanks for the pointers, I am still learning my ways around bash and c shell.

This 
# The line below must be "IFS='<newline>".  DO NOT ADD OTHER WHITESPACE!
IFS='
'
the IFS has to be broken on two lines? Why?

No, bash has a special syntax to avoid this. You can do ```
IFS=$'\n'
``` instead. They are equivalent.

---

### Post by akvino on 2008-05-30
> **geirha said:**
> No, bash has a special syntax to avoid this. You can do ```
IFS=$'\n'
``` instead. They are equivalent.

Thanks a lot. Are there other useful implications of IFS that one should be aware off?

---

### Post by HalPomeranz on 2008-05-30
> **akvino said:**
> Are there other useful implications of IFS that one should be aware off?

Modifying IFS is particularly useful when you're reading in a file of strongly delimited data, e.g. a file like /etc/passwd where the fields are separated by colons:

```

#!/bin/bash

IFS=':'

exec 9<&0 </etc/passwd
while read UNAME JUNK USERID GRPID GECOS HOMEDIR SHELL; do
    echo $UNAME $USERID $GRPID $GECOS $HOMEDIR $SHELL
done
exec 0<&9 9<&-

```

The IFS setting will result in each line of the passwd file automatically being split into fields and those fields will be assigned to variables by the "read" command in the while loop.

---

