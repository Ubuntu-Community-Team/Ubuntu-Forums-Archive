---
title: "Request for a Slightly Complex Bash Script"
date: 2011-01-26
forum: Programming Talk
---

### Post by OryulinDuos on 2011-01-26
All,

I am wondering if there is a way to write a numbered menu based bash script that options/variables are given from an external source/file.

Example:
#------------------------------------------------
#! /bin/bash

echo " Welcome to my Menu:

    1) Test1
    2) Test2
    3) Test3

Select an option:
"

read answer
clear
case "$answer" in
1) "Test1 Stuff";;
2) "Test2 Stuff";;
3) "Test3 Stuff";;
esac

#-----------------------------------------

Now what I am wanting to do is instead of manually specifying all this information as I did above, I am wanting to try and make a single external file from this script and call its contents to create the script...this next example I know for a fact wont work, but it gives you an idea of what I want to attempt to perform:


#-----------------------------------------

#! /bin/bash
TestList=`echo TestList.File`
OptionNumber=1

echo " Welcome to my Menu: "

#TestList variable is the contents of a file that contains Test1 Test2 Test3
for i in $TestList
do
    echo "$OptionNumber) $i"
    $OptionNumber) $TestList Work;; #Without actually running this information, just providing it as an option.
done

echo "Select an option: "

#-----------------------------------------

The reason I am wanting this is because a large amount of the functionality I have in most of my scripts are dynamic and regardless of what I add/remove from the menus, the base content stays the same. So I would like to maintain this one external file as opposed to maintaining 30-50 separate files...

Does this make sense? 

Is this even a valid question or is there a completely different/better way to do this?

My preference is to stay in bash, but if the other options are much more simple, then I'd gladly work on migration......

---

### Post by Smart Viking on 2011-01-26
You are wanting to to create a menu where the user have different options, and the different options do different things? That's entirely possible. I would go with python, but that's because I know it much better, bash and it's programs can do magical things.

EDIT: example in python

```

#!/usr/bin/env python
import os
print "----- omg, look, options -----"
print "1: omg, eat a cookie"
print "2: omg, not eat a cookie"
omgomg=raw_input("omg, eat a cookie?")
if omgomg == "1":
    os.system("eat cookie")
elif omgomg == "2":
    os.system("not eat cookie")
else:
    print "omg, not valid"

```

---

### Post by Darkness Des on 2011-01-26
This is entirely possible to do in Bash without too much effort. What I would do is this:

```

#!/bin/bash
# file 1, my.sh

# run script containing menu system
~/menus.sh
read choice

if [ "$choice" == "1" ]; then
  echo 'Hi mom!'
elif [ "$choice" == "2" ]; then
  echo 'Hi Des!'
fi

```

That is the first file. The second file could be:

```

#!/bin/bash
# file 2, the menu system container
echo "1) Say hi to your mother"
echo "2) Say hi to me"

```

Except changed to fit your purposes. Honestly, I had never thought of that before, but it is a good idea.

**EDIT:** I managed to forget about your for loop, but I believe that if you execute a script inside of another script, variables are stored. So, you should be good. Tell me if there are any more issues.

---

### Post by asmoore82 on 2011-01-26
Only if X is available in the production environment,
I would highly recommend using the zenity package ...

say you have a file "options.txt" like:
```
$ cat options.txt
brainstorm
design
build
test
world domination
```

then within your script, you can:
```
choice="$(
    cat options.txt |
    zenity --list --column "Options"
)"
echo "User choice: $choice"
#case "$choice" in ...
#...
```

The catch is that the matches in your case statement must match the options file exactly.
So, numbering the choices might not work out well, every time you reorder the menu,
you'd have to edit your case statement which would defeat the purpose of separating it out.

As is, though, without numbering, you could re-arrange the options freely as much as you want,
the only time you'd need to edit the case statement is to add a completely new option.

---

