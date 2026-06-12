---
title: "Mkdir from textfile in BASH-script"
date: 2008-03-31
forum: Programming Talk
---

### Post by AliBeg on 2008-03-31
Hello,
I trying to make a Bash-script to create directorys from a textfile.
I made this file "directory":
dir1/users/user1
dir1/users/user2
dir1/clients/client1
dir1/clients/client2
dir1/project

I want to execute a shell command such that I can use this textfile to make directorys. If one directory exist then the command will make the subdirectory.

How can I make this script??

Thank you!!
AliBeg

---

### Post by ghostdog74 on 2008-03-31
```


awk BEGIN'{q="\047" }
{
  cmd = "mkdir -p "q$0q
  system(cmd)
}
' directory


```
or bash

```

while read -r line
do
 mkdir -p "$line"
done < directory

```

---

### Post by jazzgossen on 2008-03-31
```
for f in `cat directory`; do mkdir -p $f; done
```

---

### Post by ghostdog74 on 2008-03-31
> **jazzgossen said:**
> ```
for f in `cat directory`; do mkdir -p $f; done
```

use a while loop instead of a for loop and cat
```

# more file
dir1/users/user1
dir1/users/user2
dir1/clients/client1
dir1/[COLOR="Red"]clients test/[/COLOR]client2
dir1/project
# for f in `cat file`; do mkdir  -p "$f"; done
mkdir: cannot create directory `dir1/users/user1': No such file or directory
mkdir: cannot create directory `dir1/users/user2': No such file or directory
mkdir: cannot create directory `dir1/clients/client1': No such file or directory
mkdir: cannot create directory `dir1/clients': No such file or directory
mkdir: cannot create directory `test/client2': No such file or directory
mkdir: cannot create directory `dir1/project': No such file or directory
# while read -r line; do mkdir -p "$f";done < file
# ls -ltr
total 8
-rw-r--r-- 1 root root   94 Mar 31 19:51 file
drwxr-xr-x 3 root root 4096 Mar 31 19:52 dir1

```

---

### Post by jazzgossen on 2008-03-31
I don't get any error messages from the for/cat solution as you do. But you're right that it doesn't handle directories with spaces in them.

---

### Post by AliBeg on 2008-03-31
Hi
Thanks for the solutions.
but i have another problem
if my text file looks like this

dir1 applications
dir1 projects
dir1 projects one
dir1 projects two
dir1 projects three

so there is no /

How can i create directorys with this file then?

Thank you!
Alibeg

---

### Post by calraith on 2008-03-31
```
#!/bin/bash

dataFile="directory"

# test for existence of $dataFile.
if [ ! -r "$dataFile" ]; then {
    echo;
    echo "ERROR: Unable to read $dataFile."
    exit 1
}; fi

cat $dataFile | while read -r line; do {
    mkdir -p "`echo $line | sed -r -e 's# #/#g'`"
}; done

exit 0
```

---

### Post by WW on 2008-03-31
I'm sure you'll get many variations for how to do this.  One way is to use the **tr** command to change the spaces to /, then pipe this to the **xargs** command to run **mkdir -p** on each of the names.  The line in blue below shows the actual command:
> 
$ ls
dirnames
$ cat dirnames
dir1 applications
dir1 projects
dir1 projects one
dir1 projects two
dir1 projects three
$ [color=blue]tr -s ' ' '/' < dirnames | xargs -L 1 mkdir -p[/color]
$ ls -F
dir1/  dirnames
$ tree
.
|-- dir1
|   |-- applications
|   `-- projects
|       |-- one
|       |-- three
|       `-- two
`-- dirnames

6 directories, 1 file
$ 


---

### Post by ghostdog74 on 2008-03-31
> **AliBeg said:**
> Hi
Thanks for the solutions.
but i have another problem
if my text file looks like this

dir1 applications
dir1 projects
dir1 projects one
dir1 projects two
dir1 projects three

so there is no /

How can i create directorys with this file then?

Thank you!
Alibeg
just substitute the blanks
```

awk BEGIN'{q="\047" ;}
{
  gsub(" ","/")
  cmd = "mkdir -p "q$0q
  system(cmd) 
}
' file

