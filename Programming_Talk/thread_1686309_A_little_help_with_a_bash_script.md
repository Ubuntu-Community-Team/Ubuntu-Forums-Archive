---
title: "A little help with a bash script"
date: 2011-02-12
forum: Programming Talk
---

### Post by CaptainMark on 2011-02-12
Im just trying to improve my bash skills and Im playing around with scripts at the moment but ive come a bit stuck, what im making is a modest script that backs up the folders in home/mark/* to /media/passport/*, ive made an entry for each of the main folders so i can easily locate errors in copying, each one looks like this ```
echo 'Copying Music'
cp -ru ~/Music/* /media/passport/Music
echo 'Done' && aplay -q ~/Documents/sounds/zelda/stereo/emptytrash.wav

```Which copies the folder and plays a quick noise to confirm, the thing is the downloads folder is often empty and that means i get error messages, which i want to work away from and have my own error handling deal with it.

The bit i need help with is constructing an if/else statement, im having trouble understanding the syntax with my limited porgramming knowledge. This is the general theory i need ```
if Downloads == empty
    echo 'downloads empty'
else
   copy downloads to passport
play confirm sound
```This is the best i could come up with after some googling```
echo 'Copying Downloads'
if [(ls -1R ~/Downloads | wc -l )-ge 2]; then
    echo 'Download Folder Empty'
else
    cp -ru ~/Downloads/* /media/passport/Downloads
fi
``` I assumed this would work as in a terminal the command (ls -1R ~/Downloads | wc -l ) gives an output of 1 for an empty folder.
Any help would be much appreciated, oh and for the sake of learning, an explaination to any code would be even better :)

---

### Post by sisco311 on 2011-02-12
[http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)

EDIT: 

[s]EDIT2:
Or you can redirect cp's error message to /dev/null and print your own one:
```
cp -ru source dest 2> /dev/null || echo "error" >&2
```[/s]

---

### Post by Rany Albeg on 2011-02-12
Hello.
First of all you missed the space after '[' and before ']'.
Second, I suggest you to use [[ instead of [ if you are writing for Bash.
No word splitting or glob expansion will be done for [[ which makes it less error prone and much easier to use.
With [[ you can also use the =~ operator to check for regular expressions, it also supports '<', '>', '&&', '||' operators and you can use '=~' for regular expression comparison.

Don't use ls to check whether a directory is empty.
Instead, use globs.
In your case use a basic * to assign PWD's entries into an array and check if the size of the array is not zero.
```
array=(*) # assign PWD's entries.
if (( ${#array[@]} )); then
   # Code in case the directory is not emtpy
else
   # Code in case the directory is emtpy
fi
```

Notice that I used (( and not [[ in this case and that is because I'm checking arithmetic values. the ${#array[@]} evaluates to the number of elements in the array, so I also recommend you to use (( when you use arithmetic and [[ otherwise.

You'll also want to use shopt with nullglob and dotglob options **before** the 'if' statment.
use ```
shopt -s dotglob nullglob
``` to set them, and ```
shopt -u dotglob nullglob
``` to unset after you are done.
**nullglob** - In case that the directory is emtpy, the glob * will be expanded to * which will make it fail. You don't want the array to contain a single *.
**dotglob** - If set, Bash includes filenames beginning with a . (dot) in the results of pathname expansion.

---

### Post by CaptainMark on 2011-02-13
Wow, that seems complex, i appreciate the help. I managed to get this to work, its shorter so i understood it a lot more, ```
echo 'Copying Downloads'
if [ -a ~/Downloads/* ]; then
    cp -ru ~/Downloads/* /media/passport/Downloads;
else
    echo 'Downloads Folder Empty';
fi
```

---

### Post by Rany Albeg on 2011-02-13
It is shorter but not necessarily better.
If you'll check ''man test'' you'll see:
> 
 EXPRESSION1 -a EXPRESSION2
              both EXPRESSION1 and EXPRESSION2 are true

Your solution seems to work but it doesn't look good.
Maybe someone more experienced than me will also tell you why it is also bad and not just ugly.

I suggest you to use my solution since in my answer I'm relying on the knowledge of people that are far more experienced than me with the Bash shell.

Don't search for shorter ways to do stuff, search for the best way even if it is longer.

Have a nice day.

---

### Post by oldfred on 2011-02-13
Most of us use rsync as it only copies new/changed files.

Bash script for backup with rsync
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

### Post by CaptainMark on 2011-02-14
It works with -e or -a for this instance, i dont understand how this ```
${#array[@]}
``` equates to the length of the array, would you mind explaining this,

---

### Post by Rany Albeg on 2011-02-14
This is just a syntax.

```
echo "${array[@]}"
``` will output all array elements properly quoted, and ```
echo "${#array[@]}"
``` will output the number of elements.

You might want to check the difference between ${array[@]} and ${array[*]}.

---

