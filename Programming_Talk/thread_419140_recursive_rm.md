---
title: "recursive rm"
date: 2007-04-22
forum: Programming Talk
---

### Post by mlissner on 2007-04-22
Amarok has been doing this annoying thing where it creates .directory files in all the directories that it makes. This creates a problem (of sorts) because later when I delete the music files through amarok, the .directory files stick around, making it hard to delete (or even find), the otherwise empty directories.

For truly empty directories, it's easy to delete them, I can do:```
find ~/Music -empty
```

However, since there's that stupid .directory file, I can't do that. So here's the question. How do I either delete the directories that only have the one file in them, or if that's too complicated, how do I delete all the .directory files (i.e. recursively rm them), so that I can find the resulting empty directories?

I know bash, some php, some perl and some C. Bash preferred, but the others OK too if people have ideas.

I've been working with a for loop, but it's just not working.

---

### Post by yabbadabbadont on 2007-04-22
```
find /path/to/basedir -type f -name ".directory" -print0 | xargs -0 rm -f
```
Just one of many different ways to find and remove the .directory files.

---

### Post by mlissner on 2007-04-22
> **yabbadabbadont said:**
> ```
find /path/to/basedir -type f -name ".directory" -print0 | xargs -0 rm -f
```
Just one of many different ways to find and remove the .directory files.

Ah ha! That's great, and infinitely easier than any solution I was working on.

So then, to remove the empty directories, I do this:```
find /path/to/basedir -empty | xargs -0 rm -f
```

Right?

Thanks for the quick response.

---

### Post by yabbadabbadont on 2007-04-22
EDIT: my initial reply was incorrect.

```
find /path/to/basedir -type d -empty -print0 | xargs -0 rmdir
```

---

### Post by yabbadabbadont on 2007-04-22
If you wanted to remove both empty **files and directories**, then I would do it like this:
```
find /path/to/basedir -empty -exec rm -rf {} \;
```
Be very careful on which directory trees you run that command as it is dangerous.

---

### Post by mlissner on 2007-04-22
It can't be that dangerous, right - Provided I don't run it as root?

I just ran the followng line a couple of times (to delete the directories that were empty, and then again to delete any newly emptied directories):```
find ~/Music -empty -print0 | xarg -0 rm -rf
```

This seemed to work fine. Your solution above is a bit too confusing for me. If you're feeling generous, may I ask what the curlies and the semi-colon do? 

Thanks - I'm learning a lot here today - this kind of thing is near impossible to learn by dabbling.

Also, just to illustrate how much time this is saving, here's the script I was working on:
```
#!/bin/bash
# Name: rmempty.sh
# Purpose: To remove empty files and directories from a path
# Author: Michael Lissner
# Date: 2-17-07

clear
echo 'Welcome to the rmempty.sh script.'
echo -n 'Please enter the directory you wish to search in: '
read searchdir

if [ -d $searchdir ]
then
  sleep 1
else
  echo rmempty.sh: invalid directory. Exiting.
  exit 1
fi

#Create a place to move things.
if [ -d ~/.Trash/rmempty ]
then
  echo -n '~/.Trash/rmempty exists. Do you wish to continue (y/n): '
  read yesno
  if [ $yesno = y ]
  then
    echo Ok. You should be ok. You will be prompted for confirmation before any files are overwritten.
    rm ~/.Trash/rmempty/rmempty.log
  else
    echo OK. Exiting.
    exit 1
  fi
else
  mkdir ~/.Trash/rmempty
fi

echo
echo Proceeding with checks...
sleep 1
echo
for i in `find $searchdir -empty | tr ' ' _`
do
 echo "`echo "$i" | tr _ ' '` contains:"
 ls -l "`echo "$i" | tr _ ' '`"
 echo -n "Move \"`echo "$i" | tr _ ' '`\" to ~/.Trash/rmempty? "
 read yesno
 if [ $yesno = y ]
 then
    echo `echo "$i" | tr _ ' '` >> ~/.Trash/rmempty/rmempty.log
    mv -i "`echo "$i" | tr _ ' '`" ~/.Trash/rmempty
    echo
 else
   sleep 1
 fi
done

echo The following files have been moved to ~/.Trash/rmempty
more ~/.Trash/rmempty/rmempty.log
echo
echo This log is located at ~/.Trash/rmempty/rmempty.log
echo You may want to run this script another few times in case new empty directories have been created.
echo 
echo Goodbye.

exit 0

```

---

