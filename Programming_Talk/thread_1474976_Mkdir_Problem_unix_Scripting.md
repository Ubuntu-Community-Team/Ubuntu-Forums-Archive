---
title: "Mkdir Problem unix Scripting"
date: 2010-05-06
forum: Programming Talk
---

### Post by hakermania on 2010-05-06
I have something very very simple! i want to make a new dir from the location where the Script prog was executed:
**#put the current dir with backslashes in case it has spaces, in a file**
[B]pwd | sed 's/ /\\ /g' > /home/$USER/currentpath
#e becomes currentpath:
e=`cat /home/$USER/currentpath`
mkdir $e/$USER
[/B]The line ** sed 's/ /\\ /g' **exists in case of a direvtory which has spaces, so it replaces every space with backslash-space. Then a variable 'e' takes the value of the current path. And then I make IN the current path a directory of the Current user.
This seems to have no errors and the line ** sed 's/ /\\ /g' **seems to work perfectly, and when I open the file 'currentpath' all seems to be OK, the script does not work when the direcory has spaces (e.g. /home/alex/my current projects/ is written in currentpath file as /home/alex/my\ current\ projects/ as it should be. the weird is that this does not work!)

thx in advance!

---

### Post by MadCow108 on 2010-05-06
does the parent folder exist?
if not you need to add -p flag to mkdir
(you could also just quote the path instead of that sed line)

---

### Post by sisco311 on 2010-05-06
Your script runs in the current working dir:
```
mkdir $USER
```
that's all you need.

In general, you have to use double quotes instead of the backslash:
```
path="/path/to/dir with spaces"
mkdir "$path"/$USER
```

---

### Post by hakermania on 2010-05-06
Ok, so, I have a variable 'x' wich has the current path (from the command pwd | sed 's/ /\\ /g' ). How to write the variable to a file WITH the quotes ("") ??
If I type
echo "$x" > blablabla
it shows just the value of x......

---

### Post by MadCow108 on 2010-05-06
escape the quotes:
echo "\"$PATH\""

I hope it makes sense in your context, it does not in what you have shown us, it seems you are just trying to work around problems caused your awkward approach

---

