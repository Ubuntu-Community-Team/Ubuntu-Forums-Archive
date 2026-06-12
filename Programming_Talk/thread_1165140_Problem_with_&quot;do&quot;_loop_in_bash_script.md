---
title: "Problem with &quot;do&quot; loop in bash script"
date: 2009-05-20
forum: Programming Talk
---

### Post by agkerr3 on 2009-05-20
I'm a bit new to bash scripting and have run into a problem with a "do" loop.  I have a script that allows users to restore archived projects.  The script asks for some basic input, uses those variables to find the project folder, and creates a ro symlink back to the archive.

The problem comes when users enter data that matches multiple archived directories  - it was causing the script to error out - so I am trying to put in a do loop that will create a separate link for each directory that it finds.  If $FULLNAME has multiple values, it attempts to make one link with the multiple values all mashed together, i.e. 
[INDENT]+ ln -s '/mnt/e1.0/archive/05000/05153.00 XXX College
05153.01 - XXX Addition' '/mnt/project2/jobs2/05000/A_05153.00 XXX College 05153.01 - XXX Addition'
[/INDENT]produces a link 
[INDENT]/mnt/project2/jobs2/05000/A_05153.00 Walsh College?05153.01 - Walsh Addition
[/INDENT]instead of two links like:
[INDENT]/mnt/project2/jobs2/05000/A_05153.00 Walsh College
/mnt/project2/jobs2/05000A_05153.01 - Walsh Addition
[/INDENT]I think this is a quoting issue but I can't suss out what I'm doing wrong.  Script follows:
[INDENT]#! /bin/bash

# a script for creating symlinks from archived projects

echo "Enter project directory (i.e. 03000)"
read -e YEAR
echo "Enter project number i.e.03155.01"
read -e PROJECT
sudo chmod 755 -R "/mnt/e1.0/archive/$YEAR/$PROJECT"*
sudo chown root:root -R "/mnt/e1.0/archive/$YEAR/$PROJECT"*

FULLNAME=`ls "/mnt/e1.0/archive/$YEAR" | grep $PROJECT`
for i in "$FULLNAME" 
do
ln -s "/mnt/e1.0/archive/$YEAR/$i" "/mnt/project2/jobs2/$YEAR/A_$i"
done
exit $?
[/INDENT]

---

### Post by odyniec on 2009-05-20
Instead of:
```
FULLNAME=`ls "/mnt/e1.0/archive/$YEAR" | grep $PROJECT`
for i in "$FULLNAME"
```
try this:
```
ls "/mnt/e1.0/archive/$YEAR" | grep $PROJECT | while read i
```

---

### Post by geirha on 2009-05-20
Why use ls at all?
```
for file in "/mnt/e1.0/archive/$YEAR/$PROJECT"*; do
  base=$(basename "$file")
  ln -vs "$file" "/mnt/project2/jobs2/$YEAR/A_$base"
done

```

---

### Post by agkerr3 on 2009-05-21
geirha-

That worked like a charm - I'm not sure how it works, but it does.

Looks like I've still got quite the learning curve in front of me.

THANKS!

---

### Post by geirha on 2009-05-21
In case you haven't already found it, the Advanced Bash-Scripting Guide at [http://tldp.org/guides.html](http://tldp.org/guides.html) is a great resource.

---