```

---

### Post by ghostdog74 on 2008-03-31
> **calraith said:**
> ```
...

cat $dataFile | while read -r line; do {
    mkdir -p "`echo $line | sed -r -e 's# #/#g'`"
}; done


```

no need cat. UUOC, as the while loop takes in file input.
also no need braces

```

while read -r line; do
    mkdir -p "`echo $line | sed -r -e 's# #/#g'`"
done

```

---

### Post by calraith on 2008-03-31
[quote=ghostdog74]no need cat. UUOC, as the while loop takes in file input.
also no need braces

```

while read -r line; do
    mkdir -p "`echo $line | sed -r -e 's# #/#g'`"
done
```[/quote]

You're right (or you would be if you added "< $dataFile" after "done").  Calling cat adds another process for no benefit.  It's just force of habit.  I do like my braces, though, just for my own obsessive compulsion for readability. :)

---

### Post by Sidster on 2010-05-13
Could we take this one step further and add something that moves files to the newly created directories?

What I've actually been scouring the interwebs for is something that will move my rather large movie collection into directories of the same name.

Example
I need to move
/Videos/Movies/Kill Bill Vol1.avi
to
/Videos/Movies/Kill Bill Vol1

So far I've created the needed directories using the script above now I just need to move my files into them. Bonus points for making the script handle spaces in file/folder names

Any help will be greatly appreciated

---

### Post by hannaman on 2010-05-14
You can use basename to get the movie name.
```
$ basename "/Videos/Movies/Kill Bill Vol1.avi" .avi
Kill Bill Vol1
```
The quotes above are used to protect spaces.

I had a script that created directories based on a timestamp for my home videos, but lost it when my hard drive crashed.  I started to rewrite the script, but it doesn't currently work and I haven't had the time to fix it, but here it is.
```
#!/bin/bash
base="/home/michael/Videos/Home Movies"
for i in `ls "$base"`; do
        cd "$base"
        if [ -f "$i" ]; then
                year=`awk -F. '{ print $1 }' "$i"`
                month=`awk -F. '{ print $2 }' "$i"`
                day=`awk -F. '{ print $3 }' "$i" | cut -d_ -f1`
                if [ -d $year ]; then
                        cd $year
                else
                        mkdir $year
                        cd $year
                fi
                if [ -d $month ]; then
                        cd $month
                else
                        mkdir $month
                        cd $month
                fi
                if [ -d $day ]; then
                        cd $day
                else
                        mkdir $day
                        cd $day
                fi
                mv "$base"/"$i" .
        fi
done

```
This is pretty simple, straightforward and not as fancy as the other examples, but it could get you started.  Also, as I stated, it didn't work right last time I tried, but you would have to change it anyway for your needs.

---

### Post by Sidster on 2010-05-14
thanks for the reply. :-)

I'll tinker a little and post the results.

If perfected I'll probably spread this around the XBMC forums and such

---

### Post by Sidster on 2010-05-14
I found this on theHTPC dot net

Credit to MattWA who posted a comment on an article for a windows bat file that does the same thing

```
#!/bin/bash
find . -name '*.*' | \
while read filename
do
      mkdir "${filename%.*}"
      directory=${filename%.*}
      mv "$filename" "$directory"/"$filename"
done
```

FTA - Comment by MattWA:

"This will work provided there is only one file associated with the movie. If you have other stuff like folder.jpg or something it probably won&#8217;t be suitable."

I have[s]n't tested[/s] this on files with spaces in the names and it works well

Edit: It would be helpful but not essential if someone could figure out how to exclude existing directories

---

### Post by hannaman on 2010-05-15
You could simply test to see if the directory already exists.
```
do
      directory=${filename%.*}
      if [ ! -d "$directory" ]; then
            mkdir "$directory"
      fi
      mv "$filename" "$directory"/"$filename"
done
```

---

### Post by adanvasco on 2011-08-12
Adding the "-maxdepth 1" option will avoid recreating directories inside directories with files.

find . -name '*.*' -maxdepth 1 | \

---

