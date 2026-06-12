---
title: "Bash issues - Set variable from user imput and use it later one"
date: 2009-08-25
forum: Programming Talk
---

### Post by pi4r0n on 2009-08-25
[FONT=Arial][SIZE=1]Hello all

I got small issue with one of my scripts and can not figure out why its not working :(

So the script should ask user to enter value and then cd to folder update svn and then  run script ./prepare_release with the value that was entered before but for some reason it does not do that and I am not sure why :(

Could someone point me to the right direction please :) and say what I am doing wrong :confused:
[/SIZE][/FONT][FONT=Arial][SIZE=1] 
```
[SIZE=2]#!/bin/bash
#
# Script:      release
# Description: Shell Script To Do Release to server
#

echo "This Script Will Do Release to server";

while read inputline
do
number="$inputline"
cd ~/1.0.4
svn update
cd release/
./prepare_release $number
cd
done[/SIZE]  
```[/SIZE][/FONT]   [FONT=Arial][SIZE=2][SIZE=1]

Cheers

pi4r0n[/SIZE]  
[/SIZE][/FONT]

---

### Post by Linteg on 2009-08-25
> **pi4r0n said:**
> So the script should ask user to enter value and then cd to folder update svn and then  run script ./prepare_release with the value that was entered before but for some reason it does not do that and I am not sure why :(

Could someone point me to the right direction please :) and say what I am doing wrong :confused:

Cheers

pi4r0n

I'm no master when it comes to bash scripting but I don't think you need the while loop for reading input. Take a look at the following example...

```
#!/bin/bash
# Creates a folder with an empty file
echo -n "Folder: "
read folder
echo -n "File: "
read file
mkdir $folder
touch $folder/$file
echo "Created folder \"$folder\" and file \"$file\""

```

---

### Post by DaithiF on 2009-08-25
[FONT=monospace]Hi,
no need for a loop,
no need to use 2 variables, just 1 will do
probably good idea to provide a prompt when asking for input

so, something like below.

[/FONT]```
#!/bin/bash
#
# Script:      release
# Description: Shell Script To Do Release to server
#

echo "This Script Will Do Release to server";

read -p "Enter Release Number: " number
cd ~/1.0.4
svn update
cd release/
./prepare_release $number
cd

```[FONT=monospace]
[/FONT]

---

