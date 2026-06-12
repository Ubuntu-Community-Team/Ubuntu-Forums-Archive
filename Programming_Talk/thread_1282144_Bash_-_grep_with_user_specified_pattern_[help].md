---
title: "Bash - grep with user specified pattern [help]"
date: 2009-10-04
forum: Programming Talk
---

### Post by ApEkV2 on 2009-10-04
Hey there. I'm having trouble getting this script to work right.
I want to input a pattern for grep, 'mtu' for instance, but having $zSearch instead of 'mtu' doesn't work.

Here is the script.
```
 #!/bin/bash

read -p "Enter the target directory to search:" zTarget
read -p "Enter the search option ['mtu']:" zSearch
read -p "Would you like to start the script [Y/N]:" zStart
if [ -e $zStart ] || [[ $zStart == [nN]* ]]; then
 echo "Exit 0"
 exit 0; fi
find $zTarget -type f -name '*.c' | while read zIn; do
	zOut=`grep -n -H [color=red] $zSearch [/color] $zIn`  [color=blue] #  This is the problem [/color]
	echo "$zOut"; done

 [color=blue] #  zName=`grep -n -H $zSearch $zFirst` doesn't work? [/color] 
```
Why doesn't the user variable work? Is there another way to input a pattern to grep?
I'm trying to search a directory full of source code for specific functions.
Any help would be appreciated!

---

### Post by A_Fiachra on 2009-10-04
Why don't you just do:

```

find . -name "*.c" | xargs grep -n -H <string>

```

Aside from that, do you mean:

```

if [ -e $zStart ] && [[ $zStart == [nN]* ]]; then

```

??

---

### Post by ApEkV2 on 2009-10-04
Well I will have to try that. Thanks

And for this.
```
 if [ -e $zStart ] && [[ $zStart == [nN]* ]]; then 
```

If zStart has a length of zero [color=red] or [/color] the letter n or N, then exit 0.
The way you have it is if it's empty and the letter n or N?
Oh and it should be [ -z $zStart ] not -e. My b I messed that up.

---

