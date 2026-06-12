---
title: "move a set amount of files to multiple folders"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by Froylan on 2013-05-19
HI!
I have more than 1000 pictures and I want to move them to my 3ds but to do that you need to have no more than 99 pictures per folder, is there any command to move 90 files to different folders, also the naming pattern of the 3ds pictures is HNI_00xx where as xx is from 01-99 and the folder naming pattern is from 1xxNIN03 where as xx is just a growing number that starts with 0

the files names will be saved as HNI_00xx and every 99 pics the 3DS will make a new folder in DCIM on the SD card starting at 100NIN03, next folder being 101NIN03

---

### Post by Froylan on 2013-05-19
anyone? :(

---

### Post by jamesisin on 2013-05-19
May I ask what is your motivation for limiting the folders to 99 images each?  Also, couldn't you just select 99 images and move them through drag-and-drop?

---

### Post by Froylan on 2013-05-19
> **jamesisin said:**
> May I ask what is your motivation for limiting the folders to 99 images each?  Also, couldn't you just select 99 images and move them through drag-and-drop?
none, the 3ds can't get more than 99 pictures per folder and by using drag-and-drop it will take a lot of time and I am looking forward to using this script at least 4 times a week

---

### Post by jamesisin on 2013-05-19
I see.

I can't write the script for you, but I can give you some general ideas on how I might structure such a script.

You could write a *find* function which scans for file names as you have outlined and lists those found files, say, into an array.  Then it's just a matter of iterating over the items in that array (something like *i=0*; *i+1*; *for i*; until i=89 (89 because 0 is 1)).  Each time you iterate out 90 files you *mv* them into a new folder.  You could put this iteration inside a different iteration which created folders until the array was exhausted.

I like both my Bash Cookbook and my Learning the Bash Shell book.

---

### Post by Froylan on 2013-05-19
I have no idea how to do that, but thanks, you gave me an idea so i'll just create a crazy combination, my best guess is that it is gonna be a nautilus script since I have experience with those

---

### Post by jamesisin on 2013-05-19
Bash is a very common Unix terminal and it's what Ubuntu uses by default.  So if you open a terminal you are using Bash.

Each of the terms in italics in my previous post are shell commands and you can learn about them using, for instance, *man find*.

Additionally there are many many many Bash tutorials and so forth on line.

Here is a script I use to batch rename files.  It uses *mv* (move) as a method to rename and could just as easily be used to move files into a different location (rather than merely move them to a different name).

[http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/](http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/)

---

### Post by Kopkins on 2013-05-20
Check out this bash guide (advanced bash scripting). It's extensive and beyond what you need, but I haven't read the whole thing and I can script well enough. It's definitely worth a look. [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Would all your pictures be in the same folder to start or would they be in different folders? 

You could probably use a simple `for' phrase. Note that the following should not be tried as is, you should learn what everything does yourself. I encourage you to learn and write your own script. What follows is a rough script that I have NOT tried or checked for code correctness. I do not recommend using it on real files. As it is, it wont run, because you should know what your doing to your files before you try out a script you know nothing about. And also, it wont do everything you asked. But it's a base for you to build on.


```

#!/bin/bash
i=1
echo "Enter Source Directory"
read s_dir               #note that if you have whitespace in your directories you will have to address that.
echo "Enter Destination Directory"
read d_dir               #it would work best to use the absolute path also.

#for files in s_dir move to d_dir and rename to HNI_00XX and restart if 99 files reached.

restart()
{
echo "Enter new destination for remaining files."
read d_dir2
if [ d_dir = d_dir2 ]
 then
  echo "Cannot move to same directory, enter new directory."
  restart
 else
  let d_dir=`echo $d_dir2`
  move
fi
}

move()
{
for file in $(ls s_dir)
 do 
  if [[ $i < 10 ]]
   then 
    mv ${s_dir}/$file $d_dir/HNI_000$i
    let i+=1
  elif [[ $i >= 10 ]]
   then 
    mv ${s_dir}/$file $d_dir/HNI_00$i
    let i+=1
  elif [[ $i = 99 ]]
    mv ${s_dir}/$file $d_dir/HNI_00$i
    let i=1
    echo "Directory reached 99 file cap."
    restart
  else
   exit
 fi
 echo "$file moved to ${d_dir}."
done
}

move

```

Good luck,

Kopkins

---

### Post by steeldriver on 2013-05-20
Why not use some modulo arithmetic to calculate the file and directory index? For example, if you count the files 0,1,.. i as you move them then

```
$((i%99))
```

will give you a file index (running from 0 to 98 - add 1 if you want to name the files 1 to 99) and 

```
$((i/99))
```

(integer division) will give you a number for the directory i.e. how many multiples of 99 you are at. You can use bash 'printf' to construct the actual names in the format you want e.g.

```
HNI_%04d
```

is a format string that says literal HNI_ followed by 4 decimal digits with zero-padding. Then you just need a single loop, something like

```
# define format strings for the directory and file names
dfmt="1%02dNIN03"
ffmt="HNI_%04d"

i=0; 
while read -rd $'\0' file; do 

  if [ $((i%99)) -eq 0 ]; then
    # generate a new sequential dir name in the given format 
    printf -v newdir "$dfmt" $((i/99))
    # test if the dir exists and create if not
    [ -d "$newdir" ] || mkdir "$newdir"
  fi

  # generate a new sequential file name in the given format
  printf -v newfile "$ffmt" $((i%99 + 1))
  # move the current file to the new dir/name and increment the counter
  echo mv "$file" "$newdir/$newfile" && ((++i))

done < <(find "$1" -type f -print0)
```

where "$1" is the directory you're trying to split, passed in as the first argument to the script - you should probably put some checking in to make sure a single argument is passed, and that it's a directory e.g.

```
if [ $# -ne 1 ] || [ ! -d "$1" ]; then
  echo "usage: $0 sourcedir"
  exit 1
fi

```

[I've left an 'echo' in - it won't actually move anything until you remove that]

---

### Post by prodigy_ on 2013-05-20
Python way (assuming that all files in the source directory are JPEG images):
```
#!/usr/bin/env python

import os

source_dir = '/path/to/source' # substitute actual path to source dir
target_dir = '/path/to/target' # substitute actual path to SD card

file_list = os.listdir(source_dir)

for i in xrange(len(file_list)//99 + 1):
    new_dir = ''.join([target_dir, '1', str(i).zfill(2), 'NIN03'])
    if not os.path.exists(new_dir):
        os.makedirs(new_dir)
    for j in xrange(1, 100):
        try:
            source_name = ''.join([source_dir, file_list[-1]])
            target_name = ''.join([new_dir, '/HNI_00', str(j).zfill(2), '.JPG'])
            if os.path.isfile(source_name):
                os.rename(source_name, target_name)
            file_list.pop()
        except IndexError:
            break
```

---

